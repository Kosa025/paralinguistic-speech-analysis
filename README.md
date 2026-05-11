# Paralinguistic Features in Emotional Speech
### A Comparative Analysis of Human and AI-Generated Voice

**Bachelor's Thesis Project** | Kozminski University (Akademia Leona Koźmińskiego)  
**Program:** Management and Artificial Intelligence  
**Supervisor:** Prof. Aleksandra Przegalińska

---

## What This Project Does

This project extracts and compares **paralinguistic features** (acoustic properties of speech beyond words) between:
- **Human emotional speech** — from the RAVDESS dataset (24 professional actors, 8 emotions)
- **AI-generated speech** — from ElevenLabs TTS (same sentences, emotion-prompted)

The core academic contribution is a **2×2 comparison matrix**:

|                    | Human Voice | AI Voice |
|--------------------|-------------|----------|
| **Human Listener** | Perceptual survey (n=30–40) | Perceptual survey |
| **AI Detector**    | Hume AI / SpeechBrain | Hume AI / SpeechBrain |

---

## Paralinguistic Features Analyzed (49 total)

| Group | Features |
|-------|----------|
| **Pitch (F0)** | mean, std, range, max, min, voiced fraction |
| **Energy** | mean, std, range |
| **Temporal** | duration, speech rate, pause count, pause rate, pause mean duration, voiced duration |
| **Spectral** | ZCR, spectral centroid (mean/std), spectral rolloff, high-frequency energy ratio |
| **Voice Quality** | HNR (Harmonics-to-Noise Ratio), jitter, shimmer |
| **MFCC** | 13 coefficients × mean + std = 26 values |

---

## Tech Stack

| Component | Tools |
|-----------|-------|
| Feature extraction | Python, librosa, praat-parselmouth |
| Data processing | pandas, numpy, scipy |
| Visualization | matplotlib, seaborn |
| TTS generation | ElevenLabs API |
| Emotion detection | Hume AI, SpeechBrain |
| Dataset | RAVDESS (Livingstone & Russo, 2018) |

---

## Project Structure

```
.
├── 01_ravdess_extraction.ipynb   # Feature extraction from RAVDESS + ElevenLabs
├── ravdess_features.csv          # Extracted features (1440 files × 49 features)
├── plots/
│   ├── sample_analysis.png       # Waveform, pitch, energy for single file
│   ├── emotion_preview.png       # Feature comparison across 8 emotions
│   └── human_vs_ai_spiketest.png # Human vs AI comparison (spike test)
└── README.md
```

---

## Dataset

**RAVDESS** — Ryerson Audio-Visual Database of Emotional Speech and Song  
1440 audio files | 24 actors (12F, 12M) | 8 emotions | 2 intensity levels  
Citation: Livingstone SR, Russo FA (2018). PLoS ONE 13(5): e0196391.  
Download: https://zenodo.org/record/1188976

> Note: RAVDESS audio files are not included in this repository due to size (~350MB). Download from Zenodo and place in `Audio_Speech_Actors_01-24/`.

---

## Key Findings (Spike Test — 6 ElevenLabs files)

Preliminary comparison of Human (RAVDESS) vs AI (ElevenLabs, voice: Adam) across angry/happy/sad:

- **Pitch range**: Human ~150–175 Hz range vs AI ~15–70 Hz — AI speaks significantly "flatter"
- **Speech rate**: AI (~0.9) speaks faster than human (~0.45)
- **HNR**: Human (~9–11 dB) vs AI (~4–7 dB) — human voice is more harmonically rich
- **Energy**: AI shows higher RMS energy (likely due to audio normalization differences)

Full analysis pending complete ElevenLabs dataset generation.

---

## Research Context

This project investigates whether AI-generated emotional speech replicates the paralinguistic patterns of human emotional speech — with implications for **adaptive educational AI systems** (AI tutors, feedback agents).

If AI cannot authentically replicate emotional speech patterns, this has direct consequences for how AI tutors should be designed, calibrated, and evaluated in educational settings.

---

## How to Run

```bash
# 1. Clone repository
git clone https://github.com/YOUR_USERNAME/paralinguistic-speech-analysis

# 2. Create virtual environment
python -m venv .venv
.venv\Scripts\activate  # Windows

# 3. Install dependencies
pip install librosa numpy scipy pandas matplotlib seaborn praat-parselmouth tqdm

# 4. Download RAVDESS dataset from Zenodo and place in Audio_Speech_Actors_01-24/

# 5. Open notebook
jupyter notebook 01_ravdess_extraction.ipynb
```

---

## Author

**Maciej** | Kozminski University | 2026  
Bachelor's thesis in Management and Artificial Intelligence
