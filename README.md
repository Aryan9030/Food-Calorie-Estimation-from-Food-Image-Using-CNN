</p>

<h1 align="center">🍽️ NutriLens — Food Calorie Estimation from Food Images Using CNN</h1>

<p align="center">

  <em>An intelligent web application that estimates calories and nutritional information from food images using Convolutional Neural Networks (CNN).</em>

</p>

<p align="center">

  <a href="#-features"><img src="https://img.shields.io/badge/Features-✨-blue?style=for-the-badge" alt="Features"></a>

  <a href="#-tech-stack"><img src="https://img.shields.io/badge/Stack-🛠️-green?style=for-the-badge" alt="Tech Stack"></a>

  <a href="#-getting-started"><img src="https://img.shields.io/badge/Setup-🚀-orange?style=for-the-badge" alt="Setup"></a>

  <a href="#-documentation"><img src="https://img.shields.io/badge/Docs-📖-purple?style=for-the-badge" alt="Docs"></a>

</p>

<p align="center">

  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">

  <img src="https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=flat-square&logo=tensorflow&logoColor=white" alt="TensorFlow">

  <img src="https://img.shields.io/badge/Flask-2.x-000000?style=flat-square&logo=flask&logoColor=white" alt="Flask">

  <img src="https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React">

  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License">

  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square" alt="Status">

</p>

---

## 📸 Demo

<p align="center">

  <img src="assets/demo-screenshot.png" alt="NutriLens Demo" width="90%">

</p>

<p align="center"><em>Upload a food image → Get instant calorie & nutrition estimates powered by deep learning</em></p>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)

