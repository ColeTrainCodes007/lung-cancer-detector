# ⚠️ Limitations & Honest Assessment

**Project:** AI Lung Cancer Detector  
**Author:** ColeTrainCodes  
**Date:** March 2026

---

## Preface

One of the most important qualities in any engineer, data scientist, or consultant is the ability to honestly assess the boundaries of what they've built. This document is a transparent breakdown of what this model cannot do, where it would fail, and what would need to change before anything like this could be responsibly deployed in a clinical environment.

This is not a disclaimer to minimize the project. It is an acknowledgment that understanding limitations is as important as understanding capabilities — and that the gap between a working prototype and a production clinical tool is significant, intentional, and worth understanding clearly.

---

## 1. Dataset Limitations

### Small Sample Size
The model was trained on **1,097 CT scan images** from a single dataset. For context, clinical-grade AI models for radiology are typically trained on hundreds of thousands to millions of images across multiple institutions and scanner types.

A model trained on 1,097 images has seen an extremely narrow slice of the variation that exists in the real world. It has not seen:
- Scans from different CT scanner manufacturers (GE, Philips, Canon, United Imaging)
- Scans taken at different voltage settings, slice thicknesses, or reconstruction algorithms
- Patients with comorbidities that alter lung appearance (emphysema, fibrosis, pneumonia, COVID-19 scarring)
- Pediatric patients
- Post-surgical anatomy
- Scans with motion artifacts or poor image quality

### Geographic & Demographic Bias
The IQ-OTH/NCCD dataset was collected from two hospitals in Iraq over a three-month period in 2019. The patient population is predominantly from the central region of Iraq — Baghdad, Wasit, Diyala, Salahuddin, and Babylon.

This introduces **demographic bias**. Lung cancer presentation can vary across populations based on genetics, environmental exposures, smoking patterns, and comorbidities. A model trained exclusively on one geographic population may not generalize well to patients from different backgrounds.

Clinical AI tools are required to demonstrate performance across diverse populations before deployment. This model has not been tested outside its source population.

### Class Imbalance
The dataset contains a significant imbalance:
- Normal: 416 images
- Malignant: 561 images
- Benign: 120 images

Even with class weighting applied during training, the model has seen far fewer examples of benign cases than the other classes. This means its ability to correctly identify benign findings is weaker than its performance on normal or malignant cases — a clinically important limitation since misclassifying a benign finding as malignant could lead to unnecessary invasive procedures.

---

## 2. Model Performance Limitations

### Validation Accuracy Gap
The model achieved:
- Training accuracy: **90.45%**
- Validation accuracy: **71.23%**

The 19-point gap between training and validation accuracy indicates **overfitting** — the model has partially memorized patterns in the training data rather than learning fully generalizable features. In a clinical context, a model that performs significantly worse on new data than on its training data is a serious concern.

For reference, FDA-cleared AI radiology tools typically demonstrate sensitivity and specificity above 90% on large independent test sets before receiving clearance.

### No Independent Test Set
Proper model evaluation requires three separate data splits: training, validation, and a completely held-out test set that the model never sees during development. This project used an 80/20 train/validation split but did not reserve a separate test set.

This means the reported validation accuracy may be slightly optimistic — the model's true performance on completely unseen data is unknown.

### Confidence Scores Are Not Calibrated
The model outputs a confidence score (e.g., "91% malignant") but this score has not been **calibrated**. An uncalibrated model might say it is 91% confident but actually be correct only 70% of the time at that confidence level. Calibration is a critical step before confidence scores can be used to make clinical decisions — such as the urgency thresholds in the recommendation engine.

### Single-Slice Classification
CT scans are three-dimensional studies — a chest CT produces hundreds of image slices through the body. This model classifies individual 2D slices in isolation. It does not:
- Analyze the full volumetric scan
- Correlate findings across multiple slices
- Measure nodule size, shape, or growth rate over time
- Account for the location of findings within the lung

A radiologist reading a CT scan reviews all slices in sequence and builds a three-dimensional mental model of what they are seeing. A single-slice classifier is a significant simplification of that process.

---

## 3. Clinical & Regulatory Limitations

### Not FDA Cleared
This model has not undergone FDA review. In the United States, AI software that is intended to aid in medical diagnosis is regulated as a medical device under 21 CFR Part 820. Depending on its intended use and risk classification, it would require either 510(k) clearance or Premarket Approval (PMA) before it could be legally used in clinical practice.

