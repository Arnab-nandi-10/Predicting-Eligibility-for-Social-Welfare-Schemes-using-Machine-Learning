# Predicting-Eligibility-for-Social-Welfare-Schemes-using-Machine-Learning


# 🏛️ Predicting Eligibility for NSAP Schemes using IBM AutoAI

## 📌 Project Overview

The **National Social Assistance Programme (NSAP)** is a flagship welfare scheme by the Government of India that provides pensions to:

* Elderly citizens
* Widows
* Persons with disabilities
  all belonging to Below Poverty Line (BPL) households.

Traditionally, verifying applications and assigning the right scheme is **manual, slow, and error-prone**.

👉 Our solution: A **multi-class machine learning model** built using **IBM AutoAI** that predicts the most appropriate NSAP sub-scheme (`IGNOAPS`, `IGNWPS`, `IGNDPS`) for an applicant/district.

---

## 🗂️ Dataset

* **Source**: [AI Kosh – District-wise Pension Data under NSAP](https://aikosh.indiaai.gov.in/web/datasets/details/district_wise_pension_data_under_the_national_social_assistance_programme_nsap_1.html)
* **Records**: \~2,085
* **Columns**: 16 (15 features + 1 target)
* **Target Column**: `schemecode`

  * `IGNOAPS` → Indira Gandhi National Old Age Pension Scheme
  * `IGNWPS` → Indira Gandhi National Widow Pension Scheme
  * `IGNDPS` → Indira Gandhi National Disability Pension Scheme

### Key Features

* `finyear`, `statename`, `districtname`
* `totalbeneficiaries`, `totalmale`, `totalfemale`, `totaltransgender`
* `totalsc`, `totalst`, `totalgen`, `totalobc`
* `totalaadhaar`, `totalmobilenumber`

---

## 🛠️ Technology Stack

* **IBM Cloud Lite Services**
* **Watson Studio AutoAI** → Model training & evaluation
* **Watson Machine Learning (WML)** → Model deployment
* **REST API** → Online predictions

---

## ⚡ Workflow

1. Upload dataset to **Watson Studio**.
2. Launch **AutoAI experiment** (Classification).
3. Select target column: **`schemecode`**.
4. Train & evaluate ML pipelines automatically.
5. Select best-performing model (**Random Forest**).
6. Deploy to **IBM Watson ML Deployment Space**.
7. Test predictions using **JSON input**.

---

## 📊 Results

* **Best Model**: Random Forest Classifier
* **Performance**: High accuracy & F1-score across all scheme classes
* **Deployment**: Model deployed as REST API (Online deployment)

**Sample Input**:

```json
{
  "input_data": [
    {
      "fields": [
        "finyear","lgdstatecode","statename","lgddistrictcode","districtname",
        "totalbeneficiaries","totalmale","totalfemale","totaltransgender",
        "totalsc","totalst","totalgen","totalobc","totalaadhaar","totalmobilenumber"
      ],
      "values": [
        ["2025-2026", 1, "JAMMU AND KASHMIR", 1, "ANANTNAG", 8231, 4960, 3271, 0, 37, 230, 7885, 79, 8165, 7052]
      ]
    }
  ]
}
```

**Sample Output**:

```json
{
  "predictions": [
    {
      "fields": ["prediction", "probability"],
      "values": [["IGNOAPS", [0.87, 0.09, 0.04]]]
    }
  ]
}
```

---

## 🎯 Wow Factor

* **End-to-End Automation** → From data upload to deployed model in minutes.
* **Scalable** → Can be integrated into government portals for real-time eligibility checks.
* **Accurate & Transparent** → Reduces manual bias and errors.

---

## 👥 End Users

* Government agencies & welfare departments
* Beneficiaries (citizens applying for pensions)
* Policy makers & analysts

---

## 🚀 Future Scope

* Extend to **applicant-level data** (age, widowhood, disability %).
* Add **fairness checks** (avoid bias by gender, caste, or region).
* Integrate with **Aadhaar / state portals**.
* Provide **multi-language support**.

---

## 📂 Repository Structure

```
NSAP-Eligibility-Prediction/
│── README.md
│── data/
│   ├── nsapallschemes.csv          # Original dataset (if allowed)
│   ├── nsapallschemes_test.csv     # Cleaned test dataset (without schemecode)
│── examples/
│   ├── sample_request.json         # Example JSON for API test
│   ├── predict.py                  # Python script to call REST API
│── docs/
│   ├── screenshots/                # Leaderboard, deployment, predictions
│   ├── Project_Presentation.pptx   # Final presentation
│   ├── Project_Presentation.pdf    # Exported presentation
```


## 🙏 Acknowledgements

* Government of India – NSAP programme
* AI Kosh for dataset
* IBM Cloud & Watson Studio Lite

---

