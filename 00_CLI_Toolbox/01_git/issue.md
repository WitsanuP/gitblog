## 🐛 issue001: "git clone" only shows main branch, cannot see other branches

### 📝 Describe the bug
After running `git clone <repo_url>`, running `git branch` only displays the `main` branch. The `feature` branch appears to be missing from the local repository.

### 💡 Cause
This is standard Git behavior. `git clone` downloads **all** branches from the server, but it only creates a local pointer for the default branch (`main`) to keep your workspace clean. The other branches are safely stored in the background as remote tracking branches.

---

### 🛠️ Solution

#### Step 1: Check hidden remote branches
Run this command to list all branches, including the ones hidden on the remote server:
```bash
git branch -a
# Look for: remotes/origin/feature
