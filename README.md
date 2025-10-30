## 🧬 Sample Input–Output Pairs (Health Checkup Dataset Example)

This repository contains `sample_data(1000)`, a **sample dataset constructed for research on large language model (LLM)-based interpretation of health checkup results**. <br>
The data were **derived from the National Health Insurance Service (NHIS) health checkup database (Korea)** and **sampled, anonymized, and structured** for demonstration and research reproducibility purposes.

---

### 📁 Dataset Composition

| File                          | Description                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------- |
| `sample_data(1000).csv`       | Input health checkup data (demographics + test results)                                 |
| `sample_data(1000)_answer_label.csv` | Categorical interpretation labels for each analyte (e.g., normal, borderline, abnormal) |


> ⚠️ This dataset was **sampled and de-identified from the original NHIS health checkup data** to serve as a **research-ready example**. <br>
> All personally identifiable information has been removed. <br>
> The **original public dataset** can be accessed at the official Korean government data portal: <br>
> 🔗 [National Health Insurance Service – Health Checkup Data (data.go.kr)](https://www.data.go.kr/data/15007122/fileData.do)

---

### 📊 Dataset Description

Each record represents the results of a single health checkup and consists of **input (features)** and **output (labels)** used for model training and evaluation.

#### 🧩 Input (`sample_data(1000).csv`)

* **Demographic information:** `sex`, `Age code (5-year old unit)`
* **Anthropometric measurements:** `Height (5 cm unit)`, `Weight (5 kg unit)`
* **Clinical test results:**

  * **Blood pressure:** `SBP`, `DBP`
  * **Blood glucose:** `FBG`
  * **Lipid profile:** `TC`, `TG`, `HDLC`, `LDLC`
  * **Liver function:** `AST`, `ALT`, `γ-GTP`
  * **Renal function:** `SC`, `UP`
  * **Hematology:** `Hb`

> ⚙️ **Age code explanation:**
> The “Age code” represents 5-year age intervals (e.g., 5 = 20–24 years, 6 = 25–29 years, 7 = 30–34 years, etc.).

#### 🧾 Output (`sample_data(1000)_answer_label.csv`)

For each analyte, a categorical label indicates the interpretation result. <br>
For example, `FBG` in `sample_data(1000)_answer_label.csv` corresponds to the fasting blood glucose interpretation: <br>
0 = normal, 1 = Diabetes, 2 = Impaired Fasting Glucose.

<details> <summary>📋 <b>Click to expand 'Label Interpretation Criteria'</b></summary>


| **Health Checkup Item**                          | **Label: Interpretation**         | **Criteria for Interpretation** |
| ------------------------------------------------ | --------------------------------- | ------------------------------- |
| **Blood Pressure (mmHg)**                        | 0: Normal                         | SBP <120 and DBP <80            |
|                                                  | 1: Elevated                       | SBP 120–129 and DBP <80         |
|                                                  | 2: Pre-hypertension               | SBP 130–139 or DBP 80–89        |
|                                                  | 3: Stage 1 Hypertension           | SBP 140–159 or DBP 90–99        |
|                                                  | 4: Stage 2 Hypertension           | SBP ≥160 or DBP ≥100            |
|                                                  | 5: Isolated Systolic Hypertension | SBP ≥140 and DBP <90            |
| **Fasting Blood Glucose (mg/dL)**                | 0: Normal                         | 70–99                           |
|                                                  | 1: Diabetes                       | ≥126                            |
|                                                  | 2: Impaired Fasting Glucose       | 100–125                         |
| **Total Cholesterol (mg/dL)**                    | 0: Normal                         | <200                            |
|                                                  | 1: Borderline                     | 200–239                         |
|                                                  | 2: High                           | ≥240                            |
| **Triglycerides (mg/dL)**                        | 0: Normal                         | <150                            |
|                                                  | 1: Borderline                     | 150–199                         |
|                                                  | 2: High                           | 200–499                         |
| **High-Density Lipoprotein Cholesterol (mg/dL)** | 0: Normal                         | 40–60                           |
|                                                  | 1: Low                            | <40                             |
|                                                  | 2: High                           | ≥60                             |
| **Low-Density Lipoprotein Cholesterol (mg/dL)**  | 0: Normal                         | <100                            |
|                                                  | 1: Abnormal                       | 100–129                         |
|                                                  | 2: Borderline                     | 130–159                         |
|                                                  | 3: High                           | 160–189                         |
|                                                  | 4: Very High                      | ≥190                            |
| **Hemoglobin (g/dL)**                            | 0: Normal (Male)                  | 14.0–17.5                       |
|                                                  | 1: Abnormal (Male)                | otherwise                       |
|                                                  | 0: Normal (Female)                | 12.3–15.3                       |
|                                                  | 1: Abnormal (Female)              | otherwise                       |
| **Urine Protein (dipstick)**                     | 0: Normal                         | 1                               |
|                                                  | 1: Abnormal                       | ≥2                              |
| **Serum Creatinine (mg/dL)**                     | 0: Normal                         | <1.5                            |
|                                                  | 1: Abnormal                       | ≥1.5                            |
| **Aspartate Aminotransferase (AST, U/L)**        | 0: Normal                         | ≤40                             |
|                                                  | 1: High                           | >40                             |
| **Alanine Aminotransferase (ALT, U/L)**          | 0: Normal                         | ≤40                             |
|                                                  | 1: High                           | >40                             |
| **γ-Glutamyl Transferase (γ-GTP, U/L)**          | 0: Normal (Male)                  | 11–63                           |
|                                                  | 1: Abnormal (Male)                | otherwise                       |
|                                                  | 0: Normal (Female)                | 8–35                            |
|                                                  | 1: Abnormal (Female)              | otherwise                       |

> **Reference sources:**
Criteria for interpretation were derived from publicly available clinical guidelines published by the
[Korea Disease Control and Prevention Agency (KDCA)](https://health.kdca.go.kr/healthinfo/biz/health/gnrlzHealthInfo/gnrlzHealthInfo/gnrlzHealthInfoMain.do?lclasSn=7)
 and [Mayo Clinic](https://www.mayocliniclabs.com/test-catalog/critical-values-and-results)
 reference ranges.
</details>

----

### 📘 Example

#### Input (`sample_data(1000).csv`)

| ID     | sex | Age code | Height | Weight | SBP | DBP | FBG | TC  | TG  | HDLC | LDLC | Hb | UP | SC | AST | ALT | γ-GTP |
| ------ | --- | -------- | ------ | ------ | --- | --- | --- | --- | --- | ---- | ---- | -- | -- | -- | --- | --- | ----- |
| SP00001 | 1   | 9        | 185    | 100    | 140 | 90  | 100 | 186 | 102 | 65   | 100  | 17 | 1  | 1  | 23  | 25  | 18    |

#### Output (`sample_data(1000)_answer_label.csv`)

| ID     | sex | Age code | BMI  | BP | FBG | TC | TG | HDLC | LDLC | Hb | UP | SC | AST | ALT | γ-GTP |
| ------ | --- | -------- | ---- | -- | --- | -- | -- | ---- | ---- | -- | -- | -- | --- | --- | ----- |
| SP00001 | 1   | 9        | 29.2 | 3  | 2   | 0  | 0  | 2    | 1    | 0  | 0  | 0  | 0   | 0   | 0     |

> **Abbreviations:** <br>
> BMI = Body Mass Index; BP = Blood Pressure; FBG = Fasting Blood Glucose; <br>
> TC = Total Cholesterol; TG = Triglycerides; HDLC = High-Density Lipoprotein Cholesterol; <br>
> LDLC = Low-Density Lipoprotein Cholesterol; Hb = Hemoglobin; <br>
> UP = Urine Protein; SC = Serum Creatinine; AST = Aspartate Aminotransferase; <br>
> ALT = Alanine Aminotransferase; γ-GTP = Gamma-Glutamyl Transferase <br>

---

### 🧠 Research Purpose

This dataset is intended to support research on **LLM-based automatic classification of health checkup results** and **prediction of retest necessity**. <br>
It may also be used for **instruction-tuning or fine-tuning** demonstrations.


---

### ⚠️ Notes

* The dataset was **sampled and anonymized** from the **NHIS health checkup data** to illustrate data structure and model training format.
* The **original NHIS data** are publicly available at [data.go.kr](https://www.data.go.kr/data/15007122/fileData.do).

---

### 📄 Citation

> To be added later

