## ✅ **Assignment Analysis & Explanation**

### 🔹 **1. Prerequisites**

**Tools needed:**

* **VS Code**: Your code editor
* **Git**: To track and manage code changes
* **GitHub account**: Where the code is stored online
* *(Optional)* **GitHub extension for VS Code**: Helps manage issues, pull requests, etc., from inside the editor.

📌 **Why it's important**: Without these, version control and remote sync cannot happen.

---

### 🔹 **2. Git Configuration**

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

**Explanation**: This sets your identity globally for all Git commits. This info appears in your commit history on GitHub.

**Alternative**: You can configure these settings locally per repo using `--local` instead of `--global`.

---

### 🔹 **3. Open/Create Project in VS Code**

Start by working inside a folder. You can create files like:

* `index.html`
* `style.css`
* `script.js`

📌 **Why**: Git works at the folder (project) level, not on individual files.

---

### 🔹 **4. Initialize Git in the Folder**

```bash
git init
```

**What it does**: Creates a `.git` hidden folder and tells Git to start tracking changes here.

**Alternative**: Use **VS Code's Source Control panel** → “Initialize Repository”.

---

### 🔹 **5. Stage and Commit Changes**

* Staging: Prepares files to be included in the commit.
* Committing: Saves a snapshot of the current state with a message.

```bash
git add .
git commit -m "Initial commit"
```

**Alternative (GUI)**: Use the `+` button to stage and the ✔️ to commit in the Source Control tab.

---

### 🔹 **6. Create GitHub Repository**

Steps done on GitHub website:

* **Don’t initialize with README** (important!)
* This prevents merge conflicts during first push.

---

### 🔹 **7. Link Local Repo to GitHub Repo**

```bash
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main
```

**Explanation**:

* `remote add origin`: Connects local Git to GitHub repo.
* `branch -M main`: Renames current branch to `main`.
* `push -u origin main`: Pushes code and tracks the `main` branch.

---

## 🔄 **Alternatives / Improvements**

| Step            | Alternative                                                            |
| --------------- | ---------------------------------------------------------------------- |
| Git init + push | Use **GitHub Desktop** GUI for simpler interface                       |
| CLI commands    | Use **VS Code’s Git GUI**: Source Control panel for staging/committing |
| Push via CLI    | Use `Publish to GitHub` from Source Control panel (after signing in)   |
| Manual login    | Use **GitHub CLI** (`gh auth login`) for smoother auth                 |

---

## 🎤 **Viva Questions & Answers – Git & GitHub**

### 🔧 Basic Concepts

1. ❓ What is Git?

   * ✅ Git is a version control system used to track changes in code and collaborate with others.

2. ❓ What is GitHub?

   * ✅ GitHub is a cloud-based platform to host Git repositories online.

3. ❓ What is the difference between Git and GitHub?

   * ✅ Git is the tool; GitHub is the service that hosts your Git repositories.

4. ❓ What is `git init`?

   * ✅ It initializes a Git repository in your project folder.

5. ❓ What does `git add .` do?

   * ✅ It stages all modified and new files for the next commit.

6. ❓ What is a commit?

   * ✅ A snapshot of your project with a message describing the changes.

7. ❓ What does `git push` do?

   * ✅ It uploads your local commits to a remote repository like GitHub.

---

### 🔁 Remote & Branches

8. ❓ What is a remote repository?

   * ✅ A remote repository is a Git repo hosted online (e.g., GitHub).

9. ❓ What is the purpose of `git remote add origin`?

   * ✅ It connects your local repo to a GitHub repo so you can push code.

10. ❓ What does `-u` do in `git push -u origin main`?

* ✅ It sets the upstream so future pushes can use `git push` without specifying branch.

11. ❓ What is the difference between `main` and `master`?

* ✅ Both are default branch names; `main` is the newer convention replacing `master`.

12. ❓ What is a branch?

* ✅ A parallel version of your project where you can experiment without affecting main code.

---

### ⚠️ Troubleshooting & GUI

13. ❓ Why shouldn't you create a README in GitHub before pushing?

* ✅ It causes a conflict if your local repo has files and GitHub has different ones.

14. ❓ Can you push code without GitHub?

* ✅ Yes, Git can be used locally only, but pushing allows online backup and collaboration.

15. ❓ What does the `Source Control` icon in VS Code do?

* ✅ It shows tracked changes, lets you stage/commit, and optionally push/pull if connected to GitHub.

16. ❓ What does `git status` do?

* ✅ It shows which files are modified, staged, or untracked.

---

## 📝 **Summary: On-Paper Logic (Short Notes)**

```bash
# Set user details
git config --gl "Name"
git config --global user.email "email@example.com"

# Initialize repo
git init

# Stage and commit
git add .
git commit -m "Initial commit"

# Connect to GitHub
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

---
