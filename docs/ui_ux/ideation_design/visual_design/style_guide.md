Based on the provided resource documents (`information_architecture.md`, `user_journey_mapping.md`, `user_stories.md`, and `affinity_mapping.md`), here is a structured style guide for the OpenSMAD platform.

---

### **1. Brand Identity Overview**

- **Mission:** To democratize and streamline the end-to-end space mission design process through an integrated, open-core software ecosystem.
- **Values:** Collaboration, innovation, accessibility, transparency, and rigor.
- **Tone of Voice:** Professional yet approachable; clear, technical but not overly academic; encouraging and empowering.
- **Constraints:** Must appeal to diverse user groups (startups, academia, enterprise) and support both cloud and air-gapped deployments. Visuals must accommodate complex engineering data without clutter.

### **2. Typography**

- **Primary Typeface:** TBD (Should be a clean, highly readable sans-serif with excellent screen readability and professional tone).
- **Secondary Typeface:** TBD (A monospace or technical sans-serif for code, data, and technical labels).
- **Hierarchy & Scale:**
  - H1: TBD (Page titles, major sections)
  - H2: TBD (Section headings)
  - H3: TBD (Subsection headings)
  - Body: TBD (Primary content)
  - Caption/Small: TBD (Labels, helper text)
- **Usage Guidelines:** Ensure sufficient line height and contrast for readability. Support screen readers with semantic heading structure. Avoid more than 3 font weights per page.

### **3. Color Palette**

- **Primary Colors:** TBD (Should convey trust, innovation, and professionalism. Likely a core blue or deep teal).
- **Secondary Colors:** TBD (A supportive palette for data visualization and UI differentiation).
- **Accent Colors:** TBD (For highlights, alerts, and interactive elements).
- **Neutrals:** TBD (For backgrounds, text, borders).
- **Usage Rules:**
  - Primary color for main CTAs and key headers.
  - Secondary palette for charts, graphs, and categorical differentiation.
  - Accent color for warnings, success states, and interactive feedback.
  - Ensure all text meets WCAG 2.1 AA contrast ratios (minimum 4.5:1).

### **4. Imagery & Iconography**

- **Image Style:** Technical but not intimidating; use clean diagrams, abstract data visualizations, and professional photography of hardware/teams where appropriate. Avoid overly casual or cartoonish illustrations.
- **Iconography:** Simple, linear, consistent stroke weight (TBD). Use a unified icon set (e.g., custom or established set like Material Icons) for UI actions and categories.
- **Tone:** Professional, clear, and inclusive. Imagery should reflect global collaboration and technological precision.

### **5. Layout & Spacing**

- **Grid System:** Responsive grid (e.g., 12-column) to accommodate complex dashboards and data panels.
- **Margins/Padding:** Consistent spacing scale (e.g., base unit of 8px) for alignment and visual rhythm.
- **Alignment:** Left-aligned text for readability; center alignment reserved for hero elements or confirmations.
- **Balance:** Use whitespace actively to separate complex information and reduce cognitive load.

### **6. Interactive Elements**

- **Buttons:**
  - Primary: Filled, using primary color.
  - Secondary: Outlined or ghost style.
  - Sizes: TBD (Large, medium, small for different contexts).
- **Links:** Underlined or distinctly colored text; clear hover state.
- **Forms:** Clear labels, consistent field heights, and obvious validation states (error, success).
- **Hover/Focus States:** Visible change in color, brightness, or underline. Focus indicators must be keyboard-accessible (visible outline).
- **Accessibility:** All interactive elements must be keyboard-navigable. Ensure color is not the only indicator of state (use icons, text labels).

### **7. Voice & Tone**

- **Voice:** Authoritative yet supportive; expert but not condescending.
- **Tone Examples:**
  - **Educational:** “Let’s walk through your first trade study.”
  - **Professional:** “Your compliance matrix has been generated per NASA STD-7009.”
  - **Error:** “We couldn’t import that file. Please check the CSV format and try again.”
- **Guideline:** Use active voice, avoid jargon unless defined, and provide clear next steps.

### **8. Do’s and Don’ts**

- **Do’s:**
  - Use the spacing scale consistently.
  - Prioritize clarity over visual flair in data-heavy views.
  - Test color contrast for accessibility.
  - Use icons to supplement text labels.
  - Maintain a consistent header/footer across all pages.
- **Don’ts:**
  - Don’t use more than 2 typefaces in one view.
  - Don’t rely solely on color to convey meaning (e.g., “red = bad”).
  - Don’t overcrowd interfaces; use progressive disclosure.
  - Don’t use low-resolution images or inconsistent icon styles.

### **9. Open Questions / TBD Areas**

- Specific primary/secondary typefaces.
- Exact HEX/RGB values for color palette.
- Detailed icon set selection and custom illustration style.
- Specific breakpoints for responsive grid.
- Detailed design system components (tables, modals, tooltips, etc.).
- Animation/motion guidelines for transitions and loading states.
- Logo usage, sizing, and clearspace rules.
