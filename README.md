# SVM Optimization 

## Dataset Overview
- **Dataset**: Wine Quality (Red variant)
- **Source**: UCI Machine Learning Repository
- **Samples**: 4,898 total
- **Features**: 11 physicochemical properties
- **Target Variable**: Wine quality (binary classification: 1 if quality ≥6, else 0)
- **Train-Test Split**: 70-30 ratio (10 unique splits)

## Methodology
1. **Preprocessing**:
   - Standardized features using `StandardScaler`
   - Binary classification threshold applied to quality ratings

2. **Optimization**:
   - RandomizedSearchCV with 20 iterations per sample
   - Hyperparameter ranges:
     - C: loguniform(0.1, 100)
     - gamma: loguniform(0.0001, 1)
     - kernel: ['linear', 'rbf']
   - 3-fold cross-validation

## Results

### Table 1: Comparative Performance
| Sample # | Train Size | Test Size | Accuracy | Best C   | Best Gamma | Kernel |
|----------|------------|-----------|----------|----------|------------|--------|
| 51       | 1119       | 480       | 0.7521   | 13.1451  | 0.0964     | linear |
| 52       | 1119       | 480       | 0.7396   | 56.7820  | 0.0001     | linear |
| 53       | 1119       | 480       | 0.7125   | 13.1451  | 0.0964     | linear |
| 54       | 1119       | 480       | 0.7417   | 56.7820  | 0.0001     | linear |
| 55       | 1119       | 480       | 0.7396   | 78.5276  | 0.0015     | linear |
| 56       | 1119       | 480       | 0.7521   | 56.7820  | 0.0001     | linear |
| 57       | 1119       | 480       | 0.7313   | 2.8016   | 0.0005     | linear |
| 58       | 1119       | 480       | 0.7417   | 78.5276  | 0.0015     | linear |
| 59       | 1119       | 480       | 0.7521   | 56.7820  | 0.0001     | linear |
| 60       | 1119       | 480       | 0.7104   | 2.8016   | 0.0005     | linear |

![Results Table](results_table.png)

### Best Performing Model
- **Top Samples**: #51, #56, #59 (tied at 75.21% accuracy)
- **Optimal Parameters**:

  ```python
  # Most frequent configuration
  SVC(C=56.782, gamma=0.0001, kernel='linear', random_state=42)
