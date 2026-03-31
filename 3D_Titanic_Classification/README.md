

- **🤖 ML-Powered Survival Prediction**: Random Forest model achieves ~80% accuracy on test data
- **3D Interactive Visualization**: Immersive Titanic ship model rendered with Three.js and HDRI environment lighting
- **🌐 Web-Based Interface**: Real-time predictions with instant results
- **📊 Comprehensive Feature Engineering**: Title extraction, age/fare binning, family size calculations
- **🎨 Professional UI/UX**: Responsive design with smooth animations and 3D camera controls

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|---------------|
| **Frontend** | HTML5, CSS3, JavaScript (ES6+), Three.js, HDRI Lighting |
| **Backend** | Flask, Python |
| **ML/Data Science** | scikit-learn (RandomForest), Pandas, NumPy, Matplotlib, Seaborn |
| **Model Serialization** | Pickle, Joblib |
| **Build Tool** | pip, Python 3.7+ |

---

## 📁 Project Structure

```
Titanic_Classification/
├── data/                           # Dataset folder
│   ├── train.csv                  # Training data (891 samples)
│   ├── test.csv                   # Test data for predictions
│   ├── gender_submission.csv      # Kaggle submission template
│   └── Titanic-Dataset.csv        # Full dataset reference
│
├── model/                         # Trained models
│   ├── final_modelVer1.pkl        # Primary Random Forest model
│   ├── titanic_rf_model.pkl       # Alternative RF model
│   ├── titanic_lr_model.pkl       # Logistic Regression baseline
│   ├── titanic_gb_model.pkl       # Gradient Boosting model
│   └── [other model variants]
│
├── backend/                       # Flask backend
│   ├── app.py                    # Flask application & routes
│   ├── utils.py                  # Prediction logic & preprocessing
│   ├── templates/
│   │   └── index.html            # Web interface (HTML)
│   └── static/
│       ├── script.js             # Frontend logic (Three.js & AJAX)
│       ├── style.css             # Styling
│       └── models/
│           └── NightSkyHDRI003_2K-HDR.hdr  # HDRI environment
│
├── notebooks/                     # Jupyter notebooks
│   ├── titanic_analysis.ipynb    # Complete EDA & model training
│   ├── model.ipynb               # Model development
│   ├── titanic-survival-prediction-ml.ipynb  # Additional analysis
│   ├── titanic_analysis.py       # Python analysis script
│   └── [other analysis notebooks]
│
├── requirements.txt              # Python dependencies
├── README.md                     # This file
└── .gitignore                    # Git ignore file
```

---

## 🚀 Quick Start

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)
- Git (optional, for cloning)

### Installation Steps

1. **Clone the Repository** (or download the ZIP):
   ```bash
   git clone <repository-url>
   cd Titanic_Classification
   ```

2. **Create a Virtual Environment** (Recommended):
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify Dataset Presence**:
   - Ensure `data/train.csv`, `data/test.csv` exist
   - Download from [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic/data) if needed

5. **Run the Flask Application**:
   ```bash
   python backend/app.py
   ```

6. **Access the Web Interface**:
   - Open browser and navigate to: `http://localhost:5000`
   - Enter passenger details and get predictions
   - Interact with the 3D Titanic model

---

## 📊 Machine Learning Model

### Model Architecture

**Primary Model**: Random Forest Classifier
- **Algorithm**: Random Forest (ensemble of decision trees)
- **Implementation**: scikit-learn
- **Model File**: `model/final_modelVer1.pkl`
- **Test Accuracy**: ~80%

**Alternative Models Available**:
- Logistic Regression (baseline)
- Gradient Boosting Classifier
- XGBoost variants

### Feature Engineering

The model uses sophisticated feature engineering:

