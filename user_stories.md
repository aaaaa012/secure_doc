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
**As a** guest user,
**I want to** scan a QR code and see a list of available documents,
**So that** I can select which ones I need access to.

### Acceptance Criteria
- [ ] System displays a "Document Hub" page.
- [ ] List shows all current documents from the owner.
- [ ] Guest can select multiple documents via checkboxes.

---

**As a** guest user,
**I want to** provide my contact details (Name, Email, Phone),
**So that** the owner knows who is requesting access.

### Acceptance Criteria
- [ ] Form requires Name, Email, and Phone.
- [ ] Submission triggers an access request to the owner.

---

**As an** owner,
**I want to** review requests and grant specific permissions (View vs. Download),
**So that** I control how my documents are used.

### Acceptance Criteria
- [ ] Owner sees guest details and selected documents.
- [ ] Owner can select "View Only" or "View & Download".
- [ ] Owner can "Approve" or "Reject".
- [ ] Approved guest receives a link valid only for selected docs.
