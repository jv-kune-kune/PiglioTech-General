
# Issue Template & Workflow Guide

<!--
This README explains how to use our issue template and outlines the workflow, 
including required fields, automations, and best practices.
-->

<details>
<summary>Table of Contents</summary>

1. [Introduction](#introduction)
2. [Workflow Overview](#workflow-overview)
3. [Mandatory Fields](#mandatory-fields)
   - [Requirement](#requirement)
   - [Priority](#priority)
   - [Size](#size)
4. [Automated Fields](#automated-fields)
   - [Type](#type)
   - [Estimate](#estimate)
   - [Assignee](#assignee)
   - [Start Date](#start-date)
   - [End Date](#end-date)
   - [Milestone](#milestone)
5. [Creating a New Issue](#creating-a-new-issue)
6. [Editing Issues & Comments](#editing-issues--comments)
7. [Example Issue](#example-issue)
8. [Markdown Tips](#markdown-tips)
9. [Best Practices](#best-practices)
10. [Conclusion](#conclusion)

</details>

---

## Introduction
This guide explains our **GitHub Issue** workflow, including how to create new issues, fill out the **mandatory fields**, and leverage automations that keep our team aligned. 

We also cover:
- How to use **comments** for updates and communication.
- How to **edit** issue descriptions and tasks lists as requirements evolve.
- Additional **Markdown** features you can use to enhance your issues.

---

## Workflow Overview

1. **Create a new issue** using our **issue template**.
   - Open the repository where the issue needs to be created.
   - Select the template and provide an initial description, title, and tasks.

2. **Submit the issue**:
   - Once you’ve filled out the template, submit the issue.
   - The issue will be automatically added to the relevant **Project** field in the right-hand sidebar.

3. **Fill in the mandatory fields** in the right-hand sidebar:
   - Navigate to the **Project** section in the sidebar, where mandatory fields will now be visible.
   - Fill out the required fields:
     - **Requirement**: Choose from `must have`, `should have`, `could have`, or `will not have`.
     - **Priority**: Assign a priority level (`P0`, `P1`, `P2`, `P3`).
     - **Size**: Choose the effort estimate (`XXS` to `XXL`).

4. **Use a conventional commit style** in the issue title:
   - Format the title with prefixes like `feat:`, `fix:`, or `chore:`.
     - Example: `feat: add "Favourites" button to book cards`.

5. **Automations** will populate or handle additional fields:
   - **Type**: Derived from the title prefix (e.g., `feat`, `fix`).
   - **Estimate**: Automatically calculated from the Size field, but can be manually adjusted if needed.
   - **Assignee**: Assigned when someone moves the issue to "In Progress" or manually self-assigns.
   - **Start Date**: Automatically added when the issue is first moved to "In Progress."
   - **End Date**: Automatically added when the issue is closed.

6. **Assign a Milestone (if applicable)**:
   - If the issue is tied to a specific release or project goal, add a milestone from the right-hand sidebar.
   - Milestones will propagate to related branches, commits, and pull requests.

7. **Labels**:
   - Add descriptive labels to categorize the issue (e.g., `team`, `UI`, `backend`).
   - Labels may also be auto-added based on text analysis of the issue content.

8. **Discuss and refine the issue**:
   - Use comments to provide updates, ask questions, or mention team members (`@username`).
   - Edit the issue description and tasks as needed to ensure clarity and accuracy.

9. **Create a feature branch** linked to the issue:
   - Use the GitHub "Create branch" button or your Git client to start a feature branch directly from the issue.

10. **Complete tasks** and **close the issue**:
    - Work through the tasks listed in the issue, checking them off as they are completed.
    - When the pull request (PR) linked to the issue is merged, close the issue to trigger automations (e.g., setting the End Date).

---

## Mandatory Fields

### Requirement
- **Field Name**: `Requirement`
- **Field Type**: Single-select
- **Options**:
  - `must have`: Non-negotiable product needs that are mandatory for the team.
  - `should have`: Important initiatives that are not vital but add significant value.
  - `could have`: Nice-to-have initiatives that will have a small impact if left out.
  - `will not have`: Initiatives and ideas that are not priority for this specific time.
- **Purpose**: This field helps categorize the importance of the issue’s feature or task.
- **How to Use**:
  - Select `must have` for features critical to project success.
  - Use `should have` for features that improve user experience significantly but are not blockers.
  - Opt for `could have` for features that are “nice-to-have.”
  - Use `will not have` to indicate features explicitly out of scope.
  
---

### Priority
- **Field Name**: `Priority`
- **Field Type**: Single-select
- **Options**:
  - `P0 (Critical)`: Urgent issues impacting live users or core functionality; requires immediate action.
  - `P1 (High)`: Key features or fixes needed for milestones; next priority after P0.
  - `P2 (Medium)`: Non-critical features or improvements; important but not urgent.
  - `P3 (Low)`: Nice-to-have tasks or exploratory items; no immediate impact.
- **Purpose**: Prioritizes issues based on urgency and importance.
- **How to Use**:
  - Assign `P0` for bugs or features that block core workflows or deliverables.
  - Use `P1` for high-priority features or fixes tied to deadlines.
  - Select `P2` for medium-priority tasks that add value but aren't urgent.
  - Use `P3` for low-priority or exploratory tasks.

---

### Size
- **Field Name**: `Size`
- **Field Type**: Single-select
- **Options**:
  - `XXS`: 0 hours of work.
  - `XS`: 1 hour of work.
  - `S`: 1–2 hours of work.
  - `M`: 2–4 hours of work.
  - `L`: 4–8 hours of work.
  - `XL`: 13–21 hours of work.
  - `XXL`: 21+ hours of work.
- **Purpose**: Helps estimate the effort and complexity of the issue.
- **How to Use**:
  - Use `XXS` for negligible work (e.g., typo fixes).
  - Use `XS` for tasks requiring less than an hour.
  - Assign `S` for small features or fixes (1–2 hours).
  - Choose `M` for medium-sized tasks (2–4 hours).
  - Assign `L` or larger for significant features or complex changes.
- **Tips**: Adjust size estimates during issue grooming if necessary.

---

## Automated Fields

1. **Type**: Derived from the title prefix (e.g., `feat`, `fix`, `chore`).
2. **Estimate**: Automatically calculated from the Size field but can be adjusted manually.
3. **Assignee**: Assigned when the issue is moved to "In Progress" or self-assigned.
4. **Start Date**: Auto-filled when moved to "In Progress."
5. **End Date**: Auto-filled when the issue is closed.
6. **Milestone**: Can be manually assigned in the sidebar.

---

## Creating a New Issue

1. **Click “New Issue”** and select our **issue template**.
   - Navigate to the repository and click the **New Issue** button.
   - Select the issue template provided.

2. **Enter a title** in the format:
   - Use [Conventional Commit](https://www.conventionalcommits.org/en/v1.0.0/) guidelines, e.g.,:
     ```
     feat: add favourite button
     ```

3. **Complete the issue template**:
   - Fill in the description, tasks, and references as prompted in the template.

4. **Submit the issue**:
   - Once you’ve filled out the template, submit the issue.
   - The issue will be automatically added to the relevant **Project** field in the right-hand sidebar.

5. **Fill in the mandatory fields** in the right-hand sidebar:
   - Navigate to the **Project** section in the sidebar, where mandatory fields will now be visible.
   - Fill out the required fields:
     - **Requirement**: Choose from `must have`, `should have`, `could have`, or `will not have`.
     - **Priority**: Assign a priority level (`P0`, `P1`, `P2`, `P3`).
     - **Size**: Choose the effort estimate (`XXS` to `XXL`).

6. **Review and refine labels**:
   - Check the auto-assigned labels (based on title and description).
   - Add any additional labels as needed to better categorize the issue.

7. **Submit updates and finalize the issue**:
   - Once all fields are complete, the issue is ready to proceed in the workflow.

---

## Example Issue
[Click to open real example issue.](https://github.com/orgs/jv-kune-kune/projects/1/views/1?filterQuery=ci&pane=issue&itemId=93907209&issue=jv-kune-kune%7CPiglioTech-General%7C15)

<details>
  <summary>Click to drop down rendered markdown example.</summary>
  
# feat: add "Favourites" button to book cards
---
# <!-- Briefly summarise the issue in a concise title -->
# Add a "Favourites" button to each book card on the book list page.

## Description
<!-- Add a short description of the problem, requirement, or goal. -->
- The button should toggle states (active/inactive) when clicked.
- Provide visual feedback (hover and active states).
- Ensure styles match the app's design system.

## Deliverables & Tasks
<!-- List actionable tasks. Break down into smaller steps if needed. -->
- [ ] Create "Favourites" button UI on book cards
- [ ] Implement click handler to toggle between active/inactive states
- [ ] Add hover and active state animations
- [ ] Update or write new tests (unit/integration) to cover this functionality

## Checklist
<!-- General development workflow steps. Remove if unsuitable. -->
- [ ] Create a feature branch from this issue
- [ ] Implement the feature or fix as specified
- [ ] Write or update tests
- [ ] Test locally and push changes
- [ ] Create a pull request (PR)
- [ ] Request a code review and address feedback
- [ ] Merge PR and close the issue

## References
<!-- Add links to issues, documentation, design specs, screenshots, or other relevant materials-->
- [Mockup for Favourites Button](https://example.com/mockup-favourites)
- Related Backend Issue #100

</details>

<details>
  <summary>Click to drop down raw markdown example.</summary>

```markdown
  
`# feat: add "Favourites" button to book cards`

# <!-- Briefly summarise the issue in a concise title -->
# Add a "Favourites" button to each book card on the book list page.

## Description
<!-- Add a short description of the problem, requirement, or goal. -->
- The button should toggle states (active/inactive) when clicked.
- Provide visual feedback (hover and active states).
- Ensure styles match the app's design system.

## Deliverables & Tasks
<!-- List actionable tasks. Break down into smaller steps if needed. -->
- [ ] Create "Favourites" button UI on book cards
- [ ] Implement click handler to toggle between active/inactive states
- [ ] Add hover and active state animations
- [ ] Update or write new tests (unit/integration) to cover this functionality

## Checklist
<!-- General development workflow steps. Remove if unsuitable. -->
- [ ] Create a feature branch from this issue
- [ ] Implement the feature or fix as specified
- [ ] Write or update tests
- [ ] Test locally and push changes
- [ ] Create a pull request (PR)
- [ ] Request a code review and address feedback
- [ ] Merge PR and close the issue

## References
<!-- Add links to issues, documentation, design specs, screenshots, or other relevant materials-->
- [Mockup for Favourites Button](https://example.com/mockup-favourites)
- Related Backend Issue #100

```

</details>

---

## Markdown Tips

1. **Headings** (`#`, `##`, `###`):
   ```markdown
   # H1
   ## H2
   ### H3
   ```

2. **Bullet Points** (`-`, `*`):
   ```markdown
   - Item 1
   - Item 2
   ```

3. **Checkboxes** (`- [ ]`, `- [x]`):
   ```markdown
   - [ ] Task 1
   - [x] Task 2
     - [ ] SubTask 1 (tab once)
     - [ ] SubSubTask 2 (tab once)
   ```

4. **Collapsible Sections** (`<details>`):
   ```markdown
   <details>
   <summary>Click to expand</summary>

   Hidden content here.

   </details>
   ```

5. **Strikethrough** (`~~`):
   ```markdown
   ~~Strikethrough text~~
   ```

6. **Bold Text** (`**text**` or `__text__`):
   ```markdown
   **This text is bold**  
   __This text is also bold__
   ```

7. **Code Blocks** (``` or indent with spaces):
   ```markdown
   Inline Code (single backticks): Use `console.log()` to debug.

   Multi-line Code Block (triple backticks ```):
   ```
   const hello = “world”;
   console.log(hello);
   ```
   ```

8. **Quoting Text** (`>`):
   ```markdown
   Single line:
   > This is a quote.

   Multi-line:
   > This is a longer quote.
   > It spans multiple lines.
   ```

9. **Referencing Issues** (`#`, `org/repo#`):
   ```markdown
   Same repo: #123 (becomes a clickable link, e.g., #123).
   Other repos: org/repo#456 (e.g., org/backend-repo#456).
   ```

10. **Mentioning Teammates** (`@username`):
    ```markdown
    - Notify specific teammates by mentioning them with `@username`. This sends them a notification and links their profile.

    - Example in a comment:
      @frontend-dev Can you review this part of the implementation?

    - Example in a task:
      - [ ] Implement click handler for the "Favourites" button (@frontend-dev)

    - Example in the description:
      The backend logic for storing favourites is handled by @backend-dev. Coordinate with them if needed.
    ```

---

## Best Practices
- **Keep Issues Focused**: Use one issue per feature, bug, or task. For larger initiatives, create multiple linked issues.
- **Update Continuously**: Edit the description and tasks as new details emerge or change. This keeps everyone on the same page.
- **Use Comments Strategically**: Discuss open questions, share progress updates, mention teammates, and link relevant commits or PRs.
- **Follow Conventional Commits**: This ensures consistent naming and helps automate workflows:
  - `feat:`, `fix:`, `chore:`, `docs:`, etc.
- **Attach Visuals & References**: Whenever possible, add screenshots or links to designs, PRs, or documentation.
- **Create Feature Branches from Issues**: This auto-links commits, making it easier to track progress and keep the code base organized.
- **Close the Loop**: After merging the PR, close the issue to trigger the **End Date** and finalize the workflow.

---

## Conclusion
By following this guide and using the **issue template** consistently:
- Your team gains **clarity** on each issue’s scope and status.
- **Automations** reduce manual overhead for labeling, assignees, and tracking.
- Clear **communication** via comments and updated descriptions helps everyone stay in sync.

Feel free to adapt this README or the template to suit your team’s workflow. If you have any questions or suggestions, please reach out via an issue or comment!

---