The regulatory process includes:
- Analytical validation (does the software perform as intended?)
- Clinical validation (does it improve patient outcomes?)
- Post-market surveillance (how does it perform in real-world use?)

None of these steps have been completed for this model.

### No HIPAA Compliance Infrastructure
Patient CT scans are Protected Health Information (PHI) under HIPAA. Any system that handles, stores, or transmits real patient scans must be built with HIPAA-compliant infrastructure — encrypted storage, access controls, audit logs, Business Associate Agreements with vendors, and more.

The current deployment on Hugging Face Spaces does not have any HIPAA compliance infrastructure. It should never be used with real patient data.

### Liability & Clinical Responsibility
In clinical practice, the legal and ethical responsibility for a diagnosis rests with the licensed physician, not with a software tool. An AI recommendation engine that suggests "immediate oncologist referral" is providing decision support — it cannot and should not replace clinical judgment.

If this tool were deployed without proper validation and a patient were harmed as a result of an incorrect classification, the legal and ethical consequences would be severe. This is why clinical validation, regulatory clearance, and physician oversight are non-negotiable requirements for real-world deployment.

---

## 4. Technical Limitations

### Input Quality Sensitivity
The model was trained on clean, standardized digital CT scan files. Performance degrades with:
- Photographs of scans taken with a smartphone camera
- Scans with compression artifacts from low-quality JPEG encoding
- Images that have been resized, cropped, or annotated before upload
- Non-CT images (X-rays, MRIs, ultrasounds) — the model will still output a classification but it will be meaningless

### No DICOM Support
Clinical CT scans are stored in **DICOM format** (.dcm files) — a medical imaging standard that contains not just the image but also metadata about the patient, the scanner, the acquisition parameters, and more. This model only accepts standard image files (JPEG, PNG). It cannot read DICOM files, which means it cannot be integrated into a clinical PACS workflow without additional engineering.

### Single Modality
This model only analyzes CT scans. It has no ability to incorporate:
- Patient history or risk factors
- Lab results
- PET scan data
- Pathology results
- Genetic markers

A radiologist integrates all of this context when reading a scan. This model sees only pixels.

### No Explainability
The model outputs a classification and a confidence score, but it does not show **why** it made that decision. It cannot highlight which region of the scan it identified as suspicious or explain which features drove the classification.

Explainability — often implemented through techniques like Grad-CAM (Gradient-weighted Class Activation Mapping) — is critical for clinical adoption. A radiologist needs to be able to look at what the AI flagged and evaluate whether it makes anatomical sense. Without explainability, the model is a black box, which reduces clinical trust and utility.

---

## 5. What Would Need to Change for Real-World Deployment

To be clear about the gap between this prototype and a deployable clinical tool, here is what would realistically need to happen:

| Requirement | Current Status | What's Needed |
|---|---|---|
| Dataset size | ~1,100 images | 100,000+ images across multiple institutions |
| Dataset diversity | Single geography, 2019 | Multi-site, multi-scanner, multi-demographic |
| Validation accuracy | 71.23% | 90%+ on independent test set |
| Independent test set | None | Held-out multi-site test set |
| Confidence calibration | Uncalibrated | Platt scaling or isotonic regression |
| 3D volumetric analysis | No | Full DICOM series processing |
| Explainability | None | Grad-CAM or similar visualization |
| DICOM support | No | Full DICOM ingestion pipeline |
| FDA clearance | No | 510(k) or PMA submission and approval |
| HIPAA compliance | No | Full PHI-compliant infrastructure |
| EHR integration | No | HL7 FHIR API development |
| Clinical trial validation | No | Multi-site prospective clinical study |
| Radiologist oversight layer | No | Human-in-the-loop review workflow |

---

## Conclusion

This project successfully demonstrates the core technical concept: a deep learning model can be trained on real clinical CT scan data, achieve meaningful classification accuracy, and be deployed as an accessible web application — all at zero cost using freely available tools.

What it does not demonstrate is clinical readiness. The distance between a working proof of concept and a safe, validated, regulatory-approved clinical tool is significant. That distance is not a reason to dismiss the technology — it is a roadmap for what comes next.

Understanding that roadmap, and being able to articulate it clearly, is what separates engineers who build things from engineers who build things that matter.

---

*This document is part of the AI Lung Cancer Detector portfolio project. It is intended to demonstrate technical self-awareness and understanding of the clinical AI development lifecycle.*
