## ✅ Step-by-Step: Push Code to GitHub Using VS Code

---

### 🔹 1. Prerequisites

Make sure you have:

* \[✔] **VS Code installed**: [https://code.visualstudio.com/](https://code.visualstudio.com/)
* \[✔] **Git installed**: [https://git-scm.com/downloads](https://git-scm.com/downloads)
* \[✔] **GitHub account**: [https://github.com](https://github.com)
* \[✔] (Optional but recommended) **GitHub extension for VS Code**
  Go to **Extensions (Ctrl+Shift+X)** → search for **GitHub Pull Requests and Issues** → install.

---

### 🔹 2. Set Up Git (if not done before)

In VS Code's **Terminal** (`` Ctrl+` ``) or CMD:

```bash
git config --global user.name "Your Full Name"
//Example, git config --global user.name "Ram"

git config --global user.email "your-email@example.com"
//Example, git config --global user.name "abc@gmail.com"
```

---

### 🔹 3. Open/Create Your Project in VS Code

* Open a folder (`File > Open Folder`) or create a new one in VS Code.
* Add some files (e.g., `index.html`, `app.py`, etc.)

---

### 🔹 4. Initialize Git in the Project

In the **VS Code Terminal** or top menu:

```bash
git init
```

Or click **Source Control icon** (left bar) → Click **Initialize Repository**.

---

### 🔹 5. Stage and Commit Changes

* Go to **Source Control panel** (icon that looks like a branch).
* Click the `+` icon to stage all changes.
* In the message box, type a commit message like `Initial commit`, then click the checkmark ✔️.

---

### 🔹 6. Create a GitHub Repository

1. Go to [GitHub](https://github.com)
2. Click **+ > New repository**
3. Name it (e.g., `my-project`)
4. Leave it **empty** (do NOT add README or .gitignore)
5. Click **Create repository**
6. Copy the HTTPS URL (e.g., `https://github.com/your-username/my-project.git`)

---

### 🔹 7. Link VS Code Project to GitHub Repo

In the **VS Code Terminal**:

```bash
git remote add origin https://github.com/your-username/my-project.git
git branch -M main
git push -u origin main
```

---

### ✅ Done!

Your code is now on GitHub.

---

### 🆓 Optional: Make It Easier Next Time

* **Sign in to GitHub in VS Code**:

  * Go to **View > Command Palette** (`Ctrl+Shift+P`)
  * Type and select: `GitHub: Sign in`
  * This lets you publish directly to GitHub from the Source Control panel.
