# Connection Pool Explanation

## What is Connection Pool?

A **connection pool** is a cache of database connections that can be reused across multiple requests. Instead of creating a new connection for every database query (which is slow), the pool maintains a set of ready-to-use connections.

### Why Use Connection Pool?

**Without Pool (Bad):**
```
Request 1 → Create connection → Query → Close connection (slow!)
Request 2 → Create connection → Query → Close connection (slow!)
Request 3 → Create connection → Query → Close connection (slow!)
```

**With Pool (Good):**
```
Request 1 → Get connection from pool → Query → Return to pool (fast!)
Request 2 → Get connection from pool → Query → Return to pool (fast!)
Request 3 → Get connection from pool → Query → Return to pool (fast!)
```

### Where is it?

**File**: `backend/config/database.js`

```javascript
const mysql = require('mysql2/promise');

const pool = mysql.createPool({
  host: process.env.DB_HOST || 'localhost',
  user: process.env.DB_USER || 'root',
  password: process.env.DB_PASSWORD || '',
  database: process.env.DB_NAME || 'mechanic_finder',
  waitForConnections: true,      // Wait if all connections are busy
  connectionLimit: 10,           // Maximum 10 connections in pool
  queueLimit: 0                  // Unlimited queue for waiting requests
});
```

### How It Works:

1. **Pool Creation**: When server starts, creates up to 10 connections
2. **Request Comes**: Gets a connection from pool
3. **Query Executes**: Uses the connection
4. **Connection Returns**: Returns connection back to pool (not closed!)
5. **Reuse**: Next request can use the same connection

### Connection Pool Settings:

- **`connectionLimit: 10`** - Maximum 10 connections at once
- **`waitForConnections: true`** - If all 10 are busy, wait for one to be free
- **`queueLimit: 0`** - Unlimited requests can wait in queue

### Where It's Used:

**File**: `backend/models/User.js`
```javascript
const db = require('../config/database');  // Gets the pool

// Uses pool.execute() instead of creating new connection
const [rows] = await db.execute(query, [userId]);
```

**File**: `backend/models/Mechanic.js`
```javascript
const db = require('../config/database');  // Gets the pool

// All queries use the pool
const [rows] = await db.execute(query, params);
```

**File**: `backend/routes/bookings.js`
```javascript
const db = require('../config/database');  // Gets the pool

// Direct SQL queries use the pool
await db.execute(query, [...]);
```

### Benefits:

✅ **Faster** - No need to create/close connections every time
✅ **Efficient** - Reuses existing connections
✅ **Scalable** - Handles multiple requests simultaneously
✅ **Safe** - Limits connections to prevent database overload




