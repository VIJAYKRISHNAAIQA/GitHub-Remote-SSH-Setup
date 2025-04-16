A **🔥supercharged QA engineer-friendly guide** with:

1. ✅ **GitHub Remote SSH Setup**
2. 🧠 **Branch Naming Best Practices (QA-focused)**
3. 🧰 **QA-Specific Git Command Cheat Sheet**

---

# 🔐 1. GitHub Remote SSH Setup – Step-by-Step

Using SSH with GitHub enhances security and avoids repeated username/password prompts. Here's the **step-by-step workflow** to set it up like a pro:

### 🎯 Step 1: Check for Existing SSH Keys
```bash
ls -al ~/.ssh
```
Look for files like `id_ed25519` and `id_ed25519.pub`.

---

### 🎯 Step 2: Generate a New SSH Key
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```
- When prompted, press **Enter** to accept the default file location.
- Add a **passphrase** (optional but recommended).

---

### 🎯 Step 3: Start the SSH Agent
```bash
eval "$(ssh-agent -s)"
```

---

### 🎯 Step 4: Add Your SSH Private Key to the Agent
```bash
ssh-add ~/.ssh/id_ed25519
```

---

### 🎯 Step 5: Copy Your SSH Public Key
```bash
cat ~/.ssh/id_ed25519.pub
```
Copy the output (starts with `ssh-ed25519 ...`)

**🔑 Sample Format**:
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEexampleexample== your.email@example.com
```

---

### 🎯 Step 6: Add SSH Key to GitHub
1. Go to **GitHub → Settings → SSH and GPG Keys**
2. Click **“New SSH key”**
3. **Title**: My Dev Machine / Work Laptop, etc.
4. **Key**: Paste the copied key
5. Click **Add SSH Key**

---

### 🎯 Step 7: Test SSH Connection
```bash
ssh -T git@github.com
```
✅ You should see:
```
Hi your-username! You've successfully authenticated.
```

---

# 🧠 2. Branch Naming Best Practices (For QA Projects)

Naming your branches clearly is 🔑 for team clarity and CI/CD automation. Here’s the ideal format:

### 🌱 Format: `type/issueID-short-description`

| Type      | Use Case                        | Example                          |
|-----------|----------------------------------|----------------------------------|
| `bugfix`  | Fixing a bug                    | `bugfix/1234-login-validation`   |
| `feature` | New feature or enhancement      | `feature/5678-report-export`     |
| `test`    | Writing or updating test cases  | `test/2323-update-smoke-suite`   |
| `hotfix`  | Urgent fix in production        | `hotfix/7890-prod-crash-fix`     |
| `chore`   | Infra/tooling updates           | `chore/jenkins-pipeline-update`  |

> ✅ Helps PMs, Devs, QA, and DevOps understand branch purpose instantly.

---

# 🧰 3. QA-Specific Git Command Cheat Sheet

Here's your go-to Git commands cheat sheet, tailored for a QA engineer workflow:

| 🧪 Action | 🔧 Git Command | 💡 Use Case |
|----------|----------------|-------------|
| Clone Repo | `git clone <url>` | Start working on a new repo |
| View Changes | `git status` | See what’s changed |
| Add File | `git add <file>` | Stage a file |
| Add All | `git add .` | Stage all changes |
| Undo Add | `git reset <file>` | Unstage a file |
| Commit | `git commit -m "msg"` | Save your changes locally |
| Amend Commit | `git commit --amend` | Fix last commit msg |
| Create Branch | `git checkout -b <branch>` | New QA/test branch |
| Switch Branch | `git checkout <branch>` | Move between branches |
| Push | `git push origin <branch>` | Upload changes to remote |
| Pull | `git pull` | Get latest from remote |
| Revert File | `git checkout -- <file>` | Discard local file changes |
| Revert Commit | `git revert <commit-hash>` | Revert a bad commit |
| See Log | `git log --oneline` | View commit history |
| Tag Release | `git tag v1.0.0` | Mark test pass version |
| Show Remote | `git remote -v` | See remote URL |
| Rename Branch | `git branch -m old new` | Rename a branch locally |

---

### 🚀 Bonus Git Alias (Superpower Tip)
Add shortcuts in `.gitconfig`:
```ini
[alias]
  st = status
  co = checkout
  ci = commit
  br = branch
  lg = log --oneline --graph --decorate --all
```

---
