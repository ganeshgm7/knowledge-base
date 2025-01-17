**AWS Certified AI Practitioner Study Notes**

The three main types of machine learning are **supervised learning, unsupervised learning, and deep learning.**

**Supervised learning** 

*   Logistic regression 
    
*   Linear regression 
    
*   Decision tree
    
*   Neural network 
    

**Semi-supervised learning** 

*   Document classification 
    
*   Sentiment analysis 
    

**Unsupervised learning** 

*   Association rule learning 
    
*   Clustering 
    
*   Dimensity reduction 
    

How can you prevent model overfitting in machine learning?

**By using techniques such as cross-validation, regularization, and pruning to simplify the model and improve its generalization.**

**Interpretability** is about understanding the internal mechanisms of a machine learning model, whereas explainability focuses on providing understandable reasons for the model's predictions and behaviours to stakeholders

**Amazon SageMaker Feature Store** is a fully managed, purpose-built repository to store, share, and manage features for machine learning (ML) models. Features are inputs to ML models used during training and inference. For example, in an application that recommends a music playlist, features could include song ratings, listening duration, and listener demographics.

**Amazon SageMaker Clarify** - SageMaker Clarify helps identify potential bias during data preparation without writing code. You specify input features, such as gender or age, and SageMaker Clarify runs an analysis job to detect potential bias in those features.

**Amazon SageMaker Data Wrangler** - Amazon SageMaker Data Wrangler reduces the time it takes to aggregate and prepare tabular and image data for ML from weeks to minutes. With SageMaker Data Wrangler, you can simplify the process of data preparation and feature engineering, and complete each step of the data preparation workflow (including data selection, cleansing, exploration, visualization, and processing at scale) from a single visual interface.

**Amazon SageMaker Ground Truth**

**Purpose**: Used for labelling training data (e.g., images, text) to build machine learning models.

**Human Review**: Allows humans to label or correct unlabelled data for training models.

**When to use**: When you need high-quality labelled data to train a model.

**Amazon Augmented AI (A2I):**

**Purpose**: Used for adding a human review to model predictions after deployment.

**Human Review**: Allows humans to review and correct predictions made by your model.

**When to use**: When you want to verify or audit model predictions before taking action.

**Temperatur** \- LLMs on Amazon Bedrock come with several inference parameters that you can set to control the response from the models. Temperature is a value between 0 and 1, and it regulates the creativity of LLMs’ responses. Use a lower temperature if you want more deterministic responses, and use a higher temperature if you want creative or different responses for the same prompt from LLMs on Amazon Bedrock.

**Top P** represents the percentage of most likely candidates that the model considers for the next token.

**Top K** represents the number of most likely candidates that the model considers for the next token.

**Stop sequences** specify the sequences of characters that stop the model from generating further tokens. If the model generates a stop sequence that you specify, it will stop generating after that sequence.

**Response length** represents the minimum or maximum number of tokens to return in the generated response.

**Amazon Connect** is the contact centre service from AWS. Amazon Q helps customer service agents provide better customer service. Amazon Q in Connect uses real-time conversation with the customer along with relevant company content to automatically recommend what to say or what actions an agent should take to better assist customers.

Model training in deep learning involves using large datasets to adjust the weights and biases of a neural network through multiple iterations, using techniques such as gradient descent to minimize the error.

Model parameters are values that define a model and its behaviour in interpreting input and generating responses. Hyperparameters are values that can be adjusted for model customization to control the training process.

**Amazon Inspector** \- is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS. It automatically assesses applications for exposure, vulnerabilities, and deviations from best practices, making it an essential tool for ensuring the security of AI systems.

**AWS Config** is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. While it is important for governance and compliance monitoring, it does not perform automated security assessments of applications.

**AWS Audit Manager** helps you continuously audit your AWS usage to simplify how you assess risk and compliance with regulations and industry standards. It focuses on audit and compliance reporting rather than automated security assessments.

**AWS Artifact** provides on-demand access to AWS compliance reports and online agreements. It helps with compliance reporting but does not offer automated security assessments of applications.

**AWS Trusted Advisor** offers guidance to help optimize your AWS environment for cost savings, performance, security, and fault tolerance. While it provides recommendations for best practices, it does not focus on auditing or evidence collection for compliance.

