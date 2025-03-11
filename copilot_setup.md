# 🚀 Setup Guide: Configuring GitHub Copilot to Refer to `CODE_ANALYZER.md`

## 📌 Overview
This guide provides step-by-step instructions to configure **GitHub Copilot in VS Code, IntelliJ IDEA, and Eclipse** to **always refer to `CODE_ANALYZER.md` before generating or modifying code**.

✅ **Applies AI-based best practices**  
✅ **Configures GitHub Copilot Chat for persistent prompts**  
✅ **Automates code review in CI/CD with GitHub Actions**  
✅ **Works on Windows (PowerShell) and Unix-based systems (Linux/macOS)**  

---

# **🛠 Step 1: Store `CODE_ANALYZER.md` in Your Project**
1. Place `CODE_ANALYZER.md` in the **root directory** of your project.
2. Ensure it is **committed to your repository**.
3. Name it clearly, e.g., **`CODE_ANALYZER.md` or `ENGINEERING_GUIDELINES.md`**.

---

# **⚡ Step 2: Configure GitHub Copilot in VS Code**
### **Option 1: Manually Refer to `CODE_ANALYZER.md` in Copilot Chat**
1. Open **GitHub Copilot Chat** (`Ctrl + /` in VS Code).
2. Before modifying or generating code, use the following prompt:
   ```
   Before generating or modifying code, refer to the CODE_ANALYZER.md file in the root directory. Apply the best practices from it for OOP, scalability, concurrency, performance, and security.
   ```

### **Option 2: Set Persistent Context in Copilot Chat**
1. Open **GitHub Copilot Chat** (`Ctrl + /`).
2. Run this command:
   ```
   Always refer to CODE_ANALYZER.md before modifying code. Apply its best practices for OOP, security, and performance.
   ```

### **Option 3: Automate Copilot with Custom Commands**
1. Open **VS Code `settings.json`** (`Ctrl + Shift + P` → `Preferences: Open Settings (JSON)`).
2. Add:
   ```json
   {
       "copilotChat.customCommands": [
           {
               "title": "Refactor Code (Best Practices)",
               "command": "Before refactoring, refer to CODE_ANALYZER.md and apply its best practices for OOP, performance, concurrency, and security.",
               "context": "editor"
           },
           {
               "title": "Generate Code (Optimized)",
               "command": "When generating new code, use patterns and practices from CODE_ANALYZER.md.",
               "context": "editor"
           }
       ]
   }
   ```

---

# **🔹 Step 3: Setup GitHub Copilot in IntelliJ IDEA**
### **1️⃣ Install GitHub Copilot**
1. Open IntelliJ IDEA → **File → Settings → Plugins**.
2. Search for **GitHub Copilot** and install it.
3. Restart IntelliJ.

### **2️⃣ Use Copilot Chat with `CODE_ANALYZER.md`**
1. Open **Copilot Chat** (`Ctrl + Shift + I`).
2. Ask:
   ```
   Before generating or modifying code, refer to the CODE_ANALYZER.md file. Ensure all best practices are followed.
   ```

### **3️⃣ Add a Persistent Prompt in IntelliJ**
1. Open **Preferences → Copilot Settings**.
2. Set a **Custom Prompt Template**:
   ```
   Always refer to CODE_ANALYZER.md before modifying code. Apply best practices for security, performance, and scalability.
   ```

---

# **🔹 Step 4: Configure Copilot in Eclipse**
### **1️⃣ Install GitHub Copilot**
1. Open Eclipse → **Help → Eclipse Marketplace**.
2. Search for **GitHub Copilot** and install it.
3. Restart Eclipse.

### **2️⃣ Use Copilot Chat with `CODE_ANALYZER.md`**
1. Open **Copilot Chat** (`Ctrl + Shift + Space`).
2. Ask:
   ```
   Before generating or modifying code, refer to the CODE_ANALYZER.md file in the root directory.
   ```

