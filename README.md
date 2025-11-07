# ✈️ British Airways — Flight Booking Conversion Prediction

Predict whether a website visitor will complete a flight booking or abandon the checkout.

---

## Business Context — Why This Matters
On airline websites, many users search for flights but **don’t finish booking**.  
Predicting conversion **before** the user completes payment allows the airline to:

✅ Offer real-time discounts  
✅ Reduce drop-off  
✅ Improve customer experience  
✅ Increase revenue

---

##  How the System Predicts Booking Completion

When a visitor interacts with the airline website, their browsing behavior is tracked:

| Behavior Tracked | Meaning |
|-----------------|---------|
| purchase_lead | Days before flight search → urgency |
| flight_duration | Total hours of the flight |
| flight_hour | Time of flight |
| user location & route | Travel feasibility |
| sales_channel | Online / Offline device type |
| extra baggage / meals | Indicates committed travelers |

The model learns patterns from **past users**:

📌 Example insights:
- Checking flights closer to travel date → **higher chance of booking**
- Round-trip travelers → **more likely to convert**
- Users selecting **extra baggage / preferred seats** → **more serious planners**

So the system predicts:
> “Will this user book — Yes or No?”  
*even before they press the Buy button.*

---

## ✅ Project Workflow

### 1️⃣ Data Collection
Dataset from **British Airways — Forage Virtual Experience**  
Realistic airline booking behavior records

---

### 2️⃣ Data Cleaning & Encoding
✔ Remove duplicates  
✔ Handle missing values  
✔ Convert text features → numerical  
Techniques used:  
- One-Hot Encoding  
- Label Encoding / Mapping  

Examples:
- `sales_channel` → Online = 0, Offline = 1  
- `route` and `trip_type` → One-Hot encoding

---

### 3️⃣ Exploratory Data Analysis (EDA)

Discovered important patterns:

| Observation | Insight |
|------------|---------|
| Short purchase lead (5–10 days) | Last-minute & more confirmed bookings |
| RoundTrip > OneWay conversions | Committed travelers |
| Wants baggage / meals | Higher booking intent |

Methods:
📊 Bar charts • Histograms • Heatmaps • Correlation plots

---

### 4️⃣ Feature Engineering
Created new useful features:

| Feature | Why? |
|---------|------|
| booking_urgency = 1 / purchase_lead | Higher urgency → more likely booking |
| Weekend flight flag | Weekend travelers tend to confirm faster |

---

### 5️⃣ Handling Class Imbalance (SMOTE)
Real case: **only ~5–10% users book**  
📉 Model becomes biased → Predicts “No” always

✔ Used **SMOTE (Synthetic Minority Oversampling Technique)**  
✔ Balances Yes/No booking equally  
✔ Model learns minority class better

---

### 6️⃣ Model Building — Random Forest Classifier

Why Random Forest?

✅ Handles nonlinear airline behavior  
✅ Robust against noise  
✅ High performance and interpretability

Model task:
> Predict: **Will this customer complete the booking?**

---

### 7️⃣ Model Evaluation

Metrics used:
- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**

Shows **strong predictive power** for real airline deployment.

---

### 8️⃣ Feature Importance — What Matters Most?

| Feature | Importance | Interpretation |
|--------|------------|----------------|
| purchase_lead | 24% | Earlier search → less commitment |
| wants_extra_baggage | 20% | Serious travelers |
| length_of_stay | 15% | Longer trips → more certainty |
| route & sales_channel | Lower influence | Can be dropped for efficiency |

✅ Helps optimize product strategy

---

## 🗂️ Dataset Description

| Column Name | Description |
|------------|-------------|
| num_passengers | Number of travelers |
| sales_channel | Online / Offline |
| trip_type | OneWay / RoundTrip |
| purchase_lead | Days before flight |
| flight_hour | Time of flight |
| route | Flight origin-destination |
| flight_duration | Total hours |
| wants_extra_baggage | Preference flag |
| wants_preferred_seat | Preference flag |
| wants_in_flight_meals | Preference flag |
| booking_complete | ✅ Target variable (1/0) |

---

## 🛠 Tech Stack
Python | Pandas | NumPy | Matplotlib | Seaborn  
**Scikit-learn | SMOTE (imbalanced-learn)**

---

## ▶️ How to Run

Install dependencies:
```bash
pip install pandas numpy scikit-learn imbalanced-learn seaborn matplotlib joblib
