
# CheXpert Chest X-ray AI

An AI-assisted chest X-ray analysis system developed as a team-based Machine Learning project under the Digital Egypt Pioneers Initiative (DEPI).

## Project Information

- Program: Digital Egypt Pioneers Initiative (DEPI)
- Project Lead: Menna Alashqar
- Project Supervisor: Antonios Malak
- Project Type: Team-based Machine Learning Project
- Project Duration: 6 weeks
- Project Status: In Development

## Project Overview

The CheXpert Chest X-ray AI project aims to develop an AI-assisted system that analyzes frontal chest X-ray images and predicts five selected findings:

1. Atelectasis
2. Cardiomegaly
3. Consolidation
4. Edema
5. Pleural Effusion

The system will combine deep learning-based multi-label classification with explainability, structured report generation, a case-grounded chatbot, a backend API, and a graphical user interface (GUI).

The project emphasizes reliable evaluation, traceability of generated information, and safety-oriented output handling. Reports and chatbot responses will be grounded in the same structured findings data to reduce unsupported medical statements.

## Objectives

- Develop a reliable preprocessing pipeline for frontal chest X-ray images.
- Train and evaluate a DenseNet121-based multi-label classification model.
- Select classification thresholds using validation data.
- Generate structured reports from model predictions.
- Implement Grad-CAM visualizations to support interpretation of model outputs.
- Develop a chatbot grounded in the current case's structured findings.
- Implement fallback behavior for unsupported medical questions.
- Integrate the components through a FastAPI backend and a single-page GUI.
- Evaluate the complete pipeline and document its methodology, results, and limitations.

## Scope

### In Scope

- Frontal chest X-ray images from the selected CheXpert dataset or an agreed fixed subset.
- Image preprocessing and data-integrity checks.
- Five-label classification using DenseNet121.
- Validation-based threshold selection.
- Structured findings output using a shared JSON schema.
- Template-based report generation.
- Grad-CAM visualizations, subject to successful implementation.
- Case-grounded chatbot responses and fallback handling.
- FastAPI endpoints and GUI integration.
- Model, chatbot, and end-to-end evaluation.
- Technical documentation and a final project paper.

### Out of Scope

- Replacing professional radiologists or clinical judgment.
- Providing definitive diagnoses or prescribing treatment.
- Making unsupported claims beyond the model's findings.
- Claiming clinical validation without appropriate evidence.

## Technical Approach

### 1. Data Preprocessing

Load the selected frontal chest X-ray images and their corresponding labels. Apply the agreed preprocessing pipeline and perform data-integrity checks to identify missing files, invalid records, and potential data leakage.

### 2. Multi-Label Classification

Use DenseNet121 as the backbone for predicting the five selected findings. The model will be trained and evaluated using an agreed multi-label learning approach, with class weighting considered to address class imbalance.

### 3. Threshold Selection and Evaluation

Select classification thresholds using validation data. Evaluate model performance using appropriate per-label metrics, including precision, recall, F1-score, and ROC-AUC where applicable.

### 4. Explainability

Use Grad-CAM to generate visualizations that highlight image regions influencing selected model outputs. These visualizations will support interpretation but will not be treated as proof of a medical finding.

### 5. Structured Report Generation

Convert model outputs into a structured findings representation. Generate template-based reports from the same findings data to maintain consistency and traceability.

### 6. Grounded Chatbot

Develop a chatbot that answers questions using the current case's structured findings and approved contextual information. Unsupported questions will trigger a safe fallback response rather than an invented medical claim.

### 7. Backend and GUI Integration

Use FastAPI to expose the necessary endpoints for image processing, prediction, report generation, explainability, and chatbot interaction. Integrate these components into a single-page graphical user interface.

## System Workflow

1. Input a frontal chest X-ray image.
2. Validate and preprocess the image.
3. Run the DenseNet121 classification model.
4. Apply validation-selected classification thresholds.
5. Produce structured findings in a shared JSON format.
6. Generate a template-based report and, where supported, Grad-CAM visualizations.
7. Provide case-grounded chatbot responses.
8. Display the outputs through the GUI using the backend API.

