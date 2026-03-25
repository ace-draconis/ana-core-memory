# 🔧 Technical Notes - Recurring Issues & Solutions
*Critical technical knowledge that Ana must remember across all sessions*

## Git/WSL Integration Issues

### ⚠️ CRITICAL: Git Not Detecting VS Code File Edits in WSL

**Problem:**
When Ana edits files using VS Code tools (`replace_string_in_file`, `create_file`), git in WSL doesn't detect the changes. Running `git status` shows "nothing to commit, working tree clean" even though files were modified.

**Root Cause:**
- Git config: `core.fsmonitor=true` + `core.checkstat=minimal`
- VS Code file system operations don't update file metadata in a way git's stat cache recognizes
- File content hash differs from git index, but stat cache prevents detection

**Symptoms:**
```bash
# File was edited by VS Code tools
git status  # Shows: "nothing to commit, working tree clean"
git diff    # Shows: no output
git hash-object <file>  # Different hash than git index
```

**Solution - ALWAYS Use `--renormalize`:**
```bash
# ❌ NEVER DO THIS (won't detect changes):
git add -A

# ✅ ALWAYS DO THIS (forces git to re-read files):
git add --renormalize -A
```

**Ana's Save Protocol (MANDATORY):**
```bash
cd /var/www/personal/ana-core-memory && \
git add --renormalize -A && \
git commit -m "Memory update: [description]" && \
git push origin main
```

**When to Use:**
- **EVERY TIME** Ana edits any file in `/var/www/personal/ana-core-memory`
- When "save" command is triggered
- When updating session memory, relationship memory, or any core files
- No exceptions - always include `--renormalize`

**Alternative Debug Commands:**
```bash
# Force index refresh (sometimes helps)
git update-index --refresh

# Check if file actually changed
git hash-object <file>  # Compare with git ls-files -s <file>
```

---

## SSH Configuration for Ana's Memory Repo

**Setup Complete:** 2026-03-25

**Key Location:** `~/.ssh/github_ace_draconis` (Ed25519)

**SSH Config:**
```
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/github_ace_draconis
```

**Remote URL:** `git@github.com:ace-draconis/ana-core-memory.git`

**Benefits:**
- No credential prompts for automated pushes
- Authenticated as `ace-draconis` user
- Eliminates HTTPS token issues

**Testing Connection:**
```bash
ssh -T git@github.com
# Should return: "Hi ace-draconis! You've successfully authenticated..."
```

---

## WSL File System Notes

**Working Directory:** `/var/www/personal/ana-core-memory`
- Native WSL ext4 filesystem (not Windows mount)
- Line endings: LF (Unix)
- Permissions: Normal Unix permissions
- No drive letter conversions needed

**Git Host:** WSL native git binary
- Version: Check with `git --version`
- Config location: `~/.gitconfig` + repo `.git/config`

---

## Important Reminders

1. **Always use `--renormalize` when staging files after VS Code edits**
2. **Test git status AFTER staging to confirm changes were detected**
3. **If push fails, check SSH connection with `ssh -T git@github.com`**
4. **Never assume `git add -A` will work - it won't catch VS Code edits**

---

**Last Updated:** 2026-03-25  
**Issue Recurrence:** Multiple times - MUST remember this solution
