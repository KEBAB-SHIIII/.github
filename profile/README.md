<div align="center">
  <img src="/assets/banner-mumtaz.png" alt="Mumtaz Banner" width="100%" />

  <h1>Mumtaz Attendance &amp; Learning Progress System</h1>

  <p>
    <strong>Digitizing tutoring attendance, AI-assisted session validation, tiered billing &amp; payroll, and student learning progress for Bimbel Mumtaz Sampit.</strong>
  </p>

  <p>
    <a href="https://your-demo-url.example.com/">
      <img src="https://img.shields.io/badge/View%20Demo-1D4ED8?style=for-the-badge&logo=vercel&logoColor=white" alt="View Demo" />
    </a>
    <a href="https://github.com/KEBAB-SHIIII/mumtaz-bimbel-dashboard/issues">
      <img src="https://img.shields.io/badge/Report%20Bug-1E3A8A?style=for-the-badge&logo=github&logoColor=white" alt="Report Bug" />
    </a>
    <a href="https://github.com/KEBAB-SHIIII/mumtaz-bimbel-dashboard/issues">
      <img src="https://img.shields.io/badge/Request%20Feature-0284C7?style=for-the-badge&logo=github&logoColor=white" alt="Request Feature" />
    </a>
  </p>
</div>

---

## About The Project

In daily tutoring operations at **Bimbel Mumtaz Sampit**, managing session attendance across tutors, students, and grade levels (`PAUD–TK` through `SMA`) is critical for accurate billing, tutor payroll, and parent communication. Previously, tutors logged sessions through disconnected Google Forms and Admins had to manually group spreadsheet rows every month to verify entries, spot duplicate or out-of-policy submissions, compute tiered tuition fees and tutor honor, and share learning progress—resulting in repetitive administrative overhead, delayed verification, and limited visibility for parents.

To solve this, we built **Mumtaz Attendance & Learning Progress System**, a centralized, role-based web platform (**Admin**, **Tutor**, and **Parent/Guardian**) powered by **Neon PostgreSQL** as the single source of truth and an independent **FastAPI Machine Learning** service. Tutors log structured sessions (1–5 subjects, schedule, duration, and learning notes) in seconds; every submission is automatically screened for anomalies before Admin approval; verified sessions lock tiered tuition billing and tutor honor snapshots; Admins generate PDF invoices and trigger on-demand 8-column Google Sheets monthly exports; and Parents securely track approved learning histories using a secret Parent Access Code.

| Role | Route | Core Capabilities |
| :--- | :--- | :--- |
| **Admin** | `/admin` | Review &amp; override AI-flagged sessions, manage master data (tutors, students, parents, subjects), inspect monthly recaps &amp; tutor payroll, generate PDF invoices, and trigger 8-column Google Sheets exports (`Absensi YYYY-MM`). |
| **Tutor** | `/tutor` | Submit structured lesson logs (1–5 subjects, auto-filled student grade &amp; school, schedule, learning material, notes, next focus), revise flagged entries, and view approved monthly honor estimates. |
| **Parent / Guardian** | `/orang-tua-murid` | Log in securely using a high-entropy **Parent Access Code** (no password required) to view approved learning histories and lesson progress for connected children. |

### AI-Assisted Attendance Screening

To reduce manual checking while keeping data accurate, every submitted or revised session passes through a **FastAPI Machine Learning & Business Guardrail** service. In general, this AI layer acts as an intelligent screening assistant that automatically checks incoming attendance logs against historical session patterns and operational rules—helping Admins spot potential **duplicate entries**, **overlapping tutor or student schedules**, and **unusual session durations or start times** (`30–180` minutes within `07:00–21:00` WIB).

Rather than replacing human judgment, the AI service provides clear, explainable review labels (`Valid`, `Needs Revision`, or `Rejected`) while strictly protecting private learning notes. Admins always hold the final decision to approve, request revision, or reject any session, and tutor submissions are never blocked even if the AI service is temporarily unavailable.

---

## Built With

