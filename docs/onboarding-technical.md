
# Onboarding Technical Guide

Welcome to the team! This guide will help you get started with your internship by covering essential topics, tools, and processes. Follow each section carefully, and don't hesitate to ask questions if anything is unclear.



---

## Introduction to the Team

### Team Goals
- Brief overview of the team's mission and current projects.
- Key deliverables expected during your internship.

---

## Workstation Setup



### Software
- **Operating System:** Recommended OS is Linux based (e.g., Ubuntu, Fedora).
- **Required Tools:** Ensure the following tools are installed:
  - [IDE/Code Editor] (e.g., VS Code, IntelliJ)
  - [Browser] (e.g., Chrome, Firefox)
  - [Terminal] (e.g., Git Bash, zsh)
  - [Other specific software] (e.g., PHP Composer, Node.js)

### Access
- **GitHub Account:** Ensure you have access to the organization's GitHub repository.
- **Microsoft Teams:** For daily reporting and team communication.

---

## Development Environment

### Every Laravel Project Ever


## Prerequisite

1. Git, Web Server, MySQL, PHP ^8.2, Composer, NodeJS ^20

```bash
sudo apt install -y apache2 git mariadb-server unzip
sudo apt -y install php8.4 php8.4-{cli,gd,mysql,pdo,mbstring,tokenizer,bcmath,xml,fpm,curl,zip,intl,bcmath}
# Install composer
curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer 
```


### Setting Up the Repository
- Clone the main project repository:
  ```bash
  git clone https://github.com/your-organization/your-repo.git
  ```
- Navigate to the project directory and install dependencies:
  ```bash
  cd your-repo
  npm install
  ```

### Configuring Environment Variables
- Create a `.env` file in the root of the project with the following keys:
  ```plaintext
  API_KEY=your-api-key
  DB_HOST=localhost
  ```



## Version Control with Git

----> [Git Best Practices](standards/git.md)

## Project Management Tools

### GitHub Project Kanban
- **Task Management:** Your tasks will be tracked in GitHub Projects or GitHub issues.

### Task Workflow
- **To Do:** Task is created and awaiting work.
- **In Progress:** Actively being worked on.
- **Code Review:** PR has been submitted and is under review.
- **Done:** Task is completed and merged into the `staging` branch.

---

## Code Review Process

### Review Guidelines
- Ensure your code adheres to the [coding standards](#best-practices).
- All code must be reviewed by at least one team member before merging.

### Providing Feedback
- Be constructive and clear in your feedback.
- Discuss any major issues in a separate meeting if necessary.

### Resolving Comments
- Address each comment in the PR and mark it as resolved once changes are made.

---



## Best Practices

### Coding Standards
- Follow the [development standards](standards/development.md) outlined in the project. 
- Write clean, maintainable, and modular code.

### Testing
- Ensure all new features have corresponding tests.
- Run tests locally before pushing any code.

### Documentation
- Document your code.
- Update relevant documentation when changes are made.

### Security
- Adhere to the security best practices outlined in [security policy](standards/security.md).
- Never commit sensitive information (API keys, passwords) to the repository.

---

We’re excited to have you on board and look forward to the great work you’ll do. If you have any questions or need further clarification, don’t hesitate to reach out to your mentor or team lead.

Happy coding!
