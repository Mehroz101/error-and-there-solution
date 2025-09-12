# 🚨 Error Knowledge Base

A personal documentation repo to track **errors, bugs, and fixes** I encounter during development.  
The goal is to quickly identify:
- ❓ What the error is  
- ⚡ Where it happened (Frontend, Backend, Database, DevOps, etc.)  
- 🔧 How it was solved  
- 📚 References for future debugging  

---

## 📂 Structure
Each error is stored as a markdown file under the `/errors` folder.

```
/errors
├── 2025/
│ ├── 2025-09-11-sequelize-mssql-login-failure.md
│ ├── 2025-09-12-react-404-style-missing.md
│ └── ...
└── template.md
```



---

## 📝 Error Doc Format
Each error file follows this structure:

```markdown
#   Short Error Title

### Error code
ERR-YYYYMMDD-001

### 📌 Category
Frontend | Backend | Database | DevOps | Other

### 💻 Technology / Language
Example: Node.js v18, NestJS v10, Sequelize v6.37, MSSQL 2019

### 🌍 Environment
Local / Staging / Production
----

## ❌ Error Message


## 🔍 Cause
Explain the reason this error occurred.

## ✅ Solution
- Step 1: ...
- Step 2: ...
- Step 3: ...

## 🔎 Verification
Explain how you confirmed the issue was resolved.

## 📚 References
- [Official Docs](https://example.com)
- [StackOverflow Discussion](https://stackoverflow.com)



```














