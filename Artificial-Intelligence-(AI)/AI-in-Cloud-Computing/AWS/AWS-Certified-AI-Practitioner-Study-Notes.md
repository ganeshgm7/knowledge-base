# AWS Certified AI Practitioner Study Notes

The three main types of machine learning are supervised learning, unsupervised learning, and deep learning.

##  Supervised learning

    - Logistic regression
    - Linear regression 
    - Decision tree
    - Neural network 
    
##  Semi-supervised learning
    
    - Document classification 
    - Sentiment analysis 
    
## Unsupervised learning 

    - Association rule learning 
    - Clustering 
    - Dimensity reduction 
    
## Techniques to Prevent Overfitting

- **Cross-Validation:** Split data into training and validation sets multiple times to ensure the model performs well across different data subsets.
- **Regularization:** Apply penalties (L1 or L2) to the model's complexity, discouraging overly complex models.
- **Pruning:** Simplify decision trees by removing sections that provide little predictive power.

## Interpretability vs. Explainability

- **Interpretability:** Understanding the internal mechanisms of a machine learning model.
- **Explainability:** Providing understandable reasons for a model's predictions and behaviors to stakeholders.

## Amazon SageMaker Tools for Machine Learning

### Amazon SageMaker Feature Store
- **Purpose:** Fully managed repository for storing, sharing, and managing ML model features.
- **Usage Example:** Features for a music recommendation app could include song ratings, listening duration, and listener demographics.

### Amazon SageMaker Clarify
- **Purpose:** Detects potential bias during data preparation without requiring code.
- **Functionality:** Analyze input features (e.g., gender, age) for bias.

### Amazon SageMaker Data Wrangler
- **Purpose:** Simplifies data aggregation and preparation for ML.
- **Functionality:** Provides a single visual interface for data selection, cleansing, exploration, visualization, and scalable processing.

### Amazon SageMaker Ground Truth
- **Purpose:** Used for labeling training data (images, text) to build ML models.
- **Human Review:** Allows human labeling or correction of unlabelled data.
- **Usage Scenario:** Needed when high-quality labeled data is required for training.

### Amazon Augmented AI (A2I)
- **Purpose:** Integrates human review into model predictions after deployment.
- **Human Review:** Enables human verification and correction of model predictions.
- **Usage Scenario:** Ideal for verifying or auditing predictions before actions are taken.

## Temperature in LLMs on Amazon Bedrock
- **Definition:** A value between 0 and 1 regulating the creativity of LLM responses.\n
- **Usage:**\n  - Lower temperature: More deterministic responses.\n  - Higher temperature: More creative and varied responses.

## Top P Sampling
- **Definition:** Represents the percentage of most likely candidates that the model considers for the next token.

## Top K Sampling
- **Definition:** Represents the number of most likely candidates that the model considers for the next token.

## Stop Sequences
- **Definition:** Specifies character sequences that stop the model from generating further tokens.\n
- **Usage:** Generation halts after encountering a defined stop sequence.

## Response Length
- **Definition:** Sets the minimum or maximum number of tokens to return in the generated response.

## Amazon Connect with Amazon Q
- **Amazon Connect:** AWS contact center service.\n
- **Amazon Q in Connect:** Enhances customer service by using real-time conversations and company content to suggest responses and actions for agents.

## Deep Learning Model Training
- **Process:** Utilizes large datasets to iteratively adjust neural network weights and biases.\n
- **Technique:** Gradient descent minimizes the error over iterations.

## Model Parameters vs. Hyperparameters
- **Model Parameters:** Values that define a model’s behavior in processing input and generating outputs.\n
- **Hyperparameters:** Configurable values that control the training process (e.g., learning rate, batch size).

## Amazon Inspector
- **Purpose:** Automated security assessment service for improving security and compliance of AWS applications.\n
- **Functionality:** Automatically checks applications for exposure, vulnerabilities, and deviations from best practices.\n
- **Use Case:** Essential for securing AI systems and applications deployed on AWS.

## AWS Config
- **Purpose:** Assess, audit, and evaluate AWS resource configurations.\n
- **Limitation:** Does not perform automated security assessments.\n
- **Use Case:** Governance and compliance monitoring.

