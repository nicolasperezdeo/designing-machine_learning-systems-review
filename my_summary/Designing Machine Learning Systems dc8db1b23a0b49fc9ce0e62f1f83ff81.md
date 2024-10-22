# Designing Machine Learning Systems

Personal Notes of Chip Huyen book

# Book Resources

- Discord Server:
- Gtihub Repository:

# Notes to myself

- At TeleMedC we could use ML for different applications besides generating predictions from eye imaging. Specifically, we should also think about using ML in internal processes such as:
    - Generating customer insights
    - Reducing costs
    - Acquiring new customers
    - Improving customer experience e.g. chatbot for teleeyeMD, automated support ticket classification.
    - Increasing customer loyalty
    - Price optimization. Most beneficial when we have a large number of transactions.
    - Ad targeting.
    - Brand Monitoring

### Tips and questions for Job Search

- Add to LinkedIn that I also have experience deploying and maintaining models (not only developing).
- For job interviews, prepare an example of how I automated the process of developing, evaluating, deploying, and updating models, which was previously done manually. This will demonstrate my ability to streamline ML workflows.
- What measures did I take in order to make my models at TeleMedC interpretable and explainable?

---

# Chapter 1: Overview of Machine Learning Systems

> ML systems are complex since they involve many different stakeholders: data scientists, ML engineers, business leaders, users and even society at large.
> 

![Untitled](Designing%20Machine%20Learning%20Systems%20dc8db1b23a0b49fc9ce0e62f1f83ff81/Untitled.png)

> Even for problems that ML can solve, ML solutions might not be the optimal solution.
> 

Definition of ML solutions:

<aside>
💭

> Machine learning is an approach to **learn** **complex patterns** from **existing data** and use these patterns to **make predictions** on **unseen data**.
> 
</aside>

“*ML is suitable if the cost of wrong predictions is cheap”* 

> **If one prediction mistake can have catastrophic consequences, ML might still be a suitable solution if, on average, the benefits of correct predictions outweigh the cost of wrong predictions.** Developing self-driving cars is challenging because an algorithmic mistake can lead to death. However, many companies still want to develop self-driving cars because they have the potential to save many lives once self-driving cars are statistically safer than human drivers.
> 

### When not to use ML?

- Unethical
- A simpler solution does the trick.
- It’s not cost-effective.

However, if ML can't solve your entire problem, it might be possible to break it into smaller components and use ML to solve some of them. For example, with a chatbot to answer customer queries, it's possible to create an ML model to match queries to one of the FAQs. If there's a match, direct the customer to the answer; if not, connect them to customer service.

> A set of ML use cases that has generated much excitement recently is in health care. There are ML systems that can detect skin cancer and diagnose diabetes. Even though many healthcare applications are geared toward consumers, because of their strict requirements for accuracy and privacy, they are usually provided through a healthcare provider such as a hospital or used to assist doctors in providing diagnoses.
> 

### Machine Learning Use Cases

Examples of use cases in corporations:

- **Reducing Costs:** Optimizing supply chain management to minimize inventory costs and reduce waste.
- **Generating customer insights/intelligence:** Analyzing customer purchase history and browsing behavior to identify trends and preferences.
- **Improving Customer experience:** Implementing a personalized recommendation system for an e-commerce platform.
- **Internal Processing Automation:** Automating document classification and routing in a large organization.
- **Interacting with customers:** Developing an AI-powered chatbot for customer support.
- **Retaining customers:** Predicting customer churn risk and implementing targeted retention strategies.
- **Recommender systems:** Suggesting relevant content to users on a streaming platform based on their viewing history.
- **Detecting Fraud:** Identifying unusual patterns in financial transactions to flag potential fraudulent activities.
- **Predicting demand fluctuations:** Forecasting product demand based on historical data, seasonality, and external factors.
- **Reducing customer churn:** Identifying at-risk customers and implementing personalized retention campaigns.

### Ml in Research vs in Production

5 Main differences between them:

![Untitled](Designing%20Machine%20Learning%20Systems%20dc8db1b23a0b49fc9ce0e62f1f83ff81/Untitled%201.png)

![Untitled](Designing%20Machine%20Learning%20Systems%20dc8db1b23a0b49fc9ce0e62f1f83ff81/Untitled%202.png)

**Computational Priorities**

> People who haven’t deployed an ML system often make the mistake of focusing too much on the model development part and not enough on the model deployment and maintenance part.
> 

If your system processes one query at a time, higher latency means lower throughput. 

| Avg. Latency | Throughput |
| --- | --- |
| 10 ms | 100 queries/sec |
| 100 ms | 10 queries/sec |

![Untitled](Designing%20Machine%20Learning%20Systems%20dc8db1b23a0b49fc9ce0e62f1f83ff81/Untitled%203.png)

> When thinking about latency, it’s important to keep in mind that latency is not an individual number but a distribution.
> 

# Chapter 2: Introduction to ML Systems Design

Four requirements are considered for ML systems:

1. Reliability
2. Scalability
3. Adaptability
4. Maintainability

## Business and ML objectives

> Many Data Scientists become too focused on hacking ML metrics without paying attention to business metrics.
> 

Understanding business contexts for ML engineers [article](https://eugeneyan.com/writing/project-quick-start/).

Before we develop an ML system, we must understand why this system is needed. If the system is built for business, we need to translate business objectives into ML objectives. The key requirements for ML systems are:

1. Reliability
2. Scalability
3. Maintainability
4. Adaptability

Before building, we need to frame the problem into a task that ML can solve.

### Business and ML Objectives

For an ML project to succeed within a business organization, it's crucial to tie the performance of an ML system to the overall business performance. Two examples illustrate this connection:

1. Predicting ad click-through rate: An increase in accuracy results in increased ad revenue.
2. Fraud detection: Every fraudulent transaction stopped results in money saved.

To gain a definitive answer on how ML metrics influence business metrics, experiments are often needed. For example, A/B testing can be used to measure the impact of ML improvements on business outcomes.

### Key Requirements for ML Systems

**Reliability:** Correct functionality at the desired level of performance. This can be hard to detect and measure in ML systems.

**Scalability:** As the system grows, it should be able to handle that growth in a reasonable way. An indispensable feature is autoscaling, which automatically adjusts the number of resources depending on usage.

**Maintainability:** It's important to structure your models and set up your infrastructure in such a way that different contributors can work using tools they are comfortable with. Code should be documented, and code, data, and artifacts should be versioned.

**Adaptability:** The system should be able to adapt to shifting data distributions and business requirements. It should have some capacity for both discovering aspects for performance improvement and allowing updates without service interruption.

### 6 Steps in ML System Design

1. Project objectives and constraints: Define stakeholders, resources, and goals.
2. Data engineering: Collect, process, and prepare data for model development.
3. Model development: Create, train, and evaluate ML models.
4. Deployment: Implement the model in a production environment.
5. Monitoring and continual learning: Track performance and update the model as needed.
6. Business analysis: Evaluate the impact of the ML system on business metrics.