| Feature | Type | Description |
|---------|------|-------------|
| **Sex_Code** | Numeric | 0 = Male, 1 = Female |
| **Pclass** | Numeric | Passenger class (1, 2, or 3) |
| **Embarked_Code** | Numeric | Embarkation port (0=Southampton, 1=Cherbourg, 2=Queenstown) |
| **Title_Code** | Numeric | Extracted from name (Mr, Mrs, Miss, Master, Rare) |
| **FamilySize** | Numeric | SibSp + Parch + 1 |
| **AgeBin_Code** | Numeric | Age bins: 0-16, 17-32, 33-48, 49-64, 65+ |
| **FareBin_Code** | Numeric | Fare bins: 0-7, 8-14, 15-31, 32+ |

### Model Training Details

**Data Preprocessing**:
1. Handle missing values (Age, Embarked)
2. Extract title from passenger names
3. Encode categorical variables
4. Create age and fare bins
5. Calculate family size

**Train-Test Split**:
- Training set: 80% of data (891 samples)
- Test set: 20% (holdout validation)

**Hyperparameters**:
- n_estimators: 100
- max_depth: 10
- random_state: 42

---

## 💻 How to Use

### Making a Prediction

1. **Via Web Interface**:
   - Fill in the passenger details form
   - Enter: Passenger Class, Gender, Age, Siblings/Spouses, Parents/Children, Fare, Embarkation Port
   - Click "Predict"
   - View survival probability and prediction

2. **Via Python API**:
   ```python
   from backend.utils import predict_survival
   
   passenger_data = {
       'Pclass': 1,
       'Sex': 'female',
       'Age': 25,
       'SibSp': 1,
       'Parch': 0,
       'Fare': 71.2833,
       'Embarked': 'C'
   }
   
   prediction, probability = predict_survival(passenger_data)
   print(f"Survived: {prediction}, Probability: {probability}")
   ```

### 3D Model Interaction

- **Rotate**: Click and drag with mouse
- **Zoom**: Scroll wheel
- **Pan**: Right-click and drag (or use keyboard)
- **Reset**: Use on-screen controls
- Rendered with Three.js and HDRI environment lighting

---

## 📈 Model Performance

| Metric | Value |
|--------|-------|
| **Accuracy** | ~80% |
| **Precision** | High (low false positives) |
| **Recall** | Balanced |
| **F1-Score** | Good |

### Feature Importance
Top predictive features (based on Random Forest):
1. Sex/Gender (most important)
2. Passenger Class (Pclass)
3. Age
4. Fare
5. Family Size

---

## 🎓 Model Training & Development

To retrain the model or explore the analysis:

1. **Open Jupyter Notebook**:
   ```bash
   jupyter notebook notebooks/titanic_analysis.ipynb
   ```

2. **Key Sections**:
   - Data Exploration & Statistics
   - Exploratory Data Analysis (EDA)
   - Feature Engineering
   - Model Training & Evaluation
   - Hyperparameter Tuning

3. **Save New Model**:
   The notebook automatically saves the trained model to `model/final_modelVer1.pkl`

---

## 🔧 Backend API

### Endpoint: `/predict`

**Method**: POST

**Request Body**:
```json
{
  "Pclass": 1,
  "Sex": "female",
  "Age": 25,
  "SibSp": 1,
  "Parch": 0,
  "Fare": 71.2833,
  "Embarked": "Cherbourg"
}
```

**Response**:
```json
{
  "prediction": 1,
  "probability": 0.92
}
```

**Error Response**:
```json
{
  "error": "Missing required field: Age"
}
```

---

## 🐛 Troubleshooting

### Issue: "Model file not found"
- **Solution**: Ensure `model/final_modelVer1.pkl` exists
- **Alternative**: Run the Jupyter notebook to retrain the model

### Issue: "Port 5000 already in use"
- **Solution**: Change port in `backend/app.py`:
  ```python
  app.run(debug=True, port=5001)
  ```

### Issue: Dependencies not installing
- **Solution**: Update pip first:
  ```bash
  pip install --upgrade pip
  pip install -r requirements.txt
  ```

### Issue: HDRI not loading in 3D view
- **Fallback**: Ambient lighting automatically activates if HDRI fails to load

---