## AWS Audit Manager
- **Purpose:** Simplifies risk assessment and compliance with regulations and industry standards.\n
- **Limitation:** Focuses on audit and compliance reporting, not automated security assessments.\n
- **Use Case:** Continuous auditing of AWS usage for compliance.

## AWS Artifact
- **Purpose:** On-demand access to AWS compliance reports and online agreements.\n
- **Limitation:** No automated security assessment capabilities.\n
- **Use Case:** Compliance documentation and reporting.

## AWS Trusted Advisor
- **Purpose:** Provides guidance for optimizing AWS environments in terms of cost, performance, security, and fault tolerance.\n
- **Limitation:** Does not perform compliance audits or evidence collection.\n
- **Use Case:** Best practice recommendations for AWS resource optimization.

## AWS CloudTrail
- **Purpose:** Records AWS API calls for auditing and operational troubleshooting.\n
- **Limitation:** Does not automate compliance assessments or collect evidence.\n
- **Use Case:** Tracking user activity and API usage for security auditing.

## Agility
- **Definition:** Easy access to a broad range of technologies enables faster innovation and the ability to build diverse solutions.\n
- **Functionality:** Quickly spin up resources as needed, including computing, storage, databases, IoT, machine learning, data lakes, and analytics.\n
- **Benefit:** Faster development and deployment of applications and services.

## Elasticity
- **Definition:** Dynamic provisioning and scaling of resources based on demand.\n
- **Functionality:** Scale resources up or down instantly to match business needs.\n
- **Benefit:** Cost-effective and efficient resource management without over-provisioning.

## Cost Savings
- **Definition:** Shift from capital expenses to variable expenses.\n
- **Functionality:** Pay only for the IT resources consumed, benefiting from lower costs due to economies of scale.\n
- **Benefit:** Significant reduction in infrastructure costs and more efficient spending.

