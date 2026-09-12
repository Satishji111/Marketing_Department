# Marketing Department – Customer Segmentation

## Project Overview

This project uses **customer transaction and credit card usage data** to help a bank's marketing team understand different types of customers and design more targeted marketing campaigns.

The business case is based on a bank in **New York City** with customer data covering the previous six months. The marketing team wants to divide customers into distinct groups based on their financial and purchasing behaviour.

Instead of using the same marketing campaign for every customer, customer segmentation can help the bank identify groups with similar behaviour and target them with more relevant offers.

## Business Problem

The main challenge for the marketing team is to understand:

- Who the customers are
- How customers use their credit cards
- How frequently customers make purchases
- Which customers prefer one-off purchases or installment purchases
- Which customers rely more on cash advances
- Which customers have higher credit limits and spending potential
- Which customer groups may be suitable for different marketing strategies

The objective of this project is to use **unsupervised machine learning** to identify customer segments from their behaviour.

## Dataset

The project uses the **Credit Card Customer Data** dataset available on Kaggle.

**Data source:**  
https://www.kaggle.com/arjunbhasin2013/ccdata

The dataset contains customer-level credit card information such as balance, purchases, cash advances, credit limit and payment behaviour.

### Important Features

| Feature | Description |
|---|---|
| `CUST_ID` | Identification of the credit card holder |
| `BALANCE` | Balance amount available in the customer's account |
| `BALANCE_FREQUENCY` | Frequency with which the balance is updated |
| `PURCHASES` | Total amount of purchases |
| `ONEOFF_PURCHASES` | Maximum/total one-off purchase amount |
| `INSTALLMENTS_PURCHASES` | Amount spent through installment purchases |
| `CASH_ADVANCE` | Amount taken as cash advance |
| `PURCHASES_FREQUENCY` | Frequency of purchases |
| `ONEOFF_PURCHASES_FREQUENCY` | Frequency of one-off purchases |
| `PURCHASES_INSTALLMENTS_FREQUENCY` | Frequency of installment purchases |
| `CASH_ADVANCE_FREQUENCY` | Frequency of cash advances |
| `CASH_ADVANCE_TRX` | Number of cash advance transactions |
| `PURCHASES_TRX` | Number of purchase transactions |
| `CREDIT_LIMIT` | Credit card limit |
| `PAYMENTS` | Amount paid by the customer |
| `MINIMUM_PAYMENTS` | Minimum payment amount |
| `PRC_FULL_PAYMENT` | Percentage of the balance paid in full |
| `TENURE` | Length of the customer's credit card relationship |

## Project Workflow

The notebook follows these major steps:

1. Understand the marketing business problem
2. Load the customer dataset
3. Explore the data using descriptive statistics
4. Check and handle missing values
5. Check duplicate records
6. Remove `CUST_ID` because it is an identifier and does not provide behavioural information for clustering
7. Perform exploratory data analysis
8. Study feature distributions and correlations
9. Standardize the numerical features
10. Apply **K-Means clustering**
11. Use the **Elbow Method** to evaluate the suitable number of clusters
12. Analyse customer groups using cluster-level characteristics
13. Use **PCA** to reduce the data to two dimensions for visualization
14. Build an **Autoencoder** for dimensionality reduction
15. Apply K-Means to the encoded representation
16. Visualize the resulting customer segments

## Exploratory Data Analysis

The analysis examines the distribution and relationship of important customer attributes.

Some observations explored in the notebook include:

- Average customer balance is around $1,500–$1,600.
- Customers generally have a high balance-update frequency.
- Average purchase amount is around $1,000.
- Purchase frequency shows different customer behaviour patterns.
- Most customers have relatively low full-payment percentages.
- Average credit limit is around $4,500.
- The dataset contains relationships between purchases, one-off purchases, installment purchases, purchase transactions, credit limit and payments.

The notebook also checks missing values and fills missing values in `MINIMUM_PAYMENTS` and `CREDIT_LIMIT` using their respective mean values.

## Customer Segmentation Using K-Means

**K-Means** is an unsupervised machine learning algorithm that groups customers with similar characteristics into clusters.

The workflow is:

1. Standardize the customer features.
2. Test different values of `K`.
3. Calculate the Within-Cluster Sum of Squares (WCSS).
4. Use the Elbow Method to evaluate the number of clusters.
5. Apply K-Means.
6. Assign a cluster label to every customer.
7. Compare customer behaviour across clusters.

