# 🌱 Plant Disease Detection

A deep‑learning‑powered web application that classifies leaf images into **39 categories** (healthy or one of 38 diseases), provides information about the ailment and recommended supplements, and even links to a marketplace.  
The model is built with **PyTorch**, packaged in a **Flask** app, and trained on the public **PlantVillage** dataset.

---

## 🔍 Project Overview

Modern agriculture can be hampered by plant diseases.  
This project demonstrates an end‑to‑end pipeline:

1. **Data**
   - Uses the [PlantVillage dataset](https://data.mendeley.com/datasets/tywbtsjrjv/1) (available on Kaggle/Mendeley).
   - Images are organised by class and fed through a standard preprocessing pipeline (`Resize(255) → CenterCrop(224) → ToTensor()`).

2. **Model**
   - Custom convolutional neural network implemented in `Flask Deployed App/CNN.py`.
   - Four convolution blocks with batch‑norm and pooling, followed by two dense layers.
   - Output layer size = 39 classes (see `idx_to_classes` mapping).
   - Weights are saved as `plant_disease_model_1_latest.pt`.

3. **Web Application**
   - `app.py` uses Flask to serve pages under `Flask Deployed App/templates`.
   - Users can upload leaf images; the server predicts a class and looks up disease/supplement info from CSV files.
   - Includes home, contact, prediction, and “market” pages with static assets under `static/`.

4. **Training Notebook**
   - `Model/Plant Disease Detection Code.ipynb` contains the full training script, data splits (85 % train / 15 % test with a validation slice), and transfer‑learning experiments (commented out).
   - The notebook also documents dataset statistics, loss/accuracy plots, and hyperparameters.

5. **Extras**
   - Demo screenshots in `WebPreview/`.
   - A small collection of test images under `test_images/` with filenames matching their labels.

---

## 🚀 Features

- ✅ Classifies 39 leaf conditions (healthy + 38 diseases).
- 📷 Web UI for uploading and analysing images.
- 📄 Displays disease description, prevention steps, and a reference image.
- 🛒 “Market” page lists supplements for each disease with purchase links.
- 🧪 Ready‑to‑use test images included.
- 🔁 Easily extensible model and UI for further research.

---

## 🛠️ Technologies & Dependencies

The application leverages:

- **Python 3.8** (minimum)
- **Flask** – web framework
- **PyTorch** – model definition and inference
- **torchvision** – transforms and datasets
- **PIL (Pillow)** – image handling
- **pandas** – CSV data lookups
- **HTML/CSS/JS** – front‑end templates
- **GitHub** – version control (this repo)

All Python dependencies are listed in `Flask Deployed App/requirements.txt`.

---

## 📁 Repository Structure

```
Plant-Disease-Detection-main/
├── Dataset collection.txt
├── Flask Deployed App/
│   ├── app.py
│   ├── CNN.py
│   ├── disease_info.csv
│   ├── plant_disease_model_1_latest.pt
│   ├── supplement_info.csv
│   ├── static/
│   │   └── uploads/
│   └── templates/
│       ├── base.html
│       ├── contact-us.html
│       ├── home.html
│       ├── index.html
│       ├── market.html
│       └── submit.html
├── Model/
│   ├── Plant Disease Detection Code.ipynb
│   └── Plant Disease Detection Code.md
├── test_images/
└── WebPreview/
```

---

## 🧩 Installation & Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/Ashish29-glitch/Plant-Disease-Detection.git
   cd Plant-Disease-Detection-main
   ```

2. **Create and activate a virtual environment**

   ```bash
   python -m venv .venv
   # Windows PowerShell
   .venv\Scripts\Activate.ps1
   # or on Unix/macOS
   source .venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   cd "Flask Deployed App"
   pip install -r requirements.txt
   ```

4. **Download the pretrained model**
   - [Model download link](https://drive.google.com/drive/folders/1o9XDIaM8wYDAxrcbVpCRRrWOlIf_2rCr?usp=sharing)
   - Save `plant_disease_model_1_latest.pt` in `Flask Deployed App/`.

5. **(Optional) Prepare the dataset**

   If you want to retrain or experiment:
   - Download the PlantVillage dataset from Kaggle/Mendeley.
   - Unzip into a folder named `Dataset/` at the project root.
   - Adjust paths in the notebook as needed.

---

## ▶️ Running the Application

From the `Flask Deployed App` directory:

```bash
python app.py
```

- Visit `http://127.0.0.1:5000/` in your browser.
- Upload a leaf image or use one from `test_images/`.
- The app will display the predicted disease along with information and supplement links.

---

## 🧪 Testing

- The `test_images/` directory contains sample images whose filenames correspond to their labels.
- Use these to verify the model’s predictions without needing to source your own leaves.

---

## 📈 Model Details

- Architecture: custom CNN (see `CNN.py`)
- Input size: 224×224 RGB
- Training parameters (not exhaustive; see notebook):

  | Parameter      | Value                |
  | -------------- | -------------------- |
  | Dataset        | PlantVillage         |
  | Classes        | 39                   |
  | Train/Val/Test | 70 %/15 %/15 %       |
  | Epochs         | 10                   |
  | Batch size     | 10                   |
  | Learning rate  | 0.001                |
  | Optimizer      | Adam                 |
  | Loss           | Binary cross‑entropy |

- Transfer‑learning experiments with ResNet‑50 (commented out) available in the notebook.

---

## 🤝 Contributing

This repository is **open source**. Contributions are welcome!

- Improve the **UI/UX** of the web app.
- Enhance the **model** (more data, different architecture, higher accuracy).
- Add documentation or new features (e.g. mobile support, REST API).
- If you modify the training, please include the updated `.ipynb`/`.md` files in `Model/`.
- Fork the repo, create a branch, and submit a pull request after your changes pass local testing.

See the [GitHub help](https://help.github.com/articles/creating-a-pull-request/) for guidance on pull requests.

## �📞 Contact

For questions or collaboration, use the contact form in the web app or open an issue on the GitHub repository.

---

Thank you for exploring the Plant Disease Detection project!  
Feel free to adapt, extend, and deploy the system to help farmers keep their crops healthy. 🌾
