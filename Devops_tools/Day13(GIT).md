# Day 13: Git

## 1. Introduction to Git

### What is Git?
**Git** is a distributed version control system used to track changes in source code during software development. It allows multiple developers to collaborate on projects efficiently, managing different versions of files and facilitating code integration.

### Key Concepts:
- **Repository**: A Git repository (repo) is a storage location for your project, including its history.
- **Commit**: A snapshot of the changes made to files in the repository.
- **Branch**: A parallel version of the repository, used to develop features or fix bugs independently.
- **Merge**: The process of combining changes from different branches into a single branch.
- **Clone**: A copy of the repository that is used to work on locally.

---

## 2. Basic Git Commands

### A. Setting Up Git
1. **Install Git**:
   - Download and install Git from the [official Git website](https://git-scm.com/).

2. **Configure Git**:
   - Set your user name and email address for commits:
     ```bash
     git config --global user.name "Your Name"
     git config --global user.email "your.email@example.com"
     ```

### B. Creating a Repository
1. **Initialize a Repository**:
   - Create a new directory for your project and initialize Git:
     ```bash
     mkdir my-project
     cd my-project
     git init
     ```

2. **Clone an Existing Repository**:
   - Clone a remote repository to your local machine:
     ```bash
     git clone https://github.com/username/repository.git
     ```

### C. Basic Operations
1. **Checking Repository Status**:
   - View the status of files in the repository:
     ```bash
     git status
     ```

2. **Adding Changes**:
   - Add files to the staging area:
     ```bash
     git add filename
     ```
   - Add all changes:
     ```bash
     git add .
     ```

3. **Committing Changes**:
   - Commit the staged changes with a message:
     ```bash
     git commit -m "Commit message"
     ```

4. **Viewing Commit History**:
   - View the commit history of the repository:
     ```bash
     git log
     ```

---

## 3. Working with Branches

### A. Creating and Switching Branches
1. **Create a New Branch**:
   - Create a new branch and switch to it:
     ```bash
     git branch new-branch
     git checkout new-branch
     ```
   - Or use a single command:
     ```bash
     git checkout -b new-branch
     ```

2. **Switch Between Branches**:
   - Switch to an existing branch:
     ```bash
     git checkout branch-name
     ```

### B. Merging Branches
1. **Merge Branches**:
   - Merge changes from one branch into the current branch:
     ```bash
     git merge branch-name
     ```

2. **Resolve Merge Conflicts**:
   - Conflicts occur when changes overlap. Resolve conflicts manually and then complete the merge:
     ```bash
     git add resolved-file
     git commit
     ```

### C. Deleting Branches
1. **Delete a Local Branch**:
   - Delete a branch that is no longer needed:
     ```bash
     git branch -d branch-name
     ```

2. **Delete a Remote Branch**:
   - Delete a branch from the remote repository:
     ```bash
     git push origin --delete branch-name
     ```

---

## 4. Working with Remote Repositories

### A. Adding a Remote Repository
1. **Add Remote**:
   - Add a remote repository URL:
     ```bash
     git remote add origin https://github.com/username/repository.git
     ```

### B. Pushing Changes
1. **Push Local Changes**:
   - Push commits to the remote repository:
     ```bash
     git push origin branch-name
     ```

### C. Pulling Changes
1. **Pull Remote Changes**:
   - Fetch and merge changes from the remote repository:
     ```bash
     git pull origin branch-name
     ```

### D. Fetching Changes
1. **Fetch Remote Changes**:
   - Fetch changes from the remote repository without merging:
     ```bash
     git fetch origin
     ```

---

## 5. Best Practices for Git

### A. Commit Messages
- **Write Clear Messages**: Use meaningful commit messages that describe the changes made.
- **Format**: Follow a consistent format for commit messages, such as a short summary followed by a detailed description.

### B. Branch Management
- **Use Branches**: Create separate branches for features, bug fixes, or experiments to keep the main branch stable.
- **Regular Merges**: Regularly merge changes from feature branches to keep them up to date with the main branch.

### C. Collaboration
- **Pull Requests**: Use pull requests for code review and discussion before merging changes to the main branch.
- **Update Frequently**: Regularly pull changes from the remote repository to stay in sync with your team.

---

## Summary
Today, we covered **Git**, including how to set up a repository, perform basic operations, work with branches, and manage remote repositories. Git is a powerful tool for version control and collaboration in software development.

**Key Takeaways:**
- **Repositories**, **Commits**, and **Branches** are fundamental concepts in Git.
- Use **basic commands** to manage and track changes.
- Follow **best practices** for effective version control and collaboration.

---

### Next Session
In the next session, we will cover **GitHub** to understand how to use Git in conjunction with GitHub for repository hosting and collaboration.

---

**Thank you!**
