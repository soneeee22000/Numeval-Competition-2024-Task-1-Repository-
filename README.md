# Numeval-Competition-2024-Task-1-Repository-

**I will be participating in the Semeval competition this year. **
The task I chose is Numeval @ semeval 2024  ( Task 1 Quantitative Understanding English)

**Task 1: Quantitative Understanding (English)**

In Task 1, our focus is on the quantitative understanding task,
which is further divided into three subtasks: Quantitative Prediction (QP),
Quantitative Natural Language Inference (QNLI),
and Quantitative Question Answering (QQA).

The Quantitative 101 dataset [1], a compilation of Numeracy-600K [2], EQUATE [3], and NumGLUE Task 3 [4], is employed for experimentation.

---

The Quantitative Prediction (QP) subtask is to predict the numerical value of a given arithmetic expression.
Context: In the third quarter of 2022, the GDP growth rate was [MASK]%.

The model must predict the approximate magnitude of the masked number based on the context.

---

The Quantitative Natural Language Inference (QNLI) subtask is to determine whether a given arithmetic expression is true or false.
Premise: The population of India reached 1.4 billion in 2022.
Hypothesis: India's population is more than 1.3 billion.

The model must determine the hypothesis is entailed from the premise statement.

---

The Quantitative Question Answering (QQA) subtask is to answer a question about a given arithmetic expression.
Question: Jenny had $20 dollars originally. After buying a notebook for $15, how much money does she have left?
Option 1: $5
Option 2: $10

The model must infer from the question and choose the correct option.

---

let's go over the public datasets given to us for this task.

The first dataset is Numeracy-600K [2], which is a large-scale dataset for numerical reasoning.
It contains 600,000 numerical reasoning problems, which are automatically generated from the English Wikipedia corpus.
Each problem is associated with a question, a context, and a numerical answer.
The answer is either a number or a number with a unit.

+++

The second dataset is *EQUATE* [3], which is a dataset for mathematical word problems.
It contains 1,000 mathematical word problems, which are collected from the Math Word Problem (MWP) dataset [5].
Each problem is associated with a question, a context, and a numerical answer.
The answer is either a number or a number with a unit.

+++

The third dataset is *NumGLUE* Task 3 [4], which is a dataset for numerical reasoning.
It contains 1,000 numerical reasoning problems, which are collected from the Math Word Problem (MWP) dataset [5].
Each problem is associated with a question, a context, and a numerical answer.
The answer is either a number or a number with a unit.

+++

***The Quantitative 101 dataset*** [1] is a compilation of Numeracy-600K [2], EQUATE [3], and NumGLUE Task 3 [4].
It contains 602,000 numerical reasoning problems, which are automatically generated from the English Wikipedia corpus and collected from the Math Word Problem (MWP) dataset [5].
Each problem is associated with a question, a context, and a numerical answer.
The answer is either a number or a number with a unit.

The Quantitative 101 dataset [1] is split into training, development, and test sets.
The training set contains 600,000 numerical reasoning problems, which are automatically generated from the English Wikipedia corpus.
The development set contains 1,000 numerical reasoning problems, which are collected from the Math Word Problem (MWP) dataset [5].
The test set contains 1,000 numerical reasoning problems, which are collected from the Math Word Problem (MWP) dataset [5].

---

Quantitative 101 dataset, which is the combination of one generated dataset (CND) and three benchmark datasets: Numeracy-600K [1], EQUATE [2], and NumGLUE Task 3 [3]. The tasks in Quantitative 101 include Comparing Numbers (ComNum), Quantitative Prediction (QP), Quantitative Natural Language Inference (QNLI), and Quantitative Question Answering (QQA).
The details of how to separate the dataset are shown in this document.

(1) Task: ComNum
There are two JSON files in the ComNum folder. "CND-OOR.json" is used for testing the phenomenon. "CND-IR.json" can be separated into training and test sets with the following code:
import pandas as pdtrain_size = 0.8            train_dataset=new_df.sample(frac=train_size,random_state=200)test_dataset=new_df.drop(train_dataset.index).reset_index(drop=True)train_dataset = train_dataset.reset_index(drop=True)

(2) Task: QP
In the QP folder, we already separated Numeracy-600K into training, development, and test sets. Note that, the original Numeracy-600K [1] did not provide such information.

(3) Task: QNLI
EQUATE has five subsets collected from different sources, including RTE-QUANT, AWP-NLI, NEWSNLI, REDDITNLI, and Stress Test.
For Stress Test, which contains 7,500 instances, we follow the splitting method in NumGLUE Task 7 to separate it into training, development, and test sets. All sets are in the "QNLI-Stress Test" folder.
Because other subsets are less than 1,000 instances, we perform the 10-fold cross-validation in the experiments. Please use the following code to separate folds:
from sklearn.model_selection import KFoldkf = KFold(n_splits=10,random_state=200)

(4) Task: QQA
We follow [3] to separate the dataset into training, development, and test sets.
---
I will be uploading everything related to the competition here! all the code, all the theory and papers that I read and the findings! If we won this competition, I will expand these results and findings to my Masters' Thesis ! I hope we win but, it's always about Trying our best ! Of Course! 
