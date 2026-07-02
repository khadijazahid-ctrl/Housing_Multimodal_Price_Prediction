
# Multimodal Housing Price Prediction (Images + Tabular Data)

## Objective

The goal of this project is to predict housing prices using a **multimodal machine learning approach** that combines:

- Structured tabular data (e.g., bedrooms, bathrooms, area, etc.)
- House images (visual features)

This allows the model to learn both numerical patterns and visual characteristics of houses for better prediction accuracy.

---

##  Dataset

The dataset contains two types of inputs:

### Tabular Data Features
- bedrooms  
- bathrooms  
- sqft  
- lot_size  
- year_built  
- neighborhood  
- house_type  

### Image Data
- Each house has a corresponding image stored in `data/images/`
- Image paths are stored in the CSV file under `image_path`

---

##  Methodology

### 1. Data Preprocessing
- Numerical features scaled using `StandardScaler`
- Categorical features encoded using `OneHotEncoder`
- Combined preprocessing using `ColumnTransformer`
- Images resized to 224×224 and converted to tensors

---

### 2. Feature Extraction

####  Image Features
- Pretrained **ResNet18** CNN
- Final fully connected layer removed
- Output: 512-dimensional feature vector

####  Tabular Features
- Processed using a Multi-Layer Perceptron (MLP)
- Learns embeddings from structured data

---

### 3. Feature Fusion
- Image and tabular features are concatenated
- Combined representation is passed through fully connected layers

---

### 4. Model Architecture
- CNN (ResNet18) → Image feature extractor  
- MLP → Tabular feature extractor  
- Fusion layer → Concatenation  
- Regression head → Predict house price  

---

### 5. Training
- Loss Function: Mean Squared Error (MSELoss)
- Optimizer: Adam
- Batch training with multiple epochs

---

### 6. Evaluation Metrics
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

---

##  Results & Observations

- The multimodal model improves performance compared to tabular-only models
- Image data adds important visual context (design, condition, structure)
- Proper feature fusion significantly impacts model accuracy

---

##  Visualizations

- Actual vs Predicted price plot
- (Optional) Training loss curve

---

## Project Structure

Housing-Multimodal-Prediction/
│
├── notebook.ipynb
├── requirements.txt
├── README.md
│
├── data/
│ ├── housing.csv
│ └── images/
│
└── saved_model.pth

## Author
Khadija Zahid
