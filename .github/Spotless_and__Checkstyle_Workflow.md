
# Commands for Spotless and Checkstyle Issue

This document contains all the required command-line instructions for completing the Spotless and Checkstyle tasks as described in the issue.

---

## Task Workflow

### 1. Run Style Check Report and Open the File
Generate a Checkstyle report and open it for review:
```bash
mvn checkstyle:checkstyle && open target/checkstyle-result.xml
```

For an HTML report (more readable):
```bash
mvn site && open target/site/checkstyle.html
```

---

### 2. Run Spotless Check (Should Fail on First Run)
Run the Spotless check to verify style violations. This will fail if there are issues:
```bash
mvn spotless:check
```

---

### 3. Apply Spotless Fixes
Automatically fix all detected style violations:
```bash
mvn spotless:apply
```

---

### 4. Re-run Spotless Check (Should Pass After Apply)
Verify that all issues have been resolved:
```bash
mvn spotless:check
```

At this point, the command should complete successfully without errors.

---

### 5. Review and Roll Back Changes (If Necessary)
To undo changes made by Spotless for review or adjustment:
```bash
git restore .
```

---

### 6. Modifying Spotless Configuration in CI Pipeline

#### Current Spotless Configuration
The pipeline currently runs Spotless in a non-blocking way:
```yaml
# Step 5: Run Spotless Check
- name: Run Spotless Check
  run: |
      mvn spotless:check || echo "Spotless violations detected. Check the logs for details."
```

#### 6.1 Run Spotless Without Applying Fixes
No changes are needed if you want Spotless to only check for violations. It will:
- Run `mvn spotless:check`.
- Fail the pipeline if violations are found (unless mitigated by `|| echo ...`).

#### 6.2 Automatically Apply Spotless Fixes in the Pipeline
To make Spotless automatically fix style issues, update the pipeline step to:
```yaml
# Step 5: Run Spotless Apply
- name: Run Spotless Apply
  run: mvn spotless:apply
```

This will automatically format the code. Any changes will need to be reviewed and committed by a developer.

#### 6.3 Enforce Clean Code by Failing the Pipeline if Fixes Were Needed
To ensure clean code and fail the pipeline if unresolved issues remain, use this configuration:
```yaml
# Step 5a: Run Spotless Apply
- name: Run Spotless Apply
  run: mvn spotless:apply

# Step 5b: Verify Spotless Check Passes
- name: Verify Spotless Check
  run: mvn spotless:check
```

---

## Notes

- Review changes made by Spotless before merging into `main`.
- Automatically committing changes directly from the pipeline is discouraged to ensure proper code review processes.

---

## GitHub Actions Configuration Summary

### Full Example for Automatically Applying Spotless Fixes
```yaml
# Step 5a: Run Spotless Apply
- name: Run Spotless Apply
  run: mvn spotless:apply

# Step 5b: Verify Spotless Check Passes
- name: Verify Spotless Check
  run: mvn spotless:check
```

### Full Example for Spotless Check Only (No Fixes)
```yaml
# Step 5: Run Spotless Check
- name: Run Spotless Check
  run: |
      mvn spotless:check || echo "Spotless violations detected. Check the logs for details."
```

---

## General Git Commands for the Workflow

### Create a New Feature Branch
```bash
git checkout -b <feature-branch-name>
```

### Stage and Commit Spotless Configuration Changes
```bash
git add .
git commit -m "Set up Spotless configuration for style enforcement"
```

### Push Feature Branch to Remote Repository
```bash
git push origin <feature-branch-name>
```

### Roll Back Local Changes (If Needed)
```bash
git restore .
```

---

## Final Notes

- Spotless is used for automatic style fixes, while Checkstyle provides detailed reporting of coding standard violations.
- Always review changes made by Spotless to ensure alignment with team coding standards before committing.
- Integrating Spotless into the CI/CD pipeline ensures consistent style enforcement across the codebase.
