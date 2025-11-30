# Functional Requirements Document (FRD)

## 1. Authentication & Authorization
The system uses **JWT (JSON Web Token)** for secure authentication.

### 1.1 Authentication Mechanism
- **Token-Based Auth**: Upon successful login, the server issues a signed JWT.
- **Storage**: The frontend stores this token (e.g., in `localStorage` or `HttpOnly` cookies).
- **Request Authorization**: All protected API endpoints require the token to be sent in the `Authorization` header: `Bearer <token>`.

### 1.2 Requirements
| ID | Feature | Description | Acceptance Criteria |
|----|---------|-------------|---------------------|
| **FR-AUTH-01** | **User Registration** | Users can create an account with email and password. | - Validate email format.<br>- Password must be at least 8 chars.<br>- Unique email check. |
| **FR-AUTH-02** | **User Login** | Users can log in to receive an access token. | - Verify credentials.<br>- Return JWT on success.<br>- Return 401 on failure. |
| **FR-AUTH-03** | **Session Management** | Users remain logged in until the token expires or they logout. | - Token expiration set to 24h (configurable).<br>- Logout clears client-side token. |

---

## 2. API Specifications (Endpoints)
The backend exposes a RESTful API. Base URL: `http://localhost:3000/api`

### 2.1 Authentication Endpoints
- **POST** `/auth/register`
  - **Payload**: `{ "email": "user@example.com", "password": "securePass123" }`
  - **Response**: `201 Created` - `{ "message": "User registered successfully" }`
  
- **POST** `/auth/login`
  - **Payload**: `{ "email": "user@example.com", "password": "securePass123" }`
  - **Response**: `200 OK` - `{ "token": "eyJhbGciOiJIUz...", "user": { "id": 1, "email": "..." } }`

### 2.2 Document Management Endpoints
- **POST** `/documents/upload`
  - **Headers**: `Authorization: Bearer <token>`, `Content-Type: multipart/form-data`
  - **Payload**: `file` (Binary)
  - **Response**: `201 Created` - `{ "documentId": "123", "url": "/storage/doc_123.pdf" }`

- **GET** `/documents`
  - **Headers**: `Authorization: Bearer <token>`
  - **Response**: `200 OK` - `[ { "id": "123", "name": "contract.pdf", "uploadedAt": "2023-10-27..." } ]`

- **GET** `/documents/:id`
  - **Headers**: `Authorization: Bearer <token>`
  - **Response**: `200 OK` - Returns file stream or download link.

### 2.3 Sharing & QR Code Endpoints
- **POST** `/share/generate-qr`
  - **Headers**: `Authorization: Bearer <token>`
  - **Payload**: `{ "documentId": "123", "accessCode": "optional-code" }`
  - **Response**: `200 OK` - `{ "qrCodeUrl": "data:image/png;base64,...", "shareLink": "http://..." }`

---

## 3. Core Functional Features

### 3.1 Document Upload
- **FR-DOC-01**: The system shall allow authenticated users to upload PDF and image files.
- **FR-DOC-02**: The system shall validate file size (max 10MB) and type before processing.
- **FR-DOC-03**: The system shall store files securely on the server's file system or cloud storage.

### 3.2 QR Code Sharing
- **FR-SHARE-01**: The system shall generate a unique URL for each shared document.
- **FR-SHARE-02**: The system shall generate a QR code image corresponding to the unique URL.
- **FR-SHARE-03**: If an access code is provided, the shared link must prompt for it before displaying the document.

### 3.3 Dashboard
- **FR-DASH-01**: The user dashboard shall display a list of all uploaded documents with metadata (name, date).
- **FR-DASH-02**: Users shall be able to delete their own documents.
