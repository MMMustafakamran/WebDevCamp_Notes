# **Git Basics: Setting Up a Local Repository and Version Control**

#### **Git Command Summary**

| Command                       | Description                  |
| ----------------------------- | ---------------------------- |
| `git init`                    | Initialize a Git repository  |
| `git add <file>`              | Stage file(s) for commit     |
| `git commit -m "message"`     | Commit changes               |
| `git log`                     | View commit history          |
| `git remote add origin <URL>` | Link remote repository       |
| `git push -u origin main`     | Push local commits to remote |

## **1. Initializing a Git Repository**

### **Command:**

```bash
git init
```

### **Expected Output:**

```
Initialized empty Git repository in /path/to/Story/.git/
```

## **2. Tracking Changes with Git**

### **Checking Git Status**

#### **Command:**

```bash
git status
```

#### **Expected Output:**

```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	chapter1.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### **Adding Files to Staging Area**

#### **Command:**

```bash
git add chapter1.txt
git status
```

git add . //adds all changed files to staging area

#### **Expected Output:**

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   chapter1.txt
```

### **Committing Changes**

#### **Command:**

```bash
git commit -m "Complete chapter 1"
```

#### **Expected Output:**

```
[master (root-commit) a1b2c3d] Complete chapter 1
 1 file changed, 1 insertion(+)
 create mode 100644 chapter1.txt
```

### **Viewing Commit History**

#### **Command:**

```bash
git log
```

#### **Expected Output:**

```
commit a1b2c3d (HEAD -> master)
Author: Your Name <you@example.com>
Date:   Mon Mar 24 12:34:56 2025 +0000

    Complete chapter 1
```

## **. Undoing Mistakes with Git**

### **Checking Differences**

#### **Command:**

```bash
git diff chapter3.txt
```

#### **Expected Output:**

```
(diff output showing differences between the last commit and current changes)
```

### **Reverting a File to Last Commit**

#### **Command:**

```bash
git checkout -- chapter3.txt
```

#### **Expected Output:**

```
(No output if successful, but the file is restored to the last committed state)
```

## **8. Summary of Git Workflow**

1. **Working Directory** → Where files exist.
2. **Staging Area** → Holds files before committing.
3. **Local Repository** → Stores committed versions.

**Creating a Remote Repository with GitHub**

### **1. Setting Up a GitHub Account**

### **2. Creating a New Repository**

### **3. Setting Up the Repository Locally**

#### **Check Local Repository Status**

```sh
cd Story  # Navigate to the project directory
git log   # View commit history
```

#### **Adding a Remote Repository**

```sh
git remote add origin <repository_URL>
```

- `origin` is a conventional name for the remote repository.

#### **Pushing Local Repository to GitHub**

```sh
git push -u origin main
```

- `-u`: Sets `origin` as the default upstream for the `main` branch.
- Uploads local commits to GitHub.

### **4. Verifying the Push**

- Refresh the GitHub repository page.
- Navigate to **Insights > Network** to see commit history.
- Click on individual commits to view changes.

### **5. Understanding Git Workflow**

#### **Local Repository Structure**

1. **Working Directory** – Files being modified.
2. **Staging Area** – Files selected for commit.
3. **Local Repository** – Committed snapshots.
4. **Remote Repository** – GitHub-hosted version.

#### **Git Command Summary**

| Command                       | Description                  |
| ----------------------------- | ---------------------------- |
| `git init`                    | Initialize a Git repository  |
| `git add <file>`              | Stage file(s) for commit     |
| `git commit -m "message"`     | Commit changes               |
| `git log`                     | View commit history          |
| `git remote add origin <URL>` | Link remote repository       |
| `git push -u origin main`     | Push local commits to remote |

### **6. Next Steps: Using .gitignore**

- Learn how to prevent sensitive files (API keys, passwords) from being pushed to GitHub.

**End of Notes**

**Git and .gitignore**

### **1. Understanding .gitignore**

- The `.gitignore` file is used to specify files and directories that Git should ignore.
- It prevents sensitive or unnecessary files from being committed to a Git repository.

### **2. Creating a .gitignore File**

- Open Terminal and navigate to your project directory:

  ```sh
  cd ~/Desktop/Project
  ```

- Create a 

  ```
  .gitignore
  ```

   file:

  ```sh
  touch .gitignore
  ```

- Open it in a text editor (e.g., VS Code):

  ```sh
  code .gitignore
  ```

### **3. Adding Rules to .gitignore**

- To ignore specific files, list them line by line:

  ```
  .DS_Store
  secrets.txt
  ```

- To ignore all 

  ```
  .txt
  ```

   files:

  ```
  *.txt
  ```

- To ignore a folder and its contents:

  ```
  /node_modules/
  ```

- To add comments:

  ```
  # Ignore log files
  *.log
  ```

### **4. Using .gitignore in a Git Repository**

#### **Initialize Git and Add Files**

```sh
  git init  # Initialize Git repository
  git add .  # Stage all files (except ignored ones)
  git status  # Check staged files
  git commit -m "Initial commit"
```

#### **Verify .gitignore Functionality**

- Check ignored files using:

  ```sh
  git status
  ```

- If a file was mistakenly added before creating 

  ```
  .gitignore
  ```

  , remove it from tracking:

  ```sh
  git rm --cached secrets.txt
  ```

### **5. Using Predefined .gitignore Templates**

- GitHub provides useful 

  ```
  .gitignore
  ```

   templates:

  - Visit [GitHub’s .gitignore templates](https://github.com/github/gitignore)
  - Copy and paste relevant sections into your `.gitignore`.

Example for **Node.js Projects**:

```sh
  node_modules/
  npm-debug.log
  .env
```

### **6. Summary of Key Commands**

| Command                   | Description                        |
| ------------------------- | ---------------------------------- |
| `touch .gitignore`        | Create a `.gitignore` file         |
| `code .gitignore`         | Open `.gitignore` in VS Code       |
| `git status`              | Check ignored files                |
| `git rm --cached <file>`  | Remove file from tracking          |
| `git add .`               | Add files (excluding ignored ones) |
| `git commit -m "message"` | Commit staged files                |

### **7. Next Steps: Git Clone**

- Learn how to clone repositories to your local system in the next lesson.



#### **3. Cloning a Repository – Command Syntax**

Use the `git clone` command:

```
git clone <repository_URL>
```

Example:

```
git clone https://github.com/user/project.git
```

