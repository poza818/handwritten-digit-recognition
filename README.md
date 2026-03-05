<div align="center">

```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║    ✍️   H A N D W R I T T E N   D I G I T               ║
║         R E C O G N I T I O N                           ║
║                                                          ║
║    CNN · MNIST · TensorFlow · Gradio · Python            ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝
```

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
- [📸 Screenshots](#-screenshots)
- [🏗️ Model Architecture](#️-model-architecture)
- [📊 Training Results](#-training-results)
- [🗂️ Project Structure](#️-project-structure)
- [🖼️ Sample Test Images](#️-sample-test-images)
- [🚀 How to Run](#-how-to-run)
  - [⭐ Option A — Kaggle (Recommended)](#-option-a--kaggle-recommended)
  - [🖥️ Option B — Own Machine (Local)](#️-option-b--own-machine-local)
- [📦 Dependencies & Libraries](#-dependencies--libraries)
- [🖥️ GUI Preview](#️-gui-preview)
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
| 📊 | **Confidence Bar** | Visual gradient bar showing prediction certainty |
| 🔢 | **All 10 Probabilities** | Individual probability bar for every digit 0–9 |
| 📋 | **Prediction History** | Last 8 predictions with source icon and timestamp |
| 💾 | **Save Drawing** | Export canvas sketch as PNG file |
| 🎨 | **Dark Theme UI** | Professional dark interface with custom CSS |
| 🌐 | **Public Link** | Gradio auto-generates a shareable public URL |
| 🔒 | **Light Theme Fix** | Forced dark theme — fully visible in any browser setting |

---

## 📸 Screenshots

> 📷 **Add your screenshots here after running the GUI!**
> Take a screenshot while the GUI is open, save to a `screenshots/` folder, push to GitHub, then replace the comments below with real image tags.

### 🖥️ Main Interface
<!-- ![Main Interface](screenshots/gui_main.png) -->
```
📁 screenshots/gui_main.png     ← Full GUI screenshot (add yours here!)
```

### ✏️ Drawing Prediction
<!-- ![Drawing Prediction](screenshots/draw_predict.png) -->
```
📁 screenshots/draw_predict.png ← Canvas drawing with result (add yours here!)
```

### 📂 Upload Prediction
<!-- ![Upload Prediction](screenshots/upload_predict.png) -->
```
📁 screenshots/upload_predict.png ← Uploaded image with result (add yours here!)
```

### 📋 Prediction History
<!-- ![Prediction History](screenshots/history.png) -->
```
📁 screenshots/history.png      ← History section (add yours here!)
```

> 💡 **How to take a screenshot:**
> `Win + Shift + S` (Windows) or `Cmd + Shift + 4` (Mac) → Save to `screenshots/` folder → Push to GitHub → Replace comment lines above with `![title](screenshots/filename.png)`

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
├── 📄 kaggle_training.py    ← STEP 1: Train & save the model (run once!)
├── 📄 kaggle_gui.py         ← STEP 2: Launch interactive GUI (run anytime!)
├── 📄 requirements.txt      ← All Python dependencies
├── 📄 README.md             ← You are here
├── 📄 LICENSE               ← MIT License
│
├── 📁 images/               ← Sample test images for the GUI
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
└── 📁 screenshots/          ← Add your GUI screenshots here!
    └── (add after running the GUI)
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

> 💡 **Tip:** Multiple versions of some digits (e.g. `4.jpeg`, `4(1).jpeg`, `4(2).jpeg`) let you test how the model handles **different handwriting styles** for the same digit!

---

## 🚀 How to Run

### ⭐ Option A — Kaggle *(Recommended)*

> ✅ **Best option** — Free GPU, no installation needed, works in browser, generates a public shareable link!

**🔹 Step 1 — Train the model** *(only once!)*

1. Go to [kaggle.com](https://www.kaggle.com) → **Create** → **New Notebook**
2. Rename it: `digit-recognition-training`
3. Settings → **Internet: ON** ✅ | Settings → **Accelerator: GPU T4** ✅
4. Paste entire `kaggle_training.py` code → **Run All**
5. Wait ~17 minutes for training to complete
6. **Output panel** (right side) → find `digit_model.keras`
7. Click `⋮` → **"Save as Kaggle Dataset"** → name it: `mnist-digit-model` → **Save**

```
⏳ Training...  (~17 minutes on Kaggle GPU T4)
✅ Test Accuracy : 99.43%
✅ Model saved  → digit_model.keras
📢 Save it as a Dataset now! (only do this once)
```

**🔹 Step 2 — Launch the GUI** *(every time!)*

1. Create **new notebook**: `digit-recognition-gui`
2. Settings → **Internet: ON** ✅
3. Right panel → **Add Data** → search `mnist-digit-model` → **Add** ✅
4. Paste entire `kaggle_gui.py` code → **Run All**
5. Public link appears in output → click it → **GUI opens!** 🎉

```
⚡ Model loaded in 3 seconds — no retraining!
🚀 Running on public URL: https://xxxxx.gradio.live
```

---

### 🖥️ Option B — Own Machine *(Local)*

> ℹ️ For running on your own laptop or PC. Requires Python to be installed.

**Requirements:**
- Python 3.8 or higher → [Download Python](https://www.python.org/downloads/)
- pip (comes with Python)
- At least 4GB RAM

**🔹 Step 1 — Clone the repo**
```bash
git clone https://github.com/Khansa972/Handwritten-Digit-Recognition.git
cd Handwritten-Digit-Recognition
```

**🔹 Step 2 — Download & Install all libraries**

First, make sure you have the `requirements.txt` file from this repo, then run:
```bash
pip install -r requirements.txt
```

Or install each library manually one by one:
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

**🔹 Step 3 — Train the model** *(only once)*
```bash
python kaggle_training.py
```
> ⚠️ Training on CPU is slower (~30–60 min). For fast training use **Option A (Kaggle GPU)**.

**🔹 Step 4 — Launch the GUI**
```bash
python kaggle_gui.py
```
> Open browser → go to: `http://127.0.0.1:7860`

---

## 📦 Dependencies & Libraries

Install everything at once:
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

## 🖥️ GUI Preview

```
╔══════════════════════════════════════════════════════════════╗
║  ✍️  Handwritten Digit Recognition                          ║
║  CNN Model trained on MNIST Dataset — by Khansa Bint-e-Zia  ║
║  [Python]  [TensorFlow]  [CNN]  [MNIST]  [AI Project]       ║
╠══════════════════════╦═══════════════════════════════════════╣
║  📂 UPLOAD IMAGE     ║  ✏️ DRAW A DIGIT                     ║
║  ┌──────────────┐    ║  ┌─────────────────────────────────┐ ║
║  │  Drop image  │    ║  │                                 │ ║
║  │  or browse   │    ║  │   Draw your digit here...       │ ║
║  └──────────────┘    ║  │                                 │ ║
║  [🔍 Predict]        ║  └─────────────────────────────────┘ ║
║                      ║  [🔍 Predict] [🗑️ Clear] [💾 Save]  ║
║  ┌─ Result ────────┐ ║  ┌─ Result ──────────────────────┐  ║
║  │  7   RECOGNIZED │ ║  │  3   PREDICTED DIGIT          │  ║
║  │      99.12%     │ ║  │      97.45%                   │  ║
║  │  ▓▓▓▓▓▓▓▓▓▓░ 99%│ ║  │  ▓▓▓▓▓▓▓▓▓░░ 97%             │  ║
║  │  ALL DIGIT PROBS│ ║  │  ALL DIGIT PROBS              │  ║
║  │  0 ░ 0.1%       │ ║  │  3 █ 97.4%                   │  ║
║  │  7 █ 99.1%      │ ║  └───────────────────────────────┘  ║
║  └─────────────────┘ ║                                      ║
╠══════════════════════╩═══════════════════════════════════════╣
║  📋 PREDICTION HISTORY                                      ║
║  [7 📂 99.1%] [3 ✏️ 97.4%] [5 ✏️ 92.5%] [1 📂 99.9%]      ║
╠══════════════════════════════════════════════════════════════╣
║  © 2024 Handwritten Digit Recognition · Khansa Bint-e-Zia   ║
╚══════════════════════════════════════════════════════════════╝
```

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

```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║   © 2024  Handwritten Digit Recognition                  ║
║   ✍️  Khansa Bint-e-Zia  ·  github.com/Khansa972         ║
║   Built with ❤️  using Python · TensorFlow · Kaggle      ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝
```

⭐ **If you found this project helpful, please star the repository!** ⭐

</div>
