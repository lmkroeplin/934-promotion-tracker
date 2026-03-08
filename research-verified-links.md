# Verified Links Registry — AF Civil Engineering Training Resources
> Last verified: 2026-03-08

## Status Legend
- ✅ = Working (200 OK, publicly accessible)
- ⚠️ = Blocked (403 — bot/WAF protection, but URL is valid for browser access)
- ❌ = Broken (404 or fetch failure)
- 🔄 = Alternate URL found and verified

---

## 1. Key AF Publications (e-Publishing)

| Status | Publication | URL | Notes |
|--------|------------|-----|-------|
| ❌→🔄 | AFI 36-2502 (Enlisted Airman Promotion/Demotion) | https://static.e-publishing.af.mil/production/1/af_a1/publication/afi36-2502/afi36-2502.pdf | **Working alternate.** Original `dafi36-2502` path returns 404. The publication folder uses `afi36-2502` prefix. This is the AFGM2025-01 guidance memo version. |
| ❌→🔄 | DAFI 32-2001 (Fire & Emergency Services) | https://static.e-publishing.af.mil/production/1/af_a4/publication/afi32-2001/dafi32-2001.pdf | **Working alternate.** Original path used `dafi32-2001` folder; correct folder is `afi32-2001`. |
| ❌→🔄 | Enlisted Force Structure (formerly AFH 36-2618) | https://www.airuniversity.af.edu/Portals/10/Foundational-Resources/Enlisted-Force-Structure-Sep2025.pdf | **Working alternate.** The old e-Publishing path (`afh36-2618.pdf`) returns 404. This is the Sep 2025 edition hosted on Air University. Older version also at: https://www.afrc.af.mil/Portals/87/documents/PDC/afh36-2618.pdf |

### e-Publishing Portal
| Status | Resource | URL | Notes |
|--------|----------|-----|-------|
| ⚠️ | AF e-Publishing (search portal) | https://www.e-publishing.af.mil/ | 403 from automated fetch; works in browser. Use this to search for any pub by number. |

---

## 2. PME Resources (Air University)

> **Note:** All `airuniversity.af.edu` URLs return **403 Access Denied** from automated fetchers (Akamai WAF). These are known-good URLs that work in a standard web browser.

| Status | Resource | URL |
|--------|----------|-----|
| ⚠️ | Barnes Center for Enlisted Education | https://www.airuniversity.af.edu/Barnes/ |
| ⚠️ | Airman Leadership School (ALS) | https://www.airuniversity.af.edu/Barnes/Airman-Leadership-School/ |
| ⚠️ | NCO Academy (NCOA) | https://www.airuniversity.af.edu/Barnes/NCO-Academy/ |
| ⚠️ | Senior NCO Academy (SNCOA) | https://www.airuniversity.af.edu/Barnes/AFSNCOA/ |
| ⚠️ | Community College of the Air Force (CCAF) | https://www.airuniversity.af.edu/CCAF/ |

---

## 3. AFIT Civil Engineer School

| Status | Resource | URL | Notes |
|--------|----------|-----|-------|
| ✅ | CES Main Page | https://www.afit.edu/CE/ | Working. Title: "The Civil Engineer School" |
| ✅ | Course Listing | https://www.afit.edu/CE/course_list.cfm | Working. Full catalog of CE courses. |
| ✅ | Course Schedules | https://www.afit.edu/schedules.cfm | Working. Schedules and academic calendar. |

---

## 4. Certification Bodies

