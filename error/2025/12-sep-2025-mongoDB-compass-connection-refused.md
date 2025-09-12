# ERR-20250912-001 | MongoDB Compass Connection Refused

## 📌 Category
Database

## 💻 Technology / Language
MongoDB Community Server v8.0, MongoDB Compass, Windows 11

## 🌍 Environment
Local

## ❌ Error Message
connect ECONNREFUSED 127.0.0.1:27017, connect ECONNREFUSED ::1:27017


## 🔍 Cause
The error occurred because the **MongoDB server process was not running**.  
Initially, MongoDB was not even installed on the system, which led to Compass failing to connect to the default port `27017`.

## ✅ Solution
**Step 1:** Verified MongoDB was not installed (`mongod --version` returned "not recognized").  
**Step 2:** Installed MongoDB Community Server :

https://www.mongodb.com/try/download/community


**Step 3:** Confirmed installation directory:
C:\Program Files\MongoDB\Server\8.0\bin
**Step 4:** Added MongoDB bin folder to Windows PATH for easy CLI access.
**Step 5:** Started MongoDB service manually:
net start "MongoDB Server"
**Step 6:** Verified service was running and listening on port 27017.
**Step 7:** Successfully connected to Compass with URI:
mongodb://localhost:27017/monogodbsite

🔎 Verification

Running worked from CMD.
```
mongod --version 
```


MongoDB Compass successfully connected to the monogodbsite database.

📚 References

[MongoDB Official Installation Docs](https://www.mongodb.com/docs/manual/installation/)

[Winget MongoDB Package](https://github.com/mongodb/mongo)

[StackOverflow – ECONNREFUSED 127.0.0.1:27017](https://stackoverflow.com/questions/17337731/mongodb-error-connect-econnrefused)
