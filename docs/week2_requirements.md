Name: Faqihah Humaira’ Binti Muhammad Firhat

Matric No.: A24AI0028

## Step A0

| Framing Element | What I Must Confirm |
|---|---|
| **Problem Evidence** | 1. Traditional flood damage assessments are costly, labour-intensive and challenging to conduct.<br>2. Damaged roads and hazardous conditions may prevent local authorities and inspection teams form reaching affected infrastructure.<br><br>**Sources:**<br>1. Mabina, L. M., Mashao, F. M., Mathivha, F. I., Singo, M. V., & Chikoore, H. (2026). Deep learning and geospatial approaches for post-flood disaster damage assessment: A systematic review. Applied Geomatics, 18(2), 95. [https://doi.org/10.1007/s12518-026-00745-8](https://doi.org/10.1007/s12518-026-00745-8)<br>2. Wagenaar, D., Curran, A., Balbi, M., Bhardwaj, A., Soden, R., Hartato, E., Mestav Sarica, G., Ruangpan, L., Molinario, G., & Lallemant, D. (2020). Invited perspectives: How machine learning will change flood risk and impact assessment. Natural Hazards and Earth System Sciences, 20(4), 1149–1161. [https://doi.org/10.5194/nhess-20-1149-2020](https://doi.org/10.5194/nhess-20-1149-2020) |
| **Existing Approaches** | 1. Flood mapping using Sentinel-1 SAR imagery with deep learning models such as U-Net, DeepLabV3 and Mask RCNN.<br>Toma, A., Șandric, I., & Mihai, B.-A. (2024). Flooded area detection and mapping from Sentinel-1 imagery. Complementary approaches and comparative performance evaluation. *European Journal of Remote Sensing*, *57*(1), 2414004. [https://doi.org/10.1080/22797254.2024.2414004](https://doi.org/10.1080/22797254.2024.2414004)<br><br>2. Geospatial data processing and model error analysis using Apache Sedona and SpaceNet8 to improve accuracy and efficiency of flood-related detection<br>Bai, Y., Yang, Z., Yu, J., Ju, R.-Y., Bin, Y., Mas, E., & Koshimura, S. (2024). *Flood data analysis on SpaceNet 8 using apache sedona* (2404.18235V1). arXiv. [https://arxiv.org/abs/2404.18235v1](https://arxiv.org/abs/2404.18235v1)<br><br>3. Interactive flood-impact map that uses real-time streamgage measurements to display potentially flooded roads, buildings and other critical locations<br>*Real-time flood impact map*. (2025). USGS. [https://www.usgs.gov/tools/real-time-flood-impact-map](https://www.usgs.gov/tools/real-time-flood-impact-map) |
| **Project / Engineering Gap** | Decision-support gap: Translating affected infrastructure and flooding using satellite imagery into actionable information for prioritizing field inspections remain challenging. |
| **Objective O1** | To develop a GeoAI-based system that integrates deep learning and geospatial analysis to support preliminary infrastructure assessment and prioritize field inspections. |
| **Objective O2** | To identify potentially flood-affected roads and buildings using satellite imagery and deep learning techniques. |
| **Objective O3** | To develop an interactive geospatial dashboard that visualizes potentially flood-affected infrastructure, preliminary inspection priorities and Explainable AI (XAI) outputs to support transparent and informed disaster management decision making. |
| **Intended Users** | **Local authorities:** View potentially flood-affected roads and buildings, examine infrastructure exposure and identify locations that may require priority field inspections.<br>**Communities:** View accessible information about potentially flood-affected infrastructure within selected areas |
| **Supported Tasks** | Identify and visualize potentially flood-affected roads and buildings using satellite imagery, assess their preliminary flood exposure and support local authorities in prioritizing infrastructure field inspections (XAI-based visual explanations). |
| **Information / Knowledge Domain** | Geospatial Information: Flood mapping, satellite imagery analysis, road networks, building footprints and infrastructure exposure assessment |
| **Operating Context** | Post-flood preliminary assessment: Used by the local authorities during post-flood assessment. Through the dashboard, authorities will be able to visualize affected infrastructure, examine preliminary inspection priorities and interpret AI predictions using XAI-based visual explanations. |
| **Important Constraints** | **Satellite imagery quality:** Cloud cover, image resolution and acquisition timing.<br>**Prediction accuracy:** AI models may incorrectly identify infrastructure as flood-affected or unaffected.<br>**Dataset generalizability:** SpaceNet8 contains imagery outside Malaysia. This may limit the model performance in different environments |
| **Explicit Out-of-Scope Tasks** | The dashboard will not determine the actual structural condition or severity of the damage.<br>The system will not automatically authorize evacuations or emergency response.<br>The system will not predict future flooding or continuously monitor live flood conditions. |
| **Evaluation Focus** | **Deep learning models:** Precision, Recall, F1-score and Intersection over Union<br>**Infrastructure assessment performance:** The ability to identify potentially flood-affected roads and buildings correctly using ground-truth annotations.<br>**Inspection prioritization:** Proposed prioritization method produces reasonable and consistent inspection priorities using defined criteria or available reference information. |

## Step A1

### Functional Requirements

| ID | Requirement |
|---|---|
| FR1 | The system shall identify potentially flood-affected roads and buildings from uploaded satellite imagery. |
| FR2 | The system shall display preliminary inspection priorities for identified infrastructure based on defined assessment criteria |
| FR3 | The system shall provide visual explanations of AI -generated predictions to help users interpret why infrastructure was classify as potentially flood-affected. |
| FR4 | The system shall not present AI-generated infrastructure assessments as verified structural damage findigns |
| FR5 | The system shall not continuously monitor live flood conditions or generate real-time flood forecasts |

## Step A2

### Non-Functional Requirements

| ID | Quality Attribute | Requirement | Measurement Method | Metric |
|---|---|---|---|---|
| NFR1 | Correctness | The system shall identify potentially flood-affected infrastructure | Evaluate on a held-out SpaceNet8 test set | Object-level<br>F1-score |
| NFR2 | Performance | The dashboard shall display an existing infrastructure assessment within an acceptable latency target | Measure loading time over 20 repeated tests on the target environment | P90 latency |
| NFR3 | Reliability | The system shall display unavailable status when infrastructure assessment results cannot be retrieved without crashing | Simulate 20 scenarios involving unavailable infrastructure assessment results | Error-handling rate |
| NFR4 | Explainability | The dashboard shall provide explanations that users can interpret correctly | Task-based testing with representative users. | Interpretation rate |

## Step A3

### Responsible AI Requirements

| # | Responsible AI Risk | Requirements | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| RAI1 | Accuracy and Reliability | System shall identify potentially flood-affected roads and buildings with sufficient accuracy to support preliminary infrastructure assessment | Evaluate predictions against ground-truth annotations from a held-out dataset’s test set. | Precision, Recall, F1-score | F1-score >= 0.80<br>Recall >= 0.80<br>Both for each flood-affected infrastructure class |
| RAI2 | Data Bias and Fairness | The system shall evaluate and report differences in prediction performance across geographical regions represented in the evaluation dataset | Evaluate the model separately on geographical distinct test subsets using identical evaluation criteria | Regional F1-score and maximum absolute difference between regional F1-scores | All evaluated regions and flag F1-score differences > 0.10 |
| RAI3 | Privacy and Safety | The system shall restrict access to infrastructure-level geospatial information designated as sensitive | Inspect 20 predefined dashboard assessment scenarios and verify that predictions are appropriately labeled. | Percentage of assessment displays correctly labeled. | 100% of tested assessment displays correctly labeled |
