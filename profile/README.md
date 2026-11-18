<div align="center">
  <img src="/assets/banner-mumtaz.png" alt="Mumtaz Banner" width="100%" />

  <h1>Mumtaz Attendance &amp; Learning Progress System</h1>

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

## About The Project

**The problem:** At **Bimbel Mumtaz Sampit**, tutors reported lessons through Google Forms, and the admin checked the spreadsheet by hand every month. That took a lot of time, mistakes and duplicate entries were easy to miss, and parents could not see what their children were learning.

**Our solution:** A web application where tutors record each lesson in a short form, the system checks every entry automatically, and the admin only reviews what looks wrong. Approved sessions feed tuition bills and tutor pay, and parents can follow their child's progress anytime.

| Who | What They Can Do |
| :--- | :--- |
| **Admin** | Review flagged sessions, manage data, see monthly summaries and tutor pay, print invoices, export reports to Google Sheets |
| **Tutor** | Record lessons quickly, fix entries that need correction, see estimated monthly pay |
| **Parent** | Log in with a private access code to see approved lessons and learning notes |

## Contributors

| Student ID | Name | Learning Path | Focus Area |
| :--- | :--- | :--- | :--- |
| DS005B6X1386 | Noreencia Beatrice | Data Science Specialist | Data analysis and Project manager |
| DS009B6Y0668 | Ghiyyas Abiyasha Winardi | Data Science Specialist | Data preparation and processing |
| AE009B6Y1064 | Muhamad Fazrin Nugraha | Next-Gen AI Engineer | Model development and AI service integration |
| AE620B6X1333 | Nasywa Salsabiila Romadhona | Next-Gen AI Engineer | AI strategy and feature planning |
| FS009B6Y0568 | Farhan Harits Prakoso | AI Full-Stack Developer | Backend, database, and AI integration |
| FS126B6Y1508 | Rama Dwi Nugraha | AI Full-Stack Developer | Frontend and UI/UX |



## AI-Assisted Attendance Screening

Each submitted or corrected session is checked automatically against the center's rules and the same tutor's or student's sessions within 30 days. This helps the admin spot duplicates, schedule clashes, and unusual hours or lengths. Admins can change any result, and sessions are still saved if the checker is unavailable.

**Flow:** Tutor submits → System checks → Valid / Revision / Reject → Admin reviews flagged sessions → Tutor fixes and resubmits

| Result | Condition | What Happens |
| :--- | :--- | :--- |
| **Valid** | No rule is broken. Exactly 30 or 180 minutes, and starting exactly at 07:00 or 21:00, are still valid | Approved automatically and counted toward billing and tutor pay |
| **Revision** | Lesson is over 180 or under 30 minutes. Starts after 21:00 or before 07:00 (WIB). Same tutor, student, subjects, date, and duration as an earlier session but a different start time. Overlapping time on the same day for the same tutor with another student, the same student with another tutor, or the same pair | On hold. Tutor can edit it, and the admin decides whether to approve |
| **Reject** | Exact copy of an earlier session (same tutor, student, subjects, date, start time, and duration) | On hold. Tutor cannot edit it, and the admin can delete it |

Priority when rules overlap: Reject, then Revision, then Valid. When two sessions clash, only the one submitted later is flagged.

---

## Built With

| Layer | Technologies |
| :--- | :--- |
| **Frontend** | ![React](https://img.shields.io/badge/React_19-0F172A?style=flat-square&logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-0F172A?style=flat-square&logo=vite&logoColor=646CFF) ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS_v4-0F172A?style=flat-square&logo=tailwind-css&logoColor=38B2AC) ![TypeScript](https://img.shields.io/badge/TypeScript-0F172A?style=flat-square&logo=typescript&logoColor=3178C6) |
| **Backend** | ![Node.js](https://img.shields.io/badge/Node.js_22+-0F172A?style=flat-square&logo=nodedotjs&logoColor=339933) ![Express](https://img.shields.io/badge/Express_5-0F172A?style=flat-square&logo=express&logoColor=FFFFFF) ![Drizzle ORM](https://img.shields.io/badge/Drizzle_ORM-0F172A?style=flat-square&logo=drizzle&logoColor=C5F74F) |
| **AI Service** | ![FastAPI](https://img.shields.io/badge/FastAPI-0F172A?style=flat-square&logo=fastapi&logoColor=009688) ![Python](https://img.shields.io/badge/Python-0F172A?style=flat-square&logo=python&logoColor=3776AB) ![LightGBM](https://img.shields.io/badge/LightGBM-0F172A?style=flat-square&logo=python&logoColor=FFD43B) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-0F172A?style=flat-square&logo=scikitlearn&logoColor=F7931E) |
| **Database** | ![Neon PostgreSQL](https://img.shields.io/badge/Neon_PostgreSQL-0F172A?style=flat-square&logo=postgresql&logoColor=00E599) |
| **Integrations** | ![Google Sheets API](https://img.shields.io/badge/Google_Sheets_API-0F172A?style=flat-square&logo=googlesheets&logoColor=34A853) ![Docker](https://img.shields.io/badge/Docker-0F172A?style=flat-square&logo=docker&logoColor=2496ED) |

---

## Project Scope

| What It Does | What It Does Not Do |
| :--- | :--- |
| Keeps all attendance, student and tutor data, billing, and pay calculations in one secure database | Use Google Sheets as the main database. It is only used to export monthly reports |
| Gives Admins, Tutors, and Parents their own pages, each showing only what they are allowed to see | Share private lesson notes or login details with the AI checker |
| Checks every session automatically, calculates bills and tutor pay by grade level, and creates PDF invoices | Count flagged sessions toward billing or pay before the admin approves them, or handle online payments |

---

## Acknowledgements

Developed as part of the **Asah** capstone program in collaboration with **Bimbel Mumtaz Sampit**.