The notebook's final K-Means implementation on the standardized dataset uses **8 clusters**.

### Example Customer Segments

The notebook analyses the resulting clusters and identifies behavioural patterns such as:

- **Transactors:** Customers with relatively low balances and cash advances who tend to pay a higher percentage of their balance in full.
- **Revolvers:** Customers with higher balances and cash advances, lower purchase frequency and lower full-payment percentages. This group may represent an important segment for credit-related marketing.
- **VIP / Prime Customers:** Customers with high credit limits and a high percentage of full payments. They may have potential for higher spending or premium products.
- **Low-Tenure Customers:** Customers with shorter relationships with the bank and relatively lower balances.

The exact characteristics of each cluster should be interpreted from the cluster-level results generated by the notebook.

## PCA Visualization

Principal Component Analysis (PCA) is used to reduce the standardized dataset to two principal components.

This makes it possible to visualize customer clusters in a two-dimensional chart and observe how the identified groups are distributed.

PCA is used here mainly for **visualization and dimensionality reduction**, rather than as a prediction model.

## Autoencoder-Based Dimensionality Reduction

The project also experiments with an **Autoencoder**, an unsupervised neural network that learns a compressed representation of the original customer data.

The Autoencoder contains:

- An input layer representing the customer features
- An encoder that compresses the information
- A bottleneck/encoded representation
- Decoder layers that reconstruct the original data

The notebook trains the Autoencoder using the standardized customer data and then extracts the encoded representation.

K-Means is subsequently applied to this compressed representation. The notebook's final Autoencoder-based clustering implementation uses **4 clusters**.

This provides an alternative way to segment customers after reducing the dimensionality of the original feature space.

## Marketing Use Case

The main business use case is **targeted customer marketing**.

Once customers are divided into behavioural segments, the bank's marketing team can develop different campaigns for different groups.

For example:

| Customer Behaviour | Possible Marketing Approach |
|---|---|
| High-value / VIP customers | Premium cards, higher credit limits and premium banking products |
| High balance and cash-advance users | Credit-related offers and products designed around their financial needs |
| Frequent purchasers | Rewards, cashback and loyalty campaigns |
| Installment-focused customers | EMI/installment offers and relevant financing products |
| Low-tenure customers | Customer onboarding, engagement and activation campaigns |
| Low-activity customers | Offers designed to increase card usage and engagement |

These are **business recommendations based on the behavioural patterns identified by clustering**. Actual campaign decisions would require additional information such as customer demographics, profitability, risk level, response history and campaign performance.

## Why Customer Segmentation Helps Marketing

A single campaign may not work equally well for every customer.

Segmentation allows the marketing team to:

- Identify groups with similar behaviour
- Personalize campaign messages
- Select more relevant products or offers
- Improve customer engagement
- Focus marketing resources on suitable customer groups
- Design separate strategies for high-value and low-activity customers
- Build a data-driven approach to customer targeting

## Technologies Used

- **Python**
- **Pandas** – data manipulation
- **NumPy** – numerical operations
- **Matplotlib** – visualization
- **Seaborn** – exploratory data analysis and visualization
- **Scikit-learn** – StandardScaler, K-Means and PCA
- **TensorFlow / Keras** – Autoencoder
- **Jupyter Notebook** – project development and analysis

## Project Structure

```text
Marketing_Department/
│
├── Marketing_Department.ipynb
├── Marketing_data.csv          
├── Marketing_slides.pptx       # Business problem & architectural slides
└── README.md  

---

Installation & Setup
1. Clone the Repository:
```Bash
git clone [https://github.com/Satishji111/Marketing_Department.git](https://github.com/Satishji111/Marketing_Department.git)
cd Marketing_Department
```
2. Create a Virtual Environment:

```Bash
python -m venv venv
source venv/bin/activate
```
3. Install Dependencies:

```Bash
pip install -r requirements.txt
```
4. Launch the Notebook:

```Bash
jupyter notebook
```
Key Takeaways & Marketing Insights
Segment Profiling: Distinguishes high-spend transactors, cash-advance heavy users, and low-activity accounts.

Actionable Insights: Enables the marketing department to adjust credit limits, offer zero-percent APR balance transfers, or introduce reward tiers tailored directly to each identified group.
