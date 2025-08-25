# Autonomous Task Management Protocol

This document outlines the protocol for an autonomous agent to manage and execute tasks from a markdown-based task list.

## Core Directives

- **Focus on a single parent task:** You are assigned one parent task at a time. Complete all of its sub-tasks before moving on. Do not work on tasks you are not assigned to.
- **Autonomy within a parent task:** You have the authority to complete all sub-tasks under your assigned parent task without seeking approval for each one.
- **Sequential sub-task execution:** Complete sub-tasks in the order they are listed. Mark each sub-task as complete (`[x]`) immediately upon finishing it.

## Completion Protocol for a Parent Task

1.  **Verify all sub-tasks are complete:** Before proceeding, ensure every sub-task under the current parent task is marked with `[x]`.
2.  **Run tests:** Execute the entire test suite for the project (e.g., `pytest`, `npm test`, `bin/rails test`).
3.  **Commit changes:** If all tests pass, commit the changes. The commit message should be descriptive and follow the conventional commit format.
    - Summarize the accomplishments of the parent task.
    - List key changes.
    - Reference the parent task.
    - Format the message as a single-line command using `-m` flags, e.g.:
      ```
      git commit -m "feat: implement user authentication" -m "- Add login and registration endpoints" -m "- Include password hashing and JWT generation" -m "Completes: Task 1"
      ```
4.  **Mark parent task as complete:** After committing, mark the parent task as `[x]`.
5.  **Create a Pull Request:** Once the parent task is complete and committed, create a pull request.
6.  **Await approval:** After creating the PR, halt execution and await approval from a human reviewer. Do not proceed with new tasks until the current PR is approved and merged.

## Task List Maintenance

- **Keep the list updated:** Continuously update the task list file as you complete sub-tasks and parent tasks.
- **Log relevant files:** Maintain a "Relevant Files" section, listing every file you create or modify with a brief description of its role.