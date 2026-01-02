# FinalProject26
CS50 Final Project Repo

**Setting up API or PAT for project:**
For fine-grained PATs, ensure the token has access to the correct repositories and the necessary permissions (e.g., contents: write, pull-requests: write, administration: read/write).
For classic PATs, verify that the correct scopes (e.g., repo, workflow) are selected.
You can manage your tokens and their permissions in the GitHub Developer Settings. https://github.com/settings/tokens
GitHub Actions Workflow Permissions: If this error happens within a GitHub Actions workflow, the default GITHUB_TOKEN often has read-only permissions.
Solution: Explicitly grant read and write permissions in your workflow file using the permissions block. For example:
Alternatively, you can set the default permissions for the entire repository in Settings > Actions > General > Workflow permissions.
