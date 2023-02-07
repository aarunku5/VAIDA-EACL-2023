#VAIDA-Crowdsourcing Evaluation Results

This repository contains the demo videos for VAIDA, and the crowdsourced samples and evaluation results for the same. 

##Data

- Crowd: Conventional Crowdsourcing Ablation Round
- Traffic: Only Traffic Signal (RYG) Visual Feedback Ablation Round
- Auto: Only AutoFix Recommendations Ablation Round
- Full: Full System Ablation Round
- TF: TextFooler modification on samples created with the Full System
- Story CLOZE Results in full system condition

Note:
- Sentence 1 refers to the premise, and Sentence 2 to the hypothesis.
- 0: contradiction, 1: entailment, 2: neutral
- Files with the suffix 'Old' contain the original SNLI samples for reference
- Files with the suffix 'New' contain data created in ablation rounds

##Video

- CrowdWorker.mp4 : Contains demo for crowdworker interface
- Analyst.mp4 : Contains demo for all visual interfaces available to the analyst

##Results

- DQI_Study_Results contains the following information
        - Term Explanations : Key for DQI Component Representations
        - SNLI Sample DQI : DQI values for original SNLI samples
        - VAIDA Sample DQI : DQI values for samples created in ablation rounds
        - DQI % Gains : Percentage gain/loss in DQI values in VAIDA compared to conventional SNLI crowdsourcing

- Model_Study_Results  contains the performance accuracy details of BERT, RoBERTa (trained on 100% of SNLI data) and GPT-3 (Fewshot) on the reference SNLI and ablation round samples

###Supplementary material

The following supplemental information is present in the appendix :

- Infrastructure Used
- Run-time Estimations
- Hyper Parameter
- Related Work
- DQI Components
- Evaluation: Artifact Case Study
- Interface Design
- AutoFix and TextFooler Examples
- User Study
- Expert and User Comments