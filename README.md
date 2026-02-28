# Sort Agent

> **Intelligent Document Organization Agent**
> Version 1.0 | Updated: 2026-02-27

---

## Overview

**Sort Agent** is an intelligent document organization system designed for Claude Code. It provides a visual dashboard for managing, analyzing, and organizing document collections with AI-powered automation.

### Key Features

- **Visual Dashboard** - Interactive web interface for task management
- **Smart File Analysis** - Automatic summarization and tagging
- **Multiple Task Modes** - Full organize, Quick organize, Analyze only, Custom
- **One-Click Launch** - Direct integration with Claude Code
- **Protocol Handler** - System-level integration for seamless workflow

---

## Quick Start

### 1. Open Dashboard
```bash
# Open in browser
dashboard.html
```

### 2. Select Target Directory
Click "Select Directory" button to choose your document folder.

### 3. Choose Task Mode
| Mode | Description | Steps |
|------|-------------|-------|
| Full Organize | Complete workflow | 7 steps |
| Quick Organize | Fast processing | 4 steps |
| Analyze Only | Read-only analysis | 4 steps |
| Custom | User defined | Variable |

### 4. Execute Task
1. Click "Start Execute"
2. Click "Launch Claude Code"
3. Click "Copy Prompt"
4. Paste in Claude Code and press Enter

---

## Task Steps

Sort Agent supports up to 7 processing steps:

| Step | Name | Description |
|------|------|-------------|
| 1 | Scan Files | Find all .md files in directory |
| 2 | Read Content | Extract text from each file |
| 3 | Generate Summary | Create 200-word summaries |
| 4 | Add Tags | Time, type, importance, topics |
| 5 | Similarity Analysis | Find duplicates and similar content |
| 6 | Generate README | Create structured index |
| 7 | Optimize Structure | Rename, merge, archive files |

---

## Directory Structure

```
sort-agent/
├── dashboard.html          # Main dashboard interface
├── README.md               # This file
├── USER_MANUAL.md          # User manual
├── FRAMEWORK.md            # Development framework
├── CLAUDE_CODE_README_TEMPLATE.md
├── CLAUDE_CODE_TASK_PROMPT.md
├── ONE_PAGE_TEMPLATE.md
├── QUICK_USE.md
├── TEMPLATES_INDEX.md
├── FILE_ANALYSIS.md
├── EXECUTION_LOG.md
└── archive/                # Backup directory
```

---

## Configuration

### Task Modes

```javascript
const ruleSteps = {
    'full': [1, 2, 3, 4, 5, 6, 7],      // Complete workflow
    'quick': [1, 2, 3, 6],               // Skip analysis & optimization
    'analyze': [1, 2, 3, 4],             // Read-only analysis
    'custom': [1, 2, 3, 4, 5, 6, 7]      // User selectable
};
```

### File Types Supported

| Type | Icon | Color |
|------|------|-------|
| Markdown | 📝 | Blue |
| HTML | 🌐 | Orange |
| JavaScript | ⚡ | Yellow |
| JSON | 📋 | Green |
| Python | 🐍 | Blue |
| Images | 🖼️ | Purple |
| PDF | 📕 | Red |

---

## Protocol Handler

Sort Agent includes a custom protocol handler for one-click launch:

```
claude-task://[base64-encoded-data]
```

### Installation
1. Download `install_launcher.bat`
2. Run as Administrator
3. Confirm installation

### Usage
Click "Launch Claude Code" button in dashboard to automatically:
- Start Claude Code
- Copy prompt to clipboard
- Switch to target directory

---

## Requirements

- **Claude Code** - Anthropic's CLI tool
- **Modern Browser** - Chrome, Edge, Firefox
- **Windows** - For protocol handler (optional)

---

## License

MIT License - Free to use and modify

---

## Support

- **Documentation**: See [USER_MANUAL.md](./USER_MANUAL.md)
- **Development**: See [FRAMEWORK.md](./FRAMEWORK.md)
- **Issues**: Report via GitHub

---

*Sort Agent v1.0 - Intelligent Document Organization*
