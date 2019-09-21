# Machine Learning Basics

 “ A computer program is said to learn from experience **E*** with respect to some class of tasks **T** and performance measure **P** , if its performance at tasks in **T** , as measured by **P** , improves with experience **E**. ”

#### Task
- Classification
- Regression
- Transcription
- Machine Translation
- Structured Output
- Anomaly Detection
- Synthesis & Sampling
- Imputation of missing values
- Denoising
- Etc..

#### Performance
To evaluate abilities of machine learning algorithm, need to design a quantitative measure of the performance (evaluate on **test set**)

Ideally, we should choose a performance measure that corresponds well to the desired behaviour of the system

#### Experience
1. **Unsupervised learning** (Learn properties of the dataset; probability distribution)
2. **Supervised learning** (Learn to predict target from features; $P(y|x)$ )


### Linear Rregression
$$
\hat y =  w^Tx + b
$$
where $w \in \mathbb{R}^n$ is a vector of parameters (control behaviour of the system)

**Performace**

Mean Squared Error

$$
MSE_{test} = \frac{1}{m}\sum_i(\hat y - y)^2_i
$$
