Based on the provided resource documents (`market_analysis.md`, `README.md`, and `business_Objectives.md`), here is the simulated ethnographic study for the OpenSMAD platform.

**Product/Service:** OpenSMAD (Open Space Mission Analysis and Design) – an integrated, open-core software ecosystem for space mission design.
**Industry/Domain:** Aerospace & Defense / Space Technology
**Target Users:** Space mission architects, engineers, and educators.
**Environment:** The primary workplace environments: startup open-plan offices, university research labs, and corporate engineering centers.
**Research Goal:** To understand the unspoken cultural norms, collaborative rituals, and environmental constraints that shape how mission design work is actually done, revealing opportunities for a new platform to fit into—and improve—these native workflows.

---

### **Environment Description**

The study took place across three primary sites over two weeks. The **startup environment** was a converted warehouse space: open-plan, whiteboards covered in constellation diagrams and cost equations, multiple monitors per engineer, and a constant background hum of casual discussion. The **academic lab** was a mix of dedicated offices for professors and a shared graduate student workspace with powerful desktops; walls were lined with posters from past conferences and mission patches. The **corporate center** featured cubicles and dedicated meeting rooms with strict security badge access; the atmosphere was quieter, more formal, with processes visibly documented and adhered to.

### **Observed Behaviors**

- **"The War Room" Ritual:** At the startup, major trade studies were conducted in impromptu meetings around a large monitor. One engineer would drive their specialized tool (e.g., Python script for orbits), while others would manually note implications in their respective domains (power, comms) on separate laptops or notebooks. The synthesis was verbal and manual.
- **The "Model Handoff" Ceremony:** In the corporate setting, a clear, sequential workflow was observed. The orbit team would "finalize" and email a data package to the propulsion team, who would then begin their work. This created noticeable waiting periods and a reluctance to make changes once a package was "sent."
- **Shadow Systems & Tribal Knowledge:** Across all sites, a heavy reliance on personal or locally maintained Excel "master sheets" was observed. These sheets acted as the de facto system integrator, pulling numbers from various official tools. Their structure and formulas were often understood only by one or two senior team members.
- **Tool Avoidance for Collaboration:** Academics and startup engineers were observed preferring to share simplified conceptual diagrams (via PowerPoint or Miro) in early-stage collaborations, even when more detailed models existed, because they lacked confidence in partners' ability to open or run their specialized tools.

### **Contexts & Constraints**

- **Cultural Constraint - "Don't Break the Chain":** In enterprise and government-adjacent work, there is a deep cultural imperative for an auditable, blame-averse decision trail. Tools that feel too "agile" or collaborative can be perceived as lacking rigor.
- **Organizational Constraint - The IT Wall:** In the corporate and university environments, installing new software, especially cloud-based, requires lengthy security and compatibility reviews conducted by a separate IT department, creating a significant adoption friction.
- **Physical Constraint - Data Sovereignty:** Observed specifically in government work, designs cannot leave a physical, air-gapped network. This completely negates the value proposition of most modern SaaS collaboration tools.
- **Social Constraint - Expertise Silos:** Organizational structures reinforce discipline silos (e.g., GNC, Thermal, Structures). Their tools and data formats are optimized for depth within the silo, not for cross-silo integration, which is often managed by systems engineers through manual labor.

### **Pain Points & Unmet Needs**

- **The Integration Tax:** Countless hours observed were spent not on design innovation, but on the manual "glue work" of copying, reformatting, and reconciling data between tools. This was a universal, accepted, yet deeply resented tax on productivity.
- **Loss of Context in Handoffs:** When a model or dataset is emailed as a static file, the rich context of assumptions, constraints, and trade-offs made by the originating engineer is lost. The receiving engineer works from a "black box."
- **Inaccessible Fidelity:** High-fidelity, high-cost tools are available but underutilized because licenses are limited or they are too complex for quick exploration. Engineers instead use simpler, less accurate tools for most tasks, reserving the "good tool" for final validation, sometimes discovering issues late.
- **No "Single Source of Truth" for the Living Design:** The mission concept is a living entity that evolves, but its current state is fragmented across emails, slide decks, Excel files, and specialized tools. There is no canonical, always-up-to-date representation that all stakeholders can reference.

### **Motivations & Drivers**

- **Motivation for Prestige & Recognition:** In academia and advanced design groups, there is a strong drive to use and create tools that are seen as "cutting-edge" by peers, sometimes at the expense of practicality or usability for less expert team members.
- **Driver: Risk Aversion as Career Preservation:** For individuals in large organizations, using the approved, expensive vendor tool is a safe career choice, even if it's inefficient. Proposing a new tool carries personal risk if anything goes wrong.
- **Driver: The "Demo-able" Artifact:** For startups, the primary driver is creating a compelling, visual, and interactive simulation or dashboard that can wow investors and customers in a meeting—polish and narrative often trump underlying model accuracy at early stages.
- **Motivation: Legacy & Mentorship:** Senior engineers are motivated to choose tools and processes that ensure their hard-won knowledge (e.g., "lessons learned" from past mission failures) is encoded and passed on to junior engineers, not lost in transient scripts.

### **Ethnographic Insights**

The core challenge is not a lack of tools, but a **crisis of integration and context**. The space mission design process is inherently collaborative and interdisciplinary, but the tools and organizational cultures are siloed and linear. Users are forced to become human APIs, manually translating data between domains. This creates a hidden "integration tax," obscures the digital thread, and slows innovation.

A successful platform cannot be just another siloed tool. It must act as a **collaborative workspace and integration layer** that respects existing cultural constraints (security, auditability) while enabling new, more fluid workflows. It must make the "living design" visible and interactive for all stakeholders, from the student in a lab to the program manager in a review, reducing the reliance on tribal knowledge and manual glue work. The key adoption strategy is not to replace all tools immediately, but to first solve the painful integration problem, becoming the indispensable "hub" where the fragmented "spokes" of the design process connect.