**AWS CloudTrail** records AWS API calls for auditing purposes and delivers log files for compliance and operational troubleshooting. It is crucial for tracking user activity but does not automate compliance assessments or evidence collection.

**Agility** refers to the ability of the cloud to give you easy access to a broad range of technologies so that you can innovate faster and build nearly anything that you can imagine. You can quickly spin up resources as you need them – from infrastructure services, such as computing, storage, and databases, to the Internet of Things, machine learning, data lakes and analytics, and much more.

**Elasticity** \- With cloud computing elasticity, you don’t have to over-provision resources upfront to handle peak levels of business activity in the future. Instead, you provision the number of resources that you need. You can scale these resources up or down instantly to grow and shrink capacity as your business needs change.

**Cost savings** - The cloud allows you to trade capital expenses (such as data centres and physical servers) for variable expenses, and only pay for IT as you consume it. Plus, the variable expenses are much lower than what you would pay to do it yourself because of the economies of scale.

**Ability to deploy globally in minutes** - With the cloud, you can expand to new geographic regions and deploy globally in minutes. For example, AWS has infrastructure all over the world, so you can deploy your application in multiple physical locations with just a few clicks. Putting applications in closer proximity to end users reduces latency and improves their experience.

*   Benefit from massive economies of scale. Trade capital expense for variable expense.
    
*   Go global in minutes and deploy applications in multiple regions around the world with just a few clicks.
    

**FM is an AI model** with a large number of parameters and trained on a massive amount of diverse data, whereas, model customization is the process of using training data to adjust the model parameter values in a base model to create a custom model.

**K-Means** is an unsupervised learning algorithm used for clustering data points into groups, while KNN is a supervised learning algorithm used for classifying data points based on their proximity to labelled examples.

**Human model evaluation** is valuable for assessing qualitative aspects of the model, whereas, **automatic model valuation** is valuable for assessing quantitative aspects of the model. Automatic model evaluation provides model scores that are calculated using various statistical methods such as BERT Score and F1.

**Reinforcement learning from human feedback (RLHF)** is a machine learning (ML) technique that uses human feedback to optimize ML models to self-learn more efficiently. Reinforcement learning (RL) techniques train software to make decisions that maximize rewards, making their outcomes more accurate.

**Average response time** measures how long it takes for the model to process input data and generate a prediction. It directly reflects the model's runtime efficiency, which is crucial in scenarios where timely decisions need to be made, such as real-time stock market predictions. A lower average response time indicates better runtime efficiency, ensuring that predictions are delivered quickly enough to be actionable.

**Model Accuracy** - While model accuracy is essential for assessing how well the model's predictions match the actual outcomes, it is not a measure of runtime efficiency. Accuracy evaluates the correctness of the model’s predictions but does not reflect how quickly those predictions are generated. 

**Data Throughput** measures the amount of data a system can process in a given time. While this can be related to the overall system performance, it does not directly assess the model's runtime efficiency in terms of how quickly it generates predictions. Average response time is a more appropriate metric for measuring runtime efficiency, particularly in real-time prediction scenarios.

The machine learning process typically follows these steps, **Data collection, Data preprocessing, Model training, and Model evaluation**.

**Convolutional Neural Networks (CNNs)** are specifically designed for processing and classifying image data. They use convolutional layers to automatically and adaptively learn spatial hierarchies of features from input images, making them highly effective for tasks such as image recognition and classification.

**Recurrent Neural Networks (RNNs)** are typically used for sequence data, such as time series or natural language processing tasks. 

**Generative Adversarial Networks (GANs)** are used for creating realistic synthetic data while preserving the statistical properties of the original data

**AWS AI service cards** are designed to offer transparency and provide users with crucial information about the intended use, limitations, and potential impacts of AWS AI services. This helps users make informed decisions and implement Responsible AI practices by understanding the implications of using these services.

**Overfitting** is when a model learns from the training data but is unable to perform well when given new data. Overfitting explains why the model has high accuracy on the training data but has low accuracy on the testing data.

**Underfitting** occurs when a model does not identify the relationships in the training data. Underfitting would lead to low accuracy on both the training data and the testing data.

**Underfit models experience high bias, whereas, overfit models experience high variance.**

Overfitting occurs when the model is overly complex and captures noise or random fluctuations in the training data rather than the underlying patterns.

