---
title: macOS Python + dbt Setup Guide
layout: default
---

# 💻 macOS Setup Guide: Python, dbt, and VS Code

A complete guide to cleanly set up Python, dbt (Cloud or Core), and VS Code using a virtual environment on macOS.

## 📦 Prerequisites

- macOS with Homebrew installed
- Terminal access
- GitHub account

## ✅ Step-by-Step Setup

### 🧼 1. (Optional) Uninstall VS Code
```bash
rm -rf "/Applications/Visual Studio Code.app"
rm -rf ~/Library/Application\ Support/Code ~/.vscode
rm -rf ~/Library/Preferences/com.microsoft.VSCode*
rm -rf ~/Library/Caches/com.microsoft.VSCode*
rm -rf ~/Library/Saved\ Application\ State/com.microsoft.VSCode*
```

### 🔁 2. Reinstall VS Code
```bash
brew uninstall --cask visual-studio-code
brew cleanup
brew install --cask visual-studio-code
open -a "Visual Studio Code"
```

### 🐍 3. Reinstall Python (Homebrew)
```bash
brew uninstall python@3.11
brew install python@3.11
echo 'export PATH="/opt/homebrew/opt/python@3.11/bin:$PATH"' >> ~/.zprofile
source ~/.zprofile
python3 --version
```

### 📁 4. Create Project Folder
```bash
mkdir -p ~/Projects/my-dbt-project
cd ~/Projects/my-dbt-project
```

### 🧪 5. Create & Activate Virtual Environment
```bash
python3 -m venv .venv
source .venv/bin/activate
which python
```

### 📦 6. Install dbt in `.venv`
**dbt Cloud CLI**
```bash
pip install --upgrade pip
pip install dbt-cloud-cli
```

**dbt Core + Adapter**
```bash
pip install dbt-core dbt-snowflake
```

### 💻 7. Open Project in VS Code
```bash
code ~/Projects/my-dbt-project
```

### ⚙️ 8. Set Python Interpreter
- Press ⇧⌘P → Python: Select Interpreter
- Pick `.venv/bin/python` or enter the path manually

### 🧾 9. Optional VS Code Settings
Create `.vscode/settings.json`:
```json
{
  "python.defaultInterpreterPath": "${workspaceFolder}/.venv/bin/python",
  "python.terminal.activateEnvironment": true,
  "terminal.integrated.env.osx": {
    "VIRTUAL_ENV": "${workspaceFolder}/.venv",
    "PATH": "${workspaceFolder}/.venv/bin:${env:PATH}"
  }
}
```

### 🔍 10. Final Test
```bash
which python
which dbt
dbt --version
```

## ✅ You're Ready!
- Clean `.venv`
- dbt working
- VS Code integrated

© 2025 Your Name
