# Sort Agent - User Manual

> Version 1.0 | Updated: 2026-02-27

---

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Dashboard Overview](#dashboard-overview)
4. [Task Modes](#task-modes)
5. [Step-by-Step Guide](#step-by-step-guide)
6. [File Selection](#file-selection)
7. [Protocol Handler Installation](#protocol-handler-installation)
8. [Troubleshooting](#troubleshooting)
9. [FAQ](#faq)

---

## Introduction

### What is Sort Agent?

Sort Agent is an intelligent document organization tool designed to work with Claude Code. It helps you:

- **Organize** documents automatically
- **Analyze** file content and relationships
- **Generate** summaries and tags
- **Create** structured documentation

### Who Should Use It?

- Developers managing project documentation
- Writers organizing content libraries
- Teams maintaining knowledge bases
- Anyone with large document collections

---

## Getting Started

### Prerequisites

1. **Claude Code** installed on your system
2. **Modern web browser** (Chrome, Edge, Firefox)
3. **Windows** (for protocol handler feature)

### First Launch

1. Open `dashboard.html` in your browser
2. You will see the main dashboard interface
3. Default directory is pre-loaded

---

## Dashboard Overview

### Main Sections

```
┌─────────────────────────────────────────────┐
│  🚀 Task Launcher                           │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐       │
│  │ Full    │ │ Quick   │ │ Analyze │       │
│  │ Organize│ │ Organize│ │ Only    │       │
│  └─────────┘ └─────────┘ └─────────┘       │
├─────────────────────────────────────────────┤
│  📋 Task Steps                              │
│  ☑ Scan Files    ☑ Read Content            │
│  ☑ Generate Summary  ☑ Add Tags            │
│  ☐ Similarity    ☐ README    ☐ Optimize    │
├─────────────────────────────────────────────┤
│  📁 Target Directory: [path]                │
│  [Start Execute]                            │
└─────────────────────────────────────────────┘
```

### Buttons

| Button | Function |
|--------|----------|
| Select Directory | Choose target folder |
| Full Organize | Select all 7 steps |
| Quick Organize | Select 4 essential steps |
| Analyze Only | Read-only analysis |
| Custom | Manual step selection |
| Start Execute | Generate and launch task |

---

## Task Modes

### Full Organize (7 Steps)

Complete document organization workflow:

1. **Scan Files** - Find all .md files
2. **Read Content** - Extract text
3. **Generate Summary** - 200-word summaries
4. **Add Tags** - Time, type, importance, topics
5. **Similarity Analysis** - Find duplicates
6. **Generate README** - Create index
7. **Optimize Structure** - Reorganize files

**Best for:** Complete documentation overhaul

### Quick Organize (4 Steps)

Fast processing without deep analysis:

1. Scan Files
2. Read Content
3. Generate Summary
4. Generate README

**Best for:** Quick documentation update

### Analyze Only (4 Steps)

Read-only analysis - no file modifications:

1. Scan Files
2. Read Content
3. Generate Summary
4. Add Tags

**Best for:** Understanding existing documentation

### Custom

Select individual steps manually.

**Best for:** Specific requirements

---

## Step-by-Step Guide

### Step 1: Select Directory

1. Click **"Select Directory"** button
2. Browse and select your document folder
3. Preview shows folder contents
4. Confirm or edit the path
5. Click **"Confirm Selection"**

### Step 2: Choose Task Mode

Click one of the mode buttons:
- Full Organize
- Quick Organize
- Analyze Only
- Custom

### Step 3: Review Steps

Check the selected steps in the task panel. For Custom mode, click individual steps to toggle.

### Step 4: Execute Task

1. Click **"Start Execute"**
2. Dialog shows generated prompt
3. Click **"Launch Claude Code"**
4. Click **"Copy Prompt"**
5. Switch to Claude Code window
6. Press **Ctrl+V** to paste
7. Press **Enter** to execute

---

## File Selection

### Folder Browser

When you click "Select Directory":

1. System folder dialog opens
2. Navigate to desired location
3. Select folder and confirm
4. Preview shows:
   - File count
   - Folder count
   - File types

### Supported File Types

| Extension | Type | Support |
|-----------|------|---------|
| .md | Markdown | Full |
| .txt | Text | Full |
| .html | HTML | Read |
| .json | JSON | Read |
| .py, .js | Code | Read |

### Path Format

Sort Agent automatically converts paths:
- Windows: `E:\folder\subfolder`
- Claude Code: `/e/folder/subfolder`

---

## Protocol Handler Installation

### What is Protocol Handler?

Protocol handler enables one-click launch of Claude Code from the browser.

### Installation Steps

1. In dashboard, click **"Download Installer"**
2. Save `install_launcher.bat`
3. Right-click → **Run as Administrator**
4. Confirm UAC prompt
5. Wait for completion message

### Verify Installation

1. Open Windows Registry (regedit)
2. Navigate to `HKEY_CLASSES_ROOT\claude-task`
3. Should show protocol configuration

### Uninstall

Delete the registry key at `HKEY_CLASSES_ROOT\claude-task`

---

## Troubleshooting

### Common Issues

#### "Directory not found"

**Solution:** Check path format. Use forward slashes for Claude Code.

```
Wrong: E:\folder\path
Right: E:/folder/path
```

#### "Claude Code not launching"

**Solution:**
1. Verify Claude Code is installed
2. Check PATH environment variable
3. Try manual launch first

#### "Prompt copied is encoded"

**Solution:** Click "Copy Prompt" button (green), not "Launch" button.

#### "Working directory wrong"

**Solution:** The prompt includes `cd` command. Wait for Claude Code to execute it first.

### Error Messages

| Error | Cause | Solution |
|-------|-------|----------|
| Protocol not registered | Handler not installed | Run installer |
| Path access denied | Permission issue | Run as admin |
| Empty directory | No .md files | Check folder |

---

## FAQ

### Q: Can I use Sort Agent with other AI tools?

A: Yes! The generated prompts work with any AI assistant that can execute shell commands.

### Q: Does Sort Agent modify my files?

A: Only in "Full Organize" mode with step 7 enabled. "Analyze Only" mode is read-only.

### Q: Can I customize the summary length?

A: Currently set to 200 words. Edit the prompt manually after copying.

### Q: Is my data sent anywhere?

A: No. All processing happens locally in Claude Code.

### Q: Can I use this on Mac/Linux?

A: The dashboard works in any browser. Protocol handler is Windows-only.

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Ctrl+V | Paste prompt in Claude Code |
| Enter | Send prompt |
| Esc | Cancel dialog |

---

## Support

For additional help:
- See [FRAMEWORK.md](./FRAMEWORK.md) for technical details
- See [README.md](./README.md) for overview

---

*Sort Agent User Manual v1.0*
