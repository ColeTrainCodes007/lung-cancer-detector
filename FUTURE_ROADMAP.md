# 🚀 Where This Technology Goes Next: A Vision for Fully Integrated AI Cancer Screening

**Project:** AI Lung Cancer Detector  
**Author:** ColeTrainCodes  
**Date:** March 2026

---

## Overview

What this project demonstrates is a proof of concept — a working AI model that can analyze a CT scan and return a classification with clinical next-step recommendations. But the real question is: what does this look like when it's fully built out, deployed at scale, and integrated into the actual healthcare system end-to-end?

This document outlines the next stages of development — from embedding AI directly into CT hardware, to real-time EHR integration, automated oncology scheduling, and what a fully streamlined patient journey could look like in the near future.

This is not speculation. Every component described here either already exists in some form, is in active clinical trials, or is being developed by major healthcare technology companies right now.

---

## Stage 1: AI Embedded Directly Into the CT Scanner

### The Problem With the Current Workflow
Today, a CT scan produces a raw image file. That file gets sent to a PACS system (Picture Archiving and Communication System), sits in a queue, and waits for a radiologist to open it and read it. That process can take hours to days.

### What Embedded AI Changes
The next generation of CT scanners will have AI inference built directly into the hardware — meaning the model runs **the moment the scan is complete**, before the patient even gets up off the table.

Companies like Siemens Healthineers, GE HealthCare, and Philips are already building AI-assisted imaging platforms. The global AI Oncology CT Scanners market is projected to grow from $0.81 billion in 2024 to $2.05 billion by 2033, driven specifically by demand for real-time AI-assisted cancer detection integrated directly into scanner hardware.

**What this looks like in practice:**
1. Patient completes CT scan
2. Raw scan data is processed by onboard AI in real time (seconds, not hours)
3. AI flags regions of interest, classifies findings, and assigns a risk score
4. Result is immediately available — before the patient leaves the imaging suite
5. High-risk results trigger an automatic alert to the ordering physician and oncology department

This is not replacing the radiologist. It is giving the radiologist a pre-analyzed, annotated scan to review — dramatically cutting the time required per read and allowing them to focus their expertise on complex or borderline cases.

---

## Stage 2: Real-Time EHR Integration

### What Is an EHR?
An Electronic Health Record (EHR) is the digital system hospitals use to store everything about a patient — their history, medications, prior scans, lab results, appointments, and more. Major platforms include Epic, Cerner, and Meditech.

### The Integration Vision
Once a scan is analyzed by the AI, the result shouldn't sit in a separate system — it should flow automatically into the patient's EHR in real time.

**The integrated workflow:**
- AI scan result → automatically written to patient EHR as a structured clinical note
- Result includes: classification (Normal / Benign / Malignant), confidence score, flagged regions with coordinates, and recommended next steps
- The attending physician receives an in-app EHR notification instantly
- The patient's care record is updated before anyone has to manually enter anything

Integrated clinical decision support systems powered by AI are increasingly being used in oncology, pulling together a patient's imaging, pathology, laboratory, and genomic information to suggest potential diagnoses and evidence-based recommendations.

This is already happening in pieces. The full integration of AI imaging results directly into EHR workflows, without human data entry as the bottleneck, is the next step.

---

## Stage 3: Automated Oncology Scheduling

### The Current Bottleneck
Even when a concerning scan result is identified quickly, the next barrier is scheduling. A patient gets a result, their doctor reviews it, decides a specialist referral is needed, has staff call the oncology office, waits for an available slot, calls the patient back, and confirms the appointment. This process routinely takes **days to weeks**.

For a fast-growing malignancy, that delay is clinically significant.

### What Automated Scheduling Looks Like
Building on the EHR integration above, the AI recommendation engine can trigger automated scheduling actions based on result urgency:

| AI Result | Urgency Flag | Automated Action |
|---|---|---|
| Malignant, confidence >85% | CRITICAL | Oncology appointment auto-booked within 48hrs, patient notified by SMS/email immediately |
| Malignant, confidence 60-85% | HIGH | Specialist referral initiated, appointment within 1 week, patient notified |
| Benign finding | MEDIUM | Follow-up imaging scheduled in 3-6 months, added to patient portal |
| Normal | ROUTINE | Next annual screening date added to patient record, reminder set |

