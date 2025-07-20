# HVAC Chiller Anomaly Detection

A machine learning-based approach to detect anomalies in HVAC chiller systems using the Building Data Genome Project 2 dataset. This project identifies potential equipment faults and inefficiencies in commercial building cooling systems.

## 🎯 Project Overview

This project analyzes chilled water consumption patterns in commercial buildings to detect anomalies that may indicate:
- Equipment malfunctions
- System inefficiencies  
- Maintenance needs
- Unusual operating conditions

## 📊 Dataset

**Source**: [Building Data Genome Project 2](https://www.kaggle.com/datasets/claytonmiller/buildingdatagenomeproject2) on Kaggle

The dataset includes:
- Chilled water consumption data from multiple buildings
- Weather data (air temperature, humidity, etc.)
- Building metadata (size, location, type)
- Hot water consumption data

## 🔧 Features

- **Data Preprocessing**: Handles missing values and normalizes consumption by building size
- **Anomaly Detection**: Uses Isolation Forest algorithm to identify unusual patterns
- **Explainable AI**: SHAP (SHapley Additive exPlanations) values for model interpretability
- **Heuristic Rules**: Statistical thresholds for additional fault detection
- **Visualization**: Multiple plots showing anomalies and their relationships with weather

## 🚀 Getting Started

### Prerequisites

```bash
pip install kagglehub pandas numpy matplotlib seaborn scikit-learn shap
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/hvac-anomaly-detection.git
cd hvac-anomaly-detection
```

2. Run the main script:
```bash
python hvac_anomaly_detection.py
```

## 📁 Project Structure

```
hvac-anomaly-detection/
│
├── hvac_anomaly_detection.py    # Main analysis script
├── README.md                    # This file
├── requirements.txt             # Python dependencies
│
├── data/                        # Generated data files
│   ├── preprocessed_chilledwater.csv
│   ├── chiller_anomalies.csv
│   └── heuristic_triggers.csv
│
├── plots/                       # Generated visualizations
│   ├── anomaly_plot.png
│   ├── shap_summary.png
│   ├── shap_anomalies.png
│   └── anomaly_analysis.png
│
└── results/                     # Analysis results
    └── anomaly_summary.txt
```

## 🔬 Methodology

### 1. Data Preprocessing
- Filter buildings with <50% missing data
- Interpolate missing values using time-based methods
- Normalize consumption by building floor area (kWh/m²)
- Merge with weather data for correlation analysis

### 2. Anomaly Detection
- **Isolation Forest**: Unsupervised algorithm that isolates anomalies
- **Contamination Rate**: Set to 5% (configurable)
- **Features**: Chilled water consumption + air temperature

### 3. Explainability
- **SHAP Values**: Explain why certain points are flagged as anomalies
- **Feature Importance**: Understand the role of temperature in predictions

### 4. Heuristic Rules
- Statistical threshold: Mean + 2 standard deviations
- Identifies periods of unusually high consumption

## 📈 Results

### Example Building: Cockatoo_health_Ashlie

- **Anomaly Rate**: ~5% of data points flagged
- **Peak Anomalies**: Concentrated during summer months (high cooling demand)
- **Key Insights**: 
  - Most anomalies occur at moderate temperatures (20-30°C)
  - Some anomalies during low-temperature periods may indicate system faults

### Visualizations Generated

1. **Time Series Plot**: Shows consumption over time with anomalies highlighted
2. **Scatter Plot**: Consumption vs. temperature with anomaly classification
3. **SHAP Summary**: Feature importance for model predictions
4. **SHAP Anomalies**: Explains what drives anomaly detection

## 📊 Key Findings

- Anomalies are not always correlated with extreme temperatures
- Some high-consumption periods during mild weather suggest equipment issues
- The model successfully identifies both demand-driven and fault-related anomalies

## 🛠️ Configuration

Key parameters you can adjust:

```python
# Anomaly detection
contamination = 0.05  # Expected percentage of anomalies (5%)

# Heuristic threshold
threshold_multiplier = 2  # Standard deviations above mean

# Building selection
building = 'Cockatoo_health_Ashlie'  # Change to analyze different buildings
```

## 📝 Usage Examples

### Analyze a Different Building
```python
# Get list of available buildings
print(valid_buildings)

# Select a new building
building = 'your_building_name'
```

### Adjust Sensitivity
```python
# More sensitive (detects more anomalies)
model = IsolationForest(contamination=0.1)

# Less sensitive (detects fewer anomalies)  
model = IsolationForest(contamination=0.02)
```

## 🔮 Future Enhancements

- [ ] Multi-building comparative analysis
- [ ] Seasonal anomaly detection
- [ ] Integration with real-time monitoring systems
- [ ] Additional features (occupancy, equipment schedules)
- [ ] Automated alert system
- [ ] Web dashboard for visualization

## 📖 References

- Miller, Clayton, et al. "The Building Data Genome Project 2" (2020)
- Liu, Fei Tony, Kai Ming Ting, and Zhi-Hua Zhou. "Isolation forest." 2008
- Lundberg, Scott M., and Su-In Lee. "A unified approach to interpreting model predictions." 2017

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Building Data Genome Project 2 team for the dataset
- Scikit-learn community for the machine learning tools
- SHAP library developers for explainability tools

## 📧 Contact

Your Name - your.email@example.com

Project Link: https://github.com/yourusername/hvac-anomaly-detection

---

⭐ **Found this project useful? Give it a star!** ⭐
