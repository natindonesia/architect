---
tags: [github, development-standards, project-management, git, pull-requests]
---

# 🛠️ Development Standards


## Table of Contents
1. [Introduction](#introduction)
2. [GitHub Issue Management](#github-issue-management)
3. [GitHub Project Workflow](#github-project-workflow)
4. [Branching Strategy](#branching-strategy)
   - [Staging Branch](#staging-branch)
   - [Production Branch](#production-branch)
5. [Pull Request Guidelines](#pull-request-guidelines)
6. [Conclusion](#conclusion)

---

## Introduction
This document outlines the development standards and practices for managing tasks, code contributions, and version control in our projects. We use GitHub as our primary platform, leveraging its Issues, Projects, and Pull Requests (PRs) features alongside a clear branching strategy.

## GitHub Issue Management

### Creating Issues
- **Purpose:** GitHub Issues are used to track bugs, enhancements, and tasks.
- **Guidelines:**
  - Provide a clear and descriptive title.
  - Use labels to categorize the issue (e.g., `bug`, `enhancement`, `documentation`).
  - Add a detailed description, including steps to reproduce the issue or the requirements for an enhancement.
  - Assign the issue to the relevant team member(s).
  - Link the issue to the relevant GitHub Project or Pull Request.

### Prioritization
- Use labels or GitHub Projects to prioritize issues (e.g., `high-priority`, `low-priority`).
- Regularly review and update the priority of issues during sprint planning.

## GitHub Project Workflow

### Creating and Managing Projects
- **Purpose:** GitHub Projects help organize and track the progress of tasks.
- **Guidelines:**
  - Use a Kanban-style board for managing tasks, with columns such as `To Do`, `In Progress`, `In Review`, and `Done`.
  - Add GitHub Issues to the appropriate project.
  - Move issues across columns as they progress through the development lifecycle.
  - Regularly review the project board during team meetings to ensure alignment and progress.

### Project Milestones
- Define clear milestones within GitHub Projects to represent significant stages or releases.
- Associate issues with milestones to track progress toward the goals.

## Branching Strategy

### Staging Branch
- **Purpose:** The `staging` branch is used for testing and validation before production deployment.
- **Guidelines:**
  - Create feature branches from `staging`.
  - Merge completed features or bug fixes back into `staging` after code review and testing.
  - The `staging` branch should be kept stable and ready for testing at all times.
  - Perform testing on the `staging` branch before any merge to `production`.

### Production Branch
- **Purpose:** The `production` branch contains the stable version of the code that is deployed to production.
- **Guidelines:**
  - Only merge into `production` from `staging` after all features and fixes have been thoroughly tested.
  - Ensure all CI/CD checks pass before merging to `production`.
  - Tag releases on the `production` branch to maintain a clear version history.

## Pull Request Guidelines

### Creating a Pull Request
- **Purpose:** Pull Requests (PRs) are used to review and merge code changes.
- **Guidelines:**
  - Create a PR from your feature branch into `staging`.
  - Provide a clear and descriptive title and description for the PR.
  - Link the PR to the related GitHub Issue(s).
  - Ensure that your branch is up to date with `staging` before creating the PR.
  - Request reviews from relevant team members.
  - Perform self-review before assigning reviewers to ensure the code meets standards.

### Code Review
- Reviewers should provide constructive feedback and focus on both functionality and code quality.
- All comments should be addressed before the PR is merged.
- Use the "Approve" or "Request Changes" options to indicate readiness or required revisions.

### Merging a Pull Request
- Once approved, the PR can be merged into `staging`.
- Ensure all CI/CD checks pass before merging.
- After merging, delete the feature branch to keep the repository clean.

## Conclusion
Following these development standards ensures a streamlined workflow, consistent code quality, and efficient collaboration. Adhering to the branching strategy and PR guidelines will help maintain a stable and reliable codebase, ready for production deployment.
