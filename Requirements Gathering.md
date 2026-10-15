
# Requirements Gathering
## CheXpert Chest X-Ray Classification and Reporting System

### 1. Project Overview

The project aims to develop an AI-based system that analyzes frontal chest X-ray images, predicts the presence of five selected medical findings, generates a structured report, and provides a chatbot interface for explaining the system's outputs.

The system is an educational prototype and is not intended to replace professional medical diagnosis or clinical judgment.

### 2. Project Objectives

- Develop a deep learning model for multi-label chest X-ray classification.
- Identify five target findings: Atelectasis, Cardiomegaly, Consolidation, Edema, and Pleural Effusion.
- Generate structured reports based on model predictions.
- Provide Grad-CAM visualizations to help users inspect image regions associated with predictions.
- Implement a case-grounded chatbot that answers questions using available case information.
- Build a graphical user interface for image submission and result presentation.
- Evaluate model performance and document the system's limitations.

### 3. Stakeholders

| Stakeholder | Interest or Responsibility |
|---|---|
| Project team | Develop, integrate, test, and document the system. |
| Project supervisor | Provide academic guidance and review project progress. |
| Intended users | Upload X-rays and view predictions, explanations, and reports. |
| Medical professionals | Potential domain experts for future evaluation; not assumed to be involved unless arranged. |

### 4. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall accept a supported frontal chest X-ray image as input. | High |
| FR-02 | The system shall validate the uploaded image format and basic input requirements. | High |
| FR-03 | The system shall preprocess the image according to the trained model's input requirements. | High |
| FR-04 | The system shall predict the five selected findings using a trained multi-label classification model. | High |
| FR-05 | The system shall display the prediction for each finding and its associated score or confidence information. | High |
| FR-06 | The system shall generate a structured report based on the available classification outputs. | High |
| FR-07 | The system shall generate Grad-CAM visualizations for supported predictions. | Medium |
| FR-08 | The system shall allow users to ask questions about the current case through a chatbot interface. | Medium |
| FR-09 | The chatbot shall use available structured case information and provide a fallback when a question cannot be answered from that information. | High |
| FR-10 | The system shall display appropriate validation errors or processing-failure messages. | High |

### 5. Non-Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| NFR-01 | The interface should be clear and easy to navigate. | High |
| NFR-02 | The system should provide results within a practical response time on the selected hardware. | Medium |
| NFR-03 | Predictions, reports, and chatbot responses should remain consistent with the available case data. | High |
| NFR-04 | The system should handle invalid inputs and processing failures without crashing. | High |
| NFR-05 | The codebase should be modular, readable, and maintained using Git and GitHub. | High |
| NFR-06 | The system should avoid unsupported medical claims and clearly communicate its limitations. | High |
| NFR-07 | Patient data should be handled responsibly, and identifiable information should not be exposed unnecessarily. | High |

### 6. Dataset Requirements

The project will use the CheXpert dataset.

- **Input:** Frontal chest X-ray images.
- **Target findings:** Atelectasis, Cardiomegaly, Consolidation, Edema, and Pleural Effusion.
- **Task type:** Multi-label image classification.
- **Preprocessing:** Image loading, validation, resizing, normalization, and label preparation.
- **Uncertain labels:** The team shall select and document a strategy for handling uncertain labels.
- **Data splitting:** Patient-level separation should be used where the available metadata permits it, to reduce the risk of patient overlap between training, validation, and test sets.
- **Data leakage:** Preprocessing and model-selection decisions shall avoid using information from the test set.

The dataset version, access method, image dimensions, label distribution, and selected uncertainty strategy must be documented during implementation.

### 7. Machine Learning Requirements

- Use DenseNet121 as the planned classification backbone.
- Configure the output layer for the five target findings.
- Use an appropriate multi-label training objective.
- Select decision thresholds using validation data rather than the test set.
- Evaluate each finding separately using suitable metrics, including precision, recall, F1-score, and ROC-AUC where appropriate.
- Address class imbalance and uncertain labels during training and evaluation.
- Record model configuration, data splits, experiments, and evaluation results.
- Avoid reporting unmeasured performance values.

### 8. Reporting and Explainability Requirements

**Structured report**
- Present the five predicted findings.
- Use predefined report templates.
- Ensure report statements reflect the available model outputs.
- Avoid presenting model predictions as confirmed clinical diagnoses.

**Grad-CAM**
- Generate visualizations for supported model predictions.
- Display the heatmap alongside the relevant X-ray and prediction.
- Explain that heatmaps are visual aids and do not prove diagnostic correctness.

### 9. Chatbot Requirements

- Answer questions about the current case using the structured findings and report.
- Avoid inventing findings that are absent from the available case information.
- Provide a clear fallback response when evidence is insufficient.
- Avoid presenting the chatbot as an independent diagnostic system.
- Keep responses consistent with the predictions and report shown in the interface.

### 10. System Architecture and Tools

| Component | Planned Technology |
|---|---|
| Programming language | Python |
| Dataset | CheXpert |
| Classification model | DenseNet121 |
| Deep learning framework | To be confirmed by the team |
| Explainability | Grad-CAM |
| Backend API | FastAPI |
| User interface | Single-page graphical interface |
| Version control | Git and GitHub |
| Experiment tracking | MLflow, if adopted by the team |

### 11. Project Constraints

- The project follows a limited academic development timeline.
- The system focuses on five selected chest X-ray findings.
- The dataset may contain uncertain labels and class imbalance.
- The availability of computational resources may limit training speed and model experimentation.
- The prototype is not a clinically validated medical device.
- Access to qualified medical reviewers for external validation is not guaranteed.

### 12. Acceptance Criteria

The project will be considered functionally complete when:

- The application accepts and validates a supported frontal chest X-ray.
- The trained model produces outputs for all five target findings.
- The interface displays the predictions and associated score information.
- A structured report is generated from the model outputs.
- Grad-CAM visualizations are available for supported predictions.
- The chatbot can answer supported case-related questions and fall back when evidence is insufficient.
- Invalid inputs and processing errors are handled appropriately.
- The team documents the evaluation methodology, results, limitations, and known failure cases.

Meeting these functional criteria does not establish clinical accuracy or safety. Those require separate, appropriate evaluation.

### 13. Open Questions

The following decisions must be finalized before or during implementation:

- Which CheXpert subset and dataset version will be used?
- How will uncertain labels be handled for each target finding?
- Which deep learning framework will be used?
- What image dimensions and normalization procedure will be applied?
- Which thresholds and evaluation metrics will be selected?
- Which image formats will the application support?
- How will chatbot responses be technically restricted to the current case?
- What hardware and deployment environment will be available?
- Will medical experts be available to review reports and explanations?

### 14. Scope Limitations

The first version will focus on the five specified findings and frontal chest X-rays. It will not claim to detect every possible chest disease, replace radiologists, provide treatment recommendations, or establish a definitive diagnosis.

Additional findings, external clinical validation, and production deployment are outside the initial scope unless the project team explicitly expands the requirements.
