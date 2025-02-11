# Clean Architecture Folder Structure

## Introduction
This folder structure is designed to seamlessly integrate with **Clean Architecture**, ensuring separation of concerns, maintainability, and scalability. The architecture enforces clear dependencies, where the core business logic remains independent of external frameworks and infrastructure.

### Principles of Clean Architecture
1. **Entities (Core Business Models)** - Represent the fundamental business objects with minimal dependencies.
2. **Use Cases (Application Logic)** - Define the application-specific business rules by interacting with entities and repositories.
3. **Repositories (Data Access Layer)** - Act as an abstraction between use cases and the data source (database or API).
4. **Gateways (Interface Layer)** - Bridge the application logic to external systems like web controllers or UI components.
5. **Infrastructure (Frameworks & Drivers)** - Contains database schemas, web controllers, APIs, and external dependencies.

## Backend Folder Structure
```
backend/
├── models/               # Core business models (Entities)
│   ├── user/
│   │   ├── index
│   │   └── user.model
│   ├── group/
│   │   ├── index
│   │   └── group.model
│   └── message/
│       ├── index
│       └── message.model
├── services/             # Application Services (Use Cases, Repositories, Gateways)
│   └── chat/
│       ├── index
│       ├── use-cases/    # Business Logic
│       │   ├── index
│       │   ├── send-message.case
│       │   ├── reply-to-message.case
│       │   ├── delete-message.case
│       │   └── react-to-message.case
│       ├── repositories/ # Data Persistence
│       │   ├── index
│       │   ├── send-message.repo
│       │   ├── reply-to-message.repo
│       │   ├── delete-message.repo
│       │   └── react-to-message.repo
│       ├── gateways/     # External Communication
│       │   ├── index
│       │   ├── send-message.gateway
│       │   ├── reply-to-message.gateway
│       │   ├── delete-message.gateway
│       │   └── react-to-message.gateway
│       └── infrastructure/
│           ├── index
│           ├── db/
│           │   ├── index
│           │   └── schema/
│           │       ├── user
│           │       ├── message
│           │       └── group
│           └── web/
│               ├── index
│               └── controllers/
│                   ├── message.controller
│                   ├── login.controller
│                   └── logout.controller
├── shared/               # Common utilities
│   ├── constants
│   ├── types
│   └── utils
└── config                # Configuration files
```

## Frontend Folder Structure
```
frontend/
├── models/               # Core business models (Entities)
│   ├── user/
│   │   ├── index
│   │   └── user.model
│   ├── group/
│   │   ├── index
│   │   └── group.model
│   └── message/
│       ├── index
│       └── message.model
├── services/             # Application Services
│   └── chat/
│       ├── index
│       ├── use-cases/
│       │   ├── index
│       │   ├── send-message.case
│       │   ├── reply-to-message.case
│       │   ├── delete-message.case
│       │   └── react-to-message.case
│       ├── repositories/
│       │   ├── index
│       │   ├── send-message.repo
│       │   ├── reply-to-message.repo
│       │   ├── delete-message.repo
│       │   └── react-to-message.repo
│       ├── gateways/
│       │   ├── index
│       │   ├── send-message.gateway
│       │   ├── reply-to-message.gateway
│       │   ├── delete-message.gateway
│       │   └── react-to-message.gateway
│       └── infrastructure/
│           ├── index
│           ├── api/
│           │   └── v1/
│           │       ├── index
│           │       └── schema/
│           │           ├── user
│           │           ├── message
│           │           └── group
│           └── web/
│               ├── index
│               ├── elements/
│               │   └── button.element
│               ├── components/
│               │   └── form.component
│               └── views/
│                   ├── home.page
│                   └── chat.page
├── shared/
│   ├── constants
│   ├── types
│   └── utils
└── config
```

## Dependency Flow in Clean Architecture
To prevent tight coupling and maintain flexibility, dependencies flow inwards:

1. **Entities** are the core and should not depend on any external layer.
2. **Use Cases** inject entities and repositories as dependencies.
3. **Repositories** act as a bridge between use cases and the data source.
   - In the backend: repositories connect to the **database**.
   - In the frontend: repositories connect to the **API**.
4. **Gateways** link use cases to external systems:
   - Backend: connects to **web controllers**.
   - Frontend: connects to the **UI components**.

### Dependency Flow
```
entity → use-case(repo) → gateway(use-case(repo)) → controller (backend) / UI (frontend)
entity → use-case(repo) → repo(schema) → database (backend) / API (frontend)
```

## Conclusion
This structure ensures a clear separation of concerns while allowing each layer to function independently. By adhering to **Clean Architecture**, the application remains **scalable, testable, and maintainable** over time. 🚀



## Some nice tools for implementing architecture:
1. https://tree.nathanfriend.com/
2. draw.io