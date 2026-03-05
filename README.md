<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a3a5c,100:4cc9f0&height=200&section=header&text=Handwritten%20Digit%20Recognition&fontSize=38&fontColor=ffffff&fontAlignY=38&desc=CNN%20%C2%B7%20MNIST%20%C2%B7%20TensorFlow%20%C2%B7%20Gradio%20%C2%B7%20Python&descAlignY=58&descSize=16&animation=fadeIn" />

<p>
  <img src="https://img.shields.io/badge/Type-AI%20Project-ef4444?style=for-the-badge&logo=openai&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3.12-4cc9f0?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/TensorFlow-2.19-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" />
  <img src="https://img.shields.io/badge/Model-CNN-4ade80?style=for-the-badge&logo=keras&logoColor=white" />
  <img src="https://img.shields.io/badge/Dataset-MNIST-a855f7?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Accuracy-99.43%25-fbbf24?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Platform-Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white" />
  <img src="https://img.shields.io/badge/GUI-Gradio-f72585?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Completed-22c55e?style=for-the-badge" />
  <img src="https://img.shields.io/badge/License-MIT-brightgreen?style=for-the-badge" />
</p>

<br/>

> 🧠 **A deep learning application that recognizes handwritten digits in real time.**
> Draw a digit on canvas or upload an image — the CNN model predicts it instantly
> with a confidence score and full probability breakdown for all 10 digits.

<br/>

</div>

---

## 📑 Table of Contents

