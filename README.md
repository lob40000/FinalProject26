# ASCII Secret Messager
#### Video Demo:  <URL HERE>
#### Description: Write a coded message in Figlet ASCII Art to send to your friends. Then decode it to see your secret message.

## Overview
A Python tool that converts plain text into a scrambled HTML table of coordinates and characters, pushes it to a GitHub repository, and allows others to "decode" and reconstruct the original ASCII art in their terminal using the **curses** library.

## 🚀 Features
- **Encode**: Convert text into various FIGlet fonts and scramble the character coordinates.
- **GitHub Integration**: Automatically creates or updates `.md` files in your repository using the PyGithub library.
- **Visual Decoding**: Fetches raw data from GitHub, parses it with BeautifulSoup, and renders the decoded art in a terminal window. 

## 📄 Summary
I broke this program into 5 functions, not including the main function. The reason is that my program can do 2 things. Code a message or decode a message that it created. See **Usage** section.
### Coding:
- The `main()` function starts by asking the user what they want to do: encode or decode. If they decide to encode, then the user is asked for the message or text they want to code. Then the user is directed to the next function named `user_choice()`. 
- In `user_choice()`, the user is asked for the font they want to use for the ASCII art formatting. A list of example fonts is displayed, but the user's font choice will be checked to make sure that it is a valid font for formatting in ASCII art using the Figlet library and module. This function uses a loop to make sure that the font is valid before leaving and returning the `user_font` to the next function for encoding.
- In `encode_table`, it takes two arguments: `text` and `user_font`. It uses the `pyfiglet.figlet_format()` function to translate your `text` into ASCII art using the `user_font`. Next, it breaks it down into x, y coordinates with the Unicode symbol as the character for our message. It saves it into a table and then uses `random.shuffle()` to mix up the order for our secret coded message. Finally, it returns our shuffled table containing our message to the `main()` function for the last step in saving our message.
- The `save_table()` function takes our shuffled table as an argument and saves it to our GitHub page for accessing later on or to send to a friend. It will ask you for the name of the file (the file doesn't allow for spaces or special characters). Once you have named your file, it will then use your `ACCESS_TOKEN` you will create, to automatically save files or update files in your GitHub page to access later. See **Setting up GitHub Fine-Grained Personal Access Token** for more details on how to set this up. Once successful in saving your newly created file, you'll get a response that your file was created and a link to save for later or to access that page to see it right away. Also, you can send that link over to your friend who is also using this program to decode that file right away.
### Decoding:
- The `main()` function starts by asking the user what they want to do: encode or decode. If they decide to decode, then the user is asked for the GitHub URL of where the coded table with your message is located. Then the user is directed to the next function named `user_url()`.
- The `user_url()` function checks that this URL is a GitHub website and that it's aimed at a `.md` file where your coded table is located. It then verifies that the URL is valid using `requests`, looking for a status code of 200. If the formatting is incorrect or if it can't validate the site, then it will request a URL again from the user until it gets a correctly formatted URL that is valid. Once validated, it returns that site's `requests` response for decoding.
- The `decode_table()` function does the final work in decoding the secret message. It creates 3 separate lists where it will parse out the shuffled table from the GitHub site file and use the `curses` module to piece together the secret message in your terminal window till it's revealed. If successful, you will see the beautiful ASCII art message that was coded for you. Simply press `q` to exit the secret message window and do it all over again if you please!
- Below you will see the different files, features, prerequisites, configurations, and usage of my program. Follow along and Enoy!

    - `project.py`: Main program file. See **Usage** section
    - `test_project.py`: Pytest file to test different functions of my program file. See **Usage** section
    - `requirements.txt`: Prerequisites for running my main program file. See **Prerequisites**
    - `README.md`: Readme file that explains what my program file is, what it does, and how to set it up on your computer/coding environment to use for yourself.

## 🛠️ Prerequisites
- Ensure you have the following libraries installed:
```
pip install beautifulsoup4 PyGithub pyfiglet requests tabulate
```

- To install all the Prerequisites with a simple command:
```
pip install -r requirements.txt
```

- Note: The `curses` library is built into most Unix systems (Linux/macOS). Windows users may need to install `windows-curses`.
```
pip install windows-curses
```

## 🔐 Setting up GitHub Fine-Grained Personal Access Token
To allow this script to create or modify files in your repository, follow these steps to generate a secure, scoped token.
1. **Generate Your Token**
  - Go to your GitHub Settings.
  - In the left sidebar, click **Developer settings** > **Personal access tokens** > **Fine-grained tokens**.
  - Click **Generate new token**.
  - **Token name**: Enter a descriptive name like ``ASCII-Code-Table``.
  - **Expiration**: Choose a timeframe (90 days is the recommended maximum).
  - **Repository access**: Select **Only select repositories** and pick your specific repository from the dropdown menu.
  - **Permissions**: Click the **Repository permissions** dropdown and find **Contents**. Set this to **Read and write**.
      - _Note: This automatically grants the required "Metadata" read-only access._
2. **Save and Use**
  - Scroll down and click Generate token.
  - Copy the token immediately. You cannot view it again once you leave the page.
  - In your Python script, update the `ACCESS_TOKEN` variable:

3. **Why Fine-Grained**?
  - **Minimal Exposure**: If your token is ever leaked, it only has access to that single repository instead of your entire GitHub account.
  - **Least Privilege**: You are only granting permission to change file Contents, not sensitive account settings.

## ⚙️ Configuration
Before running the script, you must update these variables in the code:
1. **GitHub Personal Access Token**: Replace the `ACCESS_TOKEN` with your own token generated from GitHub Settings.
```
ACCESS_TOKEN = "github_pat_your_token_here"
```
2. **Repository Name**: Update `REPO_NAME` to your specific username and repository.
```
REPO_NAME = "your_user/your_repo"
```

## 📖 Usage
1. **Access Directory**
```
cd project
```
2. **Run the script**:
```
python project.py
```
3. **Encoding**:
    1. Choose `e`.
    2. Enter your text and select a Figlet font.
    3. The script will push a new `.md` file to your GitHub and provide a link.
4. **Decoding**:
    1. Choose `d`.
    2. Paste the link to the `.md` file created during encoding.
    3. Press `q` to exit the decoder view.
  
## ✍️ Testing
1. **Access Directory**:
```
cd project
```
2. **Run the script**:
```
pytest test_project.py
```
