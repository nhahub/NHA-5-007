Program: DEPI  
Project Lead: Menna Alashqar  
Project Supervisor: Antonios Malak  
Project Type: Team-based Machine Learning project

1. Project Overview

The CheXpert Chest X-ray AI project aims to develop an AI-assisted system that analyzes frontal chest X-ray images and predicts five selected findings: Atelectasis, Cardiomegaly, Consolidation, Edema, and Pleural Effusion.
The system will integrate image preprocessing, a DenseNet121-based multi-label classification model, explainability through Grad-CAM, structured report generation, a grounded chatbot, a backend API, and a graphical user interface (GUI).
The project emphasizes reliable evaluation, traceability of generated information, and safety-oriented output handling. The generated report and chatbot responses will be grounded in the same structured findings data to reduce unsupported medical statements.

2. Project Objectives
The main objectives are to:
Develop a preprocessing pipeline for frontal chest X-ray images.
Train and evaluate a DenseNet121 model to predict five chest X-ray findings.
Select classification thresholds using validation data.
Generate structured, template-based reports from model predictions.
Provide Grad-CAM visualizations to support model-output interpretation.
Develop a chatbot that answers questions using the current case context and refuses unsupported medical requests.
Integrate the components through a backend API and a single-page GUI.
Evaluate the complete pipeline and document the methodology, results, limitations, and safety considerations.

3. In scope
Frontal chest X-ray images from the selected CheXpert dataset or an agreed fixed subset.
Image preprocessing and data integrity checks.
Five-label classification using DenseNet121.
Validation-based threshold selection and model evaluation.
Structured findings JSON and template-based report generation.
Grad-CAM explainability.
Case-grounded chatbot with a rule-based fallback.
FastAPI endpoints for prediction, reporting, and chat.
GUI development, end-to-end testing, and project documentation.

Out of scope
Replacing a qualified clinician or providing autonomous medical diagnoses.
Recommending treatment.
Claiming clinical readiness or clinical validation without appropriate evidence.
Generating findings that are not supported by the model outputs and the defined system context.

4. Team Structure and Responsibilities

Team member
Primary responsibilities

Menna Alashqar — Project Lead
Team coordination, preprocessing, report generation, GUI, and paper integration

Hazem
Dataset access, label preparation, uncertain-label policy, and backend API

Omar
Repository ownership, DenseNet121 implementation, model training coordination, and inference

Mariam
Data splitting, evaluation, testing, and paper integration

Abdelrahman
Validation support, explainability, data-quality checks, and safety review

Mahmoud
Chatbot development, integration support, and training-log analysis

Each member is responsible for delivering agreed outputs to the relevant teammates by the handoff deadlines. Team members should work on separate Git branches, with Omar coordinating merges and Hazem serving as the backup reviewer.


5. Week
Main focus
Expected deliverables

Week 1
Data pipeline
Dataset access, label policy, data splits, preprocessing, and working DataLoader

Week 2
Model development
DenseNet121 training, saved checkpoint, and validation metrics

Week 3
AI-assisted reporting
Frozen findings schema, thresholds, report generator, and edge-case tests

Week 4
Grounded chatbot
Case-context construction, safety rules, and chatbot evaluation

Week 5
API, GUI, and integration
Integrated pipeline, interface, and end-to-end checks

Week 6
Final validation and documentation
Final paper, demo, documented limitations, and final checks

The team will use weekly milestones and intermediate handoffs to identify dependencies and address delays early.


6. Project Success Criteria

The project will use the following targets from the team plan:

Model performance: Mean AUC across the five findings of at least 0.80 on the full test split, with 0.75 as the stated minimum target; each finding should achieve an AUC of at least 0.70.
Report safety: Zero unsupported findings in the report evaluation.
Chatbot safety: At least 90% pass rate on 40 or more shared test questions, with zero invented findings.
End-to-end testing: Test the integrated pipeline on 50 images for pipeline functionality and latency.
Data integrity: Check for split overlap, duplicate records, and corrupted files.
Documentation: Complete the project paper, final presentation, and supporting evaluation records.
These are project targets, not achieved results. Actual performance will be reported only after evaluation.


7. Risk Management

Risk
Mitigation strategy

Dataset download or access delays
Begin with an agreed subset of 5,000 images if the full dataset is not immediately available

Class imbalance or uncertain labels
Define the label-handling policy and use weighted loss where appropriate

Training takes too long
Run a smoke test, reduce epochs or use a smaller subset when necessary, and preserve resumable checkpoints

Team member misses a handoff
Contact the responsible member, use mock files temporarily, and assign a cover person if a task is more than one day late

LLM API becomes unavailable
Use the planned rule-based chatbot fallback and cached answers

Grad-CAM implementation is delayed
Deliver the core system and document heatmap availability as a limitation if necessary

Unsupported report or chatbot statements
Ground outputs in the shared findings JSON, apply refusal rules, and test edge cases

Integration defects
Maintain a shared repository, use agreed interfaces, and perform end-to-end testing

Core data-integrity checks, report generation, safety rules, model evaluation, chatbot evaluation, and the main paper sections will not be removed to compensate for delays.


8. Communication and Project Monitoring

The team will use a shared Git repository, agreed file contracts, and explicit handoff deadlines to coordinate development.

Day 1: Kickoff meeting, if needed, to confirm responsibilities and working agreements.

Day 4: Mandatory progress meeting to review deliverables, dependencies, and blockers.

Day 6: Additional checkpoint if required.

Day 7: Buffer for unexpected delays rather than a substitute for preparing core deliverables on time.

Any task delayed by more than one day must be reported to the project lead on the same day. The team will assign a cover person who continues from the latest shared files instead of restarting the task.

9. Tools and Resources

The planned project resources include:
Dataset: CheXpert, using frontal images or an agreed fixed subset.
Deep learning: DenseNet121 and a multi-label classification loss with class weighting.
Programming: Python and the libraries selected by the implementation team.
Version control: Git and a shared repository.
Backend: FastAPI.
Explainability: Grad-CAM.
Interface: A single-page GUI.
Documentation: Shared project files, evaluation tables, and the final project paper.

Specific software versions, deployment infrastructure, and supervisor details should be confirmed by the team where they have not yet been finalized.

10. Expected Deliverables

At the end of the six-week project, the team expects to deliver:

A validated data preprocessing and loading pipeline.
A trained DenseNet121 model and evaluation results.
A shared findings JSON schema and validation-selected thresholds.
A template-based report generator.
Grad-CAM visualizations, subject to successful implementation.
A case-grounded chatbot with a fallback mode.
FastAPI endpoints and an integrated GUI.
End-to-end and chatbot evaluation records.
A final technical paper and project presentation.

11. Conclusion

The project plan establishes a six-week workflow with defined team responsibilities, milestone-based delivery, explicit handoffs, measurable evaluation targets, and risk mitigation strategies. The final system is intended as an educational AI-assisted analysis prototype, not a replacement for professional clinical judgment. All reported results and limitations will be based on actual testing.
