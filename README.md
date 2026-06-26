# 🔐 API Security Risk Analysis Report

A professional, read-only API security audit performed on public demo APIs and enterprise SaaS ecosystem integrations, following the OWASP API Security Top 10 methodology.

## 📌 Project Overview
This repository contains a comprehensive API Security Risk Analysis — the kind of assessment performed by AppSec consultants and cybersecurity agencies for SaaS clients. The audit consists of two main components:
1. **Public/Demo API Audits**: Conducted entirely on public/demo APIs using read-only methods, with no exploitation or system modification.
2. **Enterprise Integration Analysis**: A strategic architecture and session-state security review of downstream Canva Ecosystem integrations.

| Field | Details |
| :--- | :--- |
| **Audit Types** | Read-Only API Security Risk Analysis & Strategic Integration Assessment |
| **Methodology** | OWASP API Security Top 10 |
| **Target Scopes** | JSONPlaceholder, ReqRes, Canva Ecosystem App-to-Platform Framework |
| **Layers Evaluated**| Authentication, Authorization, Session-State Boundaries, Asset Lifecycles |
| **Tools Used** | Postman, Browser DevTools, Manual Inspection, Architectural Review |
| **Report Format** | PDF / DOCX (see `/report/`) |

---

## 📁 Repository Structure
```text
api-security-audit/
│
├── README.md                        ← You are here
│
├── report/
│   ├── API Security Risk Analysis Report.pdf ← Final deliverable (PDF)
│   └── API_Security_Risk_Report.docx← Final deliverable (Word)
│
├── screenshots/
│   ├── evidence/Screenshot 2026-06-22 181714.png   ← Verifying resource retrieval logic
│   ├── evidence/Screenshot 2026-06-22 183247.png ← Public unauthenticated JSON payload raw view
│   ├──evidence/Screenshot 2026-06-22 183333.png  ← Testing state-changing operations (POST)
│   └──evidence/Screenshot 2026-06-22 183626.png ← Analyzing base route headers & routing behavior
│
├── postman/
│   └── API_Security_Audit.postman_collection.json
│
└── findings/
    ├── FINDINGS_SUMMARY.md          ← Quick risk summary
    ├── remediation_checklist.md     ← Step-by-step fix list
    └── CANVA_INTEGRATION_REVIEW.md  ← Strategic architectural deep-dive
🎯 Scope & Ethics

✅ In Scope (Allowed)


Public and demo APIs only (jsonplaceholder.typicode.com, reqres.in)
Read-only HTTP requests: GET, safe POST (login/register endpoints)
Documentation-based risk analysis
Header, token, and response structure inspection
Rate limiting behavior observation


❌ Out of Scope (Not Allowed)


Exploitation or authentication bypass attempts
Denial-of-Service (DoS) or flood testing
Attacking private, staging, or production APIs
Reverse engineering proprietary systems
Any unauthorized access or data extraction



This audit is purely educational and ethical. No systems were harmed, modified, or exploited.




🛠️ Tools Used

ToolPurposePostmanAPI endpoint testing, request inspection, response analysisBrowser DevToolsHeader inspection, network tab analysisOWASP API Top 10Risk classification frameworkManual ReviewDocumentation analysis, logic review


🔬 Methodology

This audit follows a structured 6-phase approach:

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


🚨 Key Findings Summary

#RiskAPISeverityOWASP Category1Unauthenticated access to all user dataJSONPlaceholder🔴 HighAPI1 – Broken Object Level Auth2Excessive data exposure in responsesJSONPlaceholder🟠 MediumAPI3 – Excessive Data Exposure3No rate limiting on endpointsJSONPlaceholder🟠 MediumAPI4 – Lack of Resources & Rate Limiting4Missing security headersReqRes🟡 LowAPI7 – Security Misconfiguration5Predictable resource IDs (BOLA risk)ReqRes🔴 HighAPI1 – Broken Object Level Auth6Weak or no token expiry enforcementReqRes🟠 MediumAPI2 – Broken Authentication


Full risk descriptions, business impact, and remediation steps are in the report/ folder.




📊 Risk Distribution

HIGH     ██████████  2 findings
MEDIUM   ███████     3 findings
LOW      ███         1 finding


🔧 Remediation Highlights

For API developers and SaaS teams:


Enforce authentication on every endpoint — no anonymous access to user/resource data
Implement RBAC/ABAC — users should only access their own resources
Filter response payloads — return only fields the client actually needs
Add rate limiting — per IP and per authenticated user (e.g. 100 req/min)
Set security headers — X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security
Use short-lived tokens with refresh flows — don't issue non-expiring tokens



📚 Reference Resources

ResourceLinkOWASP API Security Top 10https://github.com/OWASP/API-SecurityAPI Security Checklisthttps://github.com/shieldfy/API-Security-ChecklistPublic APIs (for testing)https://github.com/public-apis/public-apisJSONPlaceholderhttps://jsonplaceholder.typicode.comReqReshttps://reqres.in


👤 Author

FieldInfoRoleSecurity Analyst / AppSec ConsultantAudit DateJune 2026Contact( https://github.com/bondidhanush01-bit/ www.linkedin.com/in/
dhanush-bondi-978697352
)


📄 License

This project is for educational and portfolio purposes only.

All testing was performed on public demo APIs intended for developer testing.

No proprietary systems, private data, or production environments were accessed.
