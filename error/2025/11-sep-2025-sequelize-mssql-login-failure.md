
# ERR-20250911-001 | Sequelize MSSQL Login Failure (Password Must Be Changed)

## 📌 Category
Database

## 💻 Technology / Language
Node.js v22, Sequelize v6.35, MSSQL Server 2019

## 🌍 Environment
Local

## ❌ Error Message
Unable to connect to the database: AccessDeniedError [SequelizeAccessDeniedError]:
Login failed for user 'user1'. Reason: The password of the account must be changed.


## 🔍 Cause
- The SQL login `user1` had the flag **"must change password at next login"** enabled.  
- Sequelize’s MSSQL driver (`tedious`) does not support interactive password change, so the connection failed immediately.

## ✅ Solution
1. Open **SQL Server Management Studio (SSMS)** as an admin.  
2. Navigate: `Server > Security > Logins > user1 > Properties`.  
3. Reset the password.  
4. **Uncheck** `User must change password at next login`.  
5. Update Sequelize `.env` with the new password.  
6. Restart the Node app and test the connection.  

## 🔎 Verification
- Ran `await sequelize.authenticate()` → ✅ Connection successful.  