The patient receives a text or app notification with their appointment details — no phone tag, no waiting for a callback, no administrative delay.

This model already exists in other areas of healthcare. OpenTable did this for restaurants. The same logic applied to oncology referral scheduling removes one of the most dangerous and frustrating delays in the cancer care pathway.

---

## Stage 4: The Patient-Facing Experience

### Today's Patient Journey (Too Many Steps)
1. Feel concern → schedule GP appointment (1-2 weeks)
2. GP refers for CT scan → wait for referral processing (days)
3. Schedule CT scan → wait for available slot (1-4 weeks)
4. Get scan → wait for radiologist read (24-72 hours)
5. GP receives result → calls patient to schedule follow-up (days)
6. Follow-up appointment → referral to oncologist (more days)
7. Oncologist appointment → treatment planning begins

**Total time from concern to treatment planning: 6-12 weeks in many cases.**

### The AI-Integrated Patient Journey
1. Patient books CT scan directly (no GP referral needed for screening)
2. Scan completed → AI result in seconds
3. If normal: patient notified via app immediately, next screening auto-scheduled
4. If concerning: oncology appointment auto-booked, patient notified within minutes
5. Patient arrives at oncologist with scan already analyzed, annotated, and in their EHR

**Total time from scan to specialist appointment: 24-48 hours for high-risk results.**

### Patient Portal & Self-Upload
The self-upload model demonstrated in this project — where a patient can upload their own scan and receive an instant preliminary result — is a direct-to-consumer version of this workflow. It is particularly powerful for:

- **Rural and underserved populations** who lack nearby imaging centers
- **Uninsured patients** who cannot afford the traditional care pathway
- **Patients monitoring known conditions** who want more frequent, low-cost check-ins between formal appointments
- **International patients** in regions with severe radiologist shortages

---

## Stage 5: Longitudinal Monitoring — AI That Watches Over Time

### Beyond Single-Scan Classification
The current model classifies a single scan in isolation. The next evolution is **longitudinal AI monitoring** — a system that tracks a patient's scans over time and detects subtle changes that a human reviewer comparing scans months apart might miss.

MIT's Sybil model, developed at Massachusetts General Hospital, can forecast lung cancer correctly about 80-95% of the time in populations tested — even before expert human eyes can see any changes or signs of cancer.

This kind of predictive monitoring — where AI watches a series of scans and flags concerning trends before a visible tumor even forms — is one of the most powerful applications of this technology. It transforms cancer screening from a reactive process (find the cancer) to a proactive one (predict and prevent it).

**What a longitudinal monitoring system looks like:**
- Every scan a patient takes is stored and linked to their profile
- AI compares each new scan against their personal baseline and prior scans
- Any meaningful change — even subtle density shifts — triggers a flag
- The system learns the individual patient's normal, making it more sensitive over time

---

## Stage 6: The Oncologist Augmentation Layer

### Freeing Oncologists From Routine Protocol Work
AI clinical decision support platforms like IBM Watson for Oncology and Tempus analyze medical literature and patient data to suggest evidence-based treatment options, helping oncologists personalize treatment plans and match patients to clinical trials.

The vision is an AI layer that sits alongside the oncologist and handles the protocol-lookup work automatically:

- Scan result + patient demographics + staging → AI surfaces the relevant NCCN treatment guideline automatically
- Suggested treatment pathway presented as a starting point, not a mandate
- Clinical trial matching: AI searches current open trials the patient may qualify for
- Drug interaction checks, contraindication flags, dosing calculations — all automated

The oncologist focuses on what only a human can do: complex judgment calls, patient communication, nuanced case management, and research. The AI handles the information retrieval and protocol lookup.

### Reducing Fatigue-Related Diagnostic Error
With over half of radiologists reporting burnout and imaging volumes growing 3-5% annually, fatigue-related errors are a growing clinical risk. AI has demonstrated accuracy on par with or exceeding expert radiologists in breast cancer screening, leading to earlier and more reliable detection. As a second reader — a system that double-checks every scan before it's signed off — AI provides a safety net that reduces the risk of missed findings under high-volume, high-pressure conditions.

