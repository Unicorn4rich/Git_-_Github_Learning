# Comprehensive Git & GitHub Notes

## 1. Introduction to Git and GitHub

Git is a distributed version control system that helps developers manage their code and track changes over time. GitHub is a platform for hosting Git repositories, enabling collaboration on projects.

## 2. Basic Git Commands

### 2.1 Checking out and Switching Branches

- **`git checkout <commit_number>`**  
  Use this command to switch to a specific commit in the repository. This is helpful if you want to review or work on code from a past state.

  ```sh
  git checkout <commit_number>
  ```

- **`git branch`**  
  Lists all branches in your repository and highlights the current branch you are working on.

  ```sh
  git branch
  ```

- **`git branch <branch_name>`**  
  Creates a new branch with the name provided.

  ```sh
  git branch <branch_name>
  ```

- **`git switch <branch_name>`**  
  Switches to an existing branch.

  ```sh
  git switch <branch_name>
  ```

- **`git switch -c <branch_name>`**  
  Creates a new branch and switches to it.

  ```sh
  git switch -c <branch_name>
  ```

- **`git checkout <branch_name>`**  
  Another way to switch to an existing branch.

  ```sh
  git checkout <branch_name>
  ```

### 2.2 Pushing Changes

- **`git push --set-upstream origin <branch_name>`**  
  Pushes the local branch to the remote repository for the first time. This establishes an upstream connection for future pushes.

  ```sh
  git push --set-upstream origin <branch_name>
  ```

### 2.3 Viewing Commits and Log

- **`git log`**  
  Displays the commit history, showing details like commit IDs, messages, and authors.

  ```sh
  git log
  ```

- **`shift + q`**  
  Closes the `git log` window in the terminal.

- **`git log --oneline`**  
  Shows a more concise log with only the commit hash and message.

  ```sh
  git log --oneline
  ```

### 2.4 Merging Branches

- **`git merge <branch_name>`**  
  Merges changes from the specified branch into the current branch. Typically, you need to be on the `main` branch before merging.

  ```sh
  git checkout main
  git merge <branch_name>
  ```

### 2.5 Checking Status and Renaming Branches

- **`git status`**  
  Shows the current state of your working directory and staging area, helping you track changes.

  ```sh
  git status
  ```

- **`git branch -m <old_branch_name> <new_branch_name>`**  
  Renames an existing branch.

  ```sh
  git branch -m <old_branch_name> <new_branch_name>
  ```

### 2.6 Deleting Branches

- **`git branch -d <branch_name>`**  
  Deletes a local branch that is no longer needed.

  ```sh
  git branch -d <branch_name>
  ```

## 3. Advanced Git Operations

### 🔄 What git stash Does
git stash temporarily shelves (or "stashes") changes in your working directory and index (staged changes), so you can work on something else and come back to them later.

### 🚨 First, Important Note:
> **Stashes are not pushed to GitHub.**

`git stash` is **local only**—it doesn’t create commits that GitHub can see. It just saves a snapshot on your local machine. Until you **apply the stash, add, commit, and push** the changes, nothing related to the stash appears on GitHub.



### 3.1 Stashing Changes

- **`git stash`**
- Only tracked but unstaged changes get stashed.
- New untracked files (e.g., newly created files not added with git add) will NOT be stashed.

  Temporarily saves your uncommitted changes so you can switch contexts or branches without losing your progress.

  ```sh
  git stash
  ```


  - **`git stash apply`**  
  Applies the most recent stash to your working directory.

  ```sh
  git stash apply
  ```

### 3.1.1 Delete Stash

- **`stash pop`**
  - When you run git stash pop, those changes will come back.

  ```sh
  git stash pop
  ```

### 3.1.2 Drop the stash manually:

- **`git stash drop`**
  - If you used apply, drop the stash manually:

  ```sh
  git stash drop
  ```

### 3.1.3 drop a specific stash::

- **`git stash drop stash@{0}`**
  - Or view the list and drop a specific stash:

  ```sh
  git stash drop stash@{0}
  ```

  ### 🔥 Pro Tip
  If you have multiple stashes, use:
  ```bash
  git stash list
  git stash apply stash@{1}  # apply a specific one
  ```
  

- **`git stash list`**  
  Displays a list of all stashed changes.

  ```sh
  git stash list
  ```


  ### 🔁 Summary
  
  | Action | What It Does |
  |--------|--------------|
  | `git stash` | Saves changes locally (not on GitHub) |
  | `git stash apply` | Brings changes back to your working directory |
  | `git add .` | Stages those changes |
  | `git commit -m "message"` | Creates a commit GitHub will recognize |
  | `git push` | Uploads that commit to GitHub |
  

  ### 🔄 Think of It Like This:
  
  > `git stash` = "Save my local work for now, hide it"
  >  
  > `git stash apply` = "Bring back that local work so I can finish it"


  
  ### 🧠 Example Scenario
  
  You're on the `main` branch, working on a feature. Suddenly, you need to fix a bug in production.
  
  ```bash
  # Save your unfinished work (not ready to commit yet)
  git stash
  
  # Switch to the production branch and fix the bug
  git checkout production
  # ... fix the bug ...
  git commit -m "hotfix"
  git push
  
  # Go back to main and continue your feature
  git checkout main
  git stash apply  # <- This brings back your saved work
  ```
  
  ---



  

### 3.2 Working with GitHub Repositories

#### 3.2.1 Forking a Repository

- **Fork the repository**  
  Go to the GitHub repository you want to contribute to and click on the "Fork" button. This creates a copy of the repository in your own GitHub account.

