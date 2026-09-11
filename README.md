# Bank Customer Segmentation for Targeted Marketing

## Project Overview

Marketing is key for business growth, brand recognition and making money.

A main challenge for marketing teams is to spot how customers act and meet their financial needs [cite: 1].

This project builds a machine learning pipeline to perform **Customer Segmentation** for a bank in New York City [cite: 1].

With six months of credit card data the model splits customers into clear behavioral groups letting the marketing team create targeted high‑conversion ads [cite: 1].

---

## Business Use Case

* **Tailored Financial Products:** Offer custom credit card deals, installment incentives or balance‑transfer plans that match each cluster’s behavior.

* **Targeted Ad Campaigns:** Maximize return on ad spend by directing promotions to the customer segments instead of running generic campaigns [cite: 1].

* **Customer Retention & Growth:** Spot users who are less engaged encourage them to use their card and reduce churn risk with engagement [cite: 1].

---

## Dataset Description

The dataset contains transaction‑level and balance records across features [cite: 1]:

| Feature Name | Description |

| :--- | :---

| `CUST_ID` | Identification of Credit Card holder [cite: 1] |

| `BALANCE` | Balance amount left in the customers account to make purchases [cite: 1]

| `BALANCE_FREQUENCY` | Frequency of balance updates (score between 0 and 1) [cite: 1]

| `PURCHASES` | Total purchase amount made from the account [cite: 1]

| `ONEOFF_PURCHASES` | Maximum single transaction purchase amount [cite: 1]

| `INSTALLMENTS_PURCHASES` | Total amount of purchases made in installments [cite: 1] |

| `CASH_ADVANCE` | Cash in advance given by the bank to the user [cite: 1]

| `PURCHASES_FREQUENCY` | Frequency of purchases (score between 0 and 1) [cite: 1]

| `ONEOFF_PURCHASES_FREQUENCY` | Frequency of single‑payment purchases (score between 0 and 1) [cite: 1]

| `PURCHASES_INSTALLMENTS_FREQUENCY` | Frequency of installment purchases (score between 0 and 1) [cite: 1]

| `CASH_ADVANCE_FREQUENCY` | Frequency of cash advances being requested [cite: 1] |

| `CASH_ADVANCE_TRX` | Number of cash advance transactions [cite: 1]

| `PURCHASES_TRX` | Number of purchase transactions completed [cite: 1] |

| `CREDIT_LIMIT` | Credit card credit limit [cite: 1]

| `PAYMENTS` | Amount of payment executed by the user [cite: 1]

| `MINIMUM_PAYMENTS` | Minimum payment amount made by the user [cite: 1]

| `PRC_FULL_PAYMENT` | Percentage of full payment balance cleared by the user [cite: 1] |

| `TENURE` | Tenure of credit card service for the user (in months) [cite: 1]

---

## Technical Approach & Architecture

### 1. Exploratory Data. Preprocessing

* Address missing values in fields such as MINIMUM_PAYMENTS and CREDIT_LIMIT.

* Scale features with StandardScaler so that Euclidean distance calculations in clustering are not distorted by numbers [cite: 1].

### 2. Dimensionality Reduction

High‑dimensional customer profiles are compressed to filter noise reveal hidden patterns and improve clustering efficiency:

* **Autoencoders:** Deep neural networks that use an encoder‑decoder structure with a bottleneck layer to capture non‑linear relationships [cite: 1].

* **Principal Component Analysis (PCA):** A linear transformation that finds orthogonal, uncorrelated components and keeps the variance [cite: 1].

### 3. Unsupervised Clustering (K‑Means)

* **Elbow Method:** Checks Within‑Cluster Sum of Squares (WCSS) for K values to pick the best number of clusters [cite: 1].

* **Centroid Optimization:** Moves data points, to the centroid and updates cluster centers until the clusters stop changing [cite: 1].

---

## Repository Structure

```text

├── data/

│   └── Marketing_data.csv          # Credit card customer dataset

├── notebooks/

│   └── customer_segmentation.ipynb # Data processing, modeling and evaluation

├── presentations/

│   └── Marketing_slides.pptx       # Business problem & architectural slides

├── README.md                       # Project overview and instructions

└── requirements.txt                # Python environment dependencies

```
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

Actionable Insights: Enables the marketing department to adjust credit limits, offer zero-percent APR balance transfers, or introduce reward tiers tailored directly to each identified group[cite: 1].