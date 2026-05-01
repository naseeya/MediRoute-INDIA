# MediRoute India 🏥
### AI-Powered Healthcare Navigator & Cost Estimator

> **TenzorX Hackathon · Poonawalla Fincorp · Problem Statement B**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Visit%20Site-b83018?style=for-the-badge)](https://naseeya.github.io/MediRoute-INDIA)
[![Powered by Groq](https://img.shields.io/badge/Powered%20by-Groq%20Llama%203.3%2070B-orange?style=for-the-badge)](https://groq.com)
[![Data](https://img.shields.io/badge/Data-CGHS%202023%20%7C%20PM--JAY%20HBP%202.0-blue?style=for-the-badge)](#data-sources)

---

## What is MediRoute?

MediRoute is a **decision intelligence engine** — not a chatbot — that translates patient intent into structured clinical and financial recommendations.

```
Patient Intent → Clinical Pathway → Provider Ranking → Cost Estimation
```

Type any symptom, condition, or procedure in plain English or Hindi and get:

- ✅ **Real hospital recommendations** from a verified database of 80 hospitals across 28 Indian cities
- ✅ **7-component cost breakdown** (surgery, stay, diagnostics, medicines, doctor fees, consumables, contingency)
- ✅ **Comorbidity-adjusted** estimates (diabetes, cardiac history, CKD — each with cost multipliers)
- ✅ **ICD-10 / SNOMED-CT** clinical mapping via Groq Llama 3.3 70B
- ✅ **Pre-underwriting lending intelligence** for healthcare loan providers
- ✅ **PM-JAY / CGHS coverage detection** built in
- ✅ **Confidence scoring** (0–1) on every recommendation

---

## Live Demo

🌐 **[naseeya.github.io/MediRoute-INDIA](https://naseeya.github.io/MediRoute-INDIA)**

### Try these queries:
```
chest pain while walking, Nagpur, age 54, diabetic
knee replacement surgery, Jaipur, age 62, budget under 3 lakhs
angioplasty in Lucknow, 58 years, prior cardiac history
best cancer hospital in Chennai under 5 lakh
cataract surgery Coimbatore, senior citizen
```

---

## How It Works

### 1. Natural Language Input
Users describe their condition in everyday language — symptoms, procedures, or preference-based queries. Hindi transliteration supported.

### 2. Clinical NLP Mapping (Groq Llama 3.3 70B)
The AI maps input to:
- **ICD-10** and **SNOMED-CT** clinical codes
- Recommended procedure and specialist type
- Emergency flag (for acute presentations)
- Comorbidity risk factors with cost-impact multipliers

### 3. Real Hospital Matching
Queries against a verified database of **80 real hospitals** across **28 cities**:

| Coverage | Details |
|----------|---------|
| Cities | Nagpur, Jaipur, Lucknow, Bhopal, Coimbatore, Indore, Vizag, Pune, Chandigarh, Raipur, Patna, Kochi, Bhubaneswar, Guwahati, Mumbai, Delhi, Bangalore, Hyderabad, Chennai, Mysore, Madurai, Ludhiana, Agra, Vadodara, Nashik, Surat, Ahmedabad, Kolkata |
| Data Fields | Name, address, phone, GPS coords, NABH/JCI status, bed count, ICU beds, specialties, rating, insurance empanelment |
| Sources | NABH public directory, NHA empanelment lists, hospital websites |

Hospitals are ranked on a **5-dimension scoring model**:

| Dimension | Weight | Signals |
|-----------|--------|---------|
| Clinical Capability | 25% | Specialization, procedure volume, bed capacity |
| Reputation | 22% | NABH/JCI accreditation, ratings, review count |
| Affordability | 22% | Premium / mid-tier / budget classification |
| Accessibility | 18% | Distance from user, OPD availability |
| PM-JAY Coverage | 13% | Ayushman Bharat empanelment status |

### 4. Cost Estimation Engine
Costs broken into **7 components** using CGHS 2023 rates as the base:

| Component | Adjustment Factors |
|-----------|-------------------|
| Procedure / Surgery | City tier multiplier (Tier 1: 1.4×, Tier 2: 1.0×, Tier 3: 0.75×) |
| Doctor Consultation | Specialty premium |
| Hospital Stay | Room type (General / Semi-private / Private) |
| Pre/Post Diagnostics | Procedure complexity |
| Medicines & Consumables | Duration of stay |
| Contingency / Complications | Comorbidity flags |
| ICU Escalation Buffer | Diabetes +18%, prior cardiac +35% |

### 5. Lending Intelligence Layer
For healthcare lenders (Poonawalla Fincorp use case):
- Procedure-level cost confidence bands
- PM-JAY coverage as exposure-reduction signal
- Comorbidity risk tier (LOW / MODERATE / HIGH / CRITICAL)
- Suggested loan range with upper/lower bound reasoning

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML/CSS/JS — single file, zero dependencies |
| AI Engine | Groq API · Llama 3.3 70B Versatile |
| Clinical Coding | ICD-10-CM, SNOMED-CT (via LLM mapping) |
| Cost Benchmarks | CGHS 2023 Schedule, PM-JAY HBP 2.0, NHA |
| Hospital Data | 80 verified hospitals, manually curated from public sources |
| Mapping | OpenStreetMap / Leaflet.js |
| Hosting | GitHub Pages (zero backend, fully static) |

---

## Data Sources

| Dataset | Description | Usage |
|---------|-------------|-------|
| **CGHS 2023 Rate Schedule** | 1,800+ procedure codes, govt-standardized pricing | Base cost estimation |
| **PM-JAY HBP 2.0** | 1,350+ health benefit packages | Coverage detection, lender exposure |
| **NHA Cost Benchmarks** | Geo-adjusted pricing tiers | City multipliers |
| **NABH Public Directory** | Accreditation status | Hospital ranking signal |
| **OpenStreetMap** | Real GPS coordinates | Distance calculation, map display |
| **Hospital Websites / NHA Empanelment** | Beds, specialties, insurance | Provider ranking |

> ⚠️ No proprietary data used. All sources are public. Synthetic cost variance modelling ±30% applied per CGHS methodology.

---

## Responsible AI Design

- 🚫 **No diagnostic claims** — decision support only, never diagnosis or treatment advice
- 📊 **Confidence scoring** — every output carries a 0–1 score; low confidence = wider ranges
- 🔓 **Transparent ranking** — all 5 dimensions and weights disclosed to user
- ⚠️ **Risk flagging** — comorbidities surfaced proactively with cost escalation warnings
- 🔒 **Public data only** — fully auditable, no proprietary hospital pricing
- 🏥 **Professional referral** — every output closes with directive to consult a doctor

---

## Evaluation Criteria Coverage

| Criterion | Weight | Our Approach |
|-----------|--------|-------------|
| Clinical Mapping Accuracy | 20% | ICD-10 + SNOMED-CT via Llama 3.3 70B, comorbidity-aware pathway |
| Cost Estimation Logic | 25% | 7-component breakdown, CGHS base, geo + age + comorbidity adjustments |
| Provider Ranking Quality | 20% | 5-dimension transparent scoring, real NABH data, GPS distance |
| Multi-Source Intelligence | 15% | Structured (CGHS/PM-JAY) + derived (benchmarks) + real hospital DB |
| User Experience | 10% | NL input, Hindi support, confidence indicators, export PDF/text |
| Responsible AI | 10% | Explicit disclaimers, confidence bands, no diagnostic claims |

---

## Project Structure

```
MediRoute-INDIA/
├── index.html          ← Full application (single file, self-contained)
├── README.md           ← This file
├── LICENSE             ← MIT License
└── .nojekyll           ← GitHub Pages config
```

---

## Team

Built for TenzorX · Poonawalla Fincorp Hackathon · Problem Statement B — AI Healthcare Navigator

---

## Disclaimer

MediRoute is a decision-support tool only. It does not provide medical diagnosis, treatment advice, or guaranteed cost estimates. All recommendations should be verified with qualified healthcare professionals before making medical or financial decisions. Cost estimates are based on public benchmarks and may vary significantly from actual hospital charges.
