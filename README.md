[Erdős Institute Data Science Boot Camp](https://github.com/TheErdosInstitute/data-science-fall-2024), Fall 2024.

- View our 5 mins presentation ....

<h1>Fake Image Detection</h1>

<h3>Team Members:</h3>

[Heba Bou KaedBey](https://github.com/hebabkb), [Navid Bahadoran](https://github.com/navidbahadoran), [Rajeev Gopensingh](https://github.com/RajeevGopeesingh), [Chase Wiederstein](https://github.com/ChaseWiederstein), [Jonathan Engle](https://github.com/J3ngle)

<h1>Project Description</h1>

Fake image detection is increasingly crucial in combating misinformation and ensuring online authenticity. The technology addresses challenges in journalism, social media, and digital security, helping to identify manipulated or AI-generated images. Our project explores traditional machine learning methods to detect fake images effectively.

We leverage the CASIA2 Ground Truth Dataset, which contains 7,491 real images and 5,123 fake images altered through techniques such as image splicing, blurring, and color adjustments.

<h1>Recall Results</h1>

In the evaluation of recall scores for detecting fake images, Model 1 (Stack 5, one-level stacking) and Model 2 (Stack 7, two-level stacking) both achieved an impressive recall of 83%:

![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/Recall%20Scores.png)

<h1>PR AUC Results</h1>

The Precision-Recall AUC in our 11 models is shown in this graph. As it is obvious, Stack 5 (model 1) and Stack 7 (model 2) are giving high performance

![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/PR%20AUC%20Scores.png)

<h1>ROC AUC Results</h1>

Here the ROC-AUC of our models is shown. Again Stack 5 (model 1) and Stack 7 (model 2) are giving promising performance.

![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/ROC-AUC%20Scores.png)


<h1>Models Details</h1>

<h2>Model 1: Stacking Classifier with SVM Meta-Learner</h2>

<h3>Base Classifiers</h3>
- Combines Random Forest (RF), XGBoost (XGB), LightGBM (LGBM), and Support Vector Classifier (SVC).
- Each base Classifier specializes in extracting unique features for robust predictions.

<h3>Stacking</h3>
- The outputs from the base classifiers are passed to a meta-learner for final decision-making.
- Meta-Learner:An SVM with probability-based soft voting ensures accurate class separation.
- Cross-validation ensures generalization and reduces overfitting.

---
![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/One%20Level%20Stacking%20Model.png)

<h2>Model 2: Two Level Stacking Classifier</h2>

<h3>Level 1: Base Models</h3>

- Combines four base classifiers: Random Forest (RF), XGBoost (XGB), LightGBM (LGBM), and Support Vector Classifier (SVC).
  
<h3> Level 1 Meta-Learners</h3>

- Outputsfrombaseclassifiersareaggregatedintothreeseparate meta learners: LightGBM, SVC, and XGBoost.
- Each meta-learner creates robust predictions by combining the strengths of base models.

<h3> Level 2: Final Stacking</h3>

- The outputs of the three level1 meta-learners are passed into a final meta-learner SVC for ultimate classification
- Ensures a layered approach for improved accuracy and generalization.
  
---
![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/Two%20Level%20Stacking%20Model.png)

<h1>Models Evaluation</h1>

For evaluation, we chose precision-recall and AUC-ROC curves because they provide a comprehensive view of model performance. Precision-recall is critical in detecting fake images, as we prioritize minimizing false positives while identifying all altered images. AUC-ROC complements this by showing the model’s ability to distinguish between real and fake images across thresholds. These metrics highlight the effectiveness of our models, with the one-level stacking model showing superior generalization and accuracy.


![](https://github.com/hebabkb/FakevsReal/blob/main/Presentation_Images/Models%20Evaluation.png)

<h1>Model Interface</h1>

We've written a [web app](https://huggingface.co/spaces/HebaBouKaedBey/TamperedImageDetection) that showcases our models.