The training set is used for training the model, the validation set is used for tuning hyperparameters and model selection, and the test set is used for evaluating the final model performance.

It is possible to increase both bias and variance, but this typically leads to a model that performs poorly due to both underfitting and overfitting

**Amazon SageMaker Asynchronous Inference** is a capability in SageMaker that queues incoming requests and processes them asynchronously. This option is ideal for requests with large payload sizes (up to 1GB), long processing times (up to one hour), and near real-time latency requirements.

Improving model interpretability and transparency may sometimes involve trade-offs with model performance, as simpler models are often easier to interpret but may not achieve the highest performance

**Hijacking** involves manipulating an AI system to serve malicious purposes or to misbehave in unintended ways.

**Jailbreaking** refers to bypassing the built-in restrictions and safety measures of AI systems to unlock restricted functionalities or generate prohibited content.

**Real-time inference** is used for applications requiring immediate predictions with low latency, whereas batch inference is used for processing large volumes of data at once, often with higher latency. Real-time inference follows a synchronous execution mode, whereas batch inference follows an asynchronous execution mode

**Deep learning** is a subset of machine learning that uses neural networks with many layers to learn from large amounts of data, while traditional machine learning algorithms often require feature extraction and can use various methods such as decision trees or support vector machines

In traditional machine learning, a data scientist manually determines the set of relevant features that the software must analyze, whereas, in deep learning, the data scientist gives only raw data to the software and the deep learning network derives the features by itself.

Threat detection services, such as **Amazon GuardDuty**, continuously monitor the environment to identify active threats and malicious activities in real-time, providing alerts and insights to respond promptly. Vulnerability management, on the other hand, focuses on proactively identifying, assessing, and mitigating security vulnerabilities before they can be exploited. This involves regular scanning, patch management, and implementing security best practices.

**Diffusion models** work by first corrupting data with noise through a forward diffusion process and then learning to reverse this process to denoise the data. They use neural networks to predict and remove the noise step by step, ultimately generating new, structured data from random noise.

**Precision, Recall, and F1-Score are standard performance metrics used to evaluate the effectiveness of a classification system:**

**Precision**: Measures the accuracy of the positive predictions, calculated as the ratio of true positives to the sum of true positives and false positives.

**Recall** (Sensitivity): Measures the ability of the classifier to identify all positive instances, calculated as the ratio of true positives to the sum of true positives and false negatives.

**F1-Score:** The harmonic mean of Precision and Recall, providing a single metric that balances both concerns.

**Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE) R-squared** are metrics used to evaluate regression models, not classification systems.

**Throughput, Latency, and Uptime** are performance metrics used to measure system performance and reliability, not specific to classification systems.

**Benchmark datasets** are the most suitable option for evaluating an LLM for bias and discrimination with the least administrative effort. These datasets are specifically designed and curated to include a variety of scenarios that test for potential biases in model outputs. 

**Amazon Q Business guardrails** support topic-specific controls to determine the web application environment's behaviour when it encounters a mention of a blocked topic by an end-user

**Instruction-based fine-tuning** improves the performance of a pre-trained foundation model (FM) on domain-specific tasks. Instruction-based fine-tuning uses labelled examples that are formatted as prompt-response pairs and that are phrased as instructions.

**Hyperparameter tuning** is a method to adjust the behaviour of an ML algorithm. You can make changes to an ML model by using hyperparameter tuning to modify the behaviour of the algorithm.

**Model evaluation** is a step in the ML development pipeline after model training. It can be used to evaluate a model's performance and metrics. Model evaluation does not increase the number of variables in the training dataset or modify the algorithm's behaviour.

**Feature engineering** is a method for selecting and transforming variables when creating a predictive model. It includes feature creation, transformation, extraction, and selection. Feature engineering enhances the data by increasing the number of variables in the training dataset to improve model performance ultimately.

**SageMaker Model Cards** to create records and document details about ML models in a single place. SageMaker Model Cards support transparent and explainable model development by providing comprehensive, immutable documentation of essential model information.

**SageMaker Model Dashboard** is a central place to view, search, and explore all models in an AWS account. It provides insights into model deployment, usage, performance tracking, and monitoring. However, you cannot use It to create a record of essential model information, such as risk ratings, training details, and evaluation results.

