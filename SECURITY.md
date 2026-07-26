# Security Policy - XMAIL-PHISH

## OWASP Top 10 (2021) Compliance

This document outlines how XMAIL-PHISH addresses each OWASP Top 10 vulnerability.

### 1. Broken Access Control

**Risk:** Unauthorized users access restricted resources.

**Mitigation:**
- ✅ JWT-based authentication with role-based access control (RBAC)
- ✅ User permissions verified on every request
- ✅ Admin, Analyst, Viewer roles implemented
- ✅ Audit logging of all access attempts

**Implementation:** `backend/app/middleware/auth.py`

---

### 2. Cryptographic Failures

**Risk:** Sensitive data exposure due to weak encryption.

**Mitigation:**
- ✅ AES-256 encryption for sensitive data at rest
- ✅ HTTPS/TLS 1.3 for data in transit
- ✅ Secure password hashing with bcrypt (cost factor 12+)
- ✅ API keys never logged or exposed in errors
- ✅ Supabase encrypted columns for sensitive fields

**Implementation:** `backend/app/security/encryption.py`

---

### 3. Injection

**Risk:** SQL, Command, LDAP injection attacks.

**Mitigation:**
- ✅ Parameterized queries via SQLAlchemy ORM
- ✅ No raw SQL queries (exceptions use parameterization)
- ✅ Input validation & sanitization on all endpoints
- ✅ Whitelist validation for file extensions
- ✅ Command execution avoided (safe libraries only)

**Implementation:** `backend/app/utils/validators.py`, `backend/app/database/`

---

### 4. Insecure Design

**Risk:** Missing security requirements in design phase.

**Mitigation:**
- ✅ Threat modeling completed (see ARCHITECTURE.md)
- ✅ Secure defaults implemented
- ✅ Rate limiting enabled
- ✅ CORS properly configured
- ✅ CSP headers enforced

**Implementation:** `backend/app/config.py`, `backend/app/middleware/`

---

### 5. Security Misconfiguration

**Risk:** Insecure default configurations.

**Mitigation:**
- ✅ Environment-based configuration (no hardcoded secrets)
- ✅ Debug mode disabled in production
- ✅ Unnecessary HTTP methods disabled
- ✅ Security headers set (HSTS, X-Frame-Options, X-Content-Type-Options)
- ✅ Database credentials stored in environment variables

**Implementation:** `.env.example`, `backend/app/config.py`

---

### 6. Vulnerable and Outdated Components

**Risk:** Using libraries with known vulnerabilities.

**Mitigation:**
- ✅ Dependencies listed in `requirements.txt` with pinned versions
- ✅ Regular dependency scanning (pip-audit, safety)
- ✅ Only trusted, well-maintained libraries used
- ✅ CI/CD pipeline checks for vulnerabilities

**Implementation:** GitHub Actions workflows in `.github/workflows/`

---

### 7. Authentication and Session Management Failures

**Risk:** Weak authentication mechanisms.

**Mitigation:**
- ✅ JWT tokens with 24-hour expiration
- ✅ Refresh token mechanism
- ✅ Secure password requirements enforced
- ✅ Rate limiting on login attempts (5 attempts per 15 minutes)
- ✅ Account lockout after failed attempts

**Implementation:** `backend/app/routes/auth.py`, `backend/app/middleware/rate_limit.py`

---

### 8. Software and Data Integrity Failures

**Risk:** Malicious code or data modifications.

**Mitigation:**
- ✅ Code signed commits in git
- ✅ Dependency verification via checksums
- ✅ File upload validation (MIME type, size, extension)
- ✅ Hash verification for downloaded files (VirusTotal, etc.)

**Implementation:** `backend/app/services/file_handler.py`

---

### 9. Logging and Monitoring Failures

**Risk:** Insufficient logging for incident response.

**Mitigation:**
- ✅ All authentication attempts logged
- ✅ All analysis requests logged with email metadata
- ✅ Suspicious activity alerts
- ✅ Centralized logging with timestamps
- ✅ No sensitive data in logs (PII redacted)

**Implementation:** `backend/app/utils/logger.py`

---

### 10. Server-Side Request Forgery (SSRF)

**Risk:** Application makes requests to unintended internal systems.

**Mitigation:**
- ✅ URL validation before making external requests
- ✅ Whitelist of allowed domains for threat intelligence APIs
- ✅ Timeout limits on external requests (30 seconds)
- ✅ No user-controlled URLs passed to internal services

**Implementation:** `backend/app/services/threat_intel.py`

---

## Secure Coding Practices

### Input Validation
- All inputs validated against whitelist
- File extensions restricted to: .eml, .msg, .txt
- Email addresses validated with regex
- URLs validated before processing

### Output Encoding
- HTML output escaped
- JSON responses properly formatted
- Error messages don't expose system details

### Error Handling
- Generic error messages shown to users
- Detailed errors logged for debugging
- No stack traces exposed in production

### Session Management
- Sessions stored securely in Supabase
- Tokens use HTTP-only, Secure, SameSite flags
- Automatic logout after inactivity (30 minutes)

## API Security

### Authentication
- All endpoints require valid JWT token
- Token includes user ID, role, and permissions
- Tokens refreshed automatically

### Authorization
- Role-based access control enforced
- Users can only access their own analyses
- Admins can view all analyses

### Rate Limiting
- 100 requests per hour per IP
- 10 file uploads per hour per user
- 1000 API calls per day per organization

### Encryption
- Email content encrypted before storage
- API keys encrypted in database
- TLS 1.3 for all communications

## Data Protection

### Data at Rest
- PostgreSQL encryption at rest
- Sensitive fields encrypted with AES-256
- Supabase backup encryption

### Data in Transit
- HTTPS/TLS 1.3 enforced
- Certificate pinning (optional)
- Perfect forward secrecy enabled

### Data Retention
- Email analyses retained for 90 days
- Logs retained for 30 days
- User deletion removes all associated data (GDPR compliant)

## Incident Response

### Monitoring
- Real-time alerts for suspicious activity
- Automated scanning for IOCs
- Dashboard showing security metrics

### Response
- Incident playbooks documented
- Automated account lockout on attack detection
- Alert to security team

---

**Last Updated:** 2024
**Next Review:** Quarterly
