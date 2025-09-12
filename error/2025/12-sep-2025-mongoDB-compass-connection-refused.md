# 🚨  **MongoDB Compass Connection Refused**

### Error code
ERR-20250912-001


### 🗂 Category
Database

### 💻 Stack  
MongoDB Community Server 8.0 · MongoDB Compass · Windows 11

### 🌐 Environment  
Local Development

---

## ❌ Error
```
connect ECONNREFUSED 127.0.0.1:27017
connect ECONNREFUSED ::1:27017
```

---

## 🔎 Root Cause
- The **MongoDB server process was not running**.
- MongoDB wasn’t installed initially, so Compass failed to connect to the default port `27017`.

---

## ✅ Resolution Steps
1. **Verify installation**: `mongod --version` (returned "not recognized").
2. **Install MongoDB Community Server**: [Download](https://www.mongodb.com/try/download/community).
3. **Confirm installation directory**: `C:\Program Files\MongoDB\Server\8.0\bin`.
4. **Add MongoDB bin folder to PATH** for CLI access.
5. **Start MongoDB service manually**:
   ```cmd
   net start "MongoDB Server"
   ```
6. **Verify service is running** and listening on port `27017`.
7. **Connect via Compass** using URI:
   ```
   mongodb://localhost:27017/monogodbsite
   ```

---

## 🔐 Verification
```bash
mongod --version  # should return version info
```
MongoDB Compass successfully connected to the `monogodbsite` database.

---

### 📚 References
- [MongoDB Official Installation Docs](https://www.mongodb.com/docs/manual/installation/)
- [Winget MongoDB Package](https://github.com/mongodb/mongo)
- [StackOverflow – ECONNREFUSED 127.0.0.1:27017](https://stackoverflow.com/questions/17337731/mongodb-error-connect-econnrefused)
