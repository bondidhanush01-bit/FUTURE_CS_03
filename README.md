
# 🔐 API Security Risk Analysis Report

> **A professional, read-only API security audit performed on public demo APIs, following OWASP API Security Top 10 methodology.**

---

## 📌 Project Overview

This repository contains a complete **API Security Risk Analysis** — the kind of assessment performed by AppSec consultants and cybersecurity agencies for SaaS clients. The audit was conducted entirely on **public/demo APIs** using read-only methods, with no exploitation or system modification.

| Field | Details |
|---|---|
| **Audit Type** | Read-Only API Security Risk Analysis |
| **Methodology** | OWASP API Security Top 10 |
| **APIs Tested** | JSONPlaceholder, ReqRes |
| **Scope** | Authentication, Authorization, Data Exposure, Rate Limiting, Headers |
| **Tools Used** | Postman, Browser DevTools, Manual Inspection |
| **Report Format** | PDF / DOCX (see `/report/`) |

---

## 📁 Repository Structure

```
api-security-audit/
│
├── README.md                        ← You are here
│
├── report/
│   ├── API_Security_Risk_Report.pdf ← Final deliverable (PDF)
│   └── API_Security_Risk_Report.docx← Final deliverable (Word)
│
├── screenshots/
│   ├── 01_jsonplaceholder_users_response.png
│   ├── 02_reqres_unauth_user_access.png
│   ├── 03_missing_auth_headers.png
│   ├── 04_rate_limit_test.png
│   └── 05_excessive_data_exposure.png
│
├── postman/
│   └── API_Security_Audit.postman_collection.json
│
└── findings/
    ├── FINDINGS_SUMMARY.md          ← Quick risk summary
    └── remediation_checklist.md     ← Step-by-step fix list
```

---

## 🎯 Scope & Ethics

### ✅ In Scope (Allowed)
- Public and demo APIs only (`jsonplaceholder.typicode.com`, `reqres.in`)
- Read-only HTTP requests: `GET`, safe `POST` (login/register endpoints)
- Documentation-based risk analysis
- Header, token, and response structure inspection
- Rate limiting behavior observation

### ❌ Out of Scope (Not Allowed)
- Exploitation or authentication bypass attempts
- Denial-of-Service (DoS) or flood testing
- Attacking private, staging, or production APIs
- Reverse engineering proprietary systems
- Any unauthorized access or data extraction

> **This audit is purely educational and ethical. No systems were harmed, modified, or exploited.**

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Postman** | API endpoint testing, request inspection, response analysis |
| **Browser DevTools** | Header inspection, network tab analysis |
| **OWASP API Top 10** | Risk classification framework |
| **Manual Review** | Documentation analysis, logic review |

---

## 🔬 Methodology

This audit follows a structured 6-phase approach:

```
Phase 1: Reconnaissance
  └── Review API documentation, identify endpoints, map data flows

Phase 2: Authentication Analysis
  └── Test for missing/weak auth, token validation, open endpoints

Phase 3: Authorization Testing
  └── Check BOLA/IDOR — can user A access user B's data?

Phase 4: Data Exposure Review
  └── Inspect response payloads for over-sharing of sensitive fields

Phase 5: Security Header Inspection
  └── Evaluate HTTP response headers for security hygiene

Phase 6: Rate Limiting & Input Validation
  └── Observe rate limit behavior, test for improper input handling
```

---

## 🚨 Key Findings Summary

| # | Risk | API | Severity | OWASP Category |
|---|---|---|---|---|
| 1 | Unauthenticated access to all user data | JSONPlaceholder | 🔴 High | API1 – Broken Object Level Auth |
| 2 | Excessive data exposure in responses | JSONPlaceholder | 🟠 Medium | API3 – Excessive Data Exposure |
| 3 | No rate limiting on endpoints | JSONPlaceholder | 🟠 Medium | API4 – Lack of Resources & Rate Limiting |
| 4 | Missing security headers | ReqRes | 🟡 Low | API7 – Security Misconfiguration |
| 5 | Predictable resource IDs (BOLA risk) | ReqRes | 🔴 High | API1 – Broken Object Level Auth |
| 6 | Weak or no token expiry enforcement | ReqRes | 🟠 Medium | API2 – Broken Authentication |

> Full risk descriptions, business impact, and remediation steps are in the [report/](./report/) folder.

---

## 📊 Risk Distribution

```
HIGH     ██████████  2 findings
MEDIUM   ███████     3 findings
LOW      ███         1 finding
```

---

## 🔧 Remediation Highlights

**For API developers and SaaS teams:**

1. **Enforce authentication on every endpoint** — no anonymous access to user/resource data
2. **Implement RBAC/ABAC** — users should only access their own resources
3. **Filter response payloads** — return only fields the client actually needs
4. **Add rate limiting** — per IP and per authenticated user (e.g. 100 req/min)
5. **Set security headers** — `X-Content-Type-Options`, `X-Frame-Options`, `Strict-Transport-Security`
6. **Use short-lived tokens with refresh flows** — don't issue non-expiring tokens

---

## 📚 Reference Resources

| Resource | Link |
|---|---|
| OWASP API Security Top 10 | https://github.com/OWASP/API-Security |
| API Security Checklist | https://github.com/shieldfy/API-Security-Checklist |
| Public APIs (for testing) | https://github.com/public-apis/public-apis |
| JSONPlaceholder | https://jsonplaceholder.typicode.com |
| ReqRes | https://reqres.in |

---

## 👤 Author

| Field | Info |
|---|---|
| **Role** | Security Analyst / AppSec Consultant |
| **Audit Date** | June 2026 |
| **Contact** |https://github.com/bondidhanush01-bit |

---

## 📄 License

This project is for **educational and portfolio purposes only**.  
All testing was performed on **public demo APIs** intended for developer testing.  
No proprietary systems, private data, or production environments were accessed.

---

> *"Security is not a product, but a process."* — Bruce Schneier
