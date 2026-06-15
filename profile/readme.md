<!--
file: README.md
-> Menjelaskan project workspace SOP-ify
-> Menyediakan arsitektur sistem, tim project plan, dan dokumentasi sub-proyek
-->

# SOP-ify - Capstone-Project-PJK-GM069
---------------
<p> Hello folks! we are PJK-GM069! <p>
<p> This is our final project for Pijak x IBM SkillsBuild <p>

<p align="center">
  <img src="https://raw.githubusercontent.com/SOP-ify/.github/main/Logo_.png" width="300" height="300" alt="SOP-ify">
</p>
<p align="center" style="margin-bottom: 20px; line-height: 0.8;">
    <a href="[PLACEHOLDER_FIGMA_UI_UX_LINK]">UI/UX Design</a> &middot;
    <a href="[PLACEHOLDER_APK_DOWNLOAD_LINK]">APK Download</a> &middot;
    <a href="[PLACEHOLDER_PRESENTATION_SLIDE_LINK]">Presentation Slide</a> 
</p>

<!-- [PLACEHOLDER_DEMO_VIDEO_LINK] -->

#### about

Our project, SOP-ify, is a mobile application designed to assist Indonesian MSMEs (UMKM) in automatically creating structured Standard Operating Procedures (SOPs). By typing or recording a voice note of their business procedures, the system utilizes AI to translate casual and unstructured language into professional, step-by-step SOP documents.

### Architecture Diagram

Below is the system architecture showing how the Flutter mobile application, FastAPI backend, databases, and AI components interact:

```mermaid
graph TD
    subgraph ClientLayer ["Client Layer"]
        MobileApp["📱 Mobile App (Flutter)"]
    end

    subgraph ServiceAILayer ["Service & AI Layer (GCP Cloud Run - GPU)"]
        BackendAPI["⚡ FastAPI Backend (Cloud Run - GPU)"]
        SOPGen["🧠 Gemma 2 2B LoRA"]
        STT["🎙️ Speech-to-Text (faster-whisper)"]
        
        BackendAPI --> SOPGen
        BackendAPI --> STT
    end

    subgraph DataStorageLayer ["Data & Storage Layer"]
        MongoDB[("🍃 MongoDB Atlas")]
        GCS[("🪣 Google Cloud Storage")]
    end

    subgraph ModelRegistry ["Model Registry"]
        HF["🤗 Hugging Face"]
    end

    MobileApp <-->|HTTPS / REST API| BackendAPI
    BackendAPI <-->|Store/Retrieve User & SOP Data| MongoDB
    BackendAPI <-->|Upload Audio / Download SOP Docs| GCS
    SOPGen -.->|Download Model Adapter| HF
```

### Documentation
You can find our relevant documentation at the following links:
- [Machine Learning Documentation](https://github.com/SOP-ify/ML)
- [Backend Documentation](https://github.com/SOP-ify/backend-api)
- [Mobile Apps Documentation](https://github.com/SOP-ify/mobile-sopify)

# The Gang

| Name | Role | id |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| Titasari Pratiwi | Cloud Computing | APC277D6X0010 |
| Muhammad Favian Jiwani | Mobile Development | APC237D6Y0191 |
| Akmal Maulana | Cloud Computing | APC367D6Y0196 |
| Muhamad Iqbal Reza | Machine Learning | APC237D6Y0417 |
| Suryani | UI/UX Design | APC367D6X0436 |
