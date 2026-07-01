# About

This repository stores the Ansible code to manage the AWS EC2 Instance for my Personal Website [andrewflanigan.com](andrewflanigan.com)

## What it does

Ansible performs these tasks via these Roles:

- common
  - Updates and Installs packages on the Instance
  - Sets up SSH User used to deploy updated website code
  - Creates web root directory
  - Hardens SSH Config: No Password Auth, No Root User, etc
  - Configures UFW Firewall: SSH, HTTP/HTTPS, Default Deny
  - Sets up Fail2Ban
- nginx
  - Installs nginx
  - Removes default site and sets up one from template
  - Enables site and reloads
- certbot
  - Installs certbot and nginx plugins
  - Obtains a Let's Encrypt certificate
  - Sets up certbot auto-renewal

## GitHub Workflow/Actions

This repository also has a couple GitHub Workflow/Actions setup:

- Runs [ansible-lint](https://github.com/ansible/ansible-lint) on pull requests/merges
- Runs [Dependabot](https://docs.github.com/en/code-security/tutorials/secure-your-dependencies/dependabot-quickstart-guide) weekly

## Commands

```bash
# AWS
ansible-playbook playbook.yml --extra-vars "@vars.yml"

# GCP
ansible-playbook playbook.yml -i inventory-gcp --extra-vars "@vars.yml"
```
