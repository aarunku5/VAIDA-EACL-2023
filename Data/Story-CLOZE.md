# EACL-2023-ID-1134

## Real-Time Visual Feedback to Guide Benchmark Creation: A Human-and-Metric-in-the-Loop Workflow

## Conversion Map

We report results on 3 additional dataset in the previously provided supplementary material- [MNLI](https://cims.nyu.edu/~sbowman/multinli/), [SQUAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/), [Story CLOZE](https://cs.rochester.edu/nlp/rocstories/).

We detail the conversion mapping of samples from SQUAD 2.0 and Story CLOZE to an NLI format for metric calculation below:

### SQUAD 2.0

#### Original Input Fields (with example):

- **Title:** Beyoncé
- **Context:** Beyoncé Giselle Knowles-Carter (/biːˈjɒnseɪ/ bee-YON-say) (born September 4, 1981) is an American singer, songwriter, record producer and actress. Born and raised in Houston, Texas, she performed in various singing and dancing competitions as a child, and rose to fame in the late 1990s as lead singer of R&B girl-group Destiny's Child. Managed by her father, Mathew Knowles, the group became one of the world's best-selling girl groups of all time. Their hiatus saw the release of Beyoncé's debut album, Dangerously in Love (2003), which established her as a solo artist worldwide, earned five Grammy Awards and featured the Billboard Hot 100 number-one singles "Crazy in Love" and "Baby Boy". 
- **Question:** When did Beyonce start becoming popular? 
- **Answer:** in the late 1990s 

#### Conversion Map for DQI Input:

- **Premise:** Title + Context + Question
- **Hypothesis:** Answer
- **Label:** True (for correct answer), False (for incorrect answer/impossible answer)

## 

### Story CLOZE

#### Original Input Fields (with example):

- **InputSentence1**: Rick grew up in a troubled household.
- **InputSentence2:** He never found good support in family, and turned to gangs.
- **InputSentence3:** It wasn't long before Rick got shot in a robbery.
- **InputSentence4:** The incident caused him to turn a new leaf.
- **RandomFifthSentenceQuiz1:** He is happy now.
- **RandomFifthSentenceQuiz2:** He joined a gang.
- **AnswerRightEnding:** 1

#### Conversion Map for DQI Input:

Each sample is split into 2 separate samples, as follows:

- **Sample 1:**
  - **Premise:** InputSentence1 + InputSentence2 + InputSentence3 + InputSentence4
  - **Hypothesis:** RandomFifthSentenceQuiz1
  - **Label:** True (if AnswerRightEnding is 1, else False)

- **Sample 2:**
  - **Premise:** InputSentence1 + InputSentence2 + InputSentence3 + InputSentence4
  - **Hypothesis:** RandomFifthSentenceQuiz2
  - **Label:** True (if AnswerRightEnding is 2, else False)

## 

## DQI Results for Story CLOZE

Given the premise context for a Story CLOZE sample, crowdworkers create a new 'True' ending, and a new 'False' ending. Each ending is evaluated as part of a separate sample, as demonstrated in the Story CLOZE conversion map. This is done to recreate 200 Story CLOZE samples from the test set of Story CLOZE, correspondingly evaluated with DQI as 400 separate samples.

### Note: The row with "Story CLOZE" comprises of original Story CLOZE sample evaluation, and "VAIDA"  of the newly created Story CLOZE samples.

We have DQI results for the original samples vs the new samples shown below.

- **Component 1: Vocabulary**

| DATA | T1 | T2 | T3 | DQI-C1 |
| --- | --- | --- | --- | --- |
| Story CLOZE | 5.57 | 4.34 | 0.71 | 8.06 |
| VAIDA | 6.70 | 6.26 | 0.83 | 10.25 |

- **Component 2: Inter-Sample N-Gram Frequency and Relation**

| DATA | W1 | W2	| Bi T1 | Bi T2 | Adj T1	| Adj T2	| Adv T1	| Adv T2	| N T1	| N T2	| V T1	| V T2	| Tri T1	| Tri T2	| S T1	| S T2	|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 162.87 | 0.66 | 602.35 | 0.83 | 33.12 | 0.34 | 16.31 | 0.01 | 42.78 | 0.21 | 32.18 | 0.00 | 2065.46 | 0.62 | 2681.75 | 0.84 |
| VAIDA | 251.33 | 0.73 | 1008.45 | 0.98 | 58.91 | 0.51 | 31.78 | 0.14 | 64.22 | 0.29 | 49.74 | 0.06 | 2391.07 | 0.76 | 2888.54 | 0.97 |

| DATA | Word	| S	| Adj	| Adv	| N	| V	| Bi	| Tri	| DQI-C2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 402 | 200 | 103 | 11 | 241 | 86 | 985 | 1101 | 5621.89 |
| VAIDA | 489 | 200 | 184 | 17 | 252 | 108 | 1206 | 1256 | 6003.08 |

- **Component 3: Inter-Sample STS**

| DATA | T1 (SIM=0.6)	| T2 (e=0.5) |	DQI-C3 |
| --- | --- | --- | --- |
| Story CLOZE | 6.17 | 176 | 296.55 |
| VAIDA | 8.22 | 185 | 352.45 |

- **Component 4: Intra-Sample Word Similarity**

| DATA | DQI-C4 |
| --- | --- |
| Story CLOZE | 0.0031 |
| VAIDA | 0.0027 |

- **Component 5: Intra-Sample STS**

| DATA | T1 (ISIM=0.5) |	T2	| T3	| T4	| T5	| T6	| DQI-C5 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 4.12 | 0.25 | 0.06 | 0.002 | 16.47 | 0.08 | 3.14 |
| VAIDA | 6.77 | 0.38 | 0.08 | 0.001 | 24.61 | 0.10 | 4.29 |

- **Component 6: N-Gram Frequency Per Label**
											
- **True Label**

| Data	| W1	| W2	| Bi T1	| Bi T2	| Adj T1	| Adj T2	| Adv T1	| Adv T2	| N T1	| N T2	| V T1	| V T2	| Tri T1	| Tri T2	| S T1	| S T2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 110.21 | 0.45 | 298.11 | 0.81 | 65.71 | -0.02 | 14.44 | 0.32 | 31.56 | -0.1 | 40.07 | -0.12 | 1511.37 | 0.71 | 1003.28 | 0.96 |
| VAIDA | 131.65 | 0.51 | 419.67 | 1 | 51.35 | 0.02 | 22.11 | 0.26 | 51.07 | -0.02 | 43.63 | 0.01 | 1618.83 | 0.65 | 1056.89 | 1 |

| Data | Word	| S	| Adj	| Adv	| N	| V	| Bi	| Tri	| T3	| T4	| T5	| DQI-C6 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 267 | 200 | 48 | 8 | 166 | 56 | 861 | 812 | 0.17 | 0.21 | 16.87 | 185.12 |
| VAIDA | 365 | 200 | 92 | 12 | 192 | 75 | 912 | 951 | 0.14 | 0.13 | 16.99 | 211.63 |

- **False Label**

| Data	| W1	| W2	| Bi T1	| Bi T2	| Adj T1	| Adj T2	| Adv T1	| Adv T2	| N T1	| N T2	| V T1	| V T2	| Tri T1	| Tri T2	| S T1	| S T2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 120.21 | 0.35 | 264.61 | 0.78 | 55.21 | 0.02 | 15.84 | 0.41 | 33.70 | -0.08 | 35.92 | 0.03 | 1416.89 | 0.68 | 1169.13 | 1 |
| VAIDA | 135.88 | 0.43 | 476.15 | 0.93 | 48.03 | 0.04 | 20.67 | 0.37 | 39.76 | 0.01 | 39.94 | 0.08 | 1788.34 | 0.57 | 1257.45 | 1 |

| Data | Word	| S	| Adj	| Adv	| N	| V	| Bi	| Tri	| T3	| T4	| T5	| DQI-C6 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Story CLOZE | 236 | 200 | 57 | 9 | 172 | 41 | 808 | 835 | 0.18 | 0.23 | 14.21 | 156.89 |
| VAIDA | 312 | 200 | 88 | 11 | 201 | 68 | 877 | 953 | 0.16 | 0.19 | 14.79 | 198.15 |

- **Component 7: Inter-Split STS**

| DATA | DQI-C7 (SSIM=0.4) |
| --- | --- |
| Story CLOZE | 0.006 |
| VAIDA | 0.014 |

## 

## Model Results for Story CLOZE

We train BERT and RoBERTa models on samples from the Story CLOZE test and validation sets (excluding recreated samples). We evaulate model performance of BERT, RoBERTa, and GPT-3 (in fewshot setting) on both the original and recreated samples. The input format used is that of the original Story CLOZE format, prior to conversion mapping.

| DATA | RoBERTa | BERT | GPT-3 |
| --- | --- | --- | --- |
| Story CLOZE | 0.85 | 0.83 | 0.46 |
| VAIDA | 0.71 | 0.68 | 0.39 |

## 

## Interface Modification

We list the interface changes made for Story CLOZE sample creation and evaluation below:

- **Crowdworker View:**
  - Sample creation insturctions are modified to Story CLOZE data creation instructions
  - The 'Context' field populates with the first 4 story sentences
  - The 'Right Ending' and 'Wrong Ending' fields are to be filled by the crowdworker
  - Sample Evaluation happens for the 'Context+Right Ending' and then for the 'Context+Wrong Ending' samples
  - Tooltips comprise of content that marks the label as True/False for the label, and uses Context/Ending instead of Premise/Hypothesis
  
- **Analyst Views:**
  - For all components, parameters are calculated against the Story CLOZE data, post conversion mapping.
  - Color scales (based on the hyper parameters for red-yellow-green flagging of samples) for the views vary, due to different hyperparamter thresholds being used for flagging.
  - Tooltips comprise of content that marks the label as True/False for the label, and uses Context-Ending instead of Premise-Hypothesis for input field labels
  
 - **Component 1: Vocabulary**
  - The train set is taken to be samples from the validation and test set that are not recreated, there is no dev set bar.

 - **Component 6: N-Gram Frequency Per Label**
  - Views only contain True/False labels for the sample, so there are two violin plots and two box-plots for sample categories
 
 - **Component 7: Inter-Split STS**
  - Fields are marked as Context-Ending instead of Premise-Hypothesis
  -  Training Set comprises of samples from the validation and test set that are not recreated

- **Color Scales**

| Component | C1 | C2 | C3 | C4 | C5 | C6 | C7 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Red | (0-0.22) & (0.78-1.00) | (0-0.20) & (0.68-1.00) | (0-0.27) & (0.84-1.00) | (0-0.41) & (0.85-1.00) | (0-0.30) & (0.75-1.00) | (0-0.29) & (0.72-1.00) | (0-0.26) & (0.74-1.00) |
| Yellow | (0.22-0.56) & (0.65-0.78) | (0.20-0.34) & (0.45-0.68) | (0.27-0.51) & (0.57-0.84) | (0.41-0.67) & (0.75-0.78) | (0.30-0.55) & (0.65-0.75) | (0.29-0.36) & (0.43-0.72) | (0.26-0.46) & (0.61-0.74) |
| Green | (0.56-0.65) | (0.34-0.45) | (0.51-0.57) | (0.67-0.75) | (0.55-0.65) | (0.36-0.43) | (0.46-0.61) |


