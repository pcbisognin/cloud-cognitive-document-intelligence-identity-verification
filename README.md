# Cloud & Cognitive Document Intelligence for Identity Verification

This project implements an end-to-end **document ingestion and identity verification pipeline** using Azure cloud services, computer vision, and language models.  
The solution mirrors a real-world **KYC (Know Your Customer)** workflow, combining OCR, structured data extraction, facial verification, and cross-document validation.

The focus is on building a **cloud-native, production-oriented cognitive system**, rather than an academic prototype.

---

## 🔍 Problem Overview

Digital onboarding processes often require:

- Extracting structured data from identity documents  
- Verifying that a selfie matches the document photo  
- Cross-checking personal information across multiple documents  
- Automating decisions while maintaining reliability and traceability  

This project demonstrates how these challenges can be addressed using **Azure Cognitive Services**, cloud storage, and ML-based verification.

---

## 🧠 Solution Architecture

The pipeline follows these steps:

1. **Document Upload**
   - User-provided documents (ID, selfie, proof of address) are uploaded to **Azure Blob Storage**

2. **Document Intelligence (OCR + Structured Extraction)**
   - Identity documents are analyzed using **Azure Document Intelligence (Form Recognizer)**
   - Structured fields (e.g. name) are extracted
   - OCR text is parsed with **regex** when required (e.g. CPF extraction)

3. **Face Detection and Extraction**
   - Faces are detected and cropped from both ID and selfie using **Azure Face API**

4. **Face Verification**
   - Extracted faces are compared using **DeepFace** to verify identity consistency

5. **Proof-of-Address Analysis**
   - Text is extracted via OCR
   - A **large language model (LLM)** is used to extract structured fields (name, address, CPF)

6. **Cross-Document Validation**
   - Names from ID and proof-of-address are normalized and compared
   - Final checks determine document compatibility

---

## 🛠️ Technologies Used

### Cloud & Cognitive Services
- Azure Blob Storage  
- Azure Document Intelligence (Form Recognizer)  
- Azure Face API  

### Machine Learning & AI
- DeepFace (face verification)  
- Large Language Models (structured data extraction)  

### Python & Libraries
- `azure-storage-blob`
- `azure-ai-formrecognizer`
- `azure-cognitiveservices-vision-face`
- `opencv-python`
- `deepface`
- `numpy`, `pillow`, `regex`