**SageMaker Role Manager** to define user permissions for ML activities. You cannot use SageMaker Role Manager to create a record of essential model information.

**SageMaker Model Monitor** monitors the quality of ML models and data in production. You cannot use SageMaker Model Monitor to create a record of essential model information such as risk ratings, training details, and evaluation results.

**The following are the constituents of a good prompting technique:** 

• **Instructions** – a task for the model to do (description, how the model should perform) 

• **Context** – external information to guide the model 

• **Input data** – the input for which you want a response

• **Output Indicator** – the output type or format

**The company should enable model invocation logging, which allows for detailed logging of all requests and responses during model invocations in Amazon Bedrock**

**Amazon Personalize** is a fully managed machine learning (ML) service that uses your data to generate product and content recommendations for your users. You provide data about your end-users (e.g., age, location, device type), items in your catalogue (e.g., genre, price), and interactions between users and items (e.g., clicks, purchases).

**Decision Trees** are highly interpretable models that provide a clear and straightforward visualization of the decision-making process. Decision Trees work by splitting the data into subsets based on the most significant features, resulting in a tree-like structure where each branch represents a decision rule. 

**Logistic Regression** is primarily designed for binary classification problems. While it can be adapted for multiclass classification, it may not perform effectively with a large number of categories or a complex dataset like a massive movie database.

**AWS DeepRacer** is the fastest way to get rolling with reinforcement learning (RL), literally, with a fully autonomous 1/18th scale race car driven by reinforcement learning, a 3D racing simulator, and a global racing league. Developers can train, evaluate, and tune RL models in the online simulator, and deploy their models onto AWS DeepRacer. The AWS DeepRacer vehicle is a Wi-Fi-enabled, physical vehicle that can drive itself on a physical track

**Context window** determines the amount of text or information the model can consider at once while generating a response, typically measured in tokens rather than characters

**For testing and deploying customized models for Amazon Bedrock** (via fine-tuning or continued pre-training), it is mandatory to use **Provisioned Throughput**. The company should use Provisioned Throughput mode, which allows the company to reserve a specific amount of capacity in advance.

**Transformer models** are a type of neural network architecture designed to handle sequential data, such as language, in an efficient and scalable way. They rely on a mechanism called self-attention to process input data, allowing them to understand and generate language effectively. Self-attention allows the model to weigh the importance of different words in a sentence when encoding a particular word. 

The company should use **transfer learning**, a method where a model pre-trained on one task is adapted to improve performance on a different but related task by leveraging knowledge from the original task

**Reinforcement learning** involves an agent interacting with an environment by taking actions and receiving rewards or penalties, learning a policy to maximize cumulative rewards over time

**Negative prompting** refers to guiding a generative AI model to avoid certain outputs or behaviours when generating content. In the context of AWS generative 

**Few-shot prompting**, you provide a few examples of a task to the model to guide its output.

**Chain-of-thought prompting** is a technique that breaks down a complex question into smaller, logical parts that mimic a train of thought. This helps the model solve problems in a series of intermediate steps rather than directly answering the question.

**Zero-shot prompting** is a technique used in generative AI where the model is asked to perform a task or generate content without having seen any examples of that specific task during training. Instead, the model relies on its general understanding and knowledge to respond.

**Dynamic prompt engineering** involves modifying the input prompts to the Large Language Model (LLM) to customize the chatbot's responses based on the user's age. By altering the prompt dynamically, you can provide specific instructions or context to the LLM to generate age-appropriate responses.

**Continued pre-training** uses unlabeled data to pre-train a model, whereas, fine-tuning uses labeled data to train a model

**Agents for Amazon Bedrock** are fully managed capabilities that make it easier for developers to create generative AI-based applications that can complete complex tasks for a wide range of use cases and deliver up-to-date answers based on proprietary knowledge sources.

The company should use **Domain Adaptation Fine-Tuning**, which involves fine-tuning the model on domain-specific data to adapt its knowledge to that particular domain. The company should use Continued Pre-Training, which involves further training the model on a large corpus of domain-specific data, enhancing its ability to understand domain-specific terms, jargon, and context

**Increasing the number of epochs** allows the model to learn from the training data for a longer period, potentially capturing more complex patterns and relationships, which can improve accuracy. Multiple epochs are run until the accuracy of the model reaches an acceptable level, or when the error rate drops below an acceptable level.

