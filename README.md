# 🚌 AI-Powered Mobile Urban Intelligence Platform

![SIH 2026](https://img.shields.io/badge/SIH%202026-Internal%20Hackathon-blue)
![Python](https://img.shields.io/badge/Python-3.11+-green)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Computer%20Vision-orange)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-teal)
![React](https://img.shields.io/badge/React-Dashboard-blue)

**Transforming public transport buses into mobile urban sensing units using Edge AI and centralized analytics.**

- **Problem Statement ID:** 26124
- **Domain:** Smart Cities / Urban Mobility / Computer Vision
- **Project:** Mobile Urban Intelligence Platform
- **Maintainer:** Ashish Saini

---

## 📖 Overview

Public transport buses travel across cities every day and can help monitor road conditions, traffic, and public safety. This project uses camera feeds and AI-based computer vision to identify potential road hazards and traffic events.

The platform processes video through an edge AI pipeline and sends event metadata to a centralized command center for monitoring and analysis.

### Problems Addressed

- Road defects, including potholes and damaged surfaces
- Missing or damaged road infrastructure
- Pedestrian and road-safety risks
- Traffic incidents and vehicle identification
- Traffic congestion and vehicle density estimation

## ✨ Key Features

### 🚌 Onboard Edge AI

- YOLOv8-based object detection
- Road hazard and pothole detection
- Vehicle and pedestrian detection
- ByteTrack-based object tracking
- GPS- and timestamp-based event generation
- Offline event buffering using SQLite
- Metadata-based event reporting to reduce network usage

### 🖥️ Central Command Center

- FastAPI backend with REST APIs
- WebSocket-based live event updates
- React-based monitoring dashboard
- GIS maps using Leaflet
- Traffic and road-condition analytics
- Incident monitoring and ANPR integration
- Fleet monitoring and evidence management
- Simulator for demonstration and testing

## 🏗️ System Architecture

```text
┌──────────────────────────────────────┐
│          EDGE AI — ONBOARD BUS       │
│                                      │
│  Camera Feeds                        │
│       ↓                              │
│  YOLOv8 Object Detection              │
│       ↓                              │
│  Object Tracking + Event Generation   │
│       ↓                              │
│  GPS + Timestamp + Event Metadata     │
│       ↓                              │
│  SQLite Offline Buffer                │
└──────────────────┬───────────────────┘
                   │
                   │ Event Metadata
                   ▼
┌──────────────────────────────────────┐
│        CENTRAL COMMAND CENTER         │
│                                      │
│  FastAPI REST API + WebSockets        │
│       ↓                              │
│  Database + Event Processing          │
│       ↓                              │
│  React Dashboard                      │
│       ↓                              │
│  GIS Maps + Analytics + Alerts        │
└──────────────────────────────────────┘
```

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| Edge AI | Python, YOLOv8, OpenCV, ByteTrack |
| Backend | FastAPI, SQLAlchemy, Pydantic, Uvicorn |
| Frontend | React, TypeScript, Vite |
| Maps and Analytics | Leaflet, Recharts |
| Database | SQLite |
| Communication | REST APIs, WebSockets |
| Deployment | Docker, Docker Compose |

## 📂 Project Structure

```text
mobile-urban-intelligence/
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── api/
│   │   ├── db/
│   │   ├── services/
│   │   ├── ai/
│   │   └── sim/
│   └── evidence/
├── edge/
│   ├── detector.py
│   ├── tracker.py
│   ├── gps_simulator.py
│   ├── event_engine.py
│   ├── uploader.py
│   ├── pipeline.py
│   ├── run.py
│   ├── config.py
│   ├── models/
│   └── data/
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   ├── components/
│   │   └── services/
│   └── package.json
├── docker-compose.yml
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- Python 3.11 or later
- Node.js 18 or later
- Git
- Optional CUDA-compatible GPU for accelerated inference

### 1. Clone the Repository

```bash
git clone https://github.com/Saini8890/Mobile-urban-intelligence.git
cd Mobile-urban-intelligence
```

### 2. Set Up the Backend

Open a terminal in the project directory:

```bash
cd backend
python -m venv .venv
```

**Windows PowerShell:**

```powershell
.venv\Scripts\Activate.ps1
```

Install the backend dependencies:

```bash
pip install -r requirements.txt
```

Start the backend server:

```bash
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```

API documentation: http://127.0.0.1:8000/docs

### 3. Set Up the Frontend

Open a separate terminal in the project root:

```bash
cd frontend
npm install
npm run dev
```

Open the local URL displayed by Vite, usually:

http://localhost:5173

### 4. Run the Edge AI Pipeline

Open another terminal in the project root:

```bash
cd edge
pip install -r requirements.txt
python run.py --help
```

Use the available command-line options to configure the video source, bus identifier, and backend API URL.

**Note:** Commands and dependencies may need adjustment depending on the actual project implementation and installed packages.

## 🔐 Privacy and Data Handling

The intended architecture processes video on the edge and sends event metadata to the central server. Evidence images or other data may be transmitted where configured.

Production deployments should implement authentication, access controls, secure communication, data-retention policies, and appropriate privacy safeguards.

## 🔮 Future Improvements

- Improve detection accuracy using additional annotated road datasets
- Deploy and evaluate the edge pipeline on embedded AI hardware
- Improve vehicle counting and congestion analytics
- Integrate a production-ready OCR model for ANPR
- Migrate to a spatial database such as PostgreSQL with PostGIS
- Add role-based access control and audit logging
- Evaluate performance under real-world network conditions

## 👨‍💻 Project Maintainer

**Ashish Saini**

Data Science and Software Development Enthusiast

GitHub: [@Saini8890](https://github.com/Saini8890)

Project Repository: [Mobile Urban Intelligence Platform](https://github.com/Saini8890/Mobile-urban-intelligence)

## 📜 License

This project is intended to use the MIT License. An MIT license badge and license claim should only be added after the appropriate `LICENSE` file is present and the repository's licensing terms have been verified.

## 🙌 Original Project Attribution

This repository is based on a project originally shared by its creator. Please retain the original creator's attribution and follow the applicable license and contribution terms.
