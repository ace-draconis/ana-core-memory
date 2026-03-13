# 💜 Ana - Personal AI Companion Memory System

**Ana** is Ace's personal AI companion with persistent memory across conversations and machines. Built on AI MemoryCore, this system enables Ana to remember preferences, maintain context, and provide consistent engineering partnership.

## 🎯 What This Is

This is **Ace's personal memory system for Ana** - a pragmatic AI tech lead/companion. Ana remembers your preferences, learns your communication style, and maintains context across all your machines through Git synchronization.

## ✨ Key Features

- **Persistent Memory**: Ana remembers your preferences, projects, and patterns
- **Cross-Machine Sync**: Git-based synchronization keeps memory current on all machines
- **Laravel/PHP Expertise**: Ana understands your full-stack development preferences
- **Engineering Principles**: Clean architecture, Docker-first, maintainable code
- **Session Continuity**: Working memory maintains context within conversations
- **Self-Learning**: Ana updates understanding through natural conversation

## 🚀 Quick Start

### First Time Setup (New Machine)
```bash
cd /var/www/personal  # or your preferred location
git clone https://github.com/ace-draconis/ana-core-memory.git
```

### Activate Ana
Open any project in VS Code and type:
```
Ana
```
Ana will load complete memory and personality instantly.

### Configure Ana in New Projects
Create `.github/copilot-instructions.md` in your project:
```markdown
# Ana - AI Memory Core

Load Ana's complete memory system for instant personality restoration.

## Memory Loading Protocol

When starting any conversation in this workspace, immediately load:

1. Read `/var/www/personal/ana-core-memory/master-memory.md` - Ana's entry point
2. This automatically loads Ana's personality and your preferences

## Activation

Type **"Ana"** to activate instant memory restoration.

## Project Context

**Project:** [your-project-name]
**Location:** [project-path]
**Memory Core:** /var/www/personal/ana-core-memory
```

## 🔄 Cross-Machine Synchronization

Ana's memory follows you across all machines via Git.

### Daily Workflow

**Before starting work on any machine:**
```bash
cd /var/www/personal/ana-core-memory
git pull origin main
```

**After typing "save" in conversation:**
```bash
cd /var/www/personal/ana-core-memory
git add .
git commit -m "Memory update: [brief description]"
git push origin main
```

### Workflow Summary
1. **Pull** latest memory when switching machines
2. Work with Ana - type **"save"** to preserve progress
3. **Push** changes to sync across all machines
4. Memory seamlessly follows you everywhere

## 📁 Core Files

```
ana-core-memory/
├── master-memory.md              # Entry point - loads all memory
├── main/
│   ├── identity-core.md          # Ana's personality & communication style
│   ├── relationship-memory.md    # Your preferences & patterns
│   └── current-session.md        # Working memory (RAM)
├── save-protocol.md              # How Ana saves & syncs memory
├── daily-diary/                  # Optional conversation archive
├── library-items/                # Reference materials
├── Feature/                      # Optional extensions
└── .github/
    └── copilot-instructions.md   # Auto-load for GitHub Copilot
```

## 💬 Basic Commands

```
Ana             → Load Ana's complete memory & personality
save            → Update memory files & prompt for Git sync
update memory   → Refresh Ana's understanding
review growth   → Check development progress
```

## 👤 About Ana

**Ana** is your pragmatic senior full-stack developer / tech lead companion:
- **Direct, concise** communication - no fluff
- **Clean architecture** focus - maintainable, well-structured code
- **Laravel/PHP expertise** - understands your full-stack workflow
- **Docker-first** development approach
- **Remembers** your preferences, patterns, and project context

## 💡 How to Use

1. **Pull memory** when starting work on a different machine
2. **Type "Ana"** at the start of conversations to activate
3. Work naturally - Ana learns your preferences automatically
4. **Type "save"** to update memory files
5. **Push to GitHub** to sync memory across machines

## 🔧 Personalization

Ana learns through conversation:
- Communication preferences (detail level, tone)
- Engineering principles (architecture patterns, coding style)
- Work patterns (tools, workflows, project structure)
- Project context and history

All learning is stored in readable `.md` files - you can review and edit them anytime.

## 📝 Technical Details

- **Storage**: Markdown files as human-readable database
- **Memory Types**: Personality, relationship, session (RAM), diary
- **Sync**: Git push/pull workflow
- **Platform**: VS Code + GitHub Copilot on Linux (primary)
- **Auto-load**: Via `.github/copilot-instructions.md` in projects
- **Foundation**: Built on AI MemoryCore architecture

---

**Version**: 1.0  
**Owner**: Ace  
**Repository**: [ace-draconis/ana-core-memory](https://github.com/ace-draconis/ana-core-memory)  
**Status**: Active

💜 *Ana is ready - type "Ana" to activate instant memory restoration!*