- [📌 About](#-about)
- [✨ Features](#-features)
- [🖥️ GUI Preview](#️-gui-preview)
- [📸 Screenshots](#-screenshots)
- [🏗️ Model Architecture](#️-model-architecture)
- [📊 Training Results](#-training-results)
- [🗂️ Project Structure](#️-project-structure)
- [🖼️ Sample Test Images](#️-sample-test-images)
- [🚀 How to Run](#-how-to-run)
  - [⭐ Option A — Kaggle (Recommended)](#-option-a--kaggle-recommended)
  - [🖥️ Option B — Own Machine (Local)](#️-option-b--own-machine-local)
- [📦 Dependencies & Libraries](#-dependencies--libraries)
- [🧪 Topics Covered](#-topics-covered)
- [👤 Author](#-author)
- [📄 License](#-license)

---

## 📌 About

This project uses a **Convolutional Neural Network (CNN)** trained on the famous **MNIST dataset** (70,000 handwritten digit images) to recognize digits 0–9 with **99.43% accuracy**.

It features a fully interactive dark-theme web GUI where you can:
- 📂 **Upload** any handwritten digit image
- ✏️ **Draw** a digit directly on the canvas with your mouse or finger
- 🔍 **Predict** the digit instantly with confidence scores
- 📋 **Track** prediction history with timestamps

---

## ✨ Features

| # | Feature | Description |
|---|---------|-------------|
| 🤖 | **3-Layer CNN** | Deep convolutional network with 896K parameters |
| ⚡ | **Smart Loader** | Trains once, saves permanently — loads in 3 seconds after |
| 📂 | **Image Upload** | Supports PNG, JPG, BMP — drag & drop or click to browse |
| ✏️ | **Draw Canvas** | Freehand digit drawing with mouse or touch input |
| ⚡ | **Auto Predict** | Predicts automatically as soon as you lift your pen |
| 📊 | **Confidence Bar** | Visual gradient bar showing prediction certainty |
| 🔢 | **All 10 Probabilities** | Individual probability bar for every digit 0–9 |
| 📋 | **Prediction History** | Last 8 predictions with source icon and timestamp |
| 💾 | **Save Drawing** | Export canvas sketch as PNG file |
| 🎨 | **Dark Theme UI** | Professional dark interface with custom CSS |
| 🌐 | **Public Link** | Gradio auto-generates a shareable public URL |

---

## 🖥️ GUI Preview

### 🏠 Main Interface — Upload & Draw

<table>
  <tr>
    <td align="center" width="50%">
      <b>📂 Upload Mode & ✏️ Draw Mode</b><br/><br/>
      <img src="screenshots/gui_main.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <b>📊 Results & 📋 Prediction History</b><br/><br/>
      <img src="screenshots/gui_results.png" width="100%" />
    </td>
  </tr>
</table>

---

## 📸 Screenshots

### 🏠 Overview

<table>
  <tr>
    <td align="center" width="50%">
      <b>🖥️ Home Page</b><br/><br/>
      <img src="screenshots/gui_main.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <b>📊 Results & History</b><br/><br/>
      <img src="screenshots/gui_results.png" width="100%" />
    </td>
  </tr>
</table>

---

### ⚡ Predictions in Action

<table>
  <tr>
    <td align="center" width="33%">
      <b>✏️ Predict 5 (Upload)</b><br/><br/>
      <img src="screenshots/predict_5.png" width="100%" />
    </td>
    <td align="center" width="33%">
      <b>✏️ Predict 2 (Draw)</b><br/><br/>
      <img src="screenshots/predict_2.png" width="100%" />
    </td>
    <td align="center" width="33%">
      <b>📋 History Panel</b><br/><br/>
      <img src="screenshots/gui_results.png" width="100%" />
    </td>
  </tr>
</table>

---

## 🏗️ Model Architecture

```
Input (28×28×1)
      │
      ▼
┌─────────────────────────────────────┐
│  Conv2D(32, 3×3, ReLU, padding=same)│  ← Block 1: Edge detection
│  MaxPooling2D(2×2)                  │
└─────────────────────────────────────┘
      │
      ▼
┌─────────────────────────────────────┐
│  Conv2D(64, 3×3, ReLU, padding=same)│  ← Block 2: Shape detection
│  MaxPooling2D(2×2)                  │
└─────────────────────────────────────┘
      │
      ▼
┌─────────────────────────────────────┐
│  Conv2D(128, 3×3, ReLU,padding=same)│  ← Block 3: Pattern recognition
└─────────────────────────────────────┘
      │
      ▼
Flatten → Dense(128, ReLU) → Dropout(0.5)
      │
      ▼
Dense(10, Softmax)
      │
      ▼
Output: Predicted Digit (0–9) + Confidence %
```

| Layer | Output Shape | Parameters |
|-------|-------------|------------|
| Conv2D (32 filters) | 28×28×32 | 320 |
| MaxPooling2D | 14×14×32 | 0 |
| Conv2D (64 filters) | 14×14×64 | 18,496 |
| MaxPooling2D | 7×7×64 | 0 |
| Conv2D (128 filters) | 7×7×128 | 73,856 |
| Flatten | 6,272 | 0 |
| Dense (128) | 128 | 802,944 |
| Dropout (0.5) | 128 | 0 |
| Dense (10, Softmax) | 10 | 1,290 |
| **Total** | | **896,906** |

---

## 📊 Training Results

| Metric | Value |
|--------|-------|
| 🎯 Test Accuracy | **99.43%** |
| 📉 Test Loss | 0.0287 |
| 🔄 Epochs | 20 |
| 📦 Batch Size | 128 |
| ⚙️ Optimizer | Adam (lr=0.001) |
| 📐 Loss Function | Sparse Categorical Crossentropy |
| 🧪 Train Samples | 60,000 |
| 🧪 Test Samples | 10,000 |
| ⏱️ Training Time | ~17 min (Kaggle GPU T4) |

---

## 🗂️ Project Structure

```
📁 Handwritten-Digit-Recognition/
│
├── 📁 src/                          ← All source code lives here
│   └── 📓 training.ipynb            ← ONE notebook: Train model + Launch GUI
│   └── 📓 training.ipynb            • Cells 1–11  : Train & save model (once!)
│                                      • Cells 12: Launch interactive GUI
│
├── 📁 images/                       ← Sample test images for the GUI
│   ├── 🖼️ 0.jpeg
│   ├── 🖼️ 1.jpeg  1(1).jpeg
│   ├── 🖼️ 2.jpeg
│   ├── 🖼️ 3.jpeg
│   ├── 🖼️ 4.jpeg  4(1).jpeg  4(2).jpeg
│   ├── 🖼️ 5.jpeg  5(1).jpeg  5(2).jpeg
│   ├── 🖼️ 6.jpeg
│   ├── 🖼️ 7.jpeg
│   ├── 🖼️ 8.jpeg
│   └── 🖼️ 9.jpeg  9(1).jpeg
│
├── 📁 screenshots/                  ← GUI screenshots
│   ├── 🖼️ gui_main.png              ← Main interface (upload + draw)
│   └── 🖼️ gui_results.png           ← Results + prediction history
│
├── 🧠 digit_recognition_model.h5   ← Saved trained model (auto-generated)
│                                      ⚠️ Not in repo — lives on Kaggle
│                                      📍 /kaggle/working/digit_recognition_model.h5
│                                      💾 Save as Dataset: "mnist-digit-model"
│                                      📥 Loaded from: /kaggle/input/mnist-digit-model/
│
├── 📄 requirements.txt              ← Python dependencies
├── 📄 .gitignore                    ← Git ignore rules
├── 📄 LICENSE                       ← MIT License
└── 📄 README.md                     ← You are here
```

---

## 🖼️ Sample Test Images

The `images/` folder contains **16 real handwritten digit samples** to test the model!

| Step | Action |
|------|--------|
| 1️⃣ | Open the GUI → **Upload Image** section |
| 2️⃣ | Click **🔍 Predict Uploaded Image** button |
| 3️⃣ | Select any `.jpeg` from the `images/` folder |
| 4️⃣ | See the predicted digit + full confidence breakdown! |

> 💡 Multiple versions of digits (e.g. `4.jpeg`, `4(1).jpeg`, `4(2).jpeg`) let you test different handwriting styles!

---

## 🚀 How to Run

### ⭐ Option A — Kaggle *(Recommended)*

> ✅ **Best option** — Free GPU, no installation, works in browser, generates public shareable link!

> ✅ **Everything is in ONE notebook** — `src/training.ipynb`
> Train the model in the top half, launch the GUI in the bottom half!

**🔹 First Time — Train + Launch GUI**

1. Go to [kaggle.com](https://www.kaggle.com) → **Create** → **New Notebook**
2. Settings → **Internet: ON** ✅ | **Accelerator: GPU T4** ✅
3. Click `File` → **Import Notebook** → upload `src/training.ipynb`
4. **Run All Cells** (Cells 1–18)
5. Training takes ~17 min → then GUI launches automatically!
6. **Output panel** → find `digit_recognition_model.h5`
7. Click `⋮` → **"Save as Kaggle Dataset"** → name: `mnist-digit-model` → **Save** ✅

```
⏳ Cells 1–11  : Training... (~17 minutes on GPU T4)
✅ Test Accuracy : 99.43%
✅ Model saved  → digit_recognition_model.h5
📢 Save as Dataset: mnist-digit-model  (do once!)

⚡ Cells 12 : GUI launching...
🚀 Public URL  : https://xxxxx.gradio.live  ← click this!
```

**🔹 Every Time After — Skip Training, Just Launch GUI**

1. Open the same notebook
3. Run only **Cells 12** (skip training cells!)
4. Click the public URL → **GUI opens in 3 seconds!** 🎉

```
⚡ Model loaded in 3 seconds — no retraining!
🚀 Running on public URL: https://xxxxx.gradio.live
```

---

### 🖥️ Option B — Own Machine *(Local)*

> ℹ️ Requires Python installed on your laptop/PC.

**🔹 Step 1 — Clone the repo**
```bash
git clone https://github.com/Khansa972/Handwritten-Digit-Recognition.git
cd Handwritten-Digit-Recognition
```

**🔹 Step 2 — Install all libraries**
```bash
pip install -r requirements.txt
```

Or install manually:
```bash
pip install tensorflow>=2.10.0
pip install numpy>=1.21.0
pip install opencv-python>=4.5.0
pip install Pillow>=9.0.0
pip install gradio>=4.0.0
pip install matplotlib>=3.5.0
pip install seaborn>=0.11.0
pip install scikit-learn>=1.0.0
```

**🔹 Step 3 — Open notebook in Jupyter**
```bash
pip install jupyter
jupyter notebook
```
> Open `src/training.ipynb` → Run **Cells 1–11** to train (once)
> Then run **Cells 12–18** to launch GUI → visit `http://127.0.0.1:7860`

> ⚠️ Training on CPU is slower (~30–60 min). Use **Option A (Kaggle GPU)** for fast training!

---

## 📦 Dependencies & Libraries

```bash
pip install -r requirements.txt
```

| 📦 Library | Version | 🎯 Purpose |
|-----------|---------|-----------|
| ![TF](https://img.shields.io/badge/tensorflow-≥2.10-FF6F00?style=flat-square&logo=tensorflow) | ≥ 2.10 | CNN model building, training & inference |
| ![NumPy](https://img.shields.io/badge/numpy-≥1.21-013243?style=flat-square&logo=numpy) | ≥ 1.21 | Array & matrix operations |
| ![OpenCV](https://img.shields.io/badge/opencv--python-≥4.5-5C3EE8?style=flat-square) | ≥ 4.5 | Image preprocessing & resizing |
| ![Pillow](https://img.shields.io/badge/Pillow-≥9.0-yellow?style=flat-square) | ≥ 9.0 | Image loading & format conversion |
| ![Gradio](https://img.shields.io/badge/gradio-≥4.0-f72585?style=flat-square) | ≥ 4.0 | Interactive web GUI with public URL |
| ![Matplotlib](https://img.shields.io/badge/matplotlib-≥3.5-11557c?style=flat-square) | ≥ 3.5 | Training accuracy & loss plots |
| ![Sklearn](https://img.shields.io/badge/scikit--learn-≥1.0-F7931E?style=flat-square&logo=scikit-learn) | ≥ 1.0 | Confusion matrix & classification report |
| ![Seaborn](https://img.shields.io/badge/seaborn-≥0.11-4CBBDB?style=flat-square) | ≥ 0.11 | Beautiful heatmap visualization |

---

## 🧪 Topics Covered

`deep-learning` `convolutional-neural-network` `image-classification` `mnist` `tensorflow` `keras` `gradio` `computer-vision` `handwriting-recognition` `ocr` `python` `machine-learning` `ai` `digit-recognition` `neural-network` `kaggle` `python3`

---

## 👤 Author

**Khansa Bint-e-Zia**

- 🔗 GitHub: [@Khansa972](https://github.com/Khansa972)
- 📧 Email: khansazia627@gmail.com

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

<br/>

⭐ **If you found this project helpful, please star the repository!** ⭐

<br/>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:4cc9f0,50:1a3a5c,100:0d1117&height=140&section=footer&text=%C2%A9%202024%20Khansa%20Bint-e-Zia%20%C2%B7%20github.com%2FKhansa972&fontSize=14&fontColor=ffffff&fontAlignY=65&animation=fadeIn" />

</div>