## Global Deployment in Minutes
- **Definition:** Expand to new geographic regions rapidly.\n
- **Functionality:** Deploy applications globally using cloud infrastructure with a few clicks (e.g., AWS's global infrastructure).\n
- **Benefit:** Reduced latency and enhanced user experience by placing applications closer to end users.\n
- **Additional Advantages:**\n  - Benefit from massive economies of scale.\n  - Easily transition from capital expense to variable expense.\n  - Deploy applications globally in minutes.

## FM and Model Customization
FM is an AI model with a large number of parameters and trained on a massive amount of diverse data, whereas model customization is the process of using training data to adjust the model parameter values in a base model to create a custom model.

## K-Means vs KNN
K-Means is an unsupervised learning algorithm used for clustering data points into groups, while KNN is a supervised learning algorithm used for classifying data points based on their proximity to labelled examples.

## Human vs Automatic Model Evaluation
Human model evaluation is valuable for assessing qualitative aspects of the model, whereas automatic model valuation is valuable for assessing quantitative aspects of the model. Automatic model evaluation provides model scores that are calculated using various statistical methods such as BERT Score and F1.

## Reinforcement Learning from Human Feedback (RLHF)
Reinforcement learning from human feedback (RLHF) is a machine learning (ML) technique that uses human feedback to optimize ML models to self-learn more efficiently. Reinforcement learning (RL) techniques train software to make decisions that maximize rewards, making their outcomes more accurate.

## Average Response Time
Average response time measures how long it takes for the model to process input data and generate a prediction. It directly reflects the model's runtime efficiency, which is crucial in scenarios where timely decisions need to be made, such as real-time stock market predictions. A lower average response time indicates better runtime efficiency, ensuring that predictions are delivered quickly enough to be actionable.

## Model Accuracy
While model accuracy is essential for assessing how well the model's predictions match the actual outcomes, it is not a measure of runtime efficiency. Accuracy evaluates the correctness of the model’s predictions but does not reflect how quickly those predictions are generated.

## Data Throughput
Data Throughput measures the amount of data a system can process in a given time. While this can be related to the overall system performance, it does not directly assess the model's runtime efficiency in terms of how quickly it generates predictions. Average response time is a more appropriate metric for measuring runtime efficiency, particularly in real-time prediction scenarios.

## Typical Machine Learning Process
The machine learning process typically follows these steps:
1. **Data collection**  
2. **Data preprocessing**  
3. **Model training**  
4. **Model evaluation**

## Convolutional Neural Networks (CNNs)
Convolutional Neural Networks (CNNs) are specifically designed for processing and classifying image data. They use convolutional layers to automatically and adaptively learn spatial hierarchies of features from input images, making them highly effective for tasks such as image recognition and classification.

## Recurrent Neural Networks (RNNs)
Recurrent Neural Networks (RNNs) are typically used for sequence data, such as time series or natural language processing tasks.

## Generative Adversarial Networks (GANs)
Generative Adversarial Networks (GANs) are used for creating realistic synthetic data while preserving the statistical properties of the original data.

## AWS AI Service Cards
AWS AI service cards are designed to offer transparency and provide users with crucial information about the intended use, limitations, and potential impacts of AWS AI services. This helps users make informed decisions and implement Responsible AI practices by understanding the implications of using these services.

## Overfitting and Underfitting
- **Overfitting**: Occurs when a model learns from the training data but does not perform well on new data. This explains why a model might have high accuracy on the training data but low accuracy on the testing data. Overfit models experience high variance.
- **Underfitting**: Occurs when a model does not identify the relationships in the training data, leading to low accuracy on both the training and testing data. Underfit models experience high bias.

Overfitting occurs when the model is overly complex and captures noise or random fluctuations in the training data rather than the underlying patterns.

## Data Splits in Model Development
- **Training set**: Used for training the model.
- **Validation set**: Used for tuning hyperparameters and model selection.
- **Test set**: Used for evaluating the final model performance.

It is possible to increase both bias and variance, but this typically leads to a model that performs poorly due to both underfitting and overfitting.

## Amazon SageMaker Asynchronous Inference
Amazon SageMaker Asynchronous Inference is a capability in SageMaker that queues incoming requests and processes them asynchronously. This option is ideal for requests with large payload sizes (up to 1GB), long processing times (up to one hour), and near real-time latency requirements.

Improving model interpretability and transparency may sometimes involve trade-offs with model performance, as simpler models are often easier to interpret but may not achieve the highest performance.

## Hijacking
Hijacking involves manipulating an AI system to serve malicious purposes or to misbehave in unintended ways.

## Jailbreaking
Jailbreaking refers to bypassing the built-in restrictions and safety measures of AI systems to unlock restricted functionalities or generate prohibited content.

## Real-Time Inference vs. Batch Inference
Real-time inference is used for applications requiring immediate predictions with low latency, whereas batch inference is used for processing large volumes of data at once, often with higher latency. Real-time inference follows a synchronous execution mode, whereas batch inference follows an asynchronous execution mode.

## Deep Learning vs. Traditional Machine Learning
Deep learning is a subset of machine learning that uses neural networks with many layers to learn from large amounts of data, while traditional machine learning algorithms often require feature extraction and can use various methods such as decision trees or support vector machines.  

In traditional machine learning, a data scientist manually determines the set of relevant features that the software must analyze, whereas, in deep learning, the data scientist gives only raw data to the software and the deep learning network derives the features by itself.

## Threat Detection vs. Vulnerability Management
Threat detection services, such as **Amazon GuardDuty**, continuously monitor the environment to identify active threats and malicious activities in real time, providing alerts and insights to respond promptly. Vulnerability management, on the other hand, focuses on proactively identifying, assessing, and mitigating security vulnerabilities before they can be exploited. This involves regular scanning, patch management, and implementing security best practices.

## Diffusion Models
Diffusion models work by first corrupting data with noise through a forward diffusion process and then learning to reverse this process to denoise the data. They use neural networks to predict and remove the noise step by step, ultimately generating new, structured data from random noise.

## Classification Metrics: Precision, Recall, and F1-Score

- **Precision**: Measures the accuracy of the positive predictions, calculated as the ratio of true positives to the sum of true positives and false positives.  

- **Recall (Sensitivity)**: Measures the ability of the classifier to identify all positive instances, calculated as the ratio of true positives to the sum of true positives and false negatives.  

- **F1-Score**: The harmonic mean of Precision and Recall, providing a single metric that balances both concerns.

## Regression Metrics
- **Mean Absolute Error (MAE)**  
- **Root Mean Squared Error (RMSE)**  
- **R-squared**  

These are metrics used to evaluate regression models, not classification systems.

## System Performance Metrics
- **Throughput**  
- **Latency**  
- **Uptime**  

These metrics are used to measure system performance and reliability, not specific to classification systems.

## Benchmark Datasets for Bias Evaluation
Benchmark datasets are the most suitable option for evaluating an LLM for bias and discrimination with the least administrative effort. These datasets are specifically designed and curated to include a variety of scenarios that test for potential biases in model outputs.

## Amazon Q Business Guardrails
Amazon Q Business guardrails support topic-specific controls to determine the web application environment's behavior when it encounters a mention of a blocked topic by an end-user.

## Instruction-Based Fine-Tuning
Instruction-based fine-tuning improves the performance of a pre-trained foundation model (FM) on domain-specific tasks. Instruction-based fine-tuning uses labeled examples that are formatted as prompt-response pairs and that are phrased as instructions.

## Hyperparameter Tuning
Hyperparameter tuning is a method to adjust the behaviour of an ML algorithm. You can make changes to an ML model by using hyperparameter tuning to modify the behaviour of the algorithm.

## Model Evaluation
Model evaluation is a step in the ML development pipeline after model training. It can be used to evaluate a model's performance and metrics. Model evaluation does not increase the number of variables in the training dataset or modify the algorithm's behaviour.

## Feature Engineering
Feature engineering is a method for selecting and transforming variables when creating a predictive model. It includes feature creation, transformation, extraction, and selection. Feature engineering enhances the data by increasing the number of variables in the training dataset to improve model performance ultimately.

## SageMaker Model Cards
SageMaker Model Cards create records and document details about ML models in a single place. SageMaker Model Cards support transparent and explainable model development by providing comprehensive, immutable documentation of essential model information.

## SageMaker Model Dashboard
SageMaker Model Dashboard is a central place to view, search, and explore all models in an AWS account. It provides insights into model deployment, usage, performance tracking, and monitoring. However, you **cannot** use it to create a record of essential model information, such as risk ratings, training details, and evaluation results.

## SageMaker Role Manager
SageMaker Role Manager defines user permissions for ML activities. You **cannot** use SageMaker Role Manager to create a record of essential model information.

## SageMaker Model Monitor
SageMaker Model Monitor monitors the quality of ML models and data in production. You **cannot** use SageMaker Model Monitor to create a record of essential model information such as risk ratings, training details, and evaluation results.

## Constituents of a Good Prompting Technique
1. **Instructions** – a task for the model to do (description, how the model should perform)  
2. **Context** – external information to guide the model  
3. **Input Data** – the input for which you want a response  
4. **Output Indicator** – the output type or format  

## Model Invocation Logging
The company should enable model invocation logging, which allows for detailed logging of all requests and responses during model invocations in Amazon Bedrock.

## Amazon Personalize
Amazon Personalize is a fully managed machine learning (ML) service that uses your data to generate product and content recommendations for your users. You provide data about your end-users (e.g., age, location, device type), items in your catalogue (e.g., genre, price), and interactions between users and items (e.g., clicks, purchases).

## Decision Trees
Decision Trees are highly interpretable models that provide a clear and straightforward visualization of the decision-making process. Decision Trees work by splitting the data into subsets based on the most significant features, resulting in a tree-like structure where each branch represents a decision rule.

## Logistic Regression
Logistic Regression is primarily designed for binary classification problems. While it can be adapted for multiclass classification, it may not perform effectively with a large number of categories or a complex dataset like a massive movie database.

## AWS DeepRacer
AWS DeepRacer is the fastest way to get rolling with reinforcement learning (RL), literally, with a fully autonomous 1/18th scale race car driven by reinforcement learning, a 3D racing simulator, and a global racing league. Developers can train, evaluate, and tune RL models in the online simulator, and deploy their models onto AWS DeepRacer. The AWS DeepRacer vehicle is a Wi-Fi-enabled, physical vehicle that can drive itself on a physical track.

## Context Window
Context window determines the amount of text or information the model can consider at once while generating a response, typically measured in tokens rather than characters.

## Provisioned Throughput for Amazon Bedrock
For testing and deploying customized models for Amazon Bedrock (via fine-tuning or continued pre-training), it is mandatory to use **Provisioned Throughput**. The company should use Provisioned Throughput mode, which allows the company to reserve a specific amount of capacity in advance.

## Transformer Models
Transformer models are a type of neural network architecture designed to handle sequential data, such as language, in an efficient and scalable way. They rely on a mechanism called self-attention to process input data, allowing them to understand and generate language effectively. Self-attention allows the model to weigh the importance of different words in a sentence when encoding a particular word.

## Transfer Learning
The company should use **transfer learning**, a method where a model pre-trained on one task is adapted to improve performance on a different but related task by leveraging knowledge from the original task.

## Reinforcement Learning
Reinforcement learning involves an agent interacting with an environment by taking actions and receiving rewards or penalties, learning a policy to maximize cumulative rewards over time.

## Negative Prompting
Negative prompting refers to guiding a generative AI model to avoid certain outputs or behaviours when generating content.

## Few-Shot Prompting
In few-shot prompting, you provide a few examples of a task to the model to guide its output.

## Chain-of-Thought Prompting
Chain-of-thought prompting is a technique that breaks down a complex question into smaller, logical parts that mimic a train of thought. This helps the model solve problems in a series of intermediate steps rather than directly answering the question.

## Zero-Shot Prompting
Zero-shot prompting is a technique used in generative AI where the model is asked to perform a task or generate content without having seen any examples of that specific task during training. Instead, the model relies on its general understanding and knowledge to respond.

## Dynamic Prompt Engineering
Dynamic prompt engineering involves modifying the input prompts to the Large Language Model (LLM) to customize the chatbot's responses based on the user’s age. By altering the prompt dynamically, you can provide specific instructions or context to the LLM to generate age-appropriate responses.

## Continued Pre-Training vs Fine-Tuning
Continued pre-training uses unlabeled data to pre-train a model, whereas fine-tuning uses labelled data to train a model.

## Agents for Amazon Bedrock
Agents for Amazon Bedrock are fully managed capabilities that make it easier for developers to create generative AI-based applications that can complete complex tasks for a wide range of use cases and deliver up-to-date answers based on proprietary knowledge sources.

The company should use **Domain Adaptation Fine-Tuning**, which involves fine-tuning the model on domain-specific data to adapt its knowledge to that particular domain.  

The company should also use **Continued Pre-Training**, which involves further training the model on a large corpus of domain-specific data, enhancing its ability to understand domain-specific terms, jargon, and context.

## Increasing the Number of Epochs
Increasing the number of epochs allows the model to learn from the training data for a longer period, potentially capturing more complex patterns and relationships, which can improve accuracy. Multiple epochs are run until the accuracy of the model reaches an acceptable level, or when the error rate drops below an acceptable level.

## Amazon Kendra
Amazon Kendra is a highly accurate and easy-to-use enterprise search service that’s powered by ML. It allows developers to add search capabilities to their applications so their end users can discover information stored within the vast amount of content spread across their company.

## Hyperparameters for Model Tuning
The company should use **hyperparameters for model tuning**, which involves adjusting parameters such as regularization, learning rates, and dropout rates to enhance the model’s ability to generalize well to new data.

- Each AWS Region consists of a minimum of three Availability Zones (AZ).  
- Each Availability Zone (AZ) consists of one or more discrete data centres.

## Data Augmentation
Data augmentation is a technique used primarily in machine learning to artificially increase the size and variability of the training dataset by creating modified versions of the existing data (e.g., flipping images or adding noise). It is **not** related to the tasks of calculating statistics or visualizing data, which are part of Exploratory Data Analysis (EDA).

## Exploratory Data Analysis (EDA)
The company is in the **Exploratory Data Analysis (EDA)** phase, which involves examining the data through statistical summaries and visualizations to identify patterns, detect anomalies, and form hypotheses. This phase is crucial for understanding the dataset’s structure and characteristics, making it the most appropriate description of the current activities.

## Labelled vs. Unlabeled Data
Labelled data is annotated with output labels that provide specific information about each data point and is used for supervised learning. Unlabeled data lacks such annotations and is used for unsupervised learning.

## Amazon OpenSearch Service
The company should use **Amazon OpenSearch Service**, which is designed to provide fast search capabilities and supports full-text search, indexing, and similarity scoring.

## Foundation Models (FMs)
FMs use self-supervised learning to create labels from input data. However, fine-tuning an FM is a supervised learning process.

## Tokens
Tokens represent the fundamental units of text that the AI model processes. Tokens can be whole words, parts of words (sub-words), or even single characters, depending on the model’s tokenization strategy. In generative AI, the model breaks down text into these tokens to better understand the structure, meaning, and context, enabling it to generate coherent language outputs.

## Embeddings
Embeddings are **not** the correct answer to describe the fundamental units of text. They are a way of representing tokens (words, sub-words, or phrases) as numerical vectors to capture their semantic relationships in a high-dimensional space. While embeddings help the model understand the meaning and context of tokens, they are not the units of text themselves.

## Vectors
Vectors are mathematical constructs used to represent the relationships between different words or tokens in a model. While vectors are crucial for understanding how words are related in the embedding space, they do not directly represent the units of text (tokens) processed by the model.

## Sampling Bias
Sampling bias occurs when the data used to train the model does not accurately reflect the diversity of the real-world population. If certain ethnic groups are underrepresented or overrepresented in the training data, the model may learn biased patterns, causing it to flag individuals from those groups more frequently. In this scenario, sampling bias leads to discriminatory outcomes and unfairly targets specific groups based on ethnicity.

## Measurement Bias
Measurement bias is **not** the correct explanation for bias based on ethnicity in this context. It involves inaccuracies in data collection, such as faulty equipment or inconsistent measurement processes, rather than an imbalance in demographic composition.

## Observer Bias
Observer bias is irrelevant in this context because it relates to human errors or subjectivity during data analysis or observation. Since the AI model processes the data autonomously without human intervention, observer bias is not a factor in the biased outcomes of the model.

## Confirmation Bias
Confirmation bias involves selectively searching for or interpreting information to confirm existing beliefs. This type of bias does not apply to the AI system in this scenario, as there is no indication that the model is designed to reinforce any preconceptions or assumptions related to ethnicity.

## AWS Trainium
AWS Trainium is the machine learning (ML) chip that AWS purpose-built for deep learning (DL) training of 100B+ parameter models. Each Amazon Elastic Compute Cloud (Amazon EC2) Trn1 instance deploys up to 16 Trainium accelerators to deliver a high-performance, low-cost solution for DL training in the cloud.

## AWS Inferentia
AWS Inferentia is an ML chip purpose-built by AWS to deliver high-performance inference at a low cost. AWS Inferentia accelerators are designed by AWS to deliver high performance at the lowest cost in Amazon EC2 for your deep learning (DL) and generative AI inference applications.

## Amazon Forecast
Amazon Forecast is a fully managed service that uses statistical and machine learning algorithms to deliver highly accurate time-series forecasts. Based on the same technology used for time-series forecasting at Amazon.com, Forecast provides state-of-the-art algorithms to predict future time-series data based on historical data and requires no machine learning experience.

## Confusion Matrix
Confusion matrix is a tool specifically designed to evaluate the performance of classification models by displaying the number of true positives, true negatives, false positives, and false negatives.

## Mean Absolute Error (MAE)
Mean Absolute Error (MAE) measures the average magnitude of errors in a set of predictions without considering their direction. MAE is typically used in regression tasks to quantify the accuracy of a continuous variable's predictions, not for classification tasks where the outputs are categorical rather than continuous.

## Correlation Matrix
The correlation matrix measures the statistical correlation between different variables or features in a dataset, typically used to understand the relationships between continuous variables. A correlation matrix is not designed to evaluate the performance of a classification model, as it does not provide any insight into the accuracy or errors of categorical predictions.

## Plagiarism
Plagiarism involves presenting someone else's work, ideas, or creations as one's own without proper attribution. Detecting the use of generative AI tools to produce essays would help the committee identify instances where applicants might have submitted content that is not genuinely their own, thus maintaining the integrity of the admissions process.

## Hallucination
Hallucination refers to the creation of false information, which is not the main issue the admissions committee is dealing with. The committee is focused on detecting essays that are not genuinely authored by the applicants, not on the factual accuracy of the content itself.

## Bias in AI-Generated Outputs
Bias in AI-generated outputs would involve content that unfairly favours or discriminates against certain groups, which is not the same issue as ensuring that essays are the original work of the applicants.

## Misinterpretation
Misinterpretation occurs when the meaning or intent of a text is misunderstood or conveyed incorrectly. While misinterpretation might affect how an essay is read, it is not the core issue the admissions committee is focused on; their primary goal is to verify that the content is original and authored by the applicant.

## ROUGE (Recall-Oriented Understudy for Gisting Evaluation)
ROUGE measures how much overlap there is between the words or phrases in a computer-generated text and a human-written text.

### Simple Example
Imagine you and your friend both describe the same movie. If you both use similar words like "exciting," "thrilling," and "hero," ROUGE will give a high score because your descriptions overlap.

### Focus
- **Recall**: Did the computer-generated text include important words from the reference text?
- Mainly used for **summarization** tasks.

## BLEU (Bilingual Evaluation Understudy)
BLEU checks how similar a machine-generated sentence is to a human-written sentence by comparing small groups of words.

### Simple Example
Suppose you translate "The cat sits on the mat" into French, and your friend translates it too. BLEU will check how many words and word groups match between both translations.

### Focus
- **Precision**: How many words in the generated text are correct compared to the reference?
- Mainly used for **machine translation**.

## BERT (Bidirectional Encoder Representations from Transformers)
BERT is a smart AI model that understands the meaning of words in context by reading entire sentences at once (both forward and backward).

### Simple Example
Think of the word "bank." BERT can tell if you're talking about a riverbank or a money bank by looking at the other words around it.

### Focus
- Understands the **context** and **meaning** of words.
- Used for many tasks: text classification, question answering, and more.

## Amazon SageMaker GroundTruth Plus
Provides a fully managed data labeling service that helps deliver high-quality annotations. It uses a combination of human labelers and machine learning-assisted labeling to ensure accuracy and consistency in the labels.

The company should **instruct the model to stick to the prompt** by adding explicit instructions to ignore any unrelated or potentially malicious content.

## Amazon SageMaker Studio
Offers a broad set of fully managed integrated development environments (IDEs) for ML development, including:
- JupyterLab
- Code Editor based on Code-OSS (Visual Studio Code – Open Source)
- RStudio

## Amazon SageMaker Automatic Model Tuning
Can automatically choose:
- Hyperparameter ranges
- Search strategy
- Maximum runtime of a tuning job
- Early stopping type for training jobs
- Number of times to retry a training job
- Model convergence flag to stop a tuning job

These choices are based on the objective metric you provide.

## Leverage Amazon Bedrock
Make a separate copy of the base FM model and train this **private copy** of the model using the labeled training dataset.

## Maintaining Data Lineage
Involves tracking the flow, transformations, and origins of data throughout its lifecycle. This is crucial for ensuring data privacy, security, and compliance with regulatory standards.

## Amazon S3 for Model Validation Datasets
Amazon S3 is the recommended storage solution for datasets used in model validation when working with Amazon Bedrock. It provides:
- Highly scalable and durable storage
- Native integration with Amazon Bedrock
- Supports a wide range of data formats
- Seamless access from various AWS services

## Large Language Models (LLMs) Are Non-Deterministic
This means the generated text may be different each time, even if the same prompt is used. 
