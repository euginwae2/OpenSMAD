Based on the provided resource documents, here is the database schema design for the OpenSMAD platform.

### **1. Database Goals & Constraints**

- **Business Goals:** Support an integrated mission design platform with user collaboration, trade studies, and a model library/marketplace.
- **Technical Requirements:**
  - **Scalability:** Handle large datasets from batch trade studies (1000s of scenarios) and real-time collaborative data.
  - **Performance:** Support complex queries for the integrated dashboard and visualizations with sub-second latency.
  - **Compliance:** **ITAR/EAR** regulations require strict access control, data isolation, and comprehensive audit trails.
  - **Data Integrity:** Maintain a consistent "digital thread" linking requirements, design parameters, and outcomes.
  - **Flexibility:** Support extensible data models for various mission subsystems and plugin integrations.

### **2. Entity Identification**

| Entity                | Description                                                                    |
| :-------------------- | :----------------------------------------------------------------------------- |
| **users**             | Platform users (Agile Innovators, Educators, Enterprise users).                |
| **organizations**     | Companies, universities, or agencies. Contains teams.                          |
| **teams**             | Groups within an organization working on projects.                             |
| **projects**          | A mission design project (e.g., "Artemis Lite"). The primary workspace.        |
| **project_members**   | Junction table for user access to projects with roles (Owner, Editor, Viewer). |
| **requirements**      | System/mission requirements linked to a project.                               |
| **subsystem_modules** | Logical modules within a project (Orbit, Power, Propulsion, Cost).             |
| **parameters**        | Key mission parameters (ΔV, mass, cost) belonging to a module. Can be linked.  |
| **trade_studies**     | Definition of a batch analysis (variables, ranges).                            |
| **scenarios**         | Individual design permutations within a trade study.                           |
| **scenario_results**  | Computed output data for a specific scenario.                                  |
| **library_items**     | Base entity for models, templates, and components in the Library/Marketplace.  |
| **plugins**           | Extensions/add-ons with metadata and versioning.                               |
| **reports**           | Generated documents (compliance matrices, summaries).                          |
| **audit_logs**        | Immutable record of all user and system actions for compliance.                |
| **comments**          | Threaded feedback and annotations on projects or reviews.                      |

### **3. Attributes & Data Types (Key Examples)**

- **users:** `id` (UUID, PK), `email`, `hashed_password`, `name`, `role`, `organization_id` (FK), `created_at`
- **organizations:** `id` (UUID, PK), `name`, `tier` (Free, Pro, Enterprise), `itaf_restricted` (boolean)
- **projects:** `id` (UUID, PK), `name`, `description`, `team_id` (FK), `created_by` (FK to users), `created_at`, `updated_at`, `template_id` (FK to library_items, nullable)
- **parameters:** `id` (UUID, PK), `module_id` (FK), `name`, `value` (JSONB to store numeric values, units, uncertainties), `data_type`, `is_derived` (boolean), `formula` (text, for derived params), `depends_on` (self-ref FK for parameter links)
- **trade_studies:** `id` (UUID, PK), `project_id` (FK), `name`, `status` (Queued, Running, Complete), `config` (JSONB for variable definitions)
- **scenarios:** `id` (UUID, PK), `trade_study_id` (FK), `input_hash` (hash of inputs for deduplication), `status`, `created_at`
- **scenario_results:** `id` (UUID, PK), `scenario_id` (FK), `outputs` (JSONB storing all result metrics), `computed_at`
- **library_items:** `id` (UUID, PK), `name`, `type` (Orbit Model, Component Spec, Mission Template), `data` (JSONB or reference to blob storage), `version`, `visibility` (Public, Organization, Private), `vendor_id` (FK to organizations, for marketplace)
- **audit_logs:** `id` (UUID, PK), `user_id` (FK, nullable), `action`, `resource_type`, `resource_id`, `changes` (JSONB diff), `ip_address`, `timestamp`

### **4. Relationships**

