# ASCII Secret Message CODER and DECODER
#### Video Demo:  <URL HERE>
#### Description: Write a coded message in Figlet ASCII Art to send to your friends. Then decode it to see your secret message.

Your README.md file should be minimally multiple paragraphs in length, and should explain what your project is, what each of the files you wrote for the project contains and does, and if you debated certain design choices, explaining why you made them. Ensure you allocate sufficient time and energy to writing a README.md that documents your project thoroughly. Be proud of it! A README.md in the neighborhood of 500 words is likely to be sufficient for describing your project and all aspects of its functionality. If unable to reach that threshold, that probably means your project is insufficiently complex.


## 📄 Summary
A Python tool that converts plain text into a scrambled HTML table of coordinates and characters, pushes it to a GitHub repository, and allows others to "decode" and reconstruct the original ASCII art in their terminal using the **curses** library. GitHub readme best practices recommend starting with this type of overview. 
## 🚀 Features
* **Encode**: Convert text into various FIGlet fonts and scramble the character coordinates.
* **GitHub Integration**: Automatically creates or updates `.md` files in your repository using the PyGithub library.
* **Visual Decoding**: Fetches raw data from GitHub, parses it with BeautifulSoup, and renders the decoded art in a terminal window. 
## 🛠️ Prerequisites
Ensure you have the following libraries installed:
```
pip install beautifulsoup4 PyGithub pyfiglet requests tabulate
```

To install all the Prerequisites with a simple command:
```
pip install -r requirements.txt
```

Note: The `curses` library is built into most Unix systems (Linux/macOS). Windows users may need to install `windows-curses`.
```
pip install windows-curses
```


# TODO Here I will write up how to set up Github API to be able to use my program to write table to Github page as .md file.

**Setting up API or PAT for project:**
For fine-grained PATs, ensure the token has access to the correct repositories and the necessary permissions (e.g., contents: write, pull-requests: write, administration: read/write).
For classic PATs, verify that the correct scopes (e.g., repo, workflow) are selected.
You can manage your tokens and their permissions in the GitHub Developer Settings. https://github.com/settings/tokens
GitHub Actions Workflow Permissions: If this error happens within a GitHub Actions workflow, the default GITHUB_TOKEN often has read-only permissions.
Solution: Explicitly grant read and write permissions in your workflow file using the permissions block. For example:
Alternatively, you can set the default permissions for the entire repository in Settings > Actions > General > Workflow permissions.


## ⚙️ Configuration
Before running the script, you must update these variables in the code:
1. **GitHub Personal Access Token**: Replace the `ACCESS_TOKEN` with your own token generated from GitHub Settings.
2. **Repository Name**: Update `REPO_NAME` to your specific username and repository (e.g., `"your-user/your-repo"`).
## 📖 Usage
1. **Run the script**:
```
python your_script_name.py
```

2. **Encoding**:
    1. Choose `e`.
    2. Enter your text and select a Figlet font.
    3. The script will push a new `.md` file to your GitHub and provide a link.
3. **Decoding**:
    1. Choose `d`.
    2. Paste the link to the `.md` file created during encoding.
    3. Press `q` to exit the decoder view. 
