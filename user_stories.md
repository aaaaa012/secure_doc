# User Stories & Acceptance Criteria

## Epic 1: User Management
**As a** new user,
**I want to** register for an account,
**So that** I can securely access the platform.

### Acceptance Criteria
- [ ] User can enter email and password.
- [ ] System validates email format.
- [ ] System checks for existing email.
- [ ] Successful registration redirects to login.

---

**As a** registered user,
**I want to** log in with my credentials,
**So that** I can view my dashboard.

### Acceptance Criteria
- [ ] User enters email and password.
- [ ] System authenticates against database.
- [ ] Invalid credentials show error message.
- [ ] Successful login grants access to protected routes.

---

## Epic 2: Document Management
**As a** user,
**I want to** upload a PDF document,
**So that** I can store it securely.

### Acceptance Criteria
- [ ] User can select a file from their device.
- [ ] System accepts only PDF and image formats.
- [ ] File size limit is enforced (10MB).
- [ ] Uploaded file appears in the dashboard list.

---

## Epic 3: Sharing
**As a** user,
**I want to** generate a QR code for a document,
**So that** I can share it easily with others.

### Acceptance Criteria
- [ ] User selects a document to share.
- [ ] System generates a unique sharing URL.
- [ ] System displays a QR code for that URL.
- [ ] (Optional) User can set an access code.
