# Speech Understanding Major Project 🎤

This repository contains the coursework, experiments, and findings for my Speech Understanding course at IIT Jodhpur. The project explores practical applications and future challenges in speech processing, covering transcription, low-resource text-to-speech (TTS), audio denoising, and a proposal for a novel research problem.

-----

## 📜 Project Overview

This project is divided into three main parts:

1.  **Lecture Analysis & Low-Resource TTS**: A pipeline that transcribes a code-switched (English-Hindi) lecture, translates it to Telugu, and synthesizes the audio using voice cloning.
2.  **Noise Analysis & Denoising**: An analysis of noisy audio and the implementation and evaluation of two classical denoising algorithms: Spectral Subtraction and Wiener Filtering.
3.  **Selective Code-Switched Translation (Research Proposal)**: A novel proposal for a system that can translate one language in a mixed-language audio stream while preserving the other, along with the speaker's vocal characteristics.

-----

## ✨ Key Tasks and Findings

### Task 1: Lecture Transcription and Low-Resource TTS 🗣️

This task involved building a complete pipeline to process a mixed-language lecture.

  * **Transcription**: Used **OpenAI's Whisper (large-v3)** to transcribe a code-switched English-Hindi audio file. Post-processing was done to remove filler words.
      * **Result**: Achieved a **Word Error Rate (WER) of 28.4%** and a **Character Error Rate (CER) of 5.3%**, demonstrating Whisper's robustness with code-switched input.
  * **Translation**: The cleaned transcription was translated from English/Hindi to Telugu using the `deep-translator` library.
  * **Audio Synthesis**: The translated Telugu text was synthesized using **AI4Bharat's IndicF5 model**, cloning the voice from a reference audio sample.
      * **Result**: The generated audio quality was evaluated, but metrics (MOS: 1.07, PESQ: 1.61) indicated that achieving high-fidelity cross-lingual voice cloning remains a significant challenge.

### Task 2: Audio Denoising and Analysis 🎧

This section focused on enhancing speech quality by reducing background noise.

  * **Analysis**: Analyzed various audio files (clean, noisy, environmental) using metrics like SNR, Spectral Centroid, and Spectral Bandwidth.
  * **Denoising**: Implemented two classic algorithms:
    1.  **Spectral Subtraction (SS)**
    2.  **Wiener Filtering (WF)**
  * **Evaluation**: The performance of the denoising algorithms was compared against clean reference audio using PESQ, MOS, and the impact on transcription accuracy (WER).
      * **Result**: **Wiener Filtering consistently outperformed Spectral Subtraction**, yielding better perceptual quality (higher PESQ and MOS scores) and significantly lower transcription error (WER of 4.2% vs. 9.0% for SS).

### Task 3: Research Proposal - Selective Code-Switched Translation 🔬

This part of the project proposes a solution to a forward-thinking research problem in speech translation.

  * **Problem Statement**: Current speech translation systems translate the entire audio content. This proposal addresses the need for **selective translation**, where only a designated primary language (e.g., Hindi) is translated to a target language, while the secondary, code-switched language (e.g., English) is preserved. This maintains the speaker's original style and cultural nuances.
  * **Proposed Solution**: A conceptual pipeline named **SELECTIVE-CS-TRANS** is designed. It involves:
    1.  Language identification at the segment level.
    2.  Conversion of speech to discrete units.
    3.  Selective translation of primary language units.
    4.  Re-synthesis of the audio, preserving the speaker's voice, prosody, and the original code-switching pattern.
  * **Significance**: This technology could revolutionize media localization (e.g., movie dubbing), educational content, and multilingual virtual assistants by offering more authentic and natural-sounding translations.

-----

## 📂 Repository Structure

```
.
├── Audio_Files/              # Contains all input and output audio files for Q1 and Q2
├── Q1_Transcription_and_TTS/ # Jupyter notebook and code for Task 1
├── Q2_Noise_Reduction/       # Jupyter notebook and code for Task 2
├── Report/                   # The detailed project report in PDF format
└── requirements.txt          # Python dependencies for the project
```

-----

## 🚀 Getting Started

### Prerequisites

  * Python 3.8+
  * FFmpeg

### Installation

1.  **Clone the repository:**

    ```sh
    git clone https://github.com/boku13/Speech_Understanding_Major.git
    cd Speech_Understanding_Major
    ```

2.  **Create and activate a virtual environment (recommended):**

    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required dependencies:**

    ```sh
    pip install -r requirements.txt
    ```

### Usage

The code for each task is self-contained within its respective directory (`Q1_Transcription_and_TTS/` and `Q2_Noise_Reduction/`). You can run the Jupyter notebooks in these folders to see the implementation, experiments, and results for each task.

-----

## 🛠️ Technologies & Models Used

  * **Models**:
      * OpenAI **Whisper (large-v3)** for robust, multilingual ASR.
      * AI4Bharat **IndicF5** for low-resource TTS and voice cloning.
  * **Core Libraries**:
      * **Audio Processing**: `librosa`, `soundfile`
      * **Denoising**: `noisereduce`
      * **Translation**: `deep-translator`
      * **Evaluation**: `torchmetrics`, `pypesq`
      * **Data Handling**: `numpy`, `pandas`
