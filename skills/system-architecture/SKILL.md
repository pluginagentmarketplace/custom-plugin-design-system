---
name: system-architecture
description: Master software architecture and system design including design patterns, scalability, distributed systems, and technology selection. Learn to design large-scale systems and make architectural trade-offs.
---

# System Architecture & Design

## Quick Start

Architecture defines how systems are structured, how components interact, and how systems scale.

### Design Pattern Example - Observer Pattern:

```python
from abc import ABC, abstractmethod

class Observer(ABC):
    @abstractmethod
    def update(self, subject):
        pass

class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer: Observer):
        self._observers.append(observer)

    def notify(self):
        for observer in self._observers:
            observer.update(self)

# Usage
class EmailNotifier(Observer):
    def update(self, subject):
        print(f"Email: {subject.data}")

subject = Subject()
subject.attach(EmailNotifier())
subject.notify()
```

### System Design Example - URL Shortener:

```
User Request:
  POST /api/shorten
  { "url": "https://example.com/very/long/url" }

System Components:
  ├─ API Server: Handles requests
  ├─ Database: Stores URL mappings
  ├─ Cache: Redis for fast lookups
  └─ ID Generator: Creates short codes

Response:
  { "short_url": "https://short.url/abc123" }
```

## Core Concepts

### 1. Design Patterns

#### Creational Patterns
```python
# Singleton Pattern
class DatabaseConnection:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# Factory Pattern
class PaymentFactory:
    @staticmethod
    def create_processor(payment_type: str):
        if payment_type == "credit_card":
            return CreditCardProcessor()
        elif payment_type == "paypal":
            return PayPalProcessor()
```

#### Structural Patterns
```python
# Decorator Pattern
def timing_decorator(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Execution time: {time.time() - start}s")
        return result
    return wrapper

# Adapter Pattern
class LegacySystemAdapter:
    def __init__(self, legacy_system):
        self.legacy = legacy_system

    def new_interface(self):
        return self.legacy.old_method()
```

#### Behavioral Patterns
```python
# Strategy Pattern
class PaymentStrategy(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class CreditCardPayment(PaymentStrategy):
    def pay(self, amount):
        return f"Processing ${amount} via credit card"

class PaymentProcessor:
    def __init__(self, strategy: PaymentStrategy):
        self.strategy = strategy

    def process(self, amount):
        return self.strategy.pay(amount)
```

### 2. Architectural Patterns

#### Layered Architecture
```
Presentation Layer (UI)
    ↓
Business Logic Layer (Services)
    ↓
Data Access Layer (DAOs)
    ↓
Database Layer
```

#### Microservices Architecture
```
API Gateway
    ↓
├─ User Service
├─ Product Service
├─ Order Service
└─ Payment Service

[Message Queue]
├─ User events
├─ Order events
└─ Payment events
```

#### CQRS (Command Query Responsibility Segregation)
```
Write Side (Command):
  User Action → Command Handler → Event Store → Update Model

Read Side (Query):
  Query → Read Model (Denormalized) → Fast Response
```

### 3. Scalability Patterns

#### Horizontal Scaling
```
Load Balancer
    ↓
├─ Server 1
├─ Server 2
└─ Server 3

[Shared Resources]
├─ Database
├─ Cache
└─ Message Queue
```

#### Database Scaling
```
Master Database (Writes)
    ↓
├─ Replica 1 (Reads)
├─ Replica 2 (Reads)
└─ Replica 3 (Reads)

Sharding:
├─ Shard 1: Users A-M
├─ Shard 2: Users N-Z
```

### 4. CAP Theorem

- **Consistency**: All nodes see same data
- **Availability**: Every request gets response
- **Partition Tolerance**: System works despite network splits

**Trade-offs:**
- CP: Strong consistency (SQL databases)
- AP: Always available (NoSQL, eventual consistency)
- CA: Rare in distributed systems

### 5. API Design

#### RESTful Design
```
Endpoints:
  GET    /api/v1/users             List users
  POST   /api/v1/users             Create user
  GET    /api/v1/users/{id}        Get specific user
  PUT    /api/v1/users/{id}        Update user
  DELETE /api/v1/users/{id}        Delete user
  POST   /api/v1/users/{id}/posts  Create user post

Versioning: /v1/, /v2/, accept-version header
```

#### GraphQL Design
```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post!]!
}

type Query {
  user(id: ID!): User
  users: [User!]!
}

type Mutation {
  createUser(name: String!, email: String!): User
  updateUser(id: ID!, name: String): User
}
```

### 6. Event-Driven Architecture

```
Event Producer
    ↓
Event Broker (Kafka, RabbitMQ)
    ↓
├─ Event Consumer 1
├─ Event Consumer 2
└─ Event Consumer 3

Events:
├─ UserCreated
├─ OrderPlaced
└─ PaymentProcessed
```

## Advanced Topics

### System Design Interview Problems
- URL shortening service
- Social media feed
- Search engine
- Video streaming platform
- Real-time chat

### Distributed Systems
- Consensus algorithms (Raft, Paxos)
- Clock synchronization (NTP)
- Distributed transactions
- Byzantine fault tolerance

### Performance Optimization
- Caching strategies (LRU, TTL)
- Database indexing
- Query optimization
- CDN for static content

## Real-World Projects

1. **Design Twitter** - Social network architecture
2. **Design Uber** - Real-time location and matching
3. **Design Netflix** - Video streaming and recommendations
4. **Design Slack** - Real-time messaging
5. **Design Airbnb** - Search and booking system

---

**Use this skill when:**
- Designing large-scale systems
- Preparing for system design interviews
- Selecting technology stacks
- Implementing design patterns
- Solving scalability problems
