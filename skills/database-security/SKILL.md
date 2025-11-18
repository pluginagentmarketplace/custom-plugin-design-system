---
name: database-security
description: Master database management and security covering SQL, NoSQL, encryption, authentication, and compliance. Learn database design, query optimization, vulnerability prevention, and secure system architecture.
---

# Database & Security

## Quick Start

Databases store critical data securely; security prevents unauthorized access and data breaches.

### SQL Database Design:

```sql
-- Secure user table with constraints
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username VARCHAR(255) UNIQUE NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,  -- Never store plain passwords
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create index for common queries
CREATE INDEX idx_users_email ON users(email);
```

### NoSQL Document Model:

```javascript
// MongoDB schema with security
db.createCollection("users", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["username", "email", "password_hash"],
      properties: {
        _id: { bsonType: "objectId" },
        username: { bsonType: "string" },
        email: { bsonType: "string" },
        password_hash: { bsonType: "string" }
      }
    }
  }
});
```

### Application Security:

```python
# Parameterized queries prevent SQL injection
import psycopg2

connection = psycopg2.connect("dbname=mydb user=myuser")
cursor = connection.cursor()

# SECURE: Use parameterized queries
user_id = 123
cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))

# INSECURE: Don't do string concatenation
# cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")
```

## Core Concepts

### 1. SQL & Relational Databases

#### Database Normalization
```sql
-- Unnormalized (BAD)
CREATE TABLE Orders (
  OrderID INT,
  CustomerName VARCHAR(255),
  CustomerEmail VARCHAR(255),
  ProductName VARCHAR(255),
  Quantity INT
);

-- Normalized (GOOD)
CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY,
  Name VARCHAR(255),
  Email VARCHAR(255)
);

CREATE TABLE Orders (
  OrderID INT PRIMARY KEY,
  CustomerID INT FOREIGN KEY REFERENCES Customers(CustomerID),
  OrderDate DATE
);

CREATE TABLE OrderItems (
  OrderItemID INT PRIMARY KEY,
  OrderID INT FOREIGN KEY,
  ProductID INT FOREIGN KEY,
  Quantity INT
);
```

#### Query Optimization
```sql
-- Efficient query with proper indexes
EXPLAIN ANALYZE
SELECT u.name, COUNT(o.id) as order_count
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE u.created_at > '2024-01-01'
GROUP BY u.id
HAVING COUNT(o.id) > 5
ORDER BY order_count DESC;

-- Create supporting indexes
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);
```

#### PostgreSQL Advanced Features
```sql
-- Window functions
SELECT
  name,
  salary,
  AVG(salary) OVER (PARTITION BY department) as avg_dept_salary,
  RANK() OVER (PARTITION BY department ORDER BY salary DESC) as rank
FROM employees;

-- Common Table Expressions (CTE)
WITH recent_orders AS (
  SELECT * FROM orders
  WHERE created_at > NOW() - INTERVAL '30 days'
),
high_value_orders AS (
  SELECT * FROM recent_orders
  WHERE total_amount > 1000
)
SELECT * FROM high_value_orders;
```

### 2. NoSQL Databases

#### MongoDB Operations
```javascript
// Insert with validation
db.users.insertOne({
  username: "john_doe",
  email: "john@example.com",
  password_hash: bcrypt.hash("password"),
  roles: ["user"],
  created_at: new Date()
});

// Aggregation pipeline
db.orders.aggregate([
  { $match: { status: "completed" } },
  { $group: { _id: "$customer_id", total: { $sum: "$amount" } } },
  { $sort: { total: -1 } },
  { $limit: 10 }
]);
```

#### Redis Caching
```python
import redis

r = redis.Redis(host='localhost', port=6379, db=0)

# Cache data with expiration
r.setex('user:123:profile', 3600, json.dumps(user_data))

# Retrieve cached data
cached = r.get('user:123:profile')

# Rate limiting with Redis
def rate_limit(user_id, limit=100, period=3600):
    key = f"rate_limit:{user_id}"
    current = r.incr(key)
    if current == 1:
        r.expire(key, period)
    return current <= limit
```