---

## Stage 7: The Broader Vision — Democratizing Cancer Screening Globally

### The Scale of the Problem
The radiologist shortage and high screening costs are not just American problems. They are global ones. In many developing countries, there are fewer than 1 radiologist per million people. AI-assisted screening running on low-cost hardware could bring functional cancer screening to populations that currently have essentially none.

### What Full Deployment Could Look Like
- Low-cost CT kiosks in pharmacies, community health centers, and rural clinics
- Patient scans uploaded to cloud AI inference in real time
- Results returned in seconds, flagged cases routed to the nearest available specialist via telemedicine
- Entire screening interaction completed in under 30 minutes, for a fraction of the current cost

The integration of AI-driven imaging systems with telemedicine platforms and digital healthcare networks will further expand access to cancer screening in underserved regions.

---

## What Needs to Happen to Get There

None of this is science fiction. The barriers are not technological — they are regulatory, institutional, and financial:

**Regulatory:** AI medical devices require FDA 510(k) clearance or PMA approval. Several AI radiology tools have already cleared this bar — including products from Viz.ai, Aidoc, and Arterys.

**Clinical Validation:** Models need to be validated across diverse populations, scanner types, and imaging protocols before deployment. This requires large multi-site clinical trials.

**EHR Integration Standards:** HL7 FHIR is the emerging standard for healthcare data interoperability. AI tools that speak FHIR can plug into any major EHR system — this is the technical foundation that makes the integration vision possible.

**Reimbursement:** CMS and private insurers need to establish reimbursement codes for AI-assisted reads. This is already beginning to happen for specific applications.

**Trust:** Clinicians and patients need to understand and trust AI recommendations. Explainable AI — systems that can show *why* they made a classification, not just *what* they classified — is critical to adoption.

---

## This Project as a Foundation

The model built in this project is a starting point. It demonstrates:

- That a working AI classifier can be trained on real clinical data at zero cost
- That a clinical recommendation engine can be layered on top of model output
- That the full system can be deployed as an accessible web application

Scaling this from a portfolio project to a production clinical tool would require significantly more data, clinical validation, regulatory approval, and engineering. But the architecture — scan in, classification out, recommendation generated, next steps triggered — is the same.

The pipeline this project demonstrates is the same pipeline that will eventually be running inside CT scanners, connected to EHR systems, and booking oncology appointments automatically.

---

## Sources

| Organization | Resource |
|---|---|
| Massachusetts General Hospital | [AI for Early Detection of Cancer — Sybil](https://www.massgeneral.org/cancer-center/news/ai-early-detection-cancer) |
| National Cancer Institute | [Applying AI to Whole-Body Images](https://www.cancer.gov/about-nci/organization/cbiit/news-events/blog/2025/applying-artificial-intelligence-ai-whole-body-images-reveal-rare-cancers) |
| Nature — npj Precision Oncology | [The Impact of AI on Modern Oncology](https://www.nature.com/articles/s41698-026-01276-6) |
| OncoDaily | [How AI Is Transforming Cancer Care in 2025](https://oncodaily.com/oncolibrary/artificial-intelligence-ai) |
| PMC / NIH | [AI Performance in Lung Cancer Detection on CT](https://pmc.ncbi.nlm.nih.gov/articles/PMC12250385/) |
| PMC / NIH | [Integrating AI into Radiological Cancer Imaging](https://pmc.ncbi.nlm.nih.gov/articles/PMC11795265/) |
| Strategic Revenue Insights | [AI Oncology CT Scanners Market 2024–2033](https://www.openpr.com/news/4418958/ai-oncology-vibe-ct-scanners-market-size-worth-2-05-billion) |
| Nature — npj Health Systems | [AI Solutions to the Radiology Workforce Shortage](https://www.nature.com/articles/s44401-025-00023-6) |

---

*This document is a forward-looking analysis prepared as part of the AI Lung Cancer Detector portfolio project. It does not represent a product roadmap or commercial offering.*
