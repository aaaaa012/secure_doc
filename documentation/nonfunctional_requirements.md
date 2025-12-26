# Non-Functional Requirements (NFR)

## 1. Security
- **NFR-SEC-01**: All data in transit must be encrypted using TLS 1.2 or higher (HTTPS).
- **NFR-SEC-02**: Passwords must be hashed using a strong algorithm (e.g., bcrypt) before storage.
- **NFR-SEC-03**: API endpoints must be rate-limited to prevent abuse (e.g., 100 requests per minute per IP).
- **NFR-SEC-04**: JWT tokens must be signed with a strong secret key and have a defined expiration time.

## 2. Performance
- **NFR-PERF-01**: The system should load the dashboard within 2 seconds on a standard broadband connection.
- **NFR-PERF-02**: Document uploads up to 10MB should complete within 15 seconds (network dependent).
- **NFR-PERF-03**: The API should respond to read requests within 200ms (95th percentile).

## 3. Reliability & Availability
- **NFR-REL-01**: The system should aim for 99.9% uptime during business hours.
- **NFR-REL-02**: The system must gracefully handle database connection failures and provide user-friendly error messages.

## 4. Scalability
- **NFR-SCL-01**: The backend architecture should support horizontal scaling (stateless API).
- **NFR-SCL-02**: Database storage should be capable of handling at least 10,000 documents in the initial phase.

## 5. Usability
- **NFR-USE-01**: The user interface must be responsive and function correctly on mobile devices (iOS/Android).
- **NFR-USE-02**: Error messages must be clear and actionable for the end-user.
