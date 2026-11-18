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

At **Bimbel Mumtaz Sampit**, every tutoring session needs to be recorded properly. These records decide how much parents are billed, how much each tutor is paid, and what parents can see about their child's progress. Until now, tutors reported their sessions through Google Forms, and the admin had to go through the spreadsheet by hand at the end of every month. They checked each entry, looked for duplicates or mistakes, and calculated fees and tutor pay. This took a lot of time, errors were easy to miss, and parents had little visibility into what their children were learning.

**Mumtaz Attendance & Learning Progress System** is a web application that replaces this manual process. Tutors fill in a short form after each lesson. The system checks every entry automatically and flags anything that looks wrong, so the admin only reviews what needs attention. Approved sessions are counted toward tuition bills and tutor pay. Admins can print invoices and export monthly reports to Google Sheets. Parents can follow their child's learning history at any time.

| Who | How This Project Helps |
| :--- | :--- |
| **Admin** | Reviews flagged sessions, manages tutor, student, parent, and subject data, sees monthly summaries and tutor pay, prints invoices, and exports monthly reports to Google Sheets. |
| **Tutor** | Records each lesson quickly (subjects, time, duration, materials, and notes), fixes entries that need correction, and sees their estimated monthly pay. |
| **Parent / Guardian** | Logs in with a private access code (no password needed) to see approved lessons, materials, and learning notes for their child. |

**Main benefits:** less manual recap work, fewer mistakes in billing and tutor pay, faster and more consistent checking of attendance, and clearer information for parents.


| Role | Route | Core Capabilities |
| :--- | :--- | :--- |
| **Admin** | `/admin` | Review &amp; override AI-flagged sessions, manage master data (tutors, students, parents, subjects), inspect monthly recaps &amp; tutor payroll, generate PDF invoices, and trigger 8-column Google Sheets exports (`Absensi YYYY-MM`). |
| **Tutor** | `/tutor` | Submit structured lesson logs (1–5 subjects, auto-filled student grade &amp; school, schedule, learning material, notes, next focus), revise flagged entries, and view approved monthly honor estimates. |
| **Parent / Guardian** | `/orang-tua-murid` | Log in securely using a high-entropy **Parent Access Code** (no password required) to view approved learning histories and lesson progress for connected children. |

### AI-Assisted Attendance Screening

Every time a tutor submits or corrects a session, the system automatically checks it against the center's rules and against earlier sessions of the same tutor or the same student, within 30 days of the lesson date. This helps the admin spot sessions that may be duplicated, overlapping, or outside normal hours or length, without checking every entry by hand. Admins can change any result at any time, and sessions are still saved if the checker is unavailable.


**Flow:** Tutor submits → System checks → Valid / Revision / Reject → Admin reviews flagged sessions → Tutor fixes and resubmits (if Revision)

**Screening results**

| Result | When | What Happens |
| :--- | :--- | :--- |
| **Valid** | Meets all the rules | Approved automatically and counted toward billing and tutor pay |
| **Revision** | Breaks one or more rules below | On hold. Tutor can edit it, and the admin decides whether to approve |
| **Reject** | Exact copy of a session submitted earlier | On hold. Tutor cannot edit it, and the admin can delete it |

If rules from more than one group are broken, the priority is Reject, then Revision, then Valid.

**Screening rules**

| Rule | What Is Checked | Result |
| :--- | :--- | :--- |
| **Exact duplicate** | Same tutor, student, subjects, date, start time, and duration as an earlier session | Reject |
| **Similar duplicate** | Same as above, but with a different start time | Revision |
| **Too long** | Lesson lasts more than 180 minutes | Revision |
| **Too short** | Lesson lasts less than 30 minutes | Revision |
| **Starts too late** | Lesson starts after 21:00 (WIB) | Revision |
| **Starts too early** | Lesson starts before 07:00 (WIB) | Revision |
| **Tutor double-booked** | Same tutor, different student, overlapping time on the same day | Revision |
| **Student double-booked** | Same student, different tutor, overlapping time on the same day | Revision |
| **Same pair overlapping** | Same tutor and student, overlapping time on the same day, but not an exact copy | Revision |

Exactly 30 or 180 minutes, and starting exactly at 07:00 or 21:00, are still valid. Duplicate and overlap checks only look at sessions on the same date. When two sessions clash, the one submitted first is still judged on its own, and only the one submitted later is flagged.



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

| What This Project Does | What This Project Does Not Do |
| :--- | :--- |
| Keeps all attendance records, student and tutor data, and billing and pay calculations in one secure database | Use Google Sheets as the main database or for data entry. It is only used to export monthly reports |
| Gives Admins, Tutors, and Parents their own pages, each showing only the information they are allowed to see | Share private lesson notes or login details with the AI checker |
| Lets tutors record lessons quickly, with student grade and school filled in automatically | Block admins from changing the AI's result, or lose a tutor's submission when the AI checker is unavailable |
| Checks every submitted or corrected session automatically for duplicates, schedule clashes, and unusual lesson hours or lengths | Count flagged sessions toward billing or tutor pay before the admin approves them |
| Calculates tuition bills and tutor pay by grade level, creates PDF invoices, and exports monthly reports to Google Sheets | Handle bank transfers or online payments, or work as a full online learning platform |


---

## Acknowledgements

Developed as part of the **Asah** capstone program in collaboration with **Bimbel Mumtaz Sampit**, combining full-stack TypeScript engineering and machine learning to automate daily tutoring operations and strengthen data transparency for admins, tutors, and parents.
