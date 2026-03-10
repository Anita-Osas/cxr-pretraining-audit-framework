# CXR Pre-Training Dataset Audit Framework

**Anita Aigbomodion, RN**  
Clinical Data Quality Specialist | Medical AI Dataset Auditor  
anita.o.aigbo@gmail.com · Nigeria · Available for remote work

---

## What This Repository Contains

A complete pre-training dataset audit system for chest X-ray AI training data, built and applied to 50 images across four pathology classes as a demonstration 
of clinical data quality methodology.

## Repository Contents

| File | What It Is |
|------|------------|
| `Project_Summary.pdf` | 2-page summary of the audit — methodology, findings, and results table. Start here. |
| `Condensed_Framework_v2.pdf` | 1-page quick reference — all six criteria, scoring rules, and classifications on one sheet |
| `CXR_Quality_Framework_v4.docx` | Full framework document — complete criteria, sub-checks, flag templates, and worked examples |
| [Audit Results — Full Spreadsheet](https://docs.google.com/spreadsheets/d/194ja3uckrUrv_bGtgqBTrHY2w1zJ-slLyANE254WEW4/edit?usp=drivesdk) | Complete scored spreadsheet — all 50 images, scores across 14 columns, and flag notes |

---

## The Problem This Solves

Medical AI companies training on small, curated datasets gain a competitive 
advantage over volume-based approaches, but only when the training data is 
genuinely clean.

In a 500-image training set, 50 corrupted images represent 10% contamination. 
At that level, poor-quality images do not create noise. They actively corrupt the model's learned associations. A model trained on a flipped image learns 
inverted laterality. A model trained on a teaching-file arrow learns to look 
for annotations, not pathology. A model trained on undocumented lines learns 
to generate reports that ignore visible medical devices.

Pre-training audit is the mechanism that prevents this.

---

## Auditor Role — Where This Sits In The Pipeline

This framework operates between data collection and annotation. It does not diagnose pathology, confirm clinical findings, or assess whether treatments 
are correct.

**Boundary rule:** If the question can be answered by reading the documentation and metadata attached to the image, it is in scope. If it requires clinical 
interpretation of the image itself, it is escalated.

---

## Six Audit Criteria

| Criterion | What Is Checked |
|-----------|----------------|
| **C1 — Technical Quality** | Projection type, image orientation, side marker, exposure, inspiration, rotation, metadata consistency, de-identification |
| **C2 — Label Consistency** | Demographic mismatches, projection-label conflicts, label contradictions, label density, label-visual inconsistency |
| **C3 — Image Usability** | Burned-in annotation contamination, image cropping integrity, hardware artifacts, duplicate detection |
| **C4 — Device Documentation** | All visible medical devices checked for acknowledgment and position recording |
| **C5 — Report Completeness** | Five systematic review zones checked in any attached written report |
| **C1F — De-identification** | Patient-identifiable information checked in image borders |

**Scoring:** 3 = Pass · 2 = Borderline · 1 = Fail · N/A = Not applicable

---

## Four Training Classifications

| Classification | Criteria | Training Decision |
|---------------|----------|-------------------|
| **GOLDEN** | All applicable criteria score 3 | Include immediately |
| **BORDERLINE** | Any criterion scores 2 | Refer to specialist with documented flag note |
| **MIMIC** | Technically adequate but confusing artifact present | File to Stress Test Library — hard negative value |
| **REJECT** | Any criterion scores 1 | Exclude from all training sets |

---

## Pilot Project Results — 50 Images

| Pathology | Total | GOLDEN | BORDERLINE | MIMIC | REJECT |
|-----------|-------|--------|------------|-------|--------|
| Pneumonia | 13 | 5 | 4 | 0 | 4 |
| Pneumothorax | 14 | 3 | 4 | 2 | 5 |
| Pleural Effusion | 12 | 2 | 7 | 0 | 3 |
| Cardiomegaly | 11 | 2 | 3 | 2 | 4 |
| **Total** | **50** | **12** | **18** | **4** | **16** |

**32% of images were rejected outright.** In an unaudited training run, 
these 16 images would have entered the pipeline silently.

---

## What This Audit Caught That Automated Pipelines Miss

- **Burned-in annotation contamination** — Teaching file arrows burned into pixel data. AI learns to find annotations, not pathology.
- **Flipped images** — Digitisation errors reversing left-right orientation. AI learns inverted laterality.
- **De-identification failures** — Patient names still visible in image borders. Legal violation regardless of image quality.
- **Confirmed duplicate images** — Same film submitted twice under different IDs. Causes model overfitting.
- **Skin fold mimics of pneumothorax** — Lines that visually resemble a pleural line but fail the avascular zone criterion.
- **Pericardial effusion mislabelled as cardiomegaly** — Water-bottle cardiac configuration that trains the model to confuse two distinct conditions.
- **Undocumented medical devices** — Lines and tubes visible but absent from dataset documentation — a Clinical Safety Gap across all four pathology classes.

---

## Flag Note Structure

Every non-Golden decision is documented with a three-part written rationale.

**OBSERVED:** What was seen. Criterion named. Specific observation stated.  
**MEANS:** What the AI incorrectly learns if this image enters training as-is.  
**ACTION:** Flag phrase + classification. Maximum 3 sentences total.

---

## Regulatory Relevance

FDA and EU AI Act frameworks increasingly require documented training data 
quality audit trails as part of medical device clearance submissions. This 
framework produces structured, written, criterion-based documentation for 
every inclusion and exclusion decision, the format regulatory review requires.

---

## Background

- BSc Nursing Science, Ambrose Alli University (2nd Class Upper, 2023)
- NMCN Licensed 2025
- 3,500+ supervised clinical hours
- 7 months healthcare AI annotation experience
- Previous portfolio: [medical-imaging-annotation-portfolio](https://github.com/Anita-Osas/medical-imaging-annotation-portfolio) — 50 chest X-rays, ~80 annotations, 5 pathologies
- Previous portfolio: [clinical-text-annotation-portfolio](https://github.com/Anita-Osas/clinical-text-annotation-portfolio) — 550 entities, 55 relations, 18 entity types

---

*This project is an independent dataset quality review created to demonstrate clinical AI dataset auditing methodology. March 2026.*
