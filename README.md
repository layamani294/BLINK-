# Blink Counter 🎯

## Basic Details

### Team Name: ESPADA

### Team Members

- **Team Lead:** LAYA
- **Member 2:** NAZAL

## Project Description

Blink Counter is a browser-based AI project that detects and counts eye blinks using a webcam or a pre-recorded video. It uses facial landmark detection and the Eye Aspect Ratio (EAR) to identify when the eyes close and open.

The project also provides useful blink statistics such as blink count, blink rate, blink duration, and an EAR graph.

## The Problem (that doesn't exist)

Have you ever wondered:

> **"How many times did I blink today?"**

Apparently, simply blinking was not enough. We decided to create an AI system to monitor, analyze, count, and graph something humans have been doing automatically since birth.

## The Solution (that nobody asked for)

Blink Counter watches your eyes so you don't have to.

Using your webcam or a recorded video, the application detects facial landmarks, calculates the Eye Aspect Ratio (EAR), identifies eye-closure events, and counts them as blinks.

Because manually counting your own blinks would be even more ridiculous.

---

# Technical Details

## Technologies/Components Used

### Software

- **Language:** TypeScript
- **Frontend:** React
- **Build Tool:** Vite
- **AI/Computer Vision:** MediaPipe Tasks Vision – Face Landmarker
- **Styling:** Tailwind CSS
- **Icons:** Lucide React
- **Animation/UI:** Motion
- **Runtime:** Node.js
- **Browser APIs:** Webcam access through `getUserMedia()`, Canvas API, Video API

### Main Computer Vision Concept

The project uses the **Eye Aspect Ratio (EAR)** to estimate whether the eyes are open or closed.

The basic formula used is:

`EAR = (vertical_distance_1 + vertical_distance_2) / (2 × horizontal_distance)`

When the EAR falls below a configurable threshold for a required number of consecutive frames, the eyes are considered closed. When they open again, a blink event is registered.

---

# Implementation

## How It Works

1. The application loads the MediaPipe Face Landmarker model.
2. The user can enable the webcam or upload a pre-recorded video.
3. MediaPipe detects facial landmarks in each video frame.
4. Specific landmarks around the left and right eyes are extracted.
5. EAR is calculated separately for both eyes.
6. The average EAR is compared with the configured threshold.
7. Consecutive closed frames are tracked to avoid false blink detection.
8. A closed-to-open transition is registered as a blink.
9. Blink information is displayed in the dashboard.
10. The application can export the analysis results as a JSON file.

## Main Features

- Real-time webcam blink detection
- Pre-recorded video blink analysis
- Eye landmark/mesh visualization
- Left-eye and right-eye EAR calculation
- Average EAR monitoring
- Automatic blink counting
- Blink duration measurement
- Blinks-per-minute calculation
- EAR waveform graph
- Optional audio feedback
- Prolonged eye-closure alert
- Camera mirroring option
- Adjustable detection settings
- JSON export for video analysis results
- GPU acceleration with CPU fallback when required

---

# Installation

### Prerequisites

- Node.js installed
- A modern web browser
- Webcam (only required for live camera mode)
- Internet connection for loading the MediaPipe model/CDN resources

### Steps

Clone/download the project and open the project folder in a terminal.

```bash
npm install
```

Then start the development server:

```bash
npm run dev
```

Open the local address shown by Vite in your browser.

For example:

```text
http://localhost:3000
```

## Build for Production

```bash
npm run build
```

To preview the production build:

```bash
npm run preview
```

To check TypeScript:

```bash
npm run lint
```

---

# Run

```bash
npm run dev
```

Then open the Vite development-server URL in a browser.

For live detection:

1. Allow camera permission.
2. Wait for the Face Landmarker AI model to load.
3. Keep your face visible to the camera.
4. Blink normally.
5. Watch the blink counter and EAR graph update in real time.

For video analysis:

1. Select the video-analysis option.
2. Upload an MP4, WebM, or MOV video.
3. Play the video.
4. The system analyzes the detected face and records blink events.
5. View the generated statistics.
6. Export the analysis as JSON if required.

---

# Project Documentation

## Project Structure

```text
blink-counter/
│
├── src/
│   ├── components/
│   │   ├── CalibrationModal.tsx
│   │   ├── EarGraph.tsx
│   │   ├── Header.tsx
│   │   ├── LiveCameraView.tsx
│   │   ├── PythonCodeView.tsx
│   │   ├── SettingsDrawer.tsx
│   │   ├── StatsCards.tsx
│   │   └── VideoAnalysisView.tsx
│   │
│   ├── services/
│   │   └── mediapipeService.ts
│   │
│   ├── utils/
│   │   ├── audio.ts
│   │   ├── canvasDrawing.ts
│   │   └── ear.ts
│   │
│   ├── App.tsx
│   ├── main.tsx
│   ├── index.css
│   └── types.ts
│
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

---

# Screenshots

Add at least 3 screenshots of the working project here.

### Screenshot 1 – Live Blink Detection

`![Live Detection](screenshots/live-detection.png)`

*Shows the webcam interface with facial landmarks and real-time blink detection.*

### Screenshot 2 – Blink Statistics

`![Blink Statistics](screenshots/blink-statistics.png)`

*Shows the blink count, blink rate, blink duration, and related statistics.*

### Screenshot 3 – Video Analysis

`![Video Analysis](screenshots/video-analysis.png)`

*Shows blink detection and EAR analysis while processing a pre-recorded video.*

---

# Diagrams

## Workflow

```text
          START
            │
            ▼
    Load MediaPipe Model
            │
            ▼
   Webcam / Video Input
            │
            ▼
   Detect Face Landmarks
            │
            ▼
      Extract Eye Points
            │
            ▼
       Calculate EAR
            │
            ▼
  EAR < Threshold ?
       /          \
     YES           NO
      │             │
      ▼             ▼
 Track Eye      Eye Open
 Closure            │
      │             │
      └──────┬──────┘
             ▼
     Detect Blink Event
             │
             ▼
   Update Statistics/Graph
             │
             ▼
       Display Results
             │
             ▼
            END
```

*Workflow of the Blink Counter system from video input to blink statistics.*

---

# Project Demo

## Video

Add your demo video link here.

The demo should show:

- Starting the application
- Allowing camera access
- Face landmark detection
- Eye opening/closing detection
- Blink counter updating
- EAR graph changing during blinking
- Video analysis mode
- Exporting analysis data

## Additional Demos

Add any additional demonstration links, screenshots, or presentation materials here.

---

# Team Contributions

- **LAYA:** Project development, UI implementation, blink-detection logic, testing, and documentation.
- **NAZAL:** Project development, testing, debugging, and documentation.

---

# Why Is This a Useless Project?

Because nobody actually needs an AI-powered dashboard to answer the question:

**"Did I blink?"**

But now we have one anyway. 😌

---

## License

This project uses open-source libraries including MediaPipe Tasks Vision, React, Vite, Tailwind CSS, and Lucide React. Refer to the respective projects for their individual licenses.
