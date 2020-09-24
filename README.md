# Instacart-Products Reorder Prediction and Recommendation

## Define the Problem

#### Project Goal: 
The goal of this project is to examine the dataset of Instacart online grocery shopping orders and use this data to build and test models for predicting products that a user will buy again.

#### Practical use: 
Instacart is currently using several machine learning models in production on similar data to sort items for users to “buy again” and to recommend items for users while they shop.

#### Tool: 
Python 3 (Jupyter Notebook) with a wide range of libraries/packages available for data manipulation and predictive modeling algorithms.

# Data
The dataset was downloaded from S3 at: https://www.instacart.com/datasets/grocery-shopping-2017. This anonymized dataset contains a sample of over 3 million grocery orders from more than 200,000 Instacart users.

For each user, 4 and 100 of their orders are given, with the sequence of products purchased in each order.

#### orders.csv: 
It has all order details such as order_id, order_num, user_id(order by the user), and other order details. 
<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/order_df.PNG" width="650" height = "225">

#### products.csv: 
It has all product-related information such as product_id, product_name, aisle_id, department_id.
<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/product_df.PNG" width="550" height = "210">

#### order_products__prior.csv & order_products__train.csv: 
<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/order_products_prior_df.PNG" width="450" height = "225">
<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/order_products_train_df.PNG" width="450" height = "225">

Both CSV files have the same information such as product_id's associated to each order, add_to_card_order, and also the reordered information of the product. Then what is the difference between these files.?

As mentioned earlier, in this dataset, 4 to 100 orders of a customer are given and we need to predict the products that will be re-ordered. So the last order of the user has been taken out and divided into train and test sets. All the prior order information of the customers are present in order_products_prior file. We can also note that there is a column in orders.csv file called eval_set which tells us as to which of the three datasets (prior, train or test) the given row goes to.

#### Aisles.csv: 
It has the asile id and name of the asile.

<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/aisle_df.PNG" width="350" height = "225">

#### Department.csv: 
It has the department id and name of the department. 

<img src="https://github.com/veerendrababum/instacart_rec/blob/master/images/dep_df.PNG" width="350" height = "210">

# Data Discovery
1.	Import Libraries and set up a directory where python interpreter access code files
2.	Load Data
3.	Examine and Get Insights on Data
4.	Explore data analysis
5.	Feature Engineering
      * Created new features of users using user_id
      * Created new features of products using product_id
      * Created the features related to user and product

# Model Development and Testing:
1.	Build the XGBoost model(From the Instacart blog post, it is seen that they are using XGBoost as one of their models in production)
2.	Evaluate Model
3.	Use the testing dataset to test the model
4.	Create a CSV file with the predictions on the testing dataset
5.	Identify the most influential feature
