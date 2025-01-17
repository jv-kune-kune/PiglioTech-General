
# Commands for Spotless and Checkstyle Issue

This document contains all the required command-line instructions for completing the Spotless and Checkstyle tasks as described in the issue.

---

## Task Workflow

### 1. Run Style Check Report and Open the File
To generate a Checkstyle report and open it for review in one step:
```bash
mvn checkstyle:checkstyle && open target/checkstyle-result.xml
```

If you prefer an HTML report for easier review:
```bash
mvn site && open target/site/checkstyle.html
```

---

### 2. Run Spotless Check (Should Fail on First Run)
Run the Spotless check to verify style violations (this should fail if there are issues):
```bash
mvn spotless:check
```

You will see detailed output of the violations directly in the terminal.

---

### 3. Apply Spotless Fixes
To automatically fix all detected style violations:
```bash
mvn spotless:apply
```

---

### 4. Re-run Spotless Check (Should Pass After Apply)
Run the Spotless check again to ensure all issues have been resolved:
```bash
mvn spotless:check
```

At this point, the command should complete successfully with no errors.

---

### 5. Review and Roll Back Changes (If Necessary)
If you need to undo changes made by Spotless for review or adjustment, use:
```bash
git restore .
```

---

### 6. Modifying Spotless Configuration in CI Pipeline
    The pipeline currently includes the following step for Spotless:
    ```yaml
    # Step 5: Run Spotless Check
    - name: Run Spotless Check
      run: |
          mvn spotless:check || echo "Spotless violations detected. Check the logs for details."
    ```

---

    ####  Run Spotless Without Applying Fixes (Current Setup)

    ## 1. If you want Spotless to only check for violations without applying fixes, **no changes are needed**. The current configuration will:
    - Run `mvn spotless:check`.
    - Fail the pipeline if violations are found (unless mitigated by `|| echo ...`).

    ### Logs
    Violations will appear in the logs, and developers can manually fix them by running `mvn spotless:apply` locally.

---

    ## 2. Automatically Apply Spotless Fixes in the Pipeline

    To make Spotless automatically fix style issues during the pipeline:

    ### Update the Step in Your CI Workflow

    Replace the Spotless step in your workflow with:
    ```yaml
    # Step 5: Run Spotless Apply
    - name: Run Spotless Apply
      run: mvn spotless:apply
    ```

    ### Result
    - This will modify code to adhere to the style guidelines automatically.
    - Any changes made will need to be committed back to the repository by a developer after review.

---

    ## 3. Fail the Pipeline if Spotless Fixes Were Needed

    If you want to enforce clean code but fail the pipeline when fixes are needed, add a Spotless check **after** the `apply` step.

    ### Example Configuration:
    ```yaml
    # Step 5: Run Spotless Apply
    - name: Run Spotless Apply
      run: mvn spotless:apply

    # Step 6: Verify Spotless Check Passes
    - name: Verify Spotless Check
      run: mvn spotless:check
    ```

    ### Result
    - Spotless will first fix the code.
    - The pipeline will then fail if `mvn spotless:check` finds unresolved issues (e.g., if some formatting couldn't be auto-corrected).

---

## Notes

- Ensure that changes made by Spotless are reviewed before merging to `main`. Automatically committing changes within the pipeline is discouraged as it may bypass code reviews.
- Spotless fixes can be tested locally before pushing to avoid pipeline failures.

---

## GitHub Actions Configuration Summary

### Full Example for Automatically Applying Spotless Fixes
```yaml
# Step 5: Run Spotless Apply
- name: Run Spotless Apply
  run: mvn spotless:apply

# Step 6: Verify Spotless Check Passes
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

## Notes

- Spotless is used for automatic style fixes, while Checkstyle provides detailed reporting of coding standard violations.
- Always review the changes made by Spotless to ensure alignment with team coding standards before committing.
- Integrating Spotless into the CI/CD pipeline ensures consistent style enforcement across the codebase.
