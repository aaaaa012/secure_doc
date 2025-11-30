# Architecture & Workflow Diagrams

## 1. System Context Diagram
This diagram shows the high-level interaction between the user and the SecureDoc system.

```mermaid
graph LR
    User[User] -- Uploads Document --> Frontend[Web Frontend]
    User -- Scans QR Code --> Frontend
    Frontend -- API Requests (JSON) --> Backend[Node.js Backend]
    Backend -- Reads/Writes --> DB[(PostgreSQL Database)]
    Backend -- Stores Files --> Storage[File Storage]
```

## 2. Authentication Flow (JWT)
This sequence diagram illustrates the login process and token usage.

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant B as Backend
    participant D as Database

    U->>F: Enter Email & Password
    F->>B: POST /api/auth/login
    B->>D: Validate Credentials
    D-->>B: User Valid
    B-->>F: Return JWT Token
    F->>F: Store Token (LocalStorage)
    
    Note over U, F: Subsequent Request
    U->>F: Click "My Documents"
    F->>B: GET /api/documents (Auth Header: Bearer Token)
    B->>B: Verify Token Signature
    B->>D: Fetch User's Documents
    D-->>B: Return Data
    B-->>F: Return Document List
    F-->>U: Display Dashboard
```

## 3. Document Sharing Workflow
This flowchart describes the process of sharing a document via QR code.

```mermaid
flowchart TD
    A[Start] --> B{User Logged In?}
    B -- No --> C[Redirect to Login]
    B -- Yes --> D[Upload Document]
    D --> E[Generate Unique Link]
    E --> F[Create QR Code]
    F --> G[Display to User]
    G --> H[User Shares QR Code]
    H --> I[Recipient Scans Code]
    I --> J{Access Code Required?}
    J -- Yes --> K[Prompt for Code]
    K --> L{Code Correct?}
    L -- No --> K
    L -- Yes --> M[Show Document]
    J -- No --> M
    M --> N[End]
```
