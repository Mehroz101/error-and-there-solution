# 🚨 ERR-20250911-001 · Sequelize / MSSQL Login Failure — **Password Must Be Changed**

### 🗂 Category  
Database

### 💻 Stack  
Node.js 22 · Sequelize 6.35 · MSSQL Server 2019

### 🌐 Environment  
Local Development

---

## ❌ Error
```
Unable to connect to the database:
SequelizeAccessDeniedError: Login failed for user 'user1'.
Reason: The password of the account must be changed.
```

---

## 🔎 Root Cause
- SQL login **`user1`** was created with **“User must change password at next login”** enabled.  
- Sequelize’s MSSQL driver (`tedious`) can’t handle interactive password changes, so authentication fails immediately.

---

## ✅ Resolution Steps
1. **Open SSMS as an administrator.**  
2. Go to **Server ➔ Security ➔ Logins ➔ user1 ➔ Properties**.  
3. Reset the password to a secure value.  
4. **Uncheck** “User must change password at next login.”  
5. Update the new password in your Sequelize `.env`.  
6. Restart the Node app and test.

---

## 🔐 Verification
```js
await sequelize.authenticate(); // ✅ Connection successful
```

---

### 💡 Tip
For production, enforce password rotation via policy or a secrets manager (e.g., Azure Key Vault, AWS Secrets Manager) rather than SQL’s “must change” flag, which breaks automated services.
