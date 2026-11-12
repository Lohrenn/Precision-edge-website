# 🩺 Precision Edge | Surgical Robotics & AI Dynamics Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-00F2FE.svg?style=for-the-badge)](LICENSE)
[![Build Status](https://img.shields.io/badge/Deployment-GitHub%20Pages-00E676.svg?style=for-the-badge&logo=github)](https://lohrenn.github.io/Precision-Edge)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38BDF8?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Three.js](https://img.shields.io/badge/Three.js-black?style=for-the-badge&logo=three.js&logoColor=white)](https://threejs.org/)
[![Formspree](https://img.shields.io/badge/Formspree-FF6B6B?style=for-the-badge&logo=mailgun&logoColor=white)](https://formspree.io/)

> **Sub-millimeter autonomous robotic assistance for complex surgical procedures.** Powered by real-time neural haptic feedback, 8K stereoscopic 3D vision, and an interactive hospital ROI simulator.

---

## ⚡ Live Telemetry & Quick Links

- 🌐 **Live Demo & Portal:** [https://lohrenn.github.io/Precision-Edge](https://lohrenn.github.io/Precision-Edge)
- 📄 **Clinical Evaluation Report:** `precision_edge_clinical_report.pdf`
- 💬 **Formspree Endpoint Integrations:** Dual-Channel Clinical Demo & Patient Consultation Modal

---

## 📸 Key Features & Architecture

### 1. 🤖 Interactive 3D Surgical Arm Viewport
- **Three.js Canvas:** Real-time interactive 3D rendering of the 7-DOF micro-articulated surgical arm with OrbitControls, interactive node callouts, and camera reset capabilities.
- **X-Ray Wireframe Mode:** Toggleable dynamic wireframe overlay for structural inspection during clinical presentations.

### 2. 🎛️ Interactive Hospital Performance & ROI Estimator
- **Dynamic Metric Calculations:** Real-time updates calculating patient recovery day reductions, operating theatre efficiency gains, and annual cost savings based on custom monthly surgical volume and procedure complexity levels.

### 3. 🛡️ Dual-Channel Validation-Heavy Intake Modal
- **Tab-Switching UI:** Seamless toggle between **Clinical Demo Requests** (B2B / Hospital Executives) and **Patient Consultations** (B2C / Healthcare Consumers).
- **Strict Validation Cues:** Mandatory field highlighting with visual red asterisks (`*`) preventing incomplete browser posts.
- **Specialized Fields:** Includes date pickers, time windows, hospital institutional details, and dedicated consultation types (*Initial Surgical Evaluation*, *Pre-Op Planning*, *Second Opinion Review*, and *Post-Op Follow-Up*).

### 4. 📹 In-Theatre Telemetry Footage & HUD
- Integrated video player with a custom live telemetry overlay HUD displaying simulated 60 FPS system telemetry, vessel precision metrics, and tremor dampening status.

---

## 🛠️ Technical Stack

| Layer | Technology |
| :--- | :--- |
| **Frontend Framework** | HTML5, Tailwind CSS (CDNs), Custom Glassmorphism Styles |
| **Graphics Engine** | Three.js (r128), WebGL, OrbitControls |
| **Iconography & Fonts** | FontAwesome 6.4, Inter, JetBrains Mono |
| **Backend & Form Pipeline** | Formspree API (`URLSearchParams`, Asynchronous `fetch()`) |
| **Hosting & CI/CD** | GitHub Pages (`main` branch workflow) |

---

## 🔧 Engineering Challenges & Resolutions (Post-Mortem)

### Issue 1: Formspree `422 Unprocessable Entity` & Payload Drops
- **Symptom:** Submitting custom JavaScript forms to Formspree resulted in "Bad Form Post Request" errors due to JSON header mismatches and raw `FormData` serialization handling.
- **Resolution:** Re-architected form handlers to serialize payload data cleanly using `URLSearchParams(formData)` with `headers: { 'Accept': 'application/json' }`. Added hidden `<input type="hidden" name="_subject" value="...">` elements inside each form tag to distinguish B2B clinical leads from patient care inquiries.

### Issue 2: Modal Form Reset & Asynchronous UI State Management
- **Symptom:** Submitting a form caused unexpected page redirects or left old input data cached inside the modal.
- **Resolution:** Implemented `e.preventDefault()` inside `handleFormSubmit()`, hiding the inputs (`#modalFormContent`) and triggering an animated glassmorphism success container (`#modalSuccessState`) with a 1-click modal cleanup function (`form.reset()`).

---

## ⚡ Environment & Live Access

- 🌐 **Live Web Deployment:** [https://lohrenn.github.io/Precision-Edge](https://lohrenn.github.io/Precision-Edge)
- 💻 **Local Development Server:** `http://127.0.0.1:5500/Precision-edge-website/index.html#hero` (Live Server)

