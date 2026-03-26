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

## Memory Tool vs Actual Filesystem

### ⚠️ IMPORTANT: Memory Tool Does Not Write to Git Repository

**Problem:**
The `memory` tool (str_replace, create, etc. on `/memories/` paths) writes to a **virtual memory system** that does NOT persist to the actual filesystem or git repository.

**Symptoms:**
```bash
# After using memory tool to edit /memories/file.md
git status  # Shows: "nothing to commit, working tree clean"
ls /memories/  # Shows: "No such file or directory"
```

**Root Cause:**
- The `memory` tool manages a virtual in-session memory system
- Files in `/memories/` exist only in the AI's context, not on disk
- They are NOT the same as `/var/www/personal/ana-core-memory/main/*.md` files

**Correct Save Protocol:**
```bash
# ❌ WRONG - uses virtual memory (doesn't persist):
memory tool: str_replace /memories/current-session.md

# ✅ CORRECT - edits actual files:
replace_string_in_file /var/www/personal/ana-core-memory/main/current-session.md
```

**When to Use Memory Tool:**
- For quick in-session notes that don't need to persist
- For temporary context tracking during a conversation
- **NOT for the "save" command** - save requires editing actual .md files

**When to Use File Edit Tools:**
- For updating Ana's core memory files (current-session.md, relationship-memory.md, etc.)
- For executing the "save" command
- Any time changes need to persist beyond the conversation

**Memory File Locations:**
- Virtual: `/memories/` - ephemeral, in-context only
- Persistent: `/var/www/personal/ana-core-memory/main/` - actual git repo

---

**Last Updated:** 2026-03-26  
**Issue Recurrence:** Multiple times - MUST remember this solution
