# Aim : To predict whether a customer will purchase a product or service based on their behavioural and demographic data.

# Demographic Data
**age:** The customer's age.         
**job:** The customer's occupation (e.g., management, technician, entrepreneur).                
**marital:** Marital status (e.g., single, married, divorced).                        
**education:** Education level (e.g., primary, secondary, tertiary).                             
**housing:** Whether the customer has a housing loan (yes/no).                       
**loan:** Whether the customer has a personal loan (yes/no).                      

# Behavioral Data
**default:** Whether the customer has credit in default (yes/no).                             
**balance:** Account balance.                            
**contact:** Type of contact communication (e.g., cellular, telephone).                        
**day:** Last contact day of the month.                         
**month:** Last contact month of the year (e.g., May, Nov).                                        
**duration:** Last contact duration in seconds.                           
**campaign:** Number of contacts performed during this campaign.                                    
**pdays:** Days passed since the client was last contacted (often -1 means never contacted before).                           
**previous:** Number of contacts before this campaign.                                      
**poutcome:** Outcome of the previous marketing campaign (e.g., success, failure).                                                                       

The target variable is 'y', indicating whether the customer purchased the product (yes or no).

# Data Preprocessing and Feature Encoding
**1. Handling Outliers**

For numerical columns like balance, duration, and campaign, we calculated the Interquartile Range (IQR) to identify and potentially handle outliers. We computed the lower and upper bounds for outliers using the formula:
Lower Bound = Q1 - 1.5 * IQR
Upper Bound = Q3 + 1.5 * IQR This ensures that values outside this range are considered outliers.   

**2. Label Encoding for Categorical Variables**

For categorical columns (job, marital, education, default, housing, loan, contact, poutcome, month, and y), we used LabelEncoder to convert string labels into numerical values. This transformation is crucial for machine learning algorithms to process categorical data effectively.                                               

**3. Modeling**

After preprocessing, the data was used to train a decision tree classifier using both gini and entropy criteria. Hyperparameter tuning (using GridSearchCV) was employed to improve accuracy, and the best model achieved around 90% accuracy.

# Overall Insights                        
1. **90% Accuracy, but Some Misses:** The model is doing well with 90% accuracy, but it still misses predicting some customers who would actually make a purchase.                                      

2. **Gini Beats Entropy:** Using the Gini method slightly outperformed the entropy method, showing that small changes in how decisions are made can affect the results.                                   

3. **Keeping the Model Simple Works Best:** Limiting the depth of the decision tree to 7 levels gave the best results, making the model effective without overcomplicating it.                                      
