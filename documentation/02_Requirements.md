# System Requirements

## 📋 Functional Requirements

### 1. User Management
- **FR-01**: Users must be able to register with email and password.
- **FR-02**: System must enforce password complexity guidelines.
- **FR-03**: Users can update their profile information.

### 2. Document Management
- **FR-04**: Users can upload PDF, DOCX, and JPG files (Max 10MB).
- **FR-05**: All uploaded files must be encrypted at rest using AES-256.
- **FR-06**: Users can view a list of their uploaded documents with metadata (name, size, date).

### 3. Secure Sharing
- **FR-07**: Users can generate a unique QR code for a specific document or folder.
- **FR-08**: Owners can set an expiration time for share links (e.g., 1 hour, 24 hours).
- **FR-09**: Recipients must authenticate (via OTP or Pin) to access shared documents.

### 4. Notifications
- **FR-10**: Owners receive email alerts when a document is accessed.

## 🚀 Non-Functional Requirements

### Performance
- **NFR-01**: File uploads should complete within 5 seconds for a 5MB file on 4G.
- **NFR-02**: API response time should be < 200ms for metadata requests.

### Security
- **NFR-03**: All data in transit must be protected via TLS 1.3.
- **NFR-04**: System must implement Rate Limiting to prevent brute-force attacks.
- **NFR-05**: Access logs must be retained for 1 year for auditability.

### Reliability
- **NFR-06**: System availability target is 99.9% uptime.