- **One-to-Many:**
  - `organization` → `teams`, `users`, `library_items` (as vendor)
  - `team` → `projects`
  - `project` → `requirements`, `subsystem_modules`, `trade_studies`, `comments`
  - `subsystem_module` → `parameters`
  - `trade_study` → `scenarios`
  - `scenario` → `scenario_results`
- **Many-to-Many:**
  - `users` ↔ `projects` via `project_members` (with `role` attribute)
  - `projects` ↔ `library_items` (for "used components") via a junction table `project_components`
- **Self-Referencing:**
  - `parameters.depends_on` → `parameters.id` (for derived parameter graph)
  - `comments.parent_comment_id` → `comments.id` (for threading)
- **Cascading Rules:** Deletes cascade from parent to child (e.g., deleting a project deletes its requirements). For `project_members`, delete on cascade. **Critical Exception:** `audit_logs` must NEVER be cascaded; all deletions are soft/logical.

### **5. Normalization & Denormalization Strategy**

- **Normalization (to 3NF):** Core entities (`users`, `projects`, `parameters`) are fully normalized to eliminate redundancy and update anomalies. This ensures data integrity for the "digital thread."
- **Strategic Denormalization:**
  - **`scenario_results.outputs` (JSONB):** Stores all output metrics for a scenario in one queryable field. Trade-off: query complexity vs. read performance and schema flexibility for varied result types.
  - **`projects.updated_at` (maintained by triggers):** Avoids expensive `MAX()` queries to find recently updated projects.
  - **Materialized Views:** For the **Integrated Dashboard**, create a materialized view that pre-joins key `parameters` with their `subsystem_modules` and `projects` for fast, consistent reads. Refreshed on parameter change.

### **6. Indexes & Query Optimization**

- **Foreign Keys:** All FK columns indexed.
- **Composite Indexes:**
  - `projects(team_id, created_at DESC)` for team dashboards.
  - `scenarios(trade_study_id, status)` for monitoring batch jobs.
  - `parameters(module_id, name)` for quick parameter lookups.
- **JSONB Indexes:** GIN indexes on `scenario_results.outputs` for efficient filtering on common result fields (e.g., `total_cost`).
- **Query Strategy:** Use read replicas for analytical queries (trade study analysis). The dashboard materialized view serves primary UI queries.

### **7. Scalability & Future-Proofing**

- **Partitioning:** `audit_logs` and `scenario_results` partitioned by `created_at` (monthly) to manage size.
- **Sharding Strategy (Future):** If needed, shard by `organization_id` to isolate tenant data and scale horizontally. Aligns with compliance needs.
- **Schema Evolution:** Use `JSONB` columns (`parameters.value`, `config`, `outputs`) for flexible, additive changes. Employ structured migration patterns (e.g., expand/contract) to minimize downtime.

### **8. Compliance & Security**

- **Encryption:** Data encrypted at rest (TDE) and in transit (TLS). `JSONB` fields containing sensitive design values use application-level encryption.
- **Access Control:** Row-Level Security (RLS) in PostgreSQL on `projects`, `library_items` to enforce `organization` and `team` boundaries at the database layer.
- **Audit Trails:** `audit_logs` table is immutable (append-only). All DML on core tables (`projects`, `parameters`, `requirements`) triggers an audit log entry.
- **Data Residency:** Schema supports an `organization.data_region` field to control geographic storage for ITAR compliance.

### **9. Open Questions / TBD Areas**

- **Blob Storage Integration:** Exact schema for linking `library_items.data` to large files in S3/MinIO (path, version, checksum).
- **Real-Time Collaboration Data:** How are concurrent parameter edits (operational transforms) persisted? Requires an additional `parameter_versions` or `operations` table.
- **Plugin Data Storage:** Where do plugins store their proprietary configuration and results? Dedicated `plugin_data` table with `plugin_id` and `JSONB`?
- **Detailed Data Retention Policy:** How long are `scenario_results` kept? What is the archival strategy?
- **Full-Text Search Requirements:** What fields in `library_items` require search (name, description, metadata)? Need for dedicated search index (Elasticsearch).
