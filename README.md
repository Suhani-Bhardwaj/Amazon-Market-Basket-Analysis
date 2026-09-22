# Amazon Market Basket Analysis & Customer Behavior Analysis

## 📌 Project Overview

This project analyzes Amazon customer behavior using Python to identify purchasing patterns, customer segments, shopping satisfaction, review behavior, recommendation effectiveness, cart abandonment factors, and areas for business improvement.

The project uses an Amazon customer dataset containing **800 customer responses and 24 attributes** related to demographics, purchasing frequency, product categories, browsing behavior, product search methods, cart behavior, customer reviews, personalized recommendations, shopping satisfaction, and service experience.

The project follows an end-to-end data analytics and machine learning workflow:

**Data Loading → Data Cleaning → Exploratory Data Analysis → Customer Segmentation → K-Means Clustering → Visualization → Business Insights**

The project combines traditional data analysis with **Unsupervised Machine Learning using K-Means Clustering** to identify groups of customers with similar rating and satisfaction patterns.

---

## 🎯 Project Objectives

The main objectives of this project are to:

- Understand Amazon customer demographics and purchasing behavior.
- Identify the most popular product categories.
- Analyze customer purchase frequency.
- Understand how customers search for products.
- Identify major reasons for cart abandonment.
- Segment customers based on purchasing frequency.
- Use K-Means clustering to identify customer groups with similar behavioral characteristics.
- Analyze customer satisfaction and rating patterns.
- Understand the perceived usefulness and reliability of customer reviews.
- Analyze personalized recommendation responses.
- Identify services customers appreciate.
- Identify areas where customers believe Amazon can improve.
- Convert customer data into actionable business insights.

---

## 🛠️ Technologies & Tools

### Programming Language
- Python

### Libraries
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

### Machine Learning
- K-Means Clustering
- Unsupervised Learning

### Development Environment
- Jupyter Notebook

### Dataset
- CSV

---

## 📂 Project Structure