| Layer | Technologies |
| :--- | :--- |
| **Frontend** | ![React 19](https://img.shields.io/badge/React_19-0F172A?style=flat-square&logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-0F172A?style=flat-square&logo=vite&logoColor=646CFF) ![Tailwind CSS v4](https://img.shields.io/badge/Tailwind_CSS_v4-0F172A?style=flat-square&logo=tailwind-css&logoColor=38B2AC) ![TypeScript](https://img.shields.io/badge/TypeScript-0F172A?style=flat-square&logo=typescript&logoColor=3178C6) ![TanStack Query](https://img.shields.io/badge/TanStack_Query-0F172A?style=flat-square&logo=reactquery&logoColor=FF4154) ![React Router](https://img.shields.io/badge/React_Router-0F172A?style=flat-square&logo=reactrouter&logoColor=CA4245) |
| **Backend** | ![Node.js 22+](https://img.shields.io/badge/Node.js_22+-0F172A?style=flat-square&logo=nodedotjs&logoColor=339933) ![Express 5](https://img.shields.io/badge/Express_5-0F172A?style=flat-square&logo=express&logoColor=FFFFFF) ![Drizzle ORM](https://img.shields.io/badge/Drizzle_ORM-0F172A?style=flat-square&logo=drizzle&logoColor=C5F74F) ![Zod](https://img.shields.io/badge/Zod-0F172A?style=flat-square&logo=zod&logoColor=3E67B1) ![Argon2id](https://img.shields.io/badge/Argon2id-0F172A?style=flat-square&logo=letsencrypt&logoColor=38BDF8) |
| **AI &amp; ML Service** | ![FastAPI](https://img.shields.io/badge/FastAPI-0F172A?style=flat-square&logo=fastapi&logoColor=009688) ![Python](https://img.shields.io/badge/Python-0F172A?style=flat-square&logo=python&logoColor=3776AB) ![LightGBM](https://img.shields.io/badge/LightGBM-0F172A?style=flat-square&logo=python&logoColor=FFD43B) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-0F172A?style=flat-square&logo=scikitlearn&logoColor=F7931E) ![Pandas](https://img.shields.io/badge/Pandas-0F172A?style=flat-square&logo=pandas&logoColor=FFFFFF) ![Pydantic](https://img.shields.io/badge/Pydantic-0F172A?style=flat-square&logo=pydantic&logoColor=E92063) |
| **Database** | ![Neon PostgreSQL](https://img.shields.io/badge/Neon_PostgreSQL-0F172A?style=flat-square&logo=postgresql&logoColor=00E599) |
| **Integrations &amp; DevOps** | ![Google Sheets API](https://img.shields.io/badge/Google_Sheets_API-0F172A?style=flat-square&logo=googlesheets&logoColor=34A853) ![Docker](https://img.shields.io/badge/Docker-0F172A?style=flat-square&logo=docker&logoColor=2496ED) |

---

## Project Scope

| Designed To | Intentionally Does Not |
| :--- | :--- |
| Store all operational attendance logs, master data, audit trails, and locked tariff/honor snapshots in **Neon PostgreSQL** as the single source of truth | Use Google Sheets as a primary database, routine input form, or two-way sync source (strictly export-only on Admin trigger) |
| Provide dedicated role-based dashboards (`/admin`, `/tutor`, `/orang-tua-murid`) with HttpOnly cookies, Argon2id password hashing, and CSRF protection | Send private learning materials, notes, or raw personal credentials to the AI anomaly service |
| Support structured session logging (1–5 subjects per session, auto-filled student grade/school metadata, learning material, notes, and next focus) | Lock Admins out of overriding AI classifications or silently drop attendance submissions when the AI service is unreachable |
| Screen every submitted &amp; revised session via FastAPI ML + Guardrail to flag duplicates, schedule overlaps, and out-of-policy hours or durations | Auto-approve sessions, reject records, or alter tutor honor without Admin confirmation |
| Calculate tiered billing &amp; honor snapshots (`PAUD–TK` to `SMA`) for approved sessions, generate PDF invoices, and export 8-column monthly sheets (`Absensi YYYY-MM`) | Process bank transfers, online payment gateways, online exams, or act as a full academic LMS |

---

## Acknowledgements

Developed as part of the **Asah** capstone program in collaboration with **Bimbel Mumtaz Sampit**, combining full-stack TypeScript engineering and machine learning to automate daily tutoring operations and strengthen data transparency for admins, tutors, and parents.
