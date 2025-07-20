# n8n Workflow Backup to GitHub

This workflow automatically backs up all your n8n workflows into a GitHub repository daily (or manually on trigger). It compares existing files with the current ones, creates new files for new workflows, and updates the existing ones if any changes are detected.

## 🔁 Features

- Fetches all workflows from your local n8n instance.
- Checks if the workflow already exists in the GitHub repository.
- Detects changes and commits only if there's a difference.
- Creates new files for new workflows.
- Supports both manual and daily scheduled backups.
- Stores backups as `.json` files in the GitHub repository.

## 📦 Requirements

- **n8n** running locally or on a server.
- A GitHub personal access token with `repo` scope.
- A GitHub repository to store the workflows (e.g., `n8n-backups`).
- n8n GitHub credentials set up in **Credentials → GitHub API**.

## ⚙️ Setup Instructions

1. Clone or import this workflow into your n8n instance.
2. Set up the following credentials:
   - **GitHub API** credentials (`repo`, `workflow` permissions)
   - Optional: HTTP Header Auth (for secure local API access)
3. Customize the `Globals` node if needed:
   ```json
   {
     "repo.owner": "your-github-username",
     "repo.name": "n8n-backups",
     "repo.path": "workflows/"
   }


4. You can trigger the backup:

    - Manually using the Manual Trigger node.
    - Automatically every day at 8 PM via the Cron node.

    
## 🗂️ File Structure in GitHub
  Each workflow is saved as: workflow-name.json
  Files are stored directly in the root (or under a subfolder if repo.path is set).

## 🔐 Security
  Credentials have been removed from this public version.
  You must set up your own credentials in n8n before running the workflow.

## 📝 Notes
  Designed for n8n v1+.
  This repo only contains the workflow logic, not actual workflow backups.
  Works best with n8n-nodes-base.github and httpRequest nodes.


