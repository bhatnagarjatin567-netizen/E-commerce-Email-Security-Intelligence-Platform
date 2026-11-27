# CYBERGUARD — E-commerce & Email Security Intelligence Platform

CYBERGUARD is a centralized, enterprise-grade cybersecurity assessment and auditing platform. It enables authorized security engineers and analysts to audit e-commerce application security (OWASP Juice Shop), analyze suspicious email headers (.eml) with live DNS SPF/DKIM/DMARC verification, execute controlled SMTP security lab demonstrations, and generate evidence-backed assessment reports.

---

## 1. System Architecture

- **Public Marketing Website**: Professional product overview, feature directory, and transparent authorization workflows.
- **Role-Based Access Control & Admin Approval**:
  - `PENDING_APPROVAL`: New registrations are quarantined by default to protect against unauthorized scanning.
  - `ADMIN`: Full authority over user approvals, roles, permissions, target authorization, and audit logs.
  - `ANALYST`: Authorized access to execute scans against approved targets, inspect findings, and export reports.
  - `VIEWER`: Read-only access to findings and reports.
- **Evidence Verification**: Zero fake data. All findings, severity tallies, and audit events originate from verified database records.
- **Technology Stack**:
  - **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Lucide React, Recharts, Axios.
  - **Backend**: Python 3, FastAPI, SQLAlchemy ORM, Pydantic, Bcrypt, PyJWT, SQLite.
  - **Security Tools**: OpenSSL, dnspython, Python RFC822 parser, aiosmtpd, OWASP ZAP API integration.

---

## 2. Default Credentials & Initial Setup

The first administrator is provisioned automatically upon initial database startup:

- **Admin Email**: `admin@cyberguard.io`
- **Admin Password**: `CyberGuard@Admin2026!`
- **Role**: `ADMIN`
- **Permissions**: `admin:all,scan:ecommerce,scan:email,lab:smtp,report:create,report:view,user:manage,target:manage`

---

## 3. Getting Started

### Prerequisites
- Python 3.11+
- Node.js 18+ and npm
- OpenSSL (optional for live TLS certificate handshakes)

### Step 1: Start Backend (FastAPI)
```bash
cd backend
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```
API Documentation will be live at: `http://localhost:8000/docs`

### Step 2: Start Frontend (Vite)
```bash
cd frontend
npm install
npm run dev
```
Open your browser at: `http://localhost:5173`

---

## 4. Docker Deployment

To launch CYBERGUARD alongside the OWASP Juice Shop testbed and OWASP ZAP:

```bash
docker compose up -d --build
```

- **CYBERGUARD Web App**: `http://localhost:5173`
- **CYBERGUARD API**: `http://localhost:8000`
- **OWASP Juice Shop Target**: `http://localhost:3000`
- **OWASP ZAP API**: `http://localhost:8080`
