
# Literature Review

## 1. Introduction

Chest X-ray (CXR) interpretation is an important application of artificial intelligence in medical imaging. Deep learning models can learn visual patterns from labeled radiographs and predict the presence of medical findings. However, developing reliable systems requires appropriate datasets, effective model architectures, careful handling of uncertain labels, and methods for making predictions easier to interpret.

This literature review examines previous research related to chest X-ray classification, DenseNet121, explainable artificial intelligence, automated radiology reporting, and safer conversational interfaces. These topics provide the research background for the proposed CheXpert-based system.

## 2. Chest X-Ray Datasets and Uncertain Labels

Irvin et al. (2019) introduced CheXpert, a large chest radiograph dataset containing 224,316 radiographs from 65,240 patients. The dataset includes labels for 14 observations extracted from radiology reports. An important characteristic of CheXpert is its treatment of uncertainty, because radiology reports may describe findings that are not definitively present or absent.

The authors investigated different approaches to using uncertain labels during convolutional neural network training. Their results showed that different uncertainty-handling approaches were useful for different pathologies. This suggests that uncertain labels should not automatically be treated identically across all disease categories.

**Relevance to this project:** The proposed system uses CheXpert to classify five findings: Atelectasis, Cardiomegaly, Consolidation, Edema, and Pleural Effusion. An appropriate strategy for handling uncertain labels must be selected, documented, and evaluated during model development.

**Reference:** Irvin et al. (2019). [CheXpert: A Large Chest Radiograph Dataset with Uncertainty Labels and Expert Comparison](https://doi.org/10.1609/aaai.v33i01.3301590).

## 3. Deep Learning for Chest X-Ray Classification

Convolutional Neural Networks (CNNs) are commonly used for image classification because they learn visual features directly from image data. Rajpurkar et al. (2017) introduced CheXNet, a model based on DenseNet121 for pneumonia detection from chest X-rays. Their work demonstrated the potential of deep learning for identifying abnormalities in chest radiographs.

However, results obtained for pneumonia do not automatically establish equivalent performance for other findings. Each target finding requires appropriate evaluation.

The proposed project plans to use DenseNet121 as the classification backbone. The task is formulated as multi-label classification, meaning that a single X-ray may be associated with more than one finding. Model performance will be evaluated separately for each of the five target findings.

**Reference:** Rajpurkar et al. (2017). [CheXNet: Radiologist-Level Pneumonia Detection on Chest X-Rays with Deep Learning](https://arxiv.org/abs/1711.05225).

## 4. Explainable Artificial Intelligence

Deep learning predictions can be difficult to interpret because the internal decision-making process of a model is not directly understandable to users. Explainable AI methods aim to provide additional information about the features or image regions associated with a prediction.

Selvaraju et al. (2017) introduced Gradient-weighted Class Activation Mapping (Grad-CAM), which generates visual localization maps using gradients flowing into a convolutional layer. These maps highlight image regions that contribute to a model's class-specific prediction.

The proposed system plans to use Grad-CAM to visualize regions associated with predicted chest X-ray findings. Such visualizations may help users inspect model behavior. However, a heatmap alone does not prove that a prediction is correct or that the model relies on clinically meaningful evidence.

**Reference:** Selvaraju et al. (2017). [Grad-CAM: Visual Explanations From Deep Networks via Gradient-Based Localization](https://openaccess.thecvf.com/content_iccv_2017/html/Selvaraju_Grad-CAM_Visual_Explanations_ICCV_2017_paper.html).

## 5. Automated Radiology Reporting

Automated radiology reporting investigates how medical images and their predicted findings can be converted into textual reports. TieNet, proposed by Wang et al. (2018), combines image and text representations for thoracic disease classification and report-related tasks, illustrating research into the relationship between image understanding and radiology text.

Generating a report that is readable is not sufficient by itself: its statements must also remain consistent with the available evidence.

The proposed project plans to use template-based report generation. Instead of generating unrestricted medical text, the reporting component will convert structured classification outputs into a predefined report format. This design aims to make the relationship between model predictions and report statements easier to inspect.

The accuracy and usefulness of the generated reports will require evaluation.

**Reference:** Wang et al. (2018). [TieNet: Text-Image Embedding Network for Common Thorax Disease Classification and Reporting in Chest X-Rays](https://openaccess.thecvf.com/content_cvpr_2018/html/Wang_TieNet_Text-Image_Embedding_CVPR_2018_paper.html).

## 6. Grounded Conversational Interfaces and Safety

A conversational interface can help users ask questions about classification results and generated reports. However, a chatbot may produce unsupported statements if it answers questions beyond the evidence available to it.

The proposed system plans to use a case-grounded chatbot that bases its responses on the structured findings and report associated with the current X-ray. A fallback response will be used when a question cannot be answered using the available information.

This is a design strategy intended to limit unsupported responses, not a guarantee that all chatbot answers will be correct. The chatbot is intended to explain the system's outputs rather than independently diagnose patients or replace professional clinical judgment.

The system's response grounding and fallback behavior should be tested as part of the project evaluation.

## 7. Research Gap and Proposed Contribution

Previous studies have explored large chest X-ray datasets, deep learning classification, visual explanations, and automated radiology reporting. These studies provide useful foundations for building medical imaging applications. However, the performance of an individual model or component does not establish the reliability of an integrated application.

The proposed project aims to integrate the following components into a single prototype:

- Multi-label classification of five selected chest X-ray findings using DenseNet121.
- Explicit handling of uncertain labels and validation-based selection of classification thresholds.
- Grad-CAM visualizations to inspect predictions.
- Template-based report generation grounded in structured model outputs.
- A case-grounded chatbot with fallback behavior for unsupported questions.
- A FastAPI backend and a single-page graphical user interface.

The project's planned contribution is the integration of classification, visual explanation, structured reporting, and constrained question answering in one application. Its actual performance, usability, and safety remain to be established through experiments.

## 8. Conclusion

The reviewed studies provide a foundation for the proposed chest X-ray classification and reporting system. CheXpert highlights the importance of dataset quality and uncertainty handling; CheXNet demonstrates the potential of DenseNet121-based chest X-ray classification; Grad-CAM provides a method for visualizing model-associated image regions; and TieNet explores connections between image classification and radiology reporting.

Building on these research directions, the proposed project will combine multi-label classification with visual explanations, structured reports, and a grounded chatbot. Experimental evaluation will be necessary to determine how effectively these components work together and to identify the limitations of the resulting prototype.

## References

1. Irvin, J., et al. (2019). CheXpert: A Large Chest Radiograph Dataset with Uncertainty Labels and Expert Comparison. *Proceedings of the AAAI Conference on Artificial Intelligence, 33*(01), 590–597. https://doi.org/10.1609/aaai.v33i01.3301590

2. Rajpurkar, P., et al. (2017). CheXNet: Radiologist-Level Pneumonia Detection on Chest X-Rays with Deep Learning. https://arxiv.org/abs/1711.05225

3. Selvaraju, R. R., et al. (2017). Grad-CAM: Visual Explanations From Deep Networks via Gradient-Based Localization. *Proceedings of the IEEE International Conference on Computer Vision (ICCV).* https://openaccess.thecvf.com/content_iccv_2017/html/Selvaraju_Grad-CAM_Visual_Explanations_ICCV_2017_paper.html

4. Wang, X., et al. (2018). TieNet: Text-Image Embedding Network for Common Thorax Disease Classification and Reporting in Chest X-Rays. *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR).* https://openaccess.thecvf.com/content_cvpr_2018/html/Wang_TieNet_Text-Image_Embedding_CVPR_2018_paper.html