## Technology Stack

- **Programming Language:** Python
- **Deep Learning:** DenseNet121
- **Dataset:** CheXpert
- **Image Processing:** Libraries selected by the implementation team
- **Explainability:** Grad-CAM
- **Backend:** FastAPI
- **Interface:** Single-page GUI
- **Version Control:** Git and GitHub
- **Documentation:** Markdown, evaluation tables, and a technical paper

Specific library versions and deployment infrastructure will be documented once finalized.

## Project Timeline

The project follows a six-week development plan.

| Phase | Main Focus | Expected Output |
|---|---|---|
| Week 1 | Data loading, preprocessing, and integrity checks | Validated data pipeline |
| Week 2 | Model development and training preparation | Training pipeline and baseline |
| Week 3 | Model training and validation | Model checkpoints and evaluation |
| Week 4 | Threshold selection, explainability, and findings schema | Validated thresholds and structured outputs |
| Week 5 | Report generation, chatbot, and backend integration | Core application components |
| Week 6 | GUI integration, testing, documentation, and presentation | Integrated prototype and final deliverables |

The team will adjust implementation details according to dependencies and actual progress. The table represents the planned workflow, not completed milestones.

## Expected Deliverables

- Data loading and preprocessing pipeline.
- Trained DenseNet121 model and evaluation results.
- Shared findings JSON schema.
- Classification thresholds selected using validation data.
- Template-based report generator.
- Grad-CAM visualizations, subject to successful implementation.
- Case-grounded chatbot with fallback behavior.
- FastAPI backend endpoints.
- Integrated single-page GUI.
- End-to-end and chatbot evaluation records.
- Final technical paper and project presentation.

## Evaluation Strategy

The team will evaluate:

- Per-label classification performance.
- The effect of classification threshold selection.
- Data integrity and prevention of data leakage.
- Consistency between model findings and generated reports.
- Chatbot grounding and handling of unsupported questions.
- End-to-end functionality and API integration.

Performance targets are planning goals, not achieved results. Actual metrics will be reported only after testing, together with relevant limitations.

## Risk Management

| Risk | Mitigation |
|---|---|
| Class imbalance | Consider class weighting and report per-label metrics. |
| Data leakage | Apply patient-aware data splitting where metadata permits and keep evaluation data separate. |
| Limited training resources | Use an agreed fixed dataset subset and suitable batch sizes. |
| Unsupported chatbot responses | Ground responses in structured findings and implement fallback rules. |
| Integration delays | Define file contracts, separate Git branches, and explicit handoff deadlines. |
| Delayed deliverables | Review progress at milestones and assign backup support when needed. |

Core data-integrity checks, report generation, safety rules, model evaluation, chatbot evaluation, and the main paper sections will remain priorities if delays occur.

## Team Collaboration

The team will coordinate through a shared Git repository, agreed file contracts, and explicit handoff deadlines.

- **Day 1:** Kickoff meeting, if needed, to confirm responsibilities and working agreements.
- **Day 4:** Mandatory progress meeting to review deliverables, dependencies, and blockers.
- **Day 6:** Additional checkpoint if required.
- **Day 7:** Buffer for unexpected delays.

Team members should work on separate Git branches, with Omar coordinating merges and Hazem serving as the backup reviewer.

Any task delayed by more than one day must be reported to the project lead on the same day. A designated cover person will continue from the latest shared files rather than restarting the task.

## Limitations and Safety

This project is an educational AI-assisted analysis prototype and is not intended for clinical diagnosis or treatment decisions.

- Model predictions may contain false positives and false negatives.
- Grad-CAM visualizations do not establish clinical correctness.
- Performance depends on the selected dataset, preprocessing, and evaluation protocol.
- Chatbot responses must remain grounded in available case information.
- The system must communicate its limitations and avoid unsupported medical claims.

## Disclaimer

This system is developed for educational and research purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment.

## Acknowledgments

Developed as part of the Digital Egypt Pioneers Initiative (DEPI), under the supervision of Antonios Malak.

## License

No license has been specified yet. A license will be added if and when the project team decides to publish the repository under one.
