
# Steps to Create a New SSH Key and Configure it for GitHub

## Step 1: Generate a New SSH Key
1. Open your terminal (Git Bash if you're on Windows).
2. Generate a new SSH key using the following command (replace `"your_email@example.com"` with the email you use for GitHub):
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
3. When prompted to "Enter a file in which to save the key," press **Enter** to accept the default location (`/c/Users/YourUserName/.ssh/id_rsa`).
4. Optionally, enter a passphrase for your key. This adds an extra layer of security, but you can leave it blank if you prefer.

## Step 2: Start the SSH Agent
Now that the key is generated, you need to ensure the SSH agent is running.
1. Start the SSH agent:
   ```bash
   eval "$(ssh-agent -s)"
   ```
   You should see a process ID indicating that the agent is running.

2. Add your SSH private key to the agent:
   ```bash
   ssh-add ~/.ssh/id_rsa
   ```

## Step 3: Add the New SSH Key to GitHub
1. Copy the SSH key to your clipboard. Use the following command:
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
   Copy the entire output.

2. Go to your GitHub account, then navigate to **Settings** > **SSH and GPG keys** (or directly [click here](https://github.com/settings/keys)).

3. Click **New SSH key**, provide a descriptive title, and paste your SSH public key into the "Key" field. Then click **Add SSH key**.

## Step 4: Test Your SSH Connection
1. Run the following command to test your connection to GitHub:
   ```bash
   ssh -T git@github.com
   ```

2. You should see a message like:
   ```plaintext
   Hi <your-username>! You've successfully authenticated, but GitHub does not provide shell access.
   ```

## Step 5: Update or Clone Repositories Using SSH
If you need to update the remote URL for an existing repository to use SSH instead of HTTPS, run:
```bash
git remote set-url origin git@github.com:username/repo.git
```

Now you should be able to clone, pull, and push using your new SSH key without issues.
