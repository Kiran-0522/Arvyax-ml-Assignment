# 🌿 ArvyaX ML Assignment – From Understanding to Guidance

##  Overview

This project builds an intelligent system that understands user emotional state and provides meaningful guidance. The system is designed to handle noisy, short, and imperfect real-world inputs.

---

##  Approach

### Emotional State Prediction (Part 1)

* Treated as a **classification problem**
* Model used: **XGBoost Classifier**

### Intensity Prediction (Part 2)

* Treated as a **regression problem**
* Model used: **XGBoost Regressor**

---

##  Decision Engine (Part 3)

The system uses a rule-based approach combining:

* predicted_state
* predicted_intensity
* stress_level
* energy_level
* time_of_day

### Example Logic:

* High stress → box_breathing (now)
* Low energy → rest (now)
* Calm + high energy → deep_work (now)
* Night time → light_planning (tonight)

This ensures the system provides **actionable and context-aware guidance**.

---

##  Uncertainty Modeling (Part 4)

* **Confidence Score** = maximum predicted probability
* **Uncertain Flag** = 1 if confidence < 0.6 else 0

This helps the system avoid making overconfident incorrect decisions.

---

##  Feature Understanding (Part 5)

### Key Insights:

* **Text Features (TF-IDF)**:

  * Capture emotional tone and language patterns
  * Important for detecting subtle emotions

* **Metadata Features**:

  * stress_level → strongest signal for negative emotions
  * energy_level → key driver for decision making
  * sleep_hours → indirectly affects mood

### Conclusion:

Text provides emotional understanding, while metadata provides **contextual grounding**, making both essential.

---

##  Ablation Study (Part 6)

Two models were compared:

### Model 1: Text Only

* Uses only journal_text
* Performance limited due to lack of context

### Model 2: Text + Metadata

* Uses both text and contextual features
* Better performance and more stable predictions

### Result:

Text + metadata model performs better as real-world emotions depend on both language and context.

---

##  Robustness (Part 9)

The system is designed to handle real-world challenges:

### 1. Short Text Handling

* For inputs like “ok”, “fine”
* Fallback to previous_day_mood or metadata

### 2. Missing Values

* Numerical → filled with median
* Categorical → filled with “unknown”

### 3. Conflicting Signals

* Example: calm text but high stress
* System uses combined logic instead of relying on one feature

---

##  How to Run

```bash
pip install pandas numpy scikit-learn xgboost openpyxl scipy
python train.py
python predict.py
```

---

##  Output

The system generates:

predictions.csv

Columns:

* id
* predicted_state
* predicted_intensity
* confidence
* uncertain_flag
* what_to_do
* when_to_do

---

##  Final Insight

This is not just a prediction system, but a **decision-making system** designed to work under real-world uncertainty.
