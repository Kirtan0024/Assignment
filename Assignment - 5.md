**Practical Tasks**

**Task 1: House Price Prediction**



The dataset contain 1460 training data points and 80 features that might help to predict

the selling price of a house. Note: Save each resultant model by different name sothat

you can compare all of them in your final conclusion. Do as directed



**Answer** : 



House Price Prediction Project 



import numpy as np

import pandas as pd

np.random.seed(42)

num\_house = 500

sqrt = np.random.randint(800 , 4500 , size = num\_house)

bedrooms = np.random.randint(1, 6 , size = num\_house)

bathrooms = np.random.randint(1, 4 , size = num\_house)

age\_years = np.random.randint(0 , 50 , size = num\_house)



noise = np.random.normal(10 , 100 , size = num\_house)



price = 50000 + (sqrt \* 150) + (bedrooms \* 15000) + (bathrooms \* 20000) - (age\_years \* 1000) + noise



house\_data = pd.DataFrame({

&#x20;   'Sqrt' : sqrt,

&#x20;   'Bedrooms' : bedrooms,

&#x20;   'Bathrooms' : bathrooms,

&#x20;   'Age\_Years' : age\_years,

&#x20;   'Price' : price.astype(int)

})



house\_data.to\_csv("house\_price.csv" , index= False)



print(f"DataSet created successfully")



house\_data.head()



from sklearn.model\_selection import train\_test\_split

from sklearn.linear\_model import LinearRegression



df = pd.read\_csv("house\_price.csv")



X = df\[\['Sqrt' , 'Bedrooms' , 'Bathrooms' , 'Age\_Years']]



y = df\[\['Price']]



X\_train , X\_test , y\_train , y\_test = train\_test\_split(X ,y , test\_size = 0.2 , random\_state = 42)



model = LinearRegression()



model.fit(X\_train , y\_train)



print(f"Model training completed . \\n")



y\_pred = model.predict(X\_test)



**Task 2: Predicting Customer Churn**



**The data is centred on customer churn, the rate at which a commercial customer will**

**leave the commercial platform that they are currently a (paying) customer of a**

**telecommunications company**



**Answer :** 



\#Machine learning

\#supervised Machine learning

\#Linear Regression : y = mx + c

\#Logistic Regression : Sigmond Function

\#Decision Tree Classifier 

\#Classification

\#Regression



\#Random Forest Classifier



\#Linear Regression :

\#Machine learning :

\#Python With Machine Learning : NumPy

\#python Libraries to perform machine learning : Scikit-learn, TensorFlow, pytorch

Python Library : scikit-learn

matrics

mean\_squared\_error :

Mean Squared Error (MSE) : MSE is a standard matrics used to evaluate regression models. 

&#x20;   It measures the average squared difference between the estimated values and the actual values.

Lower MSE values indicate better model accuracy, with \\(0\\) representing a perfect fit.



Z - Test

P - Test

T - Test



r2\_scorer :

