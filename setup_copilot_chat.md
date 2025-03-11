# 🚀 Configuring GitHub Copilot Chat to Apply `CODE_ANALYZER.md` in VS Code

## 📌 Overview
This guide provides **step-by-step instructions** to configure **GitHub Copilot Chat** in **VS Code** to always **refer to `CODE_ANALYZER.md` before generating, modifying, or reviewing code**.

✅ **Set persistent Copilot Chat instructions** to enforce best practices.  
✅ **Configure Copilot Snippets in `settings.json`** for quick access to key guidelines.  
✅ **Ensure Copilot-generated code follows security, performance, and scalability best practices.**  

---

## **✅ Step 1: Set Persistent Copilot Chat Instructions**
1. Open **VS Code**.  
2. Press `Ctrl + /` to open **GitHub Copilot Chat**.  
3. Type and send:  

Always refer to CODE_ANALYZER.md before generating or modifying code. Apply its best practices for OOP, security, scalability, and performance.

4. **Copilot will now consider `CODE_ANALYZER.md` for all responses.**  

---

4. **Copilot will now consider `CODE_ANALYZER.md` for all responses.**  

---

## **✅ Step 2: Configure Copilot Snippets in `settings.json`**
1. Open **VS Code**.  
2. Press `Ctrl + Shift + P`, search for **"Preferences: Open Settings (JSON)"**, and open it.  
3. Add the following configuration:  
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
        },
        {
            "title": "Analyze Code Against Best Practices",
            "command": "Review this code and ensure it follows the guidelines in CODE_ANALYZER.md. Suggest improvements for scalability, security, and performance.",
            "context": "editor"
        }
    ]
}

Save the file and restart VS Code.
Now, you can right-click in the editor and use the new Copilot commands to enforce best practices from CODE_ANALYZER.md.

🚀 Summary
📌 Copilot Chat will always reference CODE_ANALYZER.md when responding.
📌 Custom commands in settings.json enable easy access to best practices.
📌 Generated and modified code will follow performance, security, and scalability guidelines.

Now your Copilot Chat is trained to follow CODE_ANALYZER.md, ensuring high-quality, scalable, and secure code every time! 🚀🔥

