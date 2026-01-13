# FinalProject26
CS50 Final Project Repo

**Setting up API or PAT for project:**
For fine-grained PATs, ensure the token has access to the correct repositories and the necessary permissions (e.g., contents: write, pull-requests: write, administration: read/write).
For classic PATs, verify that the correct scopes (e.g., repo, workflow) are selected.
You can manage your tokens and their permissions in the GitHub Developer Settings. https://github.com/settings/tokens
GitHub Actions Workflow Permissions: If this error happens within a GitHub Actions workflow, the default GITHUB_TOKEN often has read-only permissions.
Solution: Explicitly grant read and write permissions in your workflow file using the permissions block. For example:
Alternatively, you can set the default permissions for the entire repository in Settings > Actions > General > Workflow permissions.

### ASCII Secret Table Encoder/Decoder
A Python tool that converts plain text into a scrambled HTML table of coordinates and characters, pushes it to a GitHub repository, and allows others to "decode" and reconstruct the original ASCII art in their terminal using the curses library. GitHub readme best practices recommend starting with this type of overview. 
## 🚀 Features
Encode: Convert text into various FIGlet fonts and scramble the character coordinates.
GitHub Integration: Automatically creates or updates .md files in your repository using the PyGithub library.
Visual Decoding: Fetches raw data from GitHub, parses it with BeautifulSoup, and renders the decoded art in a terminal window. 
## 🛠️ Prerequisites
Ensure you have the following libraries installed:
bash
pip install beautifulsoup4 PyGithub pyfiglet requests tabulate
Use code with caution.

Note: The curses library is built into most Unix systems (Linux/macOS). Windows users may need to install windows-curses.
## ⚙️ Configuration
Before running the script, you must update these variables in the code:
GitHub Personal Access Token: Replace the ACCESS_TOKEN with your own token generated from GitHub Settings.
Repository Name: Update REPO_NAME to your specific username and repository (e.g., "your-user/your-repo").
## 📖 Usage
Run the script:
"""
# bash
python your_script_name.py
Use code with caution.
"""

# Encoding:
Choose e.
Enter your text and select a Figlet font.
The script will push a new .md file to your GitHub and provide a link.
Decoding:
Choose d.
Paste the link to the .md file created during encoding.
Press q to exit the decoder view. 
🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request. 
📜 License
Distributed under the MIT License. 