## 📚 Technologies & Libraries

### Frontend Libraries
- **Three.js** v0.132.2 - 3D rendering engine
- **RGBELoader** - HDRI environment loading
- **OrbitControls** - Camera interaction

### Backend Libraries
- **Flask** - Web framework
- **scikit-learn** - Machine learning library
- **Pandas** - Data manipulation
- **NumPy** - Numerical computing
- **Matplotlib/Seaborn** - Data visualization

### Full Dependency List
See [requirements.txt](requirements.txt) for all dependencies and versions.

---

## 📋 Dataset Information

**Titanic Dataset Source**: [Kaggle Competition](https://www.kaggle.com/c/titanic/data)

**Dataset Statistics**:
- **Training Samples**: 891 passengers
- **Features**: 11 (PassengerId, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked)
- **Target Variable**: Survived (0=Did not survive, 1=Survived)
- **Historical Event**: RMS Titanic sinking (April 15, 1912)

**Data Fields**:
- **PassengerId**: Unique identifier
- **Survived**: Target (0 or 1)
- **Pclass**: Ticket class (1st, 2nd, 3rd)
- **Name**: Passenger name
- **Sex**: Gender (male or female)
- **Age**: Age in years
- **SibSp**: Number of siblings/spouses aboard
- **Parch**: Number of parents/children aboard
- **Ticket**: Ticket number
- **Fare**: Ticket fare
- **Cabin**: Cabin number
- **Embarked**: Port of embarkation (C=Cherbourg, Q=Queenstown, S=Southampton)

---

## 🌟 Future Enhancements

### Short Term
- [ ] Add input validation and error handling on frontend
- [ ] Implement batch predictions for multiple passengers
- [ ] Add data export functionality (CSV/JSON)
- [ ] Enhanced UI with patient information display

### Medium Term
- [ ] Deploy to cloud platform (Azure, AWS, Heroku)
- [ ] Add more 3D models and interactive scenarios
- [ ] Implement model comparison dashboard
- [ ] Add real-time model performance metrics

### Long Term
- [ ] Dockerize the application
- [ ] Implement CI/CD pipeline
- [ ] Add advanced feature importance visualization
- [ ] Support for model versioning and A/B testing
- [ ] Mobile app development
- [ ] Database integration for predictions history

---

## 📖 Learning Resources

This project demonstrates several important concepts:

- **Machine Learning**: Classification, feature engineering, model evaluation
- **Data Science**: EDA, data preprocessing, statistical analysis
- **Web Development**: Flask backend, HTML/CSS/JavaScript frontend
- **3D Graphics**: Three.js, HDRI lighting, interactive visualization
- **Full-Stack Development**: Integration of ML models with web interfaces

---

## 📄 License

This project is open source and available for educational purposes. Feel free to use, modify, and distribute as needed.

---

## 👤 Author & Credits

**Project Creator**: Academic/Portfolio Project

**Built With**:
- Kaggle's Titanic Dataset
- Three.js for 3D visualization
- scikit-learn for machine learning
- Flask for web framework

**Special Thanks**:
- Kaggle community for the dataset and kernels
- Three.js documentation and examples
- scikit-learn documentation

---

## 💬 Questions & Support

For issues, questions, or suggestions:

1. **Check Troubleshooting Section**: Many common issues are addressed above
2. **Review Jupyter Notebooks**: Detailed explanations in analysis notebooks
3. **Inspect Console Logs**: Check browser console and Flask terminal for errors
4. **Code Comments**: Inline comments throughout the codebase

---

## 📌 Key Statistics

| Statistic | Value |
|-----------|-------|
| **Total Passengers** | 2,224 (training + test) |
| **Survival Rate** | ~38% |
| **Female Survival Rate** | ~74% |
| **Male Survival Rate** | ~19% |
| **First Class Survival Rate** | ~63% |
| **Third Class Survival Rate** | ~24% |

---

**Happy Exploring!** 🚢 Feel free to fork, star, and contribute to this project.