#### 3.2.2 Cloning the Repository

- **Clone the repository**  
  Clone your forked repository to your local machine to start working on it.

  ```sh
  git clone <repository_url>
  ```

#### 3.2.3 Contributing to Open Source

- **Work on an Issue**  
  Identify the issue you want to resolve and create a new branch. Make changes, and then commit your work.

- **Commit, Push, and Create a Pull Request**  
  After completing your changes, push your branch to your GitHub repository and create a pull request (PR) to the original repository.

  ```sh
  git add .
  git commit -m "Fixes issue #X"
  git push origin <branch_name>
  ```

- **Open a Pull Request**  
  Go to the original repository and open a pull request to submit your changes for review.

### 3.3 Adding Collaborators to a Repository

- Go to the repository settings.
- Navigate to the "Collaborators" section.
- Add the GitHub username of the person you want to collaborate with.

## 4. Working with Visual Studio Code and GitHub

### 4.1 Opening GitHub Repository in VSCode

- **Open the repository on GitHub**  
  Use the "Open in VSCode" button to directly open the repository in VSCode.

- **Working in VSCode**  
  Once the repository is opened in VSCode, you can use the integrated terminal and GitHub tools to manage your repository directly from the editor.

## 5. Summary

This document covers:

- Key Git commands for managing repositories, branching, and committing changes.
- Operations like stashing changes, viewing logs, and merging branches.
- GitHub-specific actions, such as forking repositories, contributing to open-source projects, and adding collaborators.
- Practical steps for integrating Git with Visual Studio Code for seamless version control management.

**Key Tools:**
- `git` for version control.
- `GitHub` for remote repositories and collaboration.
- `VSCode` for code editing and version control integration.

<----------------------------------------------------------------------------->
Shoaib Notes

# Git & GitHub Documentation by Shoaib

This document explains the most commonly used Git and GitHub commands in a structured and easy-to-understand way. It serves as a reference for beginners working on version control and collaboration using Git.

---

## Basic Git Workflow

1. **Initialize a Git repository:**
   ```bash
   git init
   ```
   Initializes a new Git repository in the current folder.

2. **Track all files:**
   ```bash
   git add .
   ```
   Adds all files to the staging area.

3. **Commit the changes:**
   ```bash
   git commit -m "Your commit message"
   ```
   Commits the staged changes with a message.

4. **Connect to GitHub repository:**
   ```bash
   git remote add origin https://github.com/YourUsername/YourRepo.git
   ```
   Connects your local project to a remote repository.

5. **Push to GitHub (first time):**
   ```bash
   git push -u origin main
   ```
   Pushes the code to GitHub and sets the upstream branch.

---

## Switching Between Commits and Branches

6. **Checkout a specific commit:**
   ```bash
   git checkout <commit-id>
   ```
   Moves the HEAD to a specific commit in a detached state. You can make changes, but you won’t be on any branch.

7. **Switch back to the main branch:**
   ```bash
   git switch main
   ```
   Returns you to the `main` branch, discarding the detached HEAD.

8. **Create a new branch from the detached state:**
   ```bash
   git switch -c newBranch
   ```
   Creates and switches to a new branch, preserving changes made during detached HEAD.

9. **Push the new branch to GitHub:**
   ```bash
   git add .
   git commit -m "Commit message"
   git push --set-upstream origin newBranch
   ```

10. **Rename current branch:**
    ```bash
    git branch -M newBranchName
    ```

11. **Merge another branch into main:**
    ```bash
    git switch main
    git merge newBranch
    ```
    Resolve any conflicts using the merge editor, then complete the merge.

12. **Delete a branch after merge:**
    ```bash
    git branch -d newBranch
    ```

---

## Working with Git Stash

1. **Why stash?**
   If you’re working on changes but need to switch branches without committing, you can stash your work temporarily.

2. **Stash changes:**
   ```bash
   git stash
   ```
   Saves uncommitted changes.

3. **View list of stashes:**
   ```bash
   git stash list
   ```

4. **Apply a stash:**
   ```bash
   git stash apply
   ```
   Applies the latest stash (but keeps it in stash list).

5. **Apply and remove stash:**
   ```bash
   git stash pop
   ```
   Applies the latest stash and removes it from the list.

6. **Remove a specific stash:**
   ```bash
   git stash drop stash@{0}
   ```
   Deletes a particular stash from the list.

7. **Force checkout to another branch (not recommended unless needed):**
   ```bash
   git checkout -f otherBranch
   ```
   WARNING: This may discard changes. Prefer using `stash` instead.

---

## Contributing to Open Source

1. **Fork the repository** you want to contribute to.

2. **Clone your forked repo** to your computer.

3. **Make code changes and commit** them in a new branch.

4. **Push your branch to GitHub:**
   ```bash
   git push --set-upstream origin yourBranch
   ```

5. **Create a Pull Request:**
   - Compare changes between your branch and the original repo.
   - Submit with a title and description.

---

## Summary of Common Commands

| Command | Description |
|--------|-------------|
| `git init` | Initialize Git repo |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Commit changes |
| `git push` | Push changes to GitHub |
| `git pull` | Pull changes from GitHub |
| `git stash` | Temporarily save changes |
| `git stash apply` | Reapply stashed changes |
| `git switch` | Switch branches |
| `git branch -M` | Rename branch |
| `git merge` | Merge branches |

---

> 📌 **Tip:** Always use `git status` to check current state before switching branches or committing.

---

Prepared by: **Shoaib**

Happy Coding! 🚀

