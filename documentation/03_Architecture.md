# Architecture & Design

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
    A[Start] --> B{Scanner is Owner?}
    
    %% Owner Flow
    B -- Yes --> C[Prompt for PIN]
    C --> D{PIN Correct?}
    D -- Yes --> E[Show All Documents]
    D -- No --> C
    
    %% Guest Flow
    B -- No --> F[Show Document Hub]
    F --> G[Guest Fills Form (Name, Email, Phone)]
    G --> H[Guest Selects Documents]
    H --> I[Send Access Request]
    I --> J[Owner Receives Notification]
    J --> K{Owner Approves?}
    K -- Yes --> L[Select Permission (View/Download)]
    L --> M[Send Access Link to Guest]
    M --> N[Guest Accesses Selected Docs]
    K -- No --> O[Request Denied]
    
    E --> P[End]
    N --> P
    O --> P
```