**Amazon Kendra** is a highly accurate and easy-to-use enterprise search service that’s powered by machine learning (ML). It allows developers to add search capabilities to their applications so their end users can discover information stored within the vast amount of content spread across their company. 

The company should use **hyperparameters for model tuning**, which involves adjusting parameters such as regularization, learning rates, and dropout rates to enhance the model's ability to generalize well to new data

*   Each AWS Region consists of a minimum of three Availability Zones (AZ)
    
*   Each Availability Zone (AZ) consists of one or more discrete data centres
    

**Data augmentation** is a technique used primarily in machine learning to artificially increase the size and variability of the training dataset by creating modified versions of the existing data, such as flipping images or adding noise. It is not related to the tasks of calculating statistics or visualizing data, which are part of EDA.

The company is in the **Exploratory Data Analysis (EDA)** phase, which involves examining the data through statistical summaries and visualizations to identify patterns, detect anomalies, and form hypotheses. This phase is crucial for understanding the dataset’s structure and characteristics, making it the most appropriate description of the current activities. 

Labelled data is annotated with output labels that provide specific information about each data point and is used for supervised learning, whereas, unlabeled data lacks such annotations and is used for unsupervised learning

The company should use **Amazon OpenSearch Service**, which is designed to provide fast search capabilities and supports full-text search, indexing, and similarity scoring

**FMs use self-supervised learning to create labels from input data, however, fine-tuning an FM is a supervised learning process.**

**Tokens** represent the fundamental units of text that the AI model processes. Tokens can be whole words, parts of words (sub-words), or even single characters, depending on the model’s tokenization strategy. In generative AI, the model breaks down text into these tokens to better understand the structure, meaning, and context, enabling it to generate coherent language outputs.

**Embeddings** are not the correct answer because they are a way of representing tokens (words, sub-words, or phrases) as numerical vectors to capture their semantic relationships in a high-dimensional space. Embeddings help the model understand the meaning and context of tokens, but they are not the units of text themselves.

**Vectors** are mathematical constructs used to represent the relationships between different words or tokens in a model. While vectors are crucial for understanding how words are related to each other in the embedding space, they do not directly represent the units of text (tokens) processed by the model.

**Sampling bias** occurs when the data used to train the model does not accurately reflect the diversity of the real-world population. If certain ethnic groups are underrepresented or overrepresented in the training data, the model may learn biased patterns, causing it to flag individuals from those groups more frequently. In this scenario, sampling bias leads to discriminatory outcomes and unfairly targets specific groups based on ethnicity.

**Measurement bias** is not the correct explanation because it involves inaccuracies in data collection, such as faulty equipment or inconsistent measurement processes. This type of bias does not inherently affect the demographic composition of the dataset and, therefore, is not directly responsible for bias based on ethnicity in the model's outputs.

**Observer bias** is irrelevant in this context because it relates to human errors or subjectivity during data analysis or observation. Since the AI model processes the data autonomously without human intervention, observer bias is not a factor in the biased outcomes of the model.

**Confirmation bias** involves selectively searching for or interpreting information to confirm existing beliefs. This type of bias does not apply to the AI system in this scenario, as there is no indication that the model is designed to reinforce any preconceptions or assumptions related to ethnicity.

**AWS Trainium** is the machine learning (ML) chip that AWS purpose-built for deep learning (DL) training of 100B+ parameter models. Each Amazon Elastic Compute Cloud (Amazon EC2) Trn1 instance deploys up to 16 Trainium accelerators to deliver a high-performance, low-cost solution for DL training in the cloud.

**AWS Inferentia** is an ML chip purpose-built by AWS to deliver high-performance inference at a low cost. AWS Inferentia accelerators are designed by AWS to deliver high performance at the lowest cost in Amazon EC2 for your deep learning (DL) and generative AI inference applications.

**Amazon Forecast** is a fully managed service that uses statistical and machine learning algorithms to deliver highly accurate time-series forecasts. Based on the same technology used for time-series forecasting at Amazon.com, Forecast provides state-of-the-art algorithms to predict future time-series data based on historical data and requires no machine learning experience.

**Confusion matrix** is a tool specifically designed to evaluate the performance of classification models by displaying the number of true positives, true negatives, false positives, and false negatives. 