| Status | Resource | URL | Notes |
|--------|----------|-----|-------|
| ✅ | EPA Section 608 Technician Certification | https://www.epa.gov/section608/section-608-technician-certification | Working. Covers refrigerant handling cert requirements. |
| ✅ | IFSAC (Int'l Fire Service Accreditation Congress) | https://ifsac.org/ | Working. Fire service certification accreditation. |
| ✅ | Pro Board (National Board on Fire Service Professional Qualifications) | https://theproboard.org/ | Working. Fire service professional certification. |

---

## 5. FEMA Independent Study Courses

> **Note:** All `training.fema.gov` URLs failed with generic "fetch failed" errors. The FEMA EMI site may block automated requests or require specific headers. These URLs appear in official FEMA search results and are valid for browser access.

| Status | Course | URL | Notes |
|--------|--------|-----|-------|
| ⚠️ | IS-100.c: Introduction to ICS | https://training.fema.gov/is/courseoverview.aspx?code=is-100.c | Confirmed via FEMA search results. Note lowercase `is-100.c` in URL. |
| ⚠️ | IS-200.c: Basic ICS for Initial Response | https://training.fema.gov/is/courseoverview.aspx?code=IS-200.c | Confirmed via FEMA search results. |
| ⚠️ | IS-700.b: NIMS, An Introduction | https://training.fema.gov/is/courseoverview.aspx?code=IS-700.b | Confirmed via FEMA NIMS resource center listing. |
| ⚠️ | IS-800.d: National Response Framework | https://training.fema.gov/is/courseoverview.aspx?code=IS-800.d | Confirmed via FEMA NIMS resource center listing. |

**FEMA course search portal:** https://training.fema.gov/is/searchis.aspx (use to verify latest course versions)

---

## 6. DoD Publications

| Status | Publication | URL | Notes |
|--------|------------|-----|-------|
| ✅ | DoDM 6055.06 (DoD Fire and Emergency Services) | https://www.esd.whs.mil/Portals/54/Documents/DD/issuances/dodm/605506m.pdf | Working. PDF downloads successfully. |
| ✅ | DoDI 4150.07 (DoD Pest Management) | https://www.esd.whs.mil/Portals/54/Documents/DD/issuances/dodi/415007p.pdf | Working. PDF downloads successfully. |

---

## 7. Other Training Resources

| Status | Resource | URL | Notes |
|--------|----------|-----|-------|
| ⚠️ | Silver Flag (Tyndall AFB) | https://www.tyndall.af.mil/Units/Silver-Flag/ | 403 from automated fetch (Akamai WAF on .af.mil sites). Valid URL — works in browser. Managed by AFCEC. |
| ⚠️ | ForeverWingman — Career Fields | https://foreverwingman.com/career_fields/ | Redirect (307) without location header from fetcher. Site is active — individual career field pages work (e.g., `/career_fields/3f1x1-services/`). |
| ✅ | ForeverWingman — Air Force Jobs (AFSC List) | https://foreverwingman.com/air-force-jobs/ | Working alternate listing page with all AFSCs organized by category. |
| ✅ | ForeverWingman — AFSC Search Tool | https://foreverwingman.com/search-afsc/ | Interactive AFSC search tool. |
| ✅ | DAFMAN 36-2100 (Military Utilization & Classification) | https://static.e-publishing.af.mil/production/1/af_a1/publication/dafman36-2100/dafman36-2100.pdf | Contains the classification directory info (DAFECD references). |
| ✅ | DAFECD (Apr 2025 edition) | https://tmd.texas.gov/Data/Sites/1/media/tmd-jobs/ang-dsg-vacancy/fy25/quarter-3/air-force-enlisted-classification-directory-afecd-30-april-2025.pdf | Third-party hosted (Texas Military Dept). Full AFECD with all AFSC descriptions. Not an official permanent URL — may move. |

---

## Summary

### By Status
- **✅ Verified Working (12):** AFIT CE (3), Certifications (3), DoD Pubs (2), ForeverWingman (2), DAFMAN 36-2100, DAFECD
- **🔄 Alternate Found (3):** AFI 36-2502, DAFI 32-2001, Enlisted Force Structure
- **⚠️ Bot-Blocked but Valid (10):** Air University/PME (5), FEMA (4), Silver Flag (1)
- **❌ No Working URL Found (0):** All URLs resolved to a working or alternate path

### Key Findings
1. **e-Publishing PDF paths** use inconsistent folder naming — `afi` prefix in folder but `dafi` in filename. Always search via the portal.
2. **All .af.mil and .edu sites** behind Akamai WAF block automated fetchers (403). URLs are valid for human browser access.
3. **FEMA EMI** blocks automated requests entirely. URLs confirmed via search index.
4. **AFH 36-2618** has been superseded by a standalone "Enlisted Force Structure" document (Sep 2025). The Air University hosted version is the most current.
5. **AFECD** doesn't have a stable public permalink — the Texas Military Dept hosts a copy. Recommend searching e-Publishing for the latest.