```text
Amazon-Market-Basket-Analysis/
│
├── Amazon.csv
├── Market_Basket_Analysis_Amazon.ipynb
├── README.md
│
└── images/
    ├── age_distribution.png
    ├── browsing_frequency_pie_chart.png
    ├── cart_abandonment_factors.png
    ├── customer_segments.png
    ├── customer_segments_by_gender.png
    ├── gender_distribution.png
    ├── improvement_areas.png
    ├── kmeans_clusters.png
    ├── most_popular_product_categories.png
    ├── personalized_recommendation_responses.png
    ├── product_search_methods.png
    ├── purchase_categories_bar_chart.png
    ├── purchase_frequency_distribution.png
    ├── recommendation_helpfulness_vs_satisfaction.png
    ├── recommendation_satisfaction_heatmap.png
    ├── review_helpfulness.png
    ├── review_reliability.png
    ├── service_appreciation.png
    └── shopping_satisfaction_levels.png
📊 Dataset

The dataset contains:

800 customer responses
24 attributes

The major attributes include:

Attribute	Description
age	Customer age
Gender	Customer gender
Purchase_Frequency	How frequently the customer purchases
Purchase_Categories	Product categories purchased
Personalized_Recommendation_Response	Customer response to personalized recommendations
Browsing_Frequency	Frequency of browsing
Product_Search_Method	Method used to search for products
Search_Result_Exploration	Search result exploration behavior
Customer_Reviews_Importance	Importance given to customer reviews
Add_to_Cart_Browsing	Add-to-cart behavior
Cart_Completion_Frequency	Frequency of completing purchases after adding products
Cart_Abandonment_Factors	Reasons for abandoning carts
Saveforlater_Frequency	Frequency of saving products for later
Review_Left	Whether customers leave reviews
Review_Reliability	Perceived reliability of reviews
Review_Helpfulness	Perceived helpfulness of reviews
Personalized_Recommendation_Rating	Rating given to personalized recommendations
Recommendation_Helpfulness	Perceived helpfulness of recommendations
Rating_Accuracy	Perceived accuracy of product ratings
Shopping_Satisfaction	Overall shopping satisfaction
Service_Appreciation	Service aspects appreciated by customers
Improvement_Areas	Areas customers believe need improvement
transaction	Transaction identifier
🧹 Data Cleaning & Preprocessing

Before performing analysis, the dataset was inspected and cleaned.

1. Dataset Inspection

The following checks were performed:

Dataset shape
Column names
Data types
Descriptive statistics
Duplicate records
Missing values
df.shape
df.columns
df.info()
df.describe(include="all")
2. Duplicate Check

Duplicate records were checked using:

df.duplicated().sum()

This helps ensure that repeated records do not distort the analysis.

3. Column Name Cleaning

Unnecessary whitespace in column names was removed:

df.columns = df.columns.str.strip()
4. Handling Missing Values

Missing values were checked using:

df.isnull().sum()

The Product_Search_Method column contained missing values.

Since this is a categorical variable, the missing values were filled using the mode, which is the most frequently occurring category.

df["Product_Search_Method"] = df["Product_Search_Method"].fillna(
    df["Product_Search_Method"].mode()[0]
)
5. Categorical Data Cleaning

Categorical values were cleaned by removing unnecessary whitespace to ensure consistent category names.

6. Numeric Conversion

Rating-related columns were converted into numeric values so that they could be used for statistical analysis and machine learning.

🔎 Exploratory Data Analysis

After preprocessing, Exploratory Data Analysis (EDA) was performed to understand customer behavior and identify important patterns.

👥 Customer Demographics
Age Distribution

The age distribution was analyzed using a histogram to understand the spread of customer ages.

Gender Distribution

Customer gender distribution was analyzed using a count plot.

🛒 Purchase Behavior
Purchase Frequency

Customer purchase frequency was analyzed to understand how often customers shop.

The most common purchase frequency was:

Once a month — 168 customers

This indicates that a significant portion of customers are moderate or occasional shoppers.

🛍️ Popular Product Categories

The Purchase_Categories column contains multiple product categories within individual cells.

The categories were split and exploded so that individual categories could be analyzed separately.

Key Finding

Clothing and Fashion was the most frequently selected product category, with approximately 450 selections.

Other highly selected categories included:

Others
Home and Kitchen
Beauty and Personal Care
Groceries and Gourmet Food
🔍 Product Search Methods

Customer product search methods were analyzed to understand how customers discover products.

Key Finding

Keyword search was the most common search method, with 327 customers.

This highlights the importance of effective search functionality, keyword matching, autocomplete, filtering, and search relevance in an e-commerce platform.

🛒 Cart Abandonment Analysis

Cart abandonment factors were analyzed to identify why customers do not complete purchases.

Major Findings
Cart Abandonment Factor	Customers
High shipping costs	224
Found a better price elsewhere	206
Changed mind / no longer needed	194
Other reasons	176
Business Insight

High shipping costs were the most frequently reported reason for cart abandonment.

Potential business responses could include:

Free-shipping thresholds
Shipping cost optimization
Competitive pricing
Abandoned-cart reminders
Improved checkout experience
👥 Customer Segmentation

Customers were segmented based on their purchase frequency.

Three customer segments were created:

1. Frequent Buyers

Customers who purchase:

Multiple times a week

2. Occasional Shoppers

Customers who purchase:

Few times a month
Once a month
Once a week
3. At-Risk Customers

Customers falling into the lower-frequency purchasing category.

Customer Segment Distribution

Customer Segment	Customers
Occasional Shoppers	485
Frequent Buyers	159
At-Risk Customers	156
Key Finding

Occasional Shoppers represent the largest customer segment.

This suggests that most customers in this dataset show moderate purchasing behavior rather than purchasing multiple times per week.

👥 Customer Segmentation by Gender

Customer segments were also analyzed across gender categories.

The analysis showed that Occasional Shoppers were the largest segment across the gender categories.

🤖 Machine Learning — K-Means Clustering
Why K-Means?

K-Means was used to identify groups of customers with similar satisfaction and rating patterns.

K-Means is an Unsupervised Machine Learning algorithm because there are no predefined cluster labels.

The algorithm discovers groups based on similarities between customers.

Features Used for Clustering

Four numerical variables were selected:

Shopping_Satisfaction
Customer_Reviews_Importance
Rating_Accuracy
Personalized_Recommendation_Rating

Each customer is represented using these four values.

K-Means then groups customers whose values are similar across these dimensions.

K-Means Configuration
from sklearn.cluster import KMeans

kmeans = KMeans(
    n_clusters=3,
    random_state=42,
    n_init=10
)

df["Cluster"] = kmeans.fit_predict(X)
Parameters

n_clusters=3

The algorithm was instructed to create three clusters.

random_state=42

Used to make the initialization reproducible.

n_init=10

Allows K-Means to try multiple initial centroid configurations and select a better solution.

Cluster Results

The three clusters contained:

Cluster	Customers
Cluster 0	302
Cluster 1	258
Cluster 2	240

The clusters represent different customer behavior patterns based on:

Shopping satisfaction
Review importance
Rating accuracy
Personalized recommendation ratings
Important Note

K-Means itself produces labels such as Cluster 0, Cluster 1, and Cluster 2. These labels do not automatically mean "high," "moderate," or "low" satisfaction.

The business interpretation of each cluster should be based on the average feature values of the customers within that cluster.

⭐ Customer Satisfaction Analysis

Shopping satisfaction was analyzed using customer satisfaction ratings.

The average shopping satisfaction was approximately:

3.01 / 5

The median was:

3 / 5

This indicates that customer satisfaction in the dataset is centered around the middle of the rating scale.

⭐ Rating Accuracy

The average rating accuracy score was approximately:

2.97 / 5

The median was:

3 / 5

This provides insight into how customers perceive the accuracy of product ratings.

🤝 Personalized Recommendations

Personalized recommendation responses were analyzed to understand whether customers feel that recommendations are relevant to them.

The responses were distributed across:

Yes
No
Sometimes

This suggests that customer perceptions of personalized recommendations are mixed.

💡 Recommendation Helpfulness vs Shopping Satisfaction

The relationship between recommendation helpfulness and shopping satisfaction was analyzed using cross-tabulation and visualization.

This analysis helps examine the distribution of shopping satisfaction across different levels of perceived recommendation helpfulness.

⭐ Review Analysis

Customer reviews were analyzed from multiple perspectives.

Review Reliability

The responses show different levels of customer trust in product reviews.

Review Helpfulness

The results were:

Response	Customers
No	289
Yes	257
Sometimes	254

The results indicate that review helpfulness is not perceived consistently by all customers.

🚚 Service Appreciation

Customers were asked which aspects of Amazon's service they appreciate.

Key Findings

Customer service and quick delivery were among the commonly appreciated service aspects.

This indicates that service quality and delivery experience are important parts of the customer experience represented in the dataset.

🔧 Improvement Areas

Customers were also analyzed based on areas where they believe Amazon could improve.

Key Finding

User Interface was one of the most frequently mentioned improvement areas, with 56 responses.

Other improvement areas included:

Product quality or accuracy
Refund-related issues
Shipping speed
Customer service responsiveness
Product recommendations
📌 Key Business Insights
1. Product Category Strategy

Clothing and Fashion was the most frequently selected product category.

This can help guide:

Product promotions
Inventory planning
Recommendation strategies
Marketing campaigns
2. Search Optimization

Keyword search was the most commonly used search method.

Improving:

Search relevance
Autocomplete
Keyword matching
Search filters

could improve product discovery.

3. Cart Abandonment

High shipping costs were the leading reported reason for cart abandonment.

Reducing shipping-related friction could potentially improve checkout completion.

4. Customer Segmentation

The majority of customers were Occasional Shoppers.

Customer segments can support more targeted strategies instead of treating every customer identically.

5. Customer Satisfaction

Average shopping satisfaction was approximately 3/5, suggesting room for improving the overall shopping experience represented in the dataset.

6. Recommendations

Customer responses to personalized recommendations were mixed, indicating opportunities to improve recommendation relevance.

7. Reviews

Review helpfulness and reliability showed mixed responses, highlighting the importance of review quality and discoverability.

8. User Experience

User interface improvements were among the frequently mentioned customer requests.

📈 Visualizations

The project contains visualizations covering:

Age distribution
Gender distribution
Purchase frequency
Product categories
Product search methods
Cart abandonment
Customer segments
Customer segments by gender
K-Means clusters
Recommendation helpfulness
Recommendation satisfaction
Review reliability
Review helpfulness
Personalized recommendations
Service appreciation
Improvement areas
Shopping satisfaction
Browsing frequency
🧠 Skills Demonstrated
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
Data Cleaning
Data Preprocessing
Exploratory Data Analysis
Statistical Analysis
Data Visualization
Customer Segmentation
Unsupervised Machine Learning
K-Means Clustering
Customer Behavior Analysis
Business Insight Generation
⚠️ Project Limitations
The dataset contains 800 customer responses, so the findings represent this dataset rather than all Amazon customers.
The dataset is primarily customer-response/survey based rather than detailed product-level transaction data.
Traditional association-rule mining such as Apriori or FP-Growth was not implemented.
The K-Means analysis uses four rating-related features and should be interpreted within the context of those features.
The project does not implement a production recommendation engine.
Purchase-frequency segmentation and K-Means clustering are two different approaches and should not be treated as the same segmentation method.
🚀 Future Improvements
1. Traditional Market Basket Analysis

Add transaction-level product data and implement:

Apriori
FP-Growth
Association Rules
Support
Confidence
Lift

This would allow identification of products that are frequently purchased together.

Example:

Product A → Product B
2. Improved K-Means Analysis

Future versions can:

Standardize numerical features using StandardScaler
Test different values of K
Use the Elbow Method
Calculate Silhouette Score
Profile each cluster using feature averages
3. Recommendation System

Build a recommendation engine using:

Association rules
Collaborative filtering
Content-based filtering
4. Predictive Analytics

Future versions could predict:

Customer churn
Cart abandonment
Customer satisfaction
Purchase probability
5. Interactive Dashboard

The analysis could be converted into an interactive dashboard using:

Power BI
Streamlit
Tableau
💻 How to Run the Project
1. Clone the repository
git clone https://github.com/YOUR-USERNAME/Amazon-Market-Basket-Analysis.git
2. Navigate to the project folder
cd Amazon-Market-Basket-Analysis
3. Install required libraries
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
4. Launch Jupyter Notebook
jupyter notebook
5. Open the notebook
Market_Basket_Analysis_Amazon.ipynb
6. Run the notebook

Make sure Amazon.csv is located in the same project directory.

📌 Project Workflow
Raw Amazon Customer Data
          ↓
Data Inspection
          ↓
Data Cleaning & Preprocessing
          ↓
Exploratory Data Analysis
          ↓
Customer Behavior Analysis
          ↓
Customer Segmentation
          ↓
K-Means Clustering
          ↓
Review & Recommendation Analysis
          ↓
Visualization
          ↓
Business Insights
📝 Conclusion

This project demonstrates how Python and Machine Learning can be used to transform customer data into meaningful business insights.

By analyzing purchasing behavior, product categories, search methods, cart abandonment, reviews, recommendations, satisfaction, and customer segments, the project provides a broader understanding of e-commerce customer behavior.

The K-Means clustering component adds an unsupervised machine-learning perspective by identifying groups of customers with similar rating and satisfaction patterns.

The analysis can help an e-commerce business understand customer needs, improve personalization, reduce cart abandonment, enhance the shopping experience, and identify areas for improvement.

👩‍💻 Author

Suhani

Aspiring Data & AI Professional

Technologies Used

Python Pandas NumPy Matplotlib Seaborn Scikit-learn Data Analysis Machine Learning K-Means Customer Segmentation Data Visualization
