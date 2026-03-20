#  Edge Deployment Plan (Part 8)

##  Objective

Deploy the system on mobile or low-resource environments with low latency and small model size.

##  Model Strategy

Use lightweight models:

* TF-IDF + Logistic Regression (instead of XGBoost)

Reason:

* Faster inference
* Smaller size
* Suitable for on-device deployment
 
##  Model Size

* Target: < 50 MB

##  Latency

* Target: < 100 ms per prediction

##  Optimizations

1. Reduce TF-IDF features

   * From 3000 → 1000

2. Model Quantization

   * Reduce memory usage

3. ONNX Conversion

   * Faster inference on mobile

##  Trade-offs

| Factor   | Tradeoff        |
| -------- | --------------- |
| Accuracy | Slight decrease |
| Speed    | Faster          |
| Size     | Smaller         |

##  Decision Engine

* Rule-based logic (lightweight)
* Runs instantly on-device
* No additional compute cost

##  Robustness Handling

### 1. Short Text

* Use fallback → previous_day_mood

### 2. Missing Values

* Median imputation

### 3. Conflicting Signals

* Combine text + metadata with weighted logic

##  Future Improvements

* Use small transformer model (MiniLM)
* Personalization based on user history
* Offline learning capability

## Final Insight

The system is designed to balance accuracy and efficiency, making it suitable for real-world mobile deployment.
