- # Git: A Comprehensive Guide

  ## Table of Contents

  - [Basic Git Workflow](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#basic-git-workflow)
  - [Setting Up a Repository](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#setting-up-a-repository)
  - [Working with Changes](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#working-with-changes)
  - [Undoing Changes](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#undoing-changes)
  - [Remote Repositories](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#remote-repositories)
  - [Using .gitignore](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#using-gitignore)
  - [Cloning Repositories](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#cloning-repositories)
  - [Branching and Merging](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#branching-and-merging)
  - [Forking and Collaboration](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#forking-and-collaboration)
  - [Command Reference](https://claude.ai/chat/6f65de8f-3bda-4ba1-924b-697c997861f8#command-reference)

  ## Basic Git Workflow

  Git manages your files through three main areas:

  1. **Working Directory** - Where files are actively edited
  2. **Staging Area** - Holds changes selected for the next commit
  3. **Local Repository** - Stores committed versions of files
  4. **Remote Repository** - GitHub-hosted version of your repository

  ## Setting Up a Repository

  ### Initializing a New Repository

  ```bash
  git init
  ```

  This creates a new Git repository in your current directory, with output like:

  ```
  Initialized empty Git repository in /path/to/your-project/.git/
  ```

  ## Working with Changes

  ### Checking Status

  View the current state of your working directory:

  ```bash
  git status
  ```

  Example output:

  ```
  On branch master
  No commits yet
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
  	chapter1.txt
  nothing added to commit but untracked files present
  ```

  ### Staging Files

  Add specific files to the staging area:

  ```bash
  git add chapter1.txt
  ```

  Add all changed files:

  ```bash
  git add .
  ```

  ### Committing Changes

  Save staged changes to the repository:

  ```bash
  git commit -m "Complete chapter 1"
  ```

  Output example:

  ```
  [master (root-commit) a1b2c3d] Complete chapter 1
   1 file changed, 1 insertion(+)
   create mode 100644 chapter1.txt
  ```

  ### Viewing History

  See a log of all commits:

  ```bash
  git log
  ```

  Example output:

  ```
  commit a1b2c3d (HEAD -> master)
  Author: Your Name <you@example.com>
  Date:   Mon Mar 24 12:34:56 2025 +0000
  
      Complete chapter 1
  ```

  ## Undoing Changes

  ### Viewing Differences

  See changes between working directory and last commit:

  ```bash
  git diff chapter3.txt
  ```

  ### Discarding Changes

  Restore a file to its state in the last commit:

  ```bash
  git checkout -- chapter3.txt
  ```

  ## Remote Repositories

  ### Setting Up a Remote Repository

  1. Create a repository on GitHub
  2. Link your local repository to the remote:

  ```bash
  git remote add origin <repository_URL>
  ```

  ### Pushing Changes to Remote

  Upload your local commits to GitHub:

  ```bash
  git push -u origin main
  ```

  The `-u` flag sets `origin` as the default upstream for the `main` branch.

  ### Verifying the Push

  - Refresh your GitHub repository page
  - Check **Insights > Network** to see commit history
  - Click individual commits to view changes

  ## Using .gitignore

  ### Creating a .gitignore File

  ```bash
  touch .gitignore
  ```

  ### Common .gitignore Patterns

  ```
  # Ignore specific files
  .DS_Store
  secrets.txt
  
  # Ignore file types
  *.log
  *.tmp
  
  # Ignore directories
  /node_modules/
  /build/
  
  # Comments explain what's being ignored
  ```

  ### Removing Previously Tracked Files

  If you already committed a file that should be ignored:

  ```bash
  git rm --cached secrets.txt
  ```

  ### Using Templates

  Browse GitHub's collection of standard .gitignore templates at [github.com/github/gitignore](https://github.com/github/gitignore)

  ## Cloning Repositories

  Download an existing repository:

  ```bash
  git clone <repository_URL>
  ```

  Example:

  ```bash
  git clone https://github.com/user/project.git
  ```

  ## Branching and Merging

  ### Creating Branches

  Create a new branch:

  ```bash
  git branch feature-branch
  ```

  List all branches (current branch marked with *):

  ```bash
  git branch
  ```

  ### Switching Branches

  Move to a different branch:

  ```bash
  git checkout feature-branch
  ```

  ### Making Changes on a Branch

  1. Switch to the branch
  2. Edit files as needed
  3. Commit changes:

  ```bash
  git add .
  git commit -m "Implement new feature"
  ```

  ### Merging Branches

  Integrate changes from a feature branch:

  1. Switch to the target branch:

  ```bash
  git checkout main
  ```

  1. Merge the feature branch:

  ```bash
  git push -u origin main
  ```

  ### Example Branching Workflow

  1. Create a branch for a new feature:

  ```bash
  git branch alien-plot
  git checkout alien-plot
  ```

  1. Make changes and commit on the branch:

  ```bash
  # Edit files
  git add .
  git commit -m "Modify chapters for alien theme"
  ```

  1. Switch back to main branch:

  ```bash
  git checkout main
  ```

  1. Make different changes on main:

  ```bash
  # Create chapter4.txt
  git add chapter4.txt
  git commit -m "Add chapter 4"
  ```

  1. Merge the feature branch into main:

  ```bash
  git merge alien-plot
  ```

  1. Push changes to remote:

  ```bash
  git push -u origin main
  ```

  ## Forking and Collaboration

  ### Forking

  A fork is a personal copy of someone else's repository on GitHub that:

  - Allows you to modify code independently
  - Lets you contribute to projects you don't have write access to
  - Creates a connection to the original repository

  ### Pull Request Workflow

  1. **Fork** the original repository on GitHub
  2. **Clone** your fork to your local machine
  3. **Make changes** and commit them
  4. **Push** your changes to your fork
  5. **Create a Pull Request** from your fork to the original repository
  6. Project maintainer **reviews and merges** your changes

  ### Collaboration Benefits

  - **Quality Control**: Code is reviewed before being merged
  - **Controlled Access**: Only trusted collaborators have direct write access
  - **Open-Source Contributions**: Allows anyone to suggest improvements

  ## Command Reference

  | Command                       | Description                                            |
  | ----------------------------- | ------------------------------------------------------ |
  | `git init`                    | Initialize a Git repository                            |
  | `git add <file>`              | Stage file(s) for commit                               |
  | `git add .`                   | Stage all changed files                                |
  | `git commit -m "message"`     | Commit staged changes                                  |
  | `git status`                  | Check working directory status                         |
  | `git log`                     | View commit history                                    |
  | `git diff`                    | View changes between working directory and last commit |
  | `git checkout -- <file>`      | Discard changes in working directory                   |
  | `git remote add origin <URL>` | Connect to remote repository                           |
  | `git push -u origin main`     | Push local commits to remote repository                |
  | `git clone <URL>`             | Clone a remote repository                              |
  | `git branch`                  | List branches                                          |
  | `git branch <name>`           | Create a new branch                                    |
  | `git checkout <branch>`       | Switch to a branch                                     |
  | `git merge <branch>`          | Merge a branch into current branch                     |
  | `git rm --cached <file>`      | Remove file from tracking                              |