# XMAIL-PHISH - Advanced Email Phishing Detection & Analysis Tool

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Security](https://img.shields.io/badge/security-OWASP%20Top%2010-red)

## 🔍 Overview

**XMAIL-PHISH** is a production-grade, enterprise-level email phishing detection and analysis platform built for government and organizational cybersecurity teams. It performs comprehensive multi-layered analysis of email messages to identify phishing attacks, credential harvesting attempts, malware delivery, and other email-based threats.

### 🎯 Key Features

- **12-Step Advanced Analysis Pipeline**
  - Input validation & email parsing
  - Header analysis & spoofing detection
  - SPF/DKIM/DMARC authentication verification
  - Domain intelligence & reputation checking
  - URL analysis with redirect chain detection
  - Attachment analysis with hash verification
  - HTML obfuscation & malicious code detection
  - NLP-based content analysis
  - Brand impersonation detection
  - Threat intelligence integration
  - Behavioral pattern analysis
  - Weighted risk scoring (0-100 scale)

- **Threat Intelligence Integration**
  - VirusTotal API
  - AbuseIPDB
  - OpenPhish
  - PhishTank
  - AlienVault OTX
  - Spamhaus

- **Production-Ready Features**
  - Role-based access control (RBAC)
  - JWT authentication
  - Rate limiting & DDoS protection
  - Comprehensive audit logging
  - Data encryption (AES-256)
  - OWASP Top 10 compliant
  - SQL injection prevention
  - XSS protection
  - CSRF protection
  - Secure file upload handling

- **Reports & Analytics**
  - Real-time risk scoring
  - Detailed analysis reports (JSON/PDF)
  - Dashboard with threat metrics
  - Email history & trend analysis
  - IOC (Indicators of Compromise) extraction

## 🏗️ Project Structure

```
XMAIL-PHISH/
├── backend/                    # Python FastAPI backend
├── frontend/                   # HTML/CSS/JavaScript frontend
├── database/                   # Supabase schema & migrations
├── docs/                       # Documentation
├── tests/                      # Test suite
├── .github/                    # GitHub workflows
├── .env.example                # Environment template
├── README.md                   # This file
└── SECURITY.md                 # Security policy
```

## 🚀 Quick Start

### Prerequisites
- Python 3.9+
- Node.js 14+ (if using modern frontend)
- Supabase account
- GitHub account
- API keys for threat intelligence services

### Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/vijsid2/XMAIL-PHISH.git
   cd XMAIL-PHISH
   ```

2. **Setup Backend**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   cp ../.env.example .env
   # Edit .env with your configuration
   python main.py
   ```

3. **Setup Frontend**
   - Navigate to `frontend/` directory
   - Open `index.html` in a web browser or run a local server

4. **Setup Database**
   - Create a Supabase project
   - Run migrations from `database/migrations/`

## 📚 Documentation

- [API Documentation](./docs/API.md)
- [Setup Guide](./docs/SETUP.md)
- [OWASP Security Audit](./docs/OWASP.md)
- [Architecture](./docs/ARCHITECTURE.md)
- [Contributing Guidelines](./CONTRIBUTING.md)

## 🔐 Security

This project implements OWASP Top 10 security controls:

1. ✅ Injection Prevention (SQL, Command, LDAP)
2. ✅ Broken Authentication (JWT + MFA support)
3. ✅ Sensitive Data Exposure (AES-256 encryption)
4. ✅ XML External Entities (XXE) Protection
5. ✅ Broken Access Control (RBAC)
6. ✅ Security Misconfiguration (Hardened defaults)
7. ✅ XSS Protection (Input sanitization, CSP headers)
8. ✅ Insecure Deserialization (Safe parsing)
9. ✅ Using Components with Known Vulnerabilities (Dependency scanning)
10. ✅ Insufficient Logging & Monitoring (Comprehensive audit logs)

See [SECURITY.md](./SECURITY.md) for details.

## 📊 Tech Stack

- **Backend:** Python 3.9+, FastAPI, SQLAlchemy
- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Database:** Supabase (PostgreSQL)
- **Authentication:** JWT + Role-based access control
- **Threat Intelligence:** Multiple free & paid APIs
- **Deployment:** Docker, Kubernetes ready

## 📝 License

MIT License - See LICENSE file

## 🤝 Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md)

## ⚠️ Disclaimer

This tool is designed for legitimate cybersecurity defense and analysis only. Unauthorized access to computer systems is illegal. Use this tool only on systems you own or have explicit permission to test.

## 📞 Support

For issues, feature requests, or security vulnerabilities, please:
1. Check existing issues
2. Create a new issue with detailed information
3. For security issues, email: security@xmailphish.local

---

**Built with ❤️ for Government & Enterprise Cybersecurity Teams**
