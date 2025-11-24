# Pre-Commit Hook Setup Guide

## 📘 Introduction
A **pre-commit hook** is a script that runs automatically **before `git commit` is created**.  
It is commonly used to validate code, check formatting, prevent committing unwanted files, or enforce team standards.

This README explains how to set up a simple pre-commit hook that **checks staged files** before committing.

---

## ⚙️ Step-by-Step Setup Guide

### **1. Navigate to Your Project Directory**

    cd /Commit-hooks
2. Go to the Git Hooks Folder
   All hooks are stored inside .git/hooks.

       cd .git/hooks
4. Create or Edit the pre-commit File

       nano pre-commit
5. Add the Pre-Commit Script
The example below performs these checks:

Prevents committing .log files

Prevents committing files larger than 1MB

Runs basic linting (example placeholder)


    #!/bin/bash

    echo " Running Pre-Commit Checks..."

    # 1. Block .log files from being committed
    if git diff --cached --name-only | grep -E "\.log$" > /dev/null; then
    echo ".log files are not allowed to be committed."
    exit 1
    fi

    # 2. Block files larger than 1MB
    large_files=$(git diff --cached --name-only | while read file; do
    if [ -f "$file" ] && [ $(stat -c%s "$file") -gt 1048576 ]; then
        echo "$file"
    fi
    done)

    if [ ! -z "$large_files" ]; then
    echo " The following files are too large (>1MB):"
    echo "$large_files"
    exit 1
    fi

# 3. Example: Lint check (placeholder)
# Replace with actual linter for your project
    echo " Linting code... (demo)"
    sleep 1

    echo " All Pre-Commit checks passed!"
    exit 0
5. Make the Hook Executable

       chmod +x pre-commit
7. Test the Hook
Try committing something:

       git add .
       git commit -m "Testing pre-commit hook"
If checks fail, the commit will be blocked.

# Conclusion
Your Git repository now uses a pre-commit hook to prevent unwanted files and maintain clean commit history.
Pre-commit hooks help teams enforce standards and avoid mistakes before committing code.

# Contact Information
For help or customization, contact:
Ayushi
📧 your-email@example.com

# References
Git Hooks Docs — https://git-scm.com/docs/githooks

Pro Git Book — https://git-scm.com/book/en/v2

yaml
Copy code