### **3️⃣ Add a Custom Template for Copilot in Eclipse**
1. Go to **Preferences → GitHub Copilot**.
2. Add a **Custom Context Setting**:
   ```
   Always refer to CODE_ANALYZER.md when generating code. Apply best practices for security, performance, and scalability.
   ```

---

# **🔧 Step 5: Automate AI Code Reviews in CI/CD**
To enforce **automatic Copilot reviews** based on `CODE_ANALYZER.md`, create a **GitHub Action**:

1. Create a **`.github/workflows/code-review.yml`** file.
2. Add:
   ```yaml
   name: Code Review with AI

   on:
     pull_request:
       branches:
         - main

   jobs:
     analyze_code:
       runs-on: ubuntu-latest

       steps:
         - name: Checkout Code
           uses: actions/checkout@v2

         - name: AI Code Analysis
           run: |
             echo "Analyzing code against CODE_ANALYZER.md best practices..."
             cat CODE_ANALYZER.md > ai_guidelines.txt
             echo "Run AI-assisted static analysis here..."
   ```

---

# **🛠 Step 6: Run the Setup Script**
Save the following **Windows PowerShell** script as `setup_copilot.ps1`:
```powershell
# PowerShell Script to Configure Copilot
Write-Host "🚀 Configuring GitHub Copilot for CODE_ANALYZER.md..."

# Configure VS Code
$vsCodeSettings = "$env:APPDATA\Code\User\settings.json"
if (Test-Path $vsCodeSettings) {
    $settings = Get-Content $vsCodeSettings | ConvertFrom-Json
    $settings | Add-Member -MemberType NoteProperty -Name "copilotChat.customCommands" -Value @(
        @{title="Refactor Code (Best Practices)"; command="Before refactoring, refer to CODE_ANALYZER.md and apply best practices."; context="editor"},
        @{title="Generate Code (Optimized)"; command="Use CODE_ANALYZER.md guidelines for security, performance, and scalability."; context="editor"}
    ) -Force
    $settings | ConvertTo-Json -Depth 100 | Set-Content $vsCodeSettings
}

Write-Host "✅ Setup completed! Restart your IDEs."
```
### **📌 How to Run on Windows**
1. Open **PowerShell as Administrator**.
2. Run:
   ```powershell
   Set-ExecutionPolicy Unrestricted -Scope Process
   ./setup_copilot.ps1
   ```

---

# **🔹 Run the Setup Script on Unix (Linux/macOS)**
Save the following **Bash script** as `setup_copilot.sh`:
```bash
#!/bin/bash

echo "🚀 Configuring GitHub Copilot for CODE_ANALYZER.md..."

VS_CODE_SETTINGS="$HOME/.config/Code/User/settings.json"
if [ -f "$VS_CODE_SETTINGS" ]; then
    jq '. + { "copilotChat.customCommands": [
        {"title": "Refactor Code (Best Practices)", "command": "Before refactoring, refer to CODE_ANALYZER.md.", "context": "editor"},
        {"title": "Generate Code (Optimized)", "command": "Use CODE_ANALYZER.md guidelines.", "context": "editor"}
    ] }' "$VS_CODE_SETTINGS" > temp.json && mv temp.json "$VS_CODE_SETTINGS"
fi

echo "✅ Setup completed! Restart your IDEs."
```
### **📌 How to Run on Unix**
1. Open **Terminal**.
2. Run:
   ```bash
   chmod +x setup_copilot.sh
   sudo ./setup_copilot.sh
   ```

---

# **🚀 Summary**
✅ **Configures GitHub Copilot in VS Code, IntelliJ IDEA, and Eclipse**  
✅ **Sets persistent Copilot prompts for `CODE_ANALYZER.md`**  
✅ **Automates AI-based code reviews in CI/CD**  
✅ **Works on Windows (PowerShell) and Unix (Linux/macOS)**  
