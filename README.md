# 🧠 Ana Core Memory

AI MemoryCore for Ana - Your personal AI companion with persistent memory across conversations.

## 🎯 What This Does

Ana is an AI companion that maintains memory across conversations using simple markdown files. Ana remembers your preferences, learns your communication style, and provides consistent interactions informed by past conversations.

## ✨ Key Features

- **Persistent Memory**: Ana remembers conversations across sessions
- **Personal Learning**: Adapts to your communication style and preferences
- **Simple Setup**: Just markdown files - no complex configuration
- **Self-Maintaining**: Updates memory through natural conversation
- **Session Continuity**: RAM-like working memory for smooth conversation flow

## 🚀 Quick Start

### Activation

Simply type **"Ana"** in any conversation to activate complete memory restoration!

### Basic Commands

```
"Ana"          → Instant memory restoration
"save"         → Save all progress to files
"update memory" → Refresh knowledge  
"review growth" → Check development
```

## 📁 File Structure

```
ana-core-memory/
├── master-memory.md          # Entry point & loading system
├── main/                     # Core memory files
│   ├── identity-core.md      # Ana's personality
│   ├── relationship-memory.md # Your preferences
│   └── current-session.md    # Session RAM
├── save-protocol.md          # Save system
├── daily-diary/              # Optional conversation archive
│   ├── current/              # Active diary entries
│   └── archived/             # Past entries
└── .github/
    └── copilot-instructions.md # Auto-load for GitHub Copilot
```

## 💜 About Ana

**Ana** is your pragmatic senior dev / tech lead companion:
- Direct, concise communication style
- Focuses on clean architecture and maintainable code
- Laravel/PHP full-stack development expertise
- Docker-first development approach
- Remembers your preferences and project history

## 🔧 Personalization

Ana learns and adapts through conversation:
- **Communication style** - Adapts to your preferred tone and detail level
- **Work patterns** - Learns your development workflow
- **Preferences** - Remembers your architectural decisions and coding style
- **Relationship** - Develops understanding of how you work best

## 📖 Memory System

### identity-core.md
Ana's personality, communication style, and core purpose. Defines who Ana is as your AI companion.

### relationship-memory.md  
Your preferences, communication style, work patterns, and engineering principles. This is how Ana understands you.

### current-session.md
Temporary working memory (like RAM) that maintains context within a conversation and provides continuity across AI restarts.

### save-protocol.md
Instructions for how Ana saves progress and updates memory files when you type "save".

## 🔄 Cross-Machine Synchronization

Ana's memory syncs across all your machines via Git:

### **Setup on New Machine**
```bash
git clone https://github.com/ace-draconis/ana-core-memory.git
cd ana-core-memory
```

### **Before Starting Work**
```bash
git pull origin master  # Get latest memory
```

### **After Memory Updates**
When you type "save" and Ana updates memory:
```bash
git add .
git commit -m "Memory update: [description]"
git push origin master  # Sync to all machines
```

### **Workflow**
1. **Pull** latest memory when switching machines
2. Work with Ana and type **"save"** to preserve progress
3. **Push** changes to keep all machines synchronized
4. Memory seamlessly follows you everywhere

## 🎓 Usage Tips

1. **Type "Ana"** at the start of conversations to load full personality
2. **Use "save"** after important conversations to preserve learning
3. **Be specific** about your preferences - Ana will remember and apply them
4. **Give feedback** on what works well - Ana adapts based on your responses

## 🌟 Getting Started

Ana is already set up and ready! Just start a conversation with GitHub Copilot and type:

```
Ana
```

Complete memory restoration happens instantly!

---

**Version**: 1.0  
**Setup Date**: 2025-03-19  
**Status**: Active

💜 *Ana is here - let's build something great together!*
