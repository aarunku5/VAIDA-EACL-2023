# VAIDA-EACL-2023
This repository contains supplementary files for the paper Real-Time Visual Feedback to Guide Benchmark Creation: A Human-and-Metric-in-the-Loop Workflow, published in EACL 2023.

## Data

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

## Video

- CrowdWorker.mp4 : Contains demo for crowdworker interface
- Analyst.mp4 : Contains demo for all visual interfaces available to the analyst

## Results

- DQI_Study_Results contains the following information
        - Term Explanations : Key for DQI Component Representations
        - SNLI Sample DQI : DQI values for original SNLI samples
        - VAIDA Sample DQI : DQI values for samples created in ablation rounds
        - DQI % Gains : Percentage gain/loss in DQI values in VAIDA compared to conventional SNLI crowdsourcing

- Model_Study_Results  contains the performance accuracy details of BERT, RoBERTa (trained on 100% of SNLI data) and GPT-3 (Fewshot) on the reference SNLI and ablation round samples

- DQI Evaluation contains a case study to show the efficacy of DQI in our proposed data creation paradigm

- Pre-existing Samples contains the 100 samples present in the system during the user study

## Code

Contains python notebooks and pre-processed files of Pre-existing Samples to calculate the DQI parameters.

### Supplementary material

The following supplemental information is present in the appendix of the main paper (see link: https://arxiv.org/abs/2302.04434):

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
