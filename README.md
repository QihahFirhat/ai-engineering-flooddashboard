# Flood-Affected Infrastructure Dashboard

> A GeoAI-based dashboard that uses deep learning and geospatial analysis to identify potentially flood-affected roads and buildings from satellite imagery, helping local authorities prioritize field inspections and support disaster management decisions.

## Problem Statement

Traditional disaster assessments often require manual field inspections, which can be slow, labour-intensive, and difficult to conduct during and after floods. Damaged roads and hazardous conditions may prevent inspection teams from reaching affected infrastructure, causing delays in assessment. AI engineering enables the use of deep learning and geospatial analysis to identify potentially flood-affected roads and buildings from satellite imagery and support preliminary infrastructure assessments.

## Evidence of the Problem

- Traditional flood damage assessments are costly, labour-intensive, and challenging to conduct, especially when damaged roads and hazardous conditions restrict access to affected areas (Mabina et al., 2026).
- Machine learning and geospatial technologies offer opportunities to improve flood risk and impact assessment, addressing limitations of conventional approaches (Wagenaar et al., 2020).

## Initial Related Work / Existing Approaches

- **Deep Learning for Flood Detection:** Uses deep learning techniques such as U-Net to identify flooded areas, roads, and buildings from satellite imagery. However, accurate infrastructure identification remains challenging.
- **Automated Flood Monitoring (Europe):** Generates flood maps to support emergency response. However, flood extent maps do not necessarily provide detailed road- and building-level impact assessments.
- **AI-Based Infrastructure Impact Assessment (Australia):** Identifies flood exposure affecting roads, buildings, railway stations, and communities. However, translating flood exposure information into reliable infrastructure-level assessments remains challenging.
- **Drone-Based Disaster Management (US):** Uses drone imagery to assess building damage after disasters. However, drone-based assessments can be constrained by flight conditions and area coverage.
- **Satellite-Based Flood Mapping:** Uses satellite imagery, including radar-based approaches that can operate under cloudy conditions or at night. However, accurately identifying affected infrastructure remains challenging.

**Engineering Gap:** Although existing systems can detect flooded areas and estimate infrastructure exposure, accurately identifying potentially affected roads and buildings remains challenging.

*Note: Specific study citations for the five existing approaches have not yet been identified in the proposal. Supporting references should be added during the literature review.*

## Project Objectives

- **O1:** To develop a GeoAI-based system that integrates deep learning and geospatial analysis to support preliminary infrastructure assessment and prioritize field inspections.
- **O2:** To identify potentially flood-affected roads and buildings using satellite imagery and deep learning techniques.
- **O3:** To visualize flood-affected infrastructure through an interactive map to support disaster management and decision-making.

## Target Users

- **Local Authorities:** To support preliminary infrastructure assessment, prioritize field inspections, and assist disaster management decisions.
- **Communities:** To access information about potentially flood-affected infrastructure.

## Data Sources

- **SpaceNet8 Dataset:** Satellite imagery and geospatial labels for flooded areas, roads, and buildings.
  - https://www.kaggle.com/code/virajkadam/spacenet8-data-download-and-eda

## Responsible AI Risks

- **Accuracy and Reliability:** The AI may incorrectly classify roads or buildings as flood-affected or unaffected due to environmental conditions, satellite imagery limitations, or prediction errors.
- **Data Bias and Fairness:** The training dataset may not represent all geographical environments, potentially affecting model accuracy across different locations.
- **Privacy and Safety:** High-resolution satellite imagery and building-level geospatial information could expose sensitive locations or infrastructure details.

## Weekly Progress

| Week | Focus | Deliverable | Status |
|------|-------|-------------|--------|
| W1 | System map + project scope | README + docs | ✅ |

## References

1. Mabina, L. M., Mashao, F. M., Mathivha, F. I., Singo, M. V., & Chikoore, H. (2026). Deep learning and geospatial approaches for post-flood disaster damage assessment: A systematic review. *Applied Geomatics, 18*(2), 95.
   https://doi.org/10.1007/s12518-026-00745-8

2. Wagenaar, D., Curran, A., Balbi, M., Bhardwaj, A., Soden, R., Hartato, E., Mestav Sarica, G., Ruangpan, L., Molinario, G., & Lallemant, D. (2020). Invited perspectives: How machine learning will change flood risk and impact assessment. *Natural Hazards and Earth System Sciences, 20*(4), 1149–1161.
   https://doi.org/10.5194/nhess-20-1149-2020