The \\(R`(2)\\) score (coefficient of determination ) is a regression matric used to evalute how well a model explains the variance of a target variable. While it is a often discussed as a value between 0 ans 1, it can actually be negative



&#x20;**Example :** 



import numpy as np

from sklearn.linear\_model import LinearRegression

from sklearn.metrics import mean\_squared\_error , r2\_score



X = np.array(\[

&#x20;   \[1.5 ,2],

&#x20;   \[2.0 ,3],

&#x20;   \[2.5 ,3],

&#x20;   \[1.8 ,2],

&#x20;   \[3.0 ,4],

&#x20;   \[1.2 ,1]

])



y = np.array(\[3.0 , 3.9 , 5.1 , 3.7 , 6.1 , 2.5])



lin\_reg = LinearRegression()

lin\_reg.fit(X ,y)



new\_house = np.array(\[\[2.2 ,3]])

predicited\_price = lin\_reg.predict(new\_house)



y\_pred = lin\_reg.predict(X)

mse = mean\_squared\_error(y ,y\_pred)



print("\_\_\_\_Linear Regression\_\_\_\_\_\_")

print(f"Intercept (b) : {lin\_reg.intercept\_ :.4f}")

print(f"Coefficients (w) : {lin\_reg.coef\_}")

print(f"Predicted price for 2,200 sq ft , 3-bed house : ${predicited\_price\[0]\*100:,.2f}k")

print(f"Mean squared error : {mse:.4f}")



&#x20;**Output :** 

\_\_\_\_Linear Regression\_\_\_\_\_\_

Intercept (b) : -0.1273

Coefficients (w) : \[ 2.4        -0.24909091]

Predicted price for 2,200 sq ft , 3-bed house : $440.55k

Mean squared error : 0.0004



**Example :** 

import numpy as np

from sklearn.linear\_model import LinearRegression

from sklearn.metrics import mean\_squared\_error, r2\_score



X = np.array(\[

&#x20;   \[1, 5, 2],

&#x20;   \[2, 0, 3],

&#x20;   \[2, 5, 3],

&#x20;   \[1, 8, 2],

&#x20;   \[3, 0, 4],

&#x20;   \[1, 2, 1]

])



y = np.array(\[3.0, 3.9, 5.1, 3.7, 6.1, 2.5])



lin\_reg = LinearRegression()

lin\_reg.fit(X, y)



new\_house = np.array(\[\[2, 2, 3]])

predicted\_price = lin\_reg.predict(new\_house)



y\_pred = lin\_reg.predict(X)

mse = mean\_squared\_error(y, y\_pred)

r2 = r2\_score(y, y\_pred)



print("\_\_\_\_\_ Linear Regression \_\_\_\_\_")

print(f"Intercept (b): {lin\_reg.intercept\_:.4f}")

print(f"Coefficients (w): {lin\_reg.coef\_}")

print(f"Predicted Price: ${predicted\_price\[0]\*100:,.2f}k")

print(f"Mean Squared Error: {mse:.4f}")

print(f'R2 Score: {r2:.4f}')



**Output :** 

\_\_\_\_\_ Linear Regression \_\_\_\_\_

Intercept (b): -0.1312

Coefficients (w): \[ 2.3951417   0.24048583 -0.24493927]

Predicted Price: $440.53k

Mean Squared Error: 0.0004

R2 Score: 0.9997



**Example :** 

import numpy as np

from sklearn.linear\_model import LinearRegression

from sklearn.metrics import mean\_squared\_error , r2\_score



X = np.array(\[

&#x20;   \[1 ,5 ],

&#x20;   \[2 ,0 ],

&#x20;   \[2 ,5 ],

&#x20;   \[1, 8 ],

&#x20;   \[3 ,0 ],

&#x20;   \[1, 2 ]

])



y = np.array(\[3.0 , 3.9 , 5.1 , 3.7 , 6.1 , 2.5])



lin\_reg = LinearRegression()

lin\_reg.fit(X ,y)



new\_house = np.array(\[\[5, 3.5]])

predicited\_price = lin\_reg.predict(new\_house)



y\_pred = lin\_reg.predict(X)

mse = mean\_squared\_error(y ,y\_pred)



print("\_\_\_\_Linear Regression\_\_\_\_\_\_")

print(f"Intercept (b) : {lin\_reg.intercept\_ :.4f}")

print(f"Coefficients (w) : {lin\_reg.coef\_}")

print(f"Predicted price for 2,200 sq ft , 3-bed house : ${predicited\_price\[0]\*100:,.2f}k")

print(f"Mean squared error : {mse:.4f}")



**Output :** 

\_\_\_\_Linear Regression\_\_\_\_\_\_

Intercept (b) : -0.0730

Coefficients (w) : \[2.04098361 0.21639344]

Predicted price for 2,200 sq ft , 3-bed house : $1,088.93k

Mean squared error : 0.0045



**Example :** 

**# logistic regression (binary classification)**

**# accusarcy\_score**

**# classification\_report**



import numpy as np

from sklearn.linear\_model import LogisticRegression

from sklearn.metrics import accuracy\_score , classification\_report



X = np.array(\[

&#x20;   \[5 , 0],

&#x20;   \[100 , 25],

&#x20;   \[8 , 1],

&#x20;   \[150 , 20],

&#x20;   \[12 ,0],

&#x20;   \[90 , 10]

])



\# target : \[0 = safe email , 1 = spam]

y = np.array(\[0, 1, 0, 1, 0, 1])

log\_reg = LogisticRegression()

log\_reg.fit(X ,y)



new\_email = np.array(\[\[110 , 12]])

probability = log\_reg.predict\_proba(new\_email)\[0]   #Returns \[prob\_0 , prob\_1]

prediction = log\_reg.predict(new\_email)\[0]



print("\\n----logistic regression-----")

print(f"Probability of being safe : {probability\[0]:.4f} , spam : {probability\[1]:.4f}")

print(f"Classification result: {'spam' if prediction == 1 else 'safe'}")

print(f"Model Accuaracy : {accuracy\_score(y , log\_reg.predict(X)) \* 100:.1f}%")



**Output :** 



\----logistic regression-----

Probability of being safe : 0.0001 , spam : 0.9999

Classification result: spam

Model Accuaracy : 100.0%



**Example :** 

**Decision tree classifier (Multiclass classification)**

**practical example : classifiying loan application risk ( 0 = low risk , 1 = medium risk, 2 - high risk)**

**based on credit score and debt-to-income (DTI) ratio.**



import numpy as np

from sklearn.tree import DecisionTreeClassifier, export\_text

from sklearn.metrics import accuracy\_score



X = np.array(\[

&#x20;   \[750, 10], #Low risk

&#x20;   \[600, 45], #High risk

&#x20;   \[680, 25], #Medium Risk

&#x20;   \[580, 50], #High Risk

&#x20;   \[790, 15], #Low risk

&#x20;   \[640, 30] #Medium risk

])



y = np.array(\[0, 2, 1, 2, 0, 1])



dt\_classifier = DecisionTreeClassifier(criterion='entropy', max\_depth =3, random\_state=42)

dt\_classifier.fit(X, y)



new\_applicant = np.array(\[\[670,20]])

risk\_pred = dt\_classifier.predict(new\_applicant)\[0]



risk\_mapping = {0: "Low Risk", 1: "Medium Risk", 2: "High Risk"}



print("\\n--- Dicision Tree Classifier ---")

print(f"Predict risk category : {risk\_mapping\[risk\_pred]}")

print("\\nGenerated Tree Rules:")



tree\_rules = export\_text(dt\_classifier, feature\_names=\['Credit Score', 'DIT Ratio'])

print(tree\_rules)



**Output :** 

\--- Dicision Tree Classifier ---

Predict risk category : Low Risk



Generated Tree Rules:

|--- Credit Score <= 620.00

|   |--- class: 2

|--- Credit Score >  620.00

|   |--- DIT Ratio <= 20.00

|   |   |--- class: 0

|   |--- DIT Ratio >  20.00

|   |   |--- class: 1



**Example :** 

**Random Forest Classifier (Ensemble Classification)**

**Practical Example : Predicting e-commerce customer churn (0 = Will Stay, 1 = Will Churn/Leave) using user activity feature**



import numpy as np

from sklearn.ensemble import RandomForestClassifier

from sklearn.metrics import accuracy\_score



x = np.array(\[

&#x20;   \[24,1,2],

&#x20;   \[3,7,0],

&#x20;   \[12,2,5],

&#x20;   \[1,9,1],

&#x20;   \[36,0,8],

&#x20;   \[6,4,2]

])



y = np.array(\[0,1,0,1,0,1])



rf\_classifier = RandomForestClassifier(n\_estimators=10, max\_depth=3, random\_state=42)

rf\_classifier.fit(x,y)



trouble\_customer = np.array(\[\[5,5,1]])

churn\_pred = rf\_classifier.predict(trouble\_customer)\[0]



print("\\n--- Random Forest Classifier ---")

print(f"Customer churn Prediction : {'Will churn' if churn\_pred == 1 else 'Will Stay'}")



importances = rf\_classifier.feature\_importances\_

features = \['Month Active', 'Support Cells', 'Item in Cart']

print("\\nFeature Importances across tyhe Forest:")

for feat, imp in zip(features, importances):

&#x20;   print(f" - {feat} : {imp\*100:.1f}%")



**Output :** 

\--- Random Forest Classifier ---

Customer churn Prediction : Will churn



Feature Importances across tyhe Forest:

&#x20;- Month Active : 30.0%

&#x20;- Support Cells : 47.0%

&#x20;- Item in Cart : 23.0%



**Example :**

**Support Vector Machine (SVM)**

**The Goal : Find the optimal hyperplane that maximizes the margin between diffrent classes.**

**Practical Example : Medical Diagnosis - predicting whether a tumor is Malignant (1) or Benign (0) based on cell radius and texture.**



**Example :** 



import numpy as np

from sklearn.svm import SVC

from sklearn.datasets import make\_classification

from sklearn.model\_selection import train\_test\_split

from sklearn.metrics import classification\_report



X, y = make\_classification(

&#x20;   n\_samples=100,

&#x20;   n\_features=2,

&#x20;   n\_informative=2,

&#x20;   n\_redundant=0,

&#x20;   random\_state=42,

&#x20;   class\_sep=1.5

)



X\_train, X\_test, y\_train, y\_test = train\_test\_split(

&#x20;   X, y,

&#x20;   test\_size=0.2,

&#x20;   random\_state=42

)



svm\_model = SVC(kernel='linear', C=1.0)



svm\_model.fit(X\_train, y\_train)



y\_pred = svm\_model.predict(X\_test)



print("--------------- Support Vector Machine ---------------")

print(f"Support Vectors Count : {len(svm\_model.support\_vectors\_)}")



print("\\nClassification Report :")

print(classification\_report(

&#x20;   y\_test,

&#x20;   y\_pred,

&#x20;   target\_names=\['Benign', 'Malignant']

))

\--------------- Support Vector Machine ---------------

Support Vectors Count : 5



Classification Report :

&#x20;             precision    recall  f1-score   support



&#x20;     Benign       1.00      1.00      1.00        11

&#x20;  Malignant       1.00      1.00      1.00         9



&#x20;   accuracy                           1.00        20

&#x20;  macro avg       1.00      1.00      1.00        20

weighted avg       1.00      1.00      1.00        20





**Example :** 

**K-Nearest Neighbors (KNN) Classifier** 

**The Goal: Classify a data point based on how its neighbors are classified (voting system based on distance).**

**Practical Example: E-commerce Product Recommendation Category-Classifying a user's preferred product category based on their Age and Daily Time Spent on the app.**



import numpy as np

from sklearn.neighbors import KNeighborsClassifier

from sklearn.preprocessing import StandardScaler



\#Dataset: \[Age, Time Spent (Minutes)]



X = np.array(\[

\[18, 15], \[22, 20], \[45, 60], \[50, 55],

\[25, 40], \[30, 35], \[55, 10], \[60, 15]

])



\# Tornet Drefarred Category : \[0 = Tech/Gadgets 1 = Home/Gardening]

y= np.array(\[0, 0, 1, 1, 0, 0, 1, 1])



\#KNN is highly sensitive to feature scales, so we normalize the data

scaler = StandardScaler()

X\_scaled = scaler.fit\_transform(X)



\#Initialize KNN with K=3 neighbors

knn = KNeighborsClassifier(n\_neighbors=3)

knn.fit(X\_scaled, y)



\#Predict for a new user: 23 years old, 45 minutes spent

new\_user = np.array(\[\[23, 45]])

new\_user\_scaled = scaler.transform(new\_user)

prediction = knn.predict(new\_user\_scaled)\[0]



print("\\nK-Nearest Neighbors (KNN)")

print(f"Predicted Category : {'Home/Gardening' if prediction == 1 else 'Tech/Gadgets'}")



**Output :** 

K-Nearest Neighbors (KNN)

Predicted Category : Tech/Gadgets





**Example :** 

**Naive Bayes Classifier**

**The Goal : Apply Bayes' Theorem with the "naive" assuumption of conditional independence between every pair of feature**

**to calculate class probabilities.**

**Practical Example : Sentiment Analysis-Classifying a short review as positive  (1) or Negative (0) based on keyword counts**

**(e.g., frequency of words like "love", "bad", "great", "waste").**



import numpy as np

from sklearn.naive\_bayes import MultinomialNB 



X = np.array(\[

&#x20;   \[2, 1, 0, 0],

&#x20;   \[0, 0, 3, 3],

&#x20;   \[1, 2, 0, 0],

&#x20;   \[0, 1, 2, 2]

])



y = np.array(\[1, 0, 1, 0])



nb\_classifier = MultinomialNB()

nb\_classifier.fit(X, y)



new\_review = np.array(\[\[1, 3, 2, 0]])

prob = nb\_classifier.predict\_proba(new\_review)\[0]

pred = nb\_classifier.predict(new\_review)\[0]



print("\\n --------------- Naive Bayes ---------------")

print(f"Probablities -> Negative: {prob\[0]:.2f}, Positive: {prob\[1]:.2f}")

print(f"Predicted sentiment : {'Positive' if pred == 1 else 'Negative'}")



**Output :** 



&#x20;--------------- Naive Bayes ---------------

Probablities -> Negative: 0.09, Positive: 0.91

Predicted sentiment : Positive



**Example :** 

**Ridge Regression (L2 Regularization)**

**The Goal : Linear Regression that adds a penalty equivalent to the square of the magnitude of coefficient to prevent**

**overfitting.**

**Practical Example : Stock / Financial Prediction-Predicting a company's future revenue based on Marketing spend, R\&D spend, and Employment counts where features might be highly correlated (multicollinearity).**



import numpy as np

from sklearn.linear\_model import Ridge

from sklearn.datasets import make\_regression



X, y = make\_regression(n\_samples=50, n\_features=4, noise=1.5, random\_state=42)

ridge\_reg = Ridge(alpha=1.5)

ridge\_reg.fit(X, y)



print("\\nRidge Regression (L2)")

print(f"Ridge Coefficients: {ridge\_reg.coef\_}")

print(f"Model R^2 Score: {ridge\_reg.score(X, y):.4f}")



**Output :** 



Ridge Regression (L2)

Ridge Coefficients: \[71.92358849 82.93392673 68.83935856 66.92445461]

Model R^2 Score: 0.9986



**Example :** 

import numpy as np

from sklearn.naive\_bayes import GaussianNB

from sklearn.metrics import confusion\_matrix



X = np.array(\[

&#x20;   \[15, 25],

&#x20;   \[450, 2],

&#x20;   \[8, 40],

&#x20;   \[240, 5],

&#x20;   \[12, 18],

&#x20;   \[600, 1]

&#x20;   

])



y = np.array(\[1, 0, 1, 0, 1, 0])



gnb = GaussianNB()

gnb.fit(X, y)



incoming\_call = np.array(\[\[20, 30]])

prediction = gnb.predict(incoming\_call)\[0]

prob = gnb.predict\_proba(incoming\_call)\[0]



print('----------------------- Naives bayes -----------------------')

print(f"Spam Probablity: {prob\[1]\*100:.1f}%")

print(f"Incoming call classification: {'Spam' if prediction == 1 else 'Legimate'}")



**Output :** 

\----------------------- Naives bayes -----------------------

Spam Probablity: 100.0%

Incoming call classification: Spam



**Example :** 

import numpy as np

from sklearn.linear\_model import LogisticRegression

X = np.array(\[

&#x20;   \[90, 200],

&#x20;   \[40, 90],

&#x20;   \[70, 120],

&#x20;   \[95, 190],

&#x20;   \[30, 80],

&#x20;   \[65, 130]

])



y = np.array(\[0, 1, 2, 0, 1, 2])



multi\_log\_reg = LogisticRegression(multi\_class='multinomial', solver='lbfgs')

multi\_log\_reg.fit(X, y)



new\_field = np.array(\[\[50, 100]])

crop\_pred = multi\_log\_reg.predict(new\_field)\[0]



crop\_mapping = {0: "Rice", 1: "Wheat", 2: "Maize"}

print("\\n---------------- Multinomial Logistic Regression ----------------")

print(f"Recommended Crop for the field : {crop\_mapping\[crop\_pred]}")



**Output :** 

\---------------- Multinomial Logistic Regression ----------------

Recommended Crop for the field : Wheat 



