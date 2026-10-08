# MeowCV

An openCV + mediapipe program that detects facial expressions and displays goated Tiktok cats like Rigby and Larry

<img src="https://github.com/reinesana/MeowCV/blob/main/assets/cat-disgust.jpeg" width="300">

---

## Introduction

**MeowCV** is a CV program that maps human facial expressions to popular cat reactions on Tiktok in real time.

Using your webcam and the mediapipe library, the system tracks key facial landmarks and displays a corresponding cat image when it detects expressions. Each cat is triggered using lightweight rules based on landmark movement like:
1. Shock → mouth opens wide
2. Tongue → mouth open without triggering shock
3. Glare → eye squint

**Note**: This program is designed to be fun and easy to extend — perfect for experimenting with facial heuristics and expression detection.

---

## How it works

1. Your webcam feed is processed in real time using mediapipe face mesh
2. Facial landmarks are extracted (mouth, eyes, nose, etc.)
3. Simple geometric heuristics determine which expression is active
4. A matching Tiktok cat reaction is displayed in a separate window

---

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/reinesana/MeowCV.git
```

### 2. Install dependencies
Python **3.9 – 3.12** required (tested on Python 3.11.7). Python **3.13+** is not supported for `mediapipe==0.10.14`.
```bash
pip install -r requirements.txt
```

### 3. Run the program
```bash
python main.py
```

---

## Configuration

You can customize how the system behaves by editing the configuration values in `main.py`.

### eye_opening_threshold — Shock Detection
Measures the vertical distance between the upper and lower eyelids for both eyes and triggers the shocked cat.
- Increase this value → shock triggers only when eyes are very wide
- Decrease this value → shock triggers more easily
```python
eye_opening_threshold = 0.026  # very exaggerated shock
eye_opening_threshold = 0.020  # subtle eye widening
```

### mouth_open_threshold — Tongue Detection
Measures the vertical distance between the upper and lower lips and triggers only when the mouth opens in a narrow “tongue-out” shape.
- Increase this value → tongue must come out more to trigger
- Decrease this value → slight mouth opening may trigger tongue
```python
mouth_open_threshold = 0.045  # tongue must be very visible
mouth_open_threshold = 0.030  # easier tongue trigger
```

### squinting_threshold — Glare Detection
Measures how close the upper and lower eyelids are and controls when the side-eye cat is triggered.
- Lower this value → glare triggers only on strong squints
- Higher this value → glare triggers more easily
```python
squinting_threshold = 0.016  # very strict glare
squinting_threshold = 0.020  # softer glare
```

---

Have fun 🐱💻

MIT License © 2026 Shana Nursoo  

## nombre
*carlos