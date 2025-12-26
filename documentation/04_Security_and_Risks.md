# Security & Risk Assessment

## 🛡️ Security Measures
1.  **Encryption**: AES-256 for file storage; bcrypt for password hashing.
2.  **Access Control**: Granular permissions (read-only, download-allowed).
3.  **Audit Trail**: Immutable logs for every file access event.

## ⚠️ Risk Matrix

| Risk ID | Description | Likelihood | Impact | Mitigation Strategy |
| :--- | :--- | :--- | :--- | :--- |
| **R-01** | **Unauthorized Access** | Low | Critical | Multi-Factor Authentication (MFA) required for sensitivity > High. |
| **R-02** | **Data Loss** | Very Low | High | Daily encrypted backups to geo-redundant storage. |
| **R-03** | **Malware Upload** | Medium | High | Integration with ClamAV to scan all files upon upload. |
| **R-04** | **Phishing Links** | Medium | Medium | Display "Verify Sender" warnings on all shared links. |

## 🧪 SWIFT / Compliance
*   **GDPR**: User right to be forgotten (Delete Account feature).
*   **Data Residency**: Data stored in compliance with local regulations.