### 3. Authentication & Authorization

#### Password Hashing
```python
import bcrypt

# Hashing passwords
password = b"user_password"
hashed = bcrypt.hashpw(password, bcrypt.gensalt())

# Verifying passwords
if bcrypt.checkpw(password, hashed):
    print("Password matches!")
```

#### JWT Implementation
```python
import jwt
from datetime import datetime, timedelta

# Create token
payload = {
    'user_id': 123,
    'username': 'john',
    'exp': datetime.utcnow() + timedelta(hours=24)
}
token = jwt.encode(payload, 'secret_key', algorithm='HS256')

# Verify token
decoded = jwt.decode(token, 'secret_key', algorithms=['HS256'])
```

#### OAuth2 Pattern
```python
# Simplified OAuth2 flow
def login_with_google():
    # 1. User redirects to Google
    auth_url = construct_auth_url('google')

    # 2. Google redirects back with code
    code = request.args.get('code')

    # 3. Exchange code for token
    token = exchange_code_for_token(code)

    # 4. Get user info and create session
    user_info = get_user_info(token)
```

### 4. Security Best Practices

#### OWASP Top 10 Prevention

```python
# 1. SQL Injection Prevention
# WRONG: query = f"SELECT * FROM users WHERE id = {user_id}"
# CORRECT:
cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))

# 2. XSS Prevention
# WRONG: response = f"<h1>Hello {user_input}</h1>"
# CORRECT:
from markupsafe import escape
response = f"<h1>Hello {escape(user_input)}</h1>"

# 3. CSRF Protection
from flask_wtf.csrf import generate_csrf

# Include CSRF token in forms
csrf_token = generate_csrf()

# 4. Secure Headers
def set_security_headers(response):
    response.headers['X-Content-Type-Options'] = 'nosniff'
    response.headers['X-Frame-Options'] = 'DENY'
    response.headers['X-XSS-Protection'] = '1; mode=block'
    return response

# 5. Input Validation
def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return re.match(pattern, email) is not None
```

#### Data Encryption
```python
from cryptography.fernet import Fernet

# Generate key
key = Fernet.generate_key()
cipher = Fernet(key)

# Encrypt sensitive data
encrypted = cipher.encrypt(b"sensitive_data")

# Decrypt
decrypted = cipher.decrypt(encrypted)
```

### 5. Compliance & Governance

#### GDPR Compliance
```python
# Data retention
def delete_user_data(user_id):
    """Right to be forgotten"""
    # Delete user account
    User.delete(user_id)
    # Delete associated data
    UserData.delete_where(user_id=user_id)
    # Log deletion for audit
    audit_log(f"User {user_id} data deleted")

# Data export
def export_user_data(user_id):
    """Data portability"""
    user = User.get(user_id)
    data = {
        'profile': user.to_dict(),
        'orders': Order.find_by_user(user_id),
        'preferences': user.preferences
    }
    return json.dumps(data)
```

## Advanced Topics

### Database Replication
```
Master Database (Write)
    ↓
├─ Replica 1 (Read)
├─ Replica 2 (Read)
└─ Replica 3 (Read)

[Synchronous vs Asynchronous]
```

### Sharding Strategy
```
Hash(user_id) % num_shards = shard_id

Shard 1: Users 0-999
Shard 2: Users 1000-1999
Shard 3: Users 2000-2999
```

### Backup & Recovery
- Full backups
- Incremental backups
- Point-in-time recovery
- Disaster recovery testing

## Real-World Projects

1. **Secure User Database** - Passwords, tokens, audit logs
2. **Multi-tenant System** - Data isolation and security
3. **Backup Strategy** - Automated backups and recovery
4. **Compliance Automation** - GDPR, HIPAA compliance
5. **Security Audit** - Vulnerability assessment

---

**Use this skill when:**
- Designing database schemas
- Implementing authentication
- Protecting against vulnerabilities
- Meeting compliance requirements
- Optimizing database queries
- Learning database administration
