# Sort Agent - Development Framework

> Technical Documentation for Developers
> Version 1.0 | Updated: 2026-02-27

---

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [File Structure](#file-structure)
3. [Core Components](#core-components)
4. [Data Flow](#data-flow)
5. [API Reference](#api-reference)
6. [Configuration](#configuration)
7. [Extension Guide](#extension-guide)
8. [Protocol Handler](#protocol-handler)

---

## Architecture Overview

### System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Sort Agent System                        │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │  Dashboard  │───▶│   Prompt    │───▶│   Claude    │     │
│  │   (HTML)    │    │  Generator  │    │    Code     │     │
│  └─────────────┘    └─────────────┘    └─────────────┘     │
│         │                  │                   │            │
│         ▼                  ▼                   ▼            │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │   File      │    │   Task      │    │   Document  │     │
│  │   System    │    │   Engine    │    │   Storage   │     │
│  └─────────────┘    └─────────────┘    └─────────────┘     │
└─────────────────────────────────────────────────────────────┘
```

### Technology Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| Storage | LocalStorage, FileSystem API |
| Integration | Custom Protocol Handler |
| Runtime | Claude Code CLI |

---

## File Structure

```
sort-agent/
├── dashboard.html              # Main application (single file)
│   ├── CSS Styles             # Embedded <style>
│   ├── HTML Structure         # UI components
│   └── JavaScript Logic       # Application logic
│
├── Documentation/
│   ├── README.md              # Project overview
│   ├── USER_MANUAL.md         # User guide
│   ├── FRAMEWORK.md           # This file
│   ├── FILE_ANALYSIS.md       # Analysis reports
│   └── EXECUTION_LOG.md       # Execution history
│
├── Templates/
│   ├── CLAUDE_CODE_README_TEMPLATE.md
│   ├── CLAUDE_CODE_TASK_PROMPT.md
│   ├── ONE_PAGE_TEMPLATE.md
│   ├── QUICK_USE.md
│   └── TEMPLATES_INDEX.md
│
└── archive/                    # Backup storage
```

---

## Core Components

### 1. Dashboard (dashboard.html)

Main application file containing all UI and logic.

**Key Sections:**
- CSS Variables for theming
- Responsive grid layout
- Interactive components
- State management

### 2. File Data Model

```javascript
const files = [
    {
        name: 'document.md',
        type: 'template',           // template, guide, log, analysis
        typeName: 'Template',
        importance: 5,              // 1-5 stars
        lines: 438,
        size: '~14 KB',
        summary: 'Document summary...',
        topics: ['topic1', 'topic2'],
        keywords: ['keyword1', 'keyword2']
    }
];
```

### 3. Task Configuration

```javascript
// Rule definitions
const ruleSteps = {
    'full': [1, 2, 3, 4, 5, 6, 7],
    'quick': [1, 2, 3, 6],
    'analyze': [1, 2, 3, 4],
    'custom': [1, 2, 3, 4, 5, 6, 7]
};

// Step definitions
const stepDefinitions = {
    1: { name: 'Scan Files', desc: '...', time: 500 },
    2: { name: 'Read Content', desc: '...', time: 1000 },
    3: { name: 'Generate Summary', desc: '...', time: 1500 },
    4: { name: 'Add Tags', desc: '...', time: 1000 },
    5: { name: 'Similarity Analysis', desc: '...', time: 2000 },
    6: { name: 'Generate README', desc: '...', time: 1000 },
    7: { name: 'Optimize Structure', desc: '...', time: 1500 }
};
```

---

## Data Flow

### Task Execution Flow

```
User Action
    │
    ▼
┌─────────────┐
│ Select Mode │
└─────┬───────┘
      │
      ▼
┌─────────────┐
│ Select Steps│
└─────┬───────┘
      │
      ▼
┌─────────────┐
│Select Target│
└─────┬───────┘
      │
      ▼
┌─────────────┐
│ Generate    │
│ Prompt      │
└─────┬───────┘
      │
      ▼
┌─────────────┐
│ Launch/     │
│ Copy        │
└─────┬───────┘
      │
      ▼
┌─────────────┐
│ Claude Code │
│ Execution   │
└─────────────┘
```

### Prompt Generation

```javascript
function generatePrompt(targetDir, steps) {
    // 1. Convert path format
    const unixPath = targetDir.replace(/\\/g, '/');

    // 2. Build step descriptions
    const stepDescriptions = {...};

    // 3. Generate prompt template
    const prompt = `
请先切换到目标工作目录：
\`\`\`bash
cd "${unixPath}" && pwd
\`\`\`

**目标目录**: ${targetDir}
**执行步骤**: ${selectedSteps}
...
    `;

    return prompt;
}
```

---

## API Reference

### Core Functions

#### Directory Functions

```javascript
// Browse folder with preview
async function browseFolder()

// Get current target directory
function getTargetDir()

// Fallback for older browsers
function fallbackBrowse()
```

#### Task Functions

```javascript
// Execute selected task
function executeTask()

// Generate prompt content
function generatePrompt(targetDir, steps)

// Select rule template
function selectRule(element, rule)
```

#### Launch Functions

```javascript
// One-click launch via protocol
function oneClickLaunch()

// Copy prompt only
function copyPromptOnly()

// Download batch script
function downloadScript()
```

#### UI Functions

```javascript
// Show execution dialog
function showExecutionDialog(promptContent, targetDir)

// Show notification
function showNotification(message, type)

// Update step count
function updateSelectedCount()
```

---

## Configuration

### CSS Variables

```css
:root {
    --primary: #6366f1;
    --primary-dark: #4f46e5;
    --secondary: #64748b;
    --success: #10b981;
    --warning: #f59e0b;
    --error: #ef4444;
    --bg: #f8fafc;
    --card: #ffffff;
    --text: #1e293b;
    --text-muted: #64748b;
    --border: #e2e8f0;
}
```

### LocalStorage Keys

| Key | Purpose |
|-----|---------|
| `customDirs` | Saved custom directories |
| `lastSelectedDir` | Last selected directory |

### Step Timing

```javascript
const stepTiming = {
    1: 500,    // Scan - fast
    2: 1000,   // Read - medium
    3: 1500,   // Summary - slower
    4: 1000,   // Tags - medium
    5: 2000,   // Similarity - slowest
    6: 1000,   // README - medium
    7: 1500    // Optimize - slower
};
```

---

## Extension Guide

### Adding New Task Mode

1. Define rule steps:
```javascript
const ruleSteps = {
    // ... existing rules
    'newmode': [1, 2, 3]  // Add new mode
};
```

2. Add rule name:
```javascript
const ruleNames = {
    // ... existing names
    'newmode': 'New Mode Name'
};
```

3. Add UI button in dashboard.html

### Adding New Step

1. Define step:
```javascript
stepDefinitions[8] = {
    name: 'New Step',
    desc: 'Description',
    time: 1000
};
```

2. Update step count in UI

### Adding File Type Support

```javascript
function getFileType(filename) {
    const types = {
        // ... existing types
        'newext': { icon: '📄', color: '#color', name: 'New Type' }
    };
}
```

---

## Protocol Handler

### Protocol URL Format

```
claude-task://[base64-encoded-data]
```

### Data Encoding

```javascript
// Encoding
const taskData = targetDir + '|||' + prompt;
const encodedData = btoa(unescape(encodeURIComponent(taskData)));
const protocolUrl = 'claude-task://' + encodedData;

// Decoding (in VBScript handler)
decodedData = URLDecode(encodedData)
targetDir = Split(decodedData, "|||")(0)
taskPrompt = Split(decodedData, "|||")(1)
```

### Registry Structure

```
HKEY_CLASSES_ROOT\claude-task
├── (Default) = "URL:Claude Task Protocol"
├── URL Protocol = ""
└── shell\open\command
    └── (Default) = "wscript.exe path\to\launcher.vbs "%1""
```

### VBScript Handler

```vbscript
' Parse protocol URL
encodedData = args(0)
decodedData = URLDecode(encodedData)

' Extract components
targetDir = Split(decodedData, "|||")(0)
taskPrompt = Split(decodedData, "|||")(1)

' Copy to clipboard
shell.Run "cmd /c echo " & prompt & " | clip", 0, True

' Launch Claude Code
launchCmd = "cmd /k cd /d """ & targetDir & """ && claude"
shell.Run launchCmd, 1, False
```

---

## Build & Deployment

### Single File Deployment

Dashboard is self-contained in `dashboard.html`:
- No external dependencies
- No build process required
- Direct browser execution

### Distribution Package

```
sort-agent-v1.0.zip
├── dashboard.html
├── README.md
├── USER_MANUAL.md
├── FRAMEWORK.md
├── install_launcher.bat
└── launcher.vbs
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-02-27 | Initial release |

---

## Contributing

1. Fork the repository
2. Create feature branch
3. Make changes
4. Submit pull request

---

## License

MIT License

---

*Sort Agent Framework v1.0*