**Mean Absolute Error (MAE)** measures the average magnitude of errors in a set of predictions without considering their direction. MAE is typically used in regression tasks to quantify the accuracy of a continuous variable's predictions, not for classification tasks where the outputs are categorical rather than continuous.

**The correlation matrix** measures the statistical correlation between different variables or features in a dataset, typically used to understand the relationships between continuous variables. A correlation matrix is not designed to evaluate the performance of a classification model, as it does not provide any insight into the accuracy or errors of categorical predictions.

**Plagiarism** involves presenting someone else's work, ideas, or creations as one's own without proper attribution. Detecting the use of generative AI tools to produce essays would help the committee identify instances where applicants might have submitted content that is not genuinely their own, thus maintaining the integrity of the admissions process

**Hallucination** refers to the creation of false information, which is not the main issue the admissions committee is dealing with. The committee is focused on detecting essays that are not genuinely authored by the applicants, not on the factual accuracy of the content itself.

**Bias** in AI-generated outputs would involve content that unfairly favours or discriminates against certain groups, which is not the same issue as ensuring that essays are the original work of the applicants.

**Misinterpretation** occurs when the meaning or intent of a text is misunderstood or conveyed incorrectly. While misinterpretation might affect how an essay is read, it is not the core issue the admissions committee is focused on; their primary goal is to verify that the content is original and authored by the applicant.

**ROUGE (Recall-Oriented Understudy for Gisting Evaluation)**

ROUGE measures how much overlap there is between the words or phrases in a computer-generated text and a human-written text.

**Simple Example:**

Imagine you and your friend both describe the same movie. If you both use similar words like "exciting," "thrilling," and "hero," ROUGE will give a high score because your descriptions overlap.

**Focus**:

*   Recall: Did the computer-generated text include important words from the reference text?
    
*   Mainly used for summarization tasks.
    

**BLEU (Bilingual Evaluation Understudy)**

BLEU checks how similar a machine-generated sentence is to a human-written sentence by comparing small groups of words.

**Simple Example:**

Suppose you translate "The cat sits on the mat" into French, and your friend translates it too. BLEU will check how many words and word groups match between both translations.

**Focus:**

*   Precision: How many words in the generated text are correct compared to the reference?
    
*   Mainly used for machine translation.
    

**BERT (Bidirectional Encoder Representations from Transformers)**

BERT is a smart AI model that understands the meaning of words in context by reading entire sentences at once (both forward and backwards).

**Simple Example:**

Think of the word "bank." BERT can tell if you're talking about a riverbank or a money bank by looking at the other words around it.

**Focus:**

*   Understands the context and meaning of words.
    
*   Used for many tasks: text classification, question answering, and more.
    

**Amazon SageMaker GroundTruth Plus** provides a fully managed data labelling service that helps deliver high-quality annotations. It uses a combination of human labellers and machine learning-assisted labelling to ensure accuracy and consistency in the labels. 

The company should instruct the model to stick to the prompt by adding explicit instructions to ignore any unrelated or potentially malicious content

**Amazon SageMaker Studio** offers a broad set of fully managed integrated development environments (IDEs) for ML development, including JupyterLab, Code Editor based on Code-OSS (Visual Studio Code – Open Source), and RStudio.

**Amazon SageMaker Automatic Model Tuning** can automatically choose hyperparameter ranges, search strategy, maximum runtime of a tuning job, early stopping type for training jobs, number of times to retry a training job, and model convergence flag to stop a tuning job, based on the objective metric you provide. 

**Leverage Amazon Bedrock to make a separate copy of the base FM model and train this private copy of the model using the labelled training dataset.**

**Maintaining data lineage** involves tracking the flow, transformations, and origins of data throughout its lifecycle. This is crucial for ensuring data privacy, security, and compliance with regulatory standards. 

**Amazon S3 is the recommended storage** solution for datasets used in model validation when working with Amazon Bedrock. S3 provides a highly scalable and durable storage platform, and it is natively integrated with Amazon Bedrock, allowing easy access to large datasets required for model customization, training, and validation tasks. It supports a wide range of data formats and allows seamless access from various AWS services.

**Large Language Models (LLMs) are non-deterministic**, which implies that the generated text may be different for every user that uses the same prompt.