# git
git commands


Here’s the correct order of steps to push code to the desired GitHub repository, ensuring you properly configure your SSH keys, Git settings, and remote repository.

### Step-by-Step Guide:

---

### 1. **Generate SSH Key (if you don't have one yet)**
   You need to generate a new SSH key that will be associated with your GitHub account.

   ```bash
   ssh-keygen -t rsa -b 4096 -C "deypadma2020@gmail.com"
   ```

   - When prompted for a file to save the key, press **Enter** to accept the default location (`~/.ssh/id_rsa`).
   - If you already have a key at that location, you may choose to overwrite it, or provide a different name.

### 2. **Add SSH Key to SSH Agent**
   Start the SSH agent and add your SSH key:

   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```

### 3. **Add SSH Key to GitHub**
   - Copy the contents of your public key (`~/.ssh/id_rsa.pub`):

     ```bash
     cat ~/.ssh/id_rsa.pub
     ```

   - Go to your GitHub account (Account 1) and:
     - Navigate to **Settings** > **SSH and GPG keys** > **New SSH key**.
     - Paste the key and give it a title.

### 4. **Verify SSH Connection to GitHub**
   Check that your SSH key is correctly configured by running:

   ```bash
   ssh -T git@github.com
   ```

   If the setup is correct, you should see a message like:

   ```
   Hi deypadma2020! You've successfully authenticated, but GitHub does not provide shell access.
   ```

### 5. **Clone the Repository**
   If you haven’t cloned your repository yet, do so now. This will download the repository to your local machine.

   ```bash
   git clone git@github.com:deypadma2020/Python_Project.git
   ```

### 6. **Set Up the Remote Repository**
   If you already cloned the repository, but you want to reconfigure the remote repository (in case it was incorrectly set), you can remove and then re-add the remote as follows:

   ```bash
   cd Python_Project  # Go to the cloned repo directory
   git remote remove origin
   git remote add origin git@github.com:deypadma2020/Python_Project.git
   ```

### 7. **Configure Git Username and Email**
   Configure Git with the correct username and email. This will ensure your commits are associated with the correct account.

   ```bash
   git config --global user.name "deypadma2020"
   git config --global user.email "deypadma2020@gmail.com"
   ```

   **Note**: This step can be done locally for just the current repository by omitting `--global`:

   ```bash
   git config user.name "deypadma2020"
   git config user.email "deypadma2020@gmail.com"
   ```

### 8. **Initialize the Repository (if needed)**
   If this is a new repository and you haven't yet initialized it (after cloning), initialize it:

   ```bash
   git init
   ```

### 9. **Add Changes**
   Add the files or changes you want to commit. In your case, you're adding the `Feature_Engineering` folder:

   ```bash
   git add ./Feature_Engineering
   ```

### 10. **Check the Status**
   It’s good to verify which files have been staged before committing:

   ```bash
   git status
   ```

### 11. **Commit Your Changes**
   Commit your changes with a meaningful message:

   ```bash
   git commit -m "Update Feature_Engineering folder"
   ```

### 12. **Push Your Changes**
   Finally, push your changes to GitHub:

   ```bash
   git push -u origin main
   ```

   The `-u` flag sets the remote `origin` as the default for future `git push` commands, so you don’t need to specify it again in the future.

---

### Summary of the Correct Order:

1. **Generate SSH key** (if needed).
2. **Add SSH key to GitHub**.
3. **Verify SSH connection** to GitHub.
4. **Clone the repository**.
5. **Set up the remote URL** (if not done during cloning).
6. **Configure Git username and email**.
7. **Initialize the repository** (if it's a new repo and not yet initialized).
8. **Add the files** you want to commit (`git add`).
9. **Commit your changes** (`git commit`).
10. **Push your changes** to GitHub.

This should ensure that you're able to push your code to the desired GitHub repository and associate the correct GitHub account with your commits. Let me know if you run into any issues!