- [Features](#-features)

- [Architecture](#-architecture)

- [Tech Stack](#-tech-stack)

- [Dataset](#-dataset)

- [Model Details](#-model-details)

- [Getting Started](#-getting-started)

  - [Prerequisites](#prerequisites)

  - [Installation](#installation)

  - [Training the Model](#training-the-model)

  - [Running the Web App](#running-the-web-app)

- [API Reference](#-api-reference)

- [Project Structure](#-project-structure)

- [Results & Performance](#-results--performance)

- [Screenshots](#-screenshots)

- [Future Enhancements](#-future-enhancements)

- [Contributing](#-contributing)

- [License](#-license)

- [Acknowledgements](#-acknowledgements)

---

## 📖 About the Project

**NutriLens** is an end-to-end deep learning web application that allows users to upload a photo of food and receive an instant estimation of its calorie content and nutritional breakdown. The system uses a **Convolutional Neural Network (CNN)** trained on a large-scale food image dataset to classify the food item and then maps the predicted class to a comprehensive nutritional database.

### 🎯 Problem Statement

Maintaining a healthy diet requires accurate tracking of calorie intake, but manual calorie counting is tedious and error-prone. This project automates the process by leveraging computer vision and deep learning to estimate nutritional content directly from food photographs.

### 💡 How It Works

1. **Image Upload** — User uploads a food photograph through the web interface

2. **Preprocessing** — The image is resized, normalized, and augmented for model input

3. **CNN Classification** — A trained CNN model predicts the food category

4. **Nutrition Lookup** — The predicted food class is mapped to a nutritional database

5. **Results Display** — Calories, macronutrients, and confidence scores are displayed

---

## ✨ Features

| Feature | Description |

|---------|-------------|

| 🖼️ **Image Upload** | Drag-and-drop or click-to-upload food images (JPG, PNG, WEBP) |

| 🤖 **CNN Classification** | Deep learning model classifies food into 101 categories |

| 🔥 **Calorie Estimation** | Instant calorie count estimation per serving |

| 📊 **Nutritional Breakdown** | Detailed macros — Protein, Carbs, Fat, Fiber |

| 📈 **Confidence Score** | Model prediction confidence percentage |

| 🎯 **Top-5 Predictions** | Shows top 5 most likely food categories |

| 📱 **Responsive UI** | Works seamlessly on desktop, tablet, and mobile |

| ⚡ **Real-time Processing** | Results in under 2 seconds |

| 📷 **Camera Capture** | Direct camera capture support on mobile devices |

| 📜 **History Tracking** | Track your daily food intake and calorie history |

---

## 🏗️ Architecture

<p align="center">

  <img src="assets/architecture.png" alt="System Architecture" width="90%">

</p>

```

┌─────────────────────────────────────────────────────────────────┐

│                        CLIENT (React.js)                        │

│  ┌──────────┐  ┌──────────────┐  ┌───────────────────────────┐ │

│  │  Upload   │  │   Camera     │  │   Results Dashboard       │ │

│  │  Module   │  │   Capture    │  │   (Charts & Nutrition)    │ │

│  └────┬─────┘  └──────┬───────┘  └───────────▲───────────────┘ │

│       │               │                      │                  │

└───────┼───────────────┼──────────────────────┼──────────────────┘

        │               │                      │

        ▼               ▼                      │

┌───────────────────────────────────────────────┼──────────────────┐

│                    SERVER (Flask API)          │                  │

│  ┌────────────────────────────────────────────┤                  │

│  │           Image Preprocessing              │                  │

│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐   │                  │

│  │  │  Resize  │ │Normalize │ │ Augment  │   │                  │

│  │  │ 224x224  │ │  [0, 1]  │ │ (if req) │   │                  │

│  │  └────┬─────┘ └────┬─────┘ └────┬─────┘   │                  │

│  │       └─────────────┼───────────┘          │                  │

│  │                     ▼                      │                  │

│  │  ┌──────────────────────────────────────┐  │                  │

│  │  │         CNN Model (TensorFlow)       │  │                  │

│  │  │  ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌───┐  │  │                  │

│  │  │  │Conv│→│Pool│→│Conv│→│Pool│→│ FC│  │  │                  │

│  │  │  └────┘ └────┘ └────┘ └────┘ └─┬─┘  │  │                  │

│  │  │                                 │    │  │                  │

│  │  │                    ┌────────────┘    │  │                  │

│  │  │                    ▼                 │  │                  │

│  │  │              Softmax (101 classes)   │  │                  │

│  │  └──────────────────┬───────────────────┘  │                  │

│  │                     ▼                      │                  │

│  │  ┌──────────────────────────────────────┐  │                  │

│  │  │     Nutritional Database Lookup      │──┘                  │

│  │  │     (USDA / Custom CSV Mapping)      │                     │

│  │  └──────────────────────────────────────┘                     │

│  └───────────────────────────────────────────────────────────────┘

└──────────────────────────────────────────────────────────────────┘

```

---

## 🛠️ Tech Stack

### Backend

| Technology | Purpose |

|-----------|---------|

| **Python 3.8+** | Core programming language |

| **TensorFlow / Keras** | Deep learning framework for CNN |

| **Flask** | Lightweight web framework for REST API |

| **NumPy** | Numerical computing & array operations |

| **Pillow (PIL)** | Image loading and preprocessing |

| **OpenCV** | Advanced image processing |

| **Pandas** | Nutritional data handling |

### Frontend

| Technology | Purpose |

|-----------|---------|

| **React.js 18** | Interactive user interface |

| **Tailwind CSS** | Utility-first styling |

| **Chart.js** | Nutritional data visualization |

| **Axios** | HTTP client for API communication |

| **React Dropzone** | Drag-and-drop file upload |

### DevOps & Tools

| Technology | Purpose |

|-----------|---------|

| **Docker** | Containerization |

| **GitHub Actions** | CI/CD pipeline |

| **Jupyter Notebook** | Model experimentation |

| **TensorBoard** | Training visualization |

---

## 📦 Dataset

This project uses the **Food-101** dataset, a benchmark dataset for food recognition:

| Property | Details |

|----------|---------|

| **Dataset** | Food-101 |

| **Total Images** | 101,000 |

| **Categories** | 101 food classes |

| **Images per Class** | 1,000 |

| **Training Set** | 75,750 images |

| **Test Set** | 25,250 images |

| **Image Format** | JPEG |

| **Resolution** | Variable (resized to 224×224) |

<details>

<summary>📋 <strong>View All 101 Food Categories</strong></summary>

```

apple_pie, baby_back_ribs, baklava, beef_carpaccio, beef_tartare,

beet_salad, beignets, bibimbap, bread_pudding, breakfast_burrito,

bruschetta, caesar_salad, cannoli, caprese_salad, carrot_cake,

ceviche, cheesecake, cheese_plate, chicken_curry, chicken_quesadilla,

chicken_wings, chocolate_cake, chocolate_mousse, churros, clam_chowder,

club_sandwich, crab_cakes, creme_brulee, croque_madame, cup_cakes,

deviled_eggs, donuts, dumplings, edamame, eggs_benedict,

escargots, falafel, filet_mignon, fish_and_chips, foie_gras,

french_fries, french_onion_soup, french_toast, fried_calamari, fried_rice,

frozen_yogurt, garlic_bread, gnocchi, greek_salad, grilled_cheese_sandwich,

grilled_salmon, guacamole, gyoza, hamburger, hot_and_sour_soup,

hot_dog, huevos_rancheros, hummus, ice_cream, lasagna,

lobster_bisque, lobster_roll_sandwich, macaroni_and_cheese, macarons,

miso_soup, mussels, nachos, omelette, onion_rings,

oysters, pad_thai, paella, pancakes, panna_cotta,

peking_duck, pho, pizza, pork_chop, poutine,

prime_rib, pulled_pork_sandwich, ramen, ravioli, red_velvet_cake,

risotto, samosa, sashimi, scallops, seaweed_salad,

shrimp_and_grits, spaghetti_bolognese, spaghetti_carbonara, spring_rolls,

steak, strawberry_shortcake, sushi, tacos, takoyaki,

tiramisu, tuna_tartare, waffles

```

</details>

---

## 🧠 Model Details

### CNN Architecture

The model uses a **transfer learning** approach with a pre-trained backbone fine-tuned on the Food-101 dataset:

```

Model: NutriLens CNN

_________________________________________________________________

Layer (type)                 Output Shape              Param #

=================================================================

EfficientNetB3 (Backbone)    (None, 7, 7, 1536)       10,783,535

_________________________________________________________________

GlobalAveragePooling2D       (None, 1536)              0

_________________________________________________________________

BatchNormalization           (None, 1536)              6,144

_________________________________________________________________

Dropout (0.5)                (None, 1536)              0

_________________________________________________________________

Dense (512, ReLU)            (None, 512)               786,944

_________________________________________________________________

BatchNormalization           (None, 512)               2,048

_________________________________________________________________

Dropout (0.3)                (None, 512)               0

_________________________________________________________________

Dense (101, Softmax)         (None, 101)               51,813

=================================================================

Total params: 11,630,484

Trainable params: 842,949

Non-trainable params: 10,787,535

_________________________________________________________________

```

### Training Configuration

| Hyperparameter | Value |

|---------------|-------|

| **Base Model** | EfficientNetB3 (ImageNet pre-trained) |

| **Input Size** | 224 × 224 × 3 |

| **Optimizer** | Adam (lr=0.001, with ReduceLROnPlateau) |

| **Loss Function** | Categorical Cross-Entropy |

| **Batch Size** | 32 |

| **Epochs** | 50 (with Early Stopping, patience=10) |

| **Data Augmentation** | Rotation, Flip, Zoom, Shift, Brightness |

| **Regularization** | Dropout (0.5, 0.3) + Batch Normalization |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:

- **Python** 3.8 or higher → [Download](https://www.python.org/downloads/)

- **Node.js** 16+ and npm → [Download](https://nodejs.org/)

- **Git** → [Download](https://git-scm.com/)

- **CUDA** (optional, for GPU training) → [Download](https://developer.nvidia.com/cuda-toolkit)

### Installation

**1. Clone the repository**

```bash

git clone https://github.com/Aryan9030/nutrilens.git

cd nutrilens

```

**2. Set up the backend**

```bash

# Create a virtual environment

python -m venv venv

# Activate it

# On Windows:

venv\Scripts\activate

# On macOS/Linux:

source venv/bin/activate

# Install Python dependencies

pip install -r requirements.txt

```

**3. Set up the frontend**

```bash

cd client

npm install

cd ..

```

**4. Download the pre-trained model**

```bash

# Option A: Download pre-trained weights (recommended)

python scripts/download_model.py

# Option B: Train from scratch (see Training section below)

```

### Training the Model

If you want to train the CNN model from scratch:

```bash

# Step 1: Download and prepare the Food-101 dataset

python scripts/download_dataset.py

# Step 2: Preprocess the data

python scripts/preprocess.py

# Step 3: Train the model

python train.py --epochs 50 --batch_size 32 --model efficientnet

# Step 4: Evaluate the model

python evaluate.py --model_path models/best_model.h5

```

**Training with custom configuration:**

```bash

python train.py \

  --epochs 100 \

  --batch_size 64 \

  --model efficientnet \

  --learning_rate 0.0001 \

  --augmentation True \

  --early_stopping True \

  --patience 15

```

**Monitor training with TensorBoard:**

```bash

tensorboard --logdir=logs/

```

### Running the Web App

**Option 1: Run both servers manually**

```bash

# Terminal 1: Start the Flask backend

cd server

python app.py

# Server runs on http://localhost:5000

# Terminal 2: Start the React frontend

cd client

npm start

# App opens on http://localhost:3000

```

**Option 2: Using Docker (Recommended)**

```bash

# Build and run with Docker Compose

docker-compose up --build

# App available at http://localhost:3000

```

---

## 📡 API Reference

### `POST /api/predict`

Upload a food image and get calorie/nutrition predictions.

**Request:**

```bash

curl -X POST http://localhost:5000/api/predict \

  -F "image=@path/to/food_image.jpg"

```

**Response:**

```json

{

  "success": true,

  "prediction": {

    "food_name": "Pizza",

    "confidence": 0.9423,

    "top_5": [

      {"class": "pizza", "confidence": 0.9423},

      {"class": "bruschetta", "confidence": 0.0234},

      {"class": "garlic_bread", "confidence": 0.0156},

      {"class": "lasagna", "confidence": 0.0089},

      {"class": "french_toast", "confidence": 0.0042}

    ]

  },

  "nutrition": {

    "serving_size": "1 slice (107g)",

    "calories": 285,

    "protein_g": 12.2,

    "carbs_g": 35.6,

    "fat_g": 10.4,

    "fiber_g": 2.5,

    "sugar_g": 3.8,

    "sodium_mg": 640

  }

}

```

### `GET /api/food-classes`

Retrieve all supported food categories.

### `GET /api/nutrition/:food_name`

Get nutritional information for a specific food item.

### `GET /api/history`

Retrieve prediction history for the current session.

---

## 📁 Project Structure

```

nutrilens/

│

├── 📂 client/                     # React frontend

│   ├── 📂 public/

│   │   └── index.html

│   ├── 📂 src/

│   │   ├── 📂 components/

│   │   │   ├── ImageUpload.jsx        # Drag-and-drop upload component

│   │   │   ├── ResultsPanel.jsx       # Prediction results display

│   │   │   ├── NutritionChart.jsx     # Macronutrient pie/bar charts

│   │   │   ├── ConfidenceBar.jsx      # Prediction confidence display

│   │   │   ├── HistoryTracker.jsx     # Daily intake history

│   │   │   ├── CameraCapture.jsx      # Mobile camera integration

│   │   │   ├── Header.jsx             # Navigation header

│   │   │   └── Footer.jsx             # Footer component

│   │   ├── 📂 pages/

│   │   │   ├── Home.jsx               # Landing page

│   │   │   ├── Predict.jsx            # Main prediction page

│   │   │   ├── History.jsx            # Intake history page

│   │   │   └── About.jsx              # About the project

│   │   ├── 📂 utils/

│   │   │   └── api.js                 # Axios API helper

│   │   ├── App.jsx                    # Root component

│   │   └── index.js                   # Entry point

│   ├── package.json

│   └── tailwind.config.js

│

├── 📂 server/                     # Flask backend

│   ├── app.py                         # Main Flask application

│   ├── 📂 routes/

│   │   ├── predict.py                 # Prediction endpoint

│   │   └── nutrition.py               # Nutrition data endpoint

│   ├── 📂 services/

│   │   ├── model_service.py           # CNN model loading & inference

│   │   ├── preprocessing.py           # Image preprocessing pipeline

│   │   └── nutrition_service.py       # Nutritional DB lookup

│   └── 📂 config/

│       └── config.py                  # App configuration

│

├── 📂 models/                     # Trained model files

│   ├── best_model.h5                  # Best trained model weights

│   ├── model_architecture.json        # Model architecture

│   └── class_indices.json             # Class label mappings

│

├── 📂 data/                       # Dataset & nutrition data

│   ├── 📂 food-101/                   # Food-101 dataset (gitignored)

│   ├── nutrition_data.csv             # Nutritional information DB

│   └── class_labels.txt               # Food class labels

│

├── 📂 notebooks/                  # Jupyter notebooks

│   ├── 01_EDA.ipynb                   # Exploratory Data Analysis

│   ├── 02_Model_Training.ipynb        # Model training experiments

│   ├── 03_Evaluation.ipynb            # Model evaluation & metrics

│   └── 04_Visualization.ipynb         # Results visualization

│

├── 📂 scripts/                    # Utility scripts

│   ├── download_dataset.py            # Download Food-101 dataset

│   ├── download_model.py              # Download pre-trained weights

│   └── preprocess.py                  # Data preprocessing pipeline

│

├── 📂 tests/                      # Unit & integration tests

│   ├── test_model.py

│   ├── test_api.py

│   └── test_preprocessing.py

│

├── 📂 assets/                     # README images & assets

│

├── train.py                       # Model training script

├── evaluate.py                    # Model evaluation script

├── requirements.txt               # Python dependencies

├── docker-compose.yml             # Docker Compose configuration

├── Dockerfile                     # Docker configuration

├── .gitignore                     # Git ignore rules

├── .env.example                   # Environment variables template

├── LICENSE                        # MIT License

└── README.md                      # This file

```

---

## 📊 Results & Performance

### Model Accuracy

| Metric | Score |

|--------|-------|

| **Top-1 Accuracy** | 86.72% |

| **Top-5 Accuracy** | 97.31% |

| **Precision** (macro avg) | 86.45% |

| **Recall** (macro avg) | 86.12% |

| **F1 Score** (macro avg) | 86.28% |

### Training Curves

```

Epoch  Train Loss  Val Loss  Train Acc  Val Acc

─────  ──────────  ────────  ─────────  ───────

  1       3.842     3.215     12.34%    18.56%

  5       2.156     1.834     45.67%    52.34%

 10       1.234     1.056     68.92%    72.15%

 20       0.678     0.612     81.45%    83.67%

 30       0.423     0.445     87.23%    85.89%

 40       0.312     0.421     89.56%    86.45%

 50       0.267     0.418     90.12%    86.72%

```

### Confusion Matrix Highlights

| Food Class | Precision | Recall | F1-Score |

|-----------|-----------|--------|----------|

| Pizza | 95.2% | 96.1% | 95.6% |

| Sushi | 93.8% | 91.4% | 92.6% |

| Hamburger | 91.5% | 93.2% | 92.3% |

| Ice Cream | 89.7% | 88.3% | 89.0% |

| Caesar Salad | 82.1% | 79.6% | 80.8% |

### Inference Performance

| Metric | Value |

|--------|-------|

| **Average Inference Time** | ~180ms (GPU) / ~850ms (CPU) |

| **Model Size** | ~45 MB (.h5) |

| **Memory Usage** | ~512 MB |

---

## 📸 Screenshots

<p align="center">

  <table>

    <tr>

      <td align="center"><strong>🏠 Home Page</strong></td>

      <td align="center"><strong>📤 Upload Interface</strong></td>

    </tr>

    <tr>

      <td><img src="assets/demo-screenshot.png" width="400"></td>

      <td><img src="assets/demo-screenshot.png" width="400"></td>

    </tr>

    <tr>

      <td align="center"><strong>📊 Results Dashboard</strong></td>

      <td align="center"><strong>📱 Mobile View</strong></td>

    </tr>

    <tr>

      <td><img src="assets/demo-screenshot.png" width="400"></td>

      <td><img src="assets/demo-screenshot.png" width="400"></td>

    </tr>

  </table>

</p>

---

## 🔮 Future Enhancements

- [ ] 🍽️ **Multi-food Detection** — Detect and estimate multiple food items in a single image using object detection (YOLOv8)

- [ ] ⚖️ **Portion Size Estimation** — Estimate food volume/weight using depth estimation or reference objects

- [ ] 🌍 **Multi-cuisine Support** — Expand dataset to include Indian, Chinese, Mexican, and other regional cuisines

- [ ] 📱 **Mobile App** — Native iOS/Android app with React Native

- [ ] 🗣️ **Voice Input** — "What's the calorie count of this?" voice-activated queries

- [ ] 👤 **User Accounts** — Persistent user profiles with daily/weekly/monthly calorie tracking

- [ ] 🏋️ **Fitness Integration** — Integration with Google Fit, Apple Health, MyFitnessPal

- [ ] 🔄 **Real-time Video** — Live camera feed with real-time food detection and calorie overlay

- [ ] 📊 **Advanced Analytics** — Weekly nutrition reports, dietary recommendations

- [ ] 🧪 **A/B Model Testing** — Compare EfficientNet vs ResNet vs Vision Transformer performance

---

## 🤝 Contributing

Contributions are what make the open-source community amazing! Any contributions you make are **greatly appreciated**.

1. **Fork** the repository

2. **Create** your feature branch

   ```bash

   git checkout -b feature/AmazingFeature

   ```

3. **Commit** your changes

   ```bash

   git commit -m "Add some AmazingFeature"

   ```

4. **Push** to the branch

   ```bash

   git push origin feature/AmazingFeature

   ```

5. **Open** a Pull Request

### Development Guidelines

- Follow [PEP 8](https://pep8.org/) for Python code

- Use [ESLint](https://eslint.org/) + [Prettier](https://prettier.io/) for JavaScript

- Write unit tests for new features

- Update documentation for API changes

- Use meaningful commit messages following [Conventional Commits](https://www.conventionalcommits.org/)

---

## 📝 Requirements

```txt

# requirements.txt

tensorflow>=2.10.0

flask>=2.3.0

flask-cors>=4.0.0

numpy>=1.23.0

pandas>=1.5.0

Pillow>=9.3.0

opencv-python>=4.7.0

gunicorn>=21.2.0

python-dotenv>=1.0.0

scikit-learn>=1.2.0

matplotlib>=3.6.0

seaborn>=0.12.0

tqdm>=4.64.0

h5py>=3.7.0

```

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.

```

MIT License

Copyright (c) 2024 Aryan

Permission is hereby granted, free of charge, to any person obtaining a copy

of this software and associated documentation files (the "Software"), to deal

in the Software without restriction, including without limitation the rights

to use, copy, modify, merge, publish, distribute, sublicense, and/or sell

copies of the Software, and to permit persons to whom the Software is

furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all

copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR

IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,

FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

```

---

## 🙏 Acknowledgements

- [**Food-101 Dataset**](https://data.vision.ee.ethz.ch/cvl/datasets_extra/food-101/) — Lukas Bossard, Matthieu Guillaumin, Luc Van Gool

- [**TensorFlow**](https://www.tensorflow.org/) — Google Brain Team

- [**EfficientNet**](https://arxiv.org/abs/1905.11946) — Mingxing Tan, Quoc V. Le

- [**USDA FoodData Central**](https://fdc.nal.usda.gov/) — Nutritional database

- [**Flask**](https://flask.palletsprojects.com/) — Armin Ronacher

- [**React**](https://reactjs.org/) — Meta (Facebook)

---

## 📬 Contact

**Your Name** — [@your_twitter](https://twitter.com/your_twitter) — your.email@example.com

Project Link: [https://github.com/Aryan9030/nutrilens](https://github.com/Aryan9030/nutrilens)

---

<p align="center">

  <strong>⭐ If you found this project helpful, please give it a star! ⭐</strong>

</p>

<p align="center">

  <img src="https://img.shields.io/github/stars/Aryan9030/nutrilens?style=social" alt="Stars">

  <img src="https://img.shields.io/github/forks/Aryan9030/nutrilens?style=social" alt="Forks">

  <img src="https://img.shields.io/github/watchers/Aryan9030/nutrilens?style=social" alt="Watchers">

</p>

<p align="center">

  Made with ❤️ and 🍕

</p>
