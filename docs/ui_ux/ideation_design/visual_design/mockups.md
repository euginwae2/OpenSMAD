Based on the provided resource documents (`information_architecture.md`, `user_journey_mapping.md`, `user_stories.md`, and `affinity_mapping.md`), here is a structured high-fidelity mockup specification for the OpenSMAD platform.

---

### **1. Platform Goals & Context**

- **Purpose:** To create an integrated, open-core software ecosystem that democratizes and streamlines the end-to-end space mission design process.
- **Objectives:** Reduce cost, time, and risk; accelerate innovation and collaboration; establish OpenSMAD as an industry-standard platform.
- **Key Constraints:** Must support cloud and on-premises deployments; low/no cost core; ITAR/EAR compliance; auditable decision trail; users have basic engineering knowledge.

### **2. Page Inventory**

- **Primary Screens:**
  1. **Landing / Marketing Homepage**
  2. **User Login / Sign-Up Page**
  3. **Main Application Dashboard (User's Home)**
  4. **Project Workspace** (within Mission Designer)
  5. **Trade Study Manager** (Scenario Configurator, Batch Job Queue, Comparative Visualizer)
  6. **Library & Marketplace** (Model Library, Marketplace browsing)
  7. **Collaborate Section** (Project Sharing, Review Workspaces: SRR, PDR, CDR)
  8. **Reports & Docs Hub** (Report Generator, Template Gallery, Export Hub)
  9. **Learn Portal** (Tutorials, Example Missions, API Docs)
  10. **User Account & Admin** (Profile, Team Management, Billing, System Settings)
- **Modal Dialogs & Key Sub-views:**
  - **Onboarding Wizard** (post-sign-up)
  - **Data Import Wizard**
  - **Sharing & Access Modal**
  - **Report Configuration & Export Modal**
  - **Batch Simulation Launch Confirmation**

### **3. Mockup Specifications**

_(Note: Specific values for Typography, Color, and Spacing are TBD and must be defined in a finalized Style Guide.)_

- **General Layout Structure:**

  - **Header:** Persistent top bar with: Platform Logo, Primary Navigation (Dashboard, Mission Designer, Library, Collaborate, Reports, Learn, User Account), Notifications icon, User avatar/menu.
  - **Body:** Dynamic content area. Uses a responsive grid system (e.g., 12-column). Background: Neutral Light (TBD).
  - **Footer:** Minimal footer with copyright, privacy/terms links, status indicator (e.g., "Cloud Synced" or "Offline Mode").

- **Page-Specific Specifications:**

  1.  **Main Application Dashboard:**

      - **Layout:** Modular grid of cards/widgets.
      - **Content Widgets:** "Recent Projects" (list with thumbnails), "Team Activity Feed" (scrollable), "Quick-Access Templates" (grid of icons/titles), "Getting Started" guide card for new users.
      - **Styling:** Cards have subtle shadow, consistent corner radius. Headers within cards use H3 typography.

  2.  **Project Workspace:**

      - **Layout:** Left Sidebar (sub-navigation: Requirements Manager, Subsystem Modules list). Main Canvas (Integrated Design Dashboard with parameter tiles and central visualization pane).
      - **Integrated Design Dashboard:** Key parameters (ΔV, mass, power, cost, reliability) displayed as interconnected, editable tiles. Central area for orbit diagram or system block diagram.
      - **Styling:** Parameter tiles have a distinct border when editable. Visualization pane has a clean, dark background (TBD) for contrast with orbital lines/data.

  3.  **Trade Study Manager – Comparative Visualizer:**

      - **Layout:** Left panel: Scenario list with key outcome metrics. Main panel: Large, multi-axis chart (e.g., Pareto front) and data table beneath.
      - **Styling:** Chart uses a clear, accessible qualitative color palette (TBD Secondary colors) for different scenarios. Interactive chart elements have tooltips on hover.

  4.  **Collaborate – Review Workspace:**
      - **Layout:** Central document/viewer (e.g., mission dashboard in read-only mode). Right Sidebar: "Comment Panel" with threaded comments and annotation tools.
      - **Styling:** Review interface has a distinct, slightly muted color treatment to indicate read-only/comment mode. Annotation tools (highlight, pin) are clearly visible.

### **4. Interactive Elements (Static Representation)**

- **Buttons:**
  - **Primary:** [TBD Fill Color], medium corner radius, bold label. **Hover:** Darker shade. **Active:** Insetshadow. **Disabled:** 40% opacity.
- **Text Fields:**
  - **Default:** Light border. **Focus:** Border color changes to Primary color (TBD). **Error:** Border and helper text use Accent Error color (TBD Red).
- **Messages:**
  - **Success Toast:** Green accent background (TBD), checkmark icon, positioned top-right.
  - **Error Banner:** Red accent background (TBD), alert icon, positioned below header with clear dismissal (X).

### **5. Navigation & Flow**

- **Primary Flow:** Consistent top navigation bar allows direct jump between major sections.
- **Secondary/Contextual Navigation:** Left sidebar appears in context-heavy areas (Mission Designer, Collaborate) for sub-section navigation.
- **Breadcrumbs:** Appears below header in detailed workspaces (e.g., _Mission Designer > Project: Artemis Lite > Power Subsystem_).
- **Modal Flows:** Modals (e.g., Share, Export) are centered, dim background, with clear primary actions on the right and secondary dismissal on the left.

### **6. Accessibility Considerations**

- **Contrast:** All text and interactive elements must meet WCAG 2.1 AA contrast ratios (minimum 4.5:1). This is a constraint.
- **Typography:** Font sizes must be legible. Hierarchy must be programmatically defined (H1, H2, etc.) for screen readers.
- **Keyboard Navigation:** Full keyboard navigability required. Focus states must be visually distinct (e.g., blue outline on focused button).
- **Interactive Elements:** Form inputs must have associated labels. Icons must have tooltips or `aria-labels`.
- **TBD:** Specific contrast ratios for graphs and data visualizations.

### **7. Open Questions / TBD Areas**

- Finalized color palette (HEX/RGB values for Primary, Secondary, Accent, Neutral scales).
- Finalized typography system (font families, precise scale for H1-H6, body, caption).
- Standardized spacing scale (e.g., 8pt grid) and exact values for margins/padding.
- Detailed specifications for complex data visualization components (orbit viewer, 3D models, advanced charts).
- Specific styling for all iconography.
- Mobile and tablet responsive breakpoints and behavior.
- Dark mode specification.
