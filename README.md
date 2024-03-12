# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required library and read the dataframe.


2.Write a function computeCost to generate the cost function.


3.Perform iterations og gradient steps with learning rate.


4.Plot the Cost function using Gradient Descent and generate the required graph. 

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: VAISHNAVI S .A
RegisterNumber:  212223220119
*/
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data=pd.read_csv("ex1.txt",header=None)
plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def computeCost(X,y,theta):
    m=len(y) 
    h=X.dot(theta) 
    square_err=(h-y)**2
    return 1/(2*m)*np.sum(square_err)

data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))
computeCost(X,y,theta) 

def gradientDescent(X,y,theta,alpha,num_iters):
    m=len(y)
    J_history=[] #empty list
    for i in range(num_iters):
        predictions=X.dot(theta)
        error=np.dot(X.transpose(),(predictions-y))
        descent=alpha*(1/m)*error
        theta-=descent
        J_history.append(computeCost(X,y,theta))
    return theta,J_history

theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1")

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Gradient Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")
def predict(x,theta):
    predictions=np.dot(theta.transpose(),x)
    return predictions[0]

predict1=predict(np.array([1,3.5]),theta)*10000
print("For Population = 35000, we predict a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("For Population = 70000, we predict a profit of $"+str(round(predict2,0)))

```

## Output:
Profit prediction:

![267988413-ee8f17a5-0da1-4cac-a04e-7cc713fa5bc0](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/b23a4721-7ac3-489d-856c-49ee80fdb85c)

Function output:

![267988518-e782a2c3-7adf-48fc-b15d-8a5a27773e82](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/f7f336e0-9347-45e9-b92a-537455e8bc81)

Gradient descent:

![267988571-5abb3f34-b344-49d2-aa64-fcebca3f3acc](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/988db05a-249b-400c-9e6c-4426ded60562)

Cost function using Gradient Descent:

![267988615-213be6b8-a5d8-433f-bcd0-75f73edbff98](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/a21dd99c-a19e-4c18-96c0-9f763c7c655c)

Linear Regression using Profit Prediction:

![267988650-d41d1d08-52d9-4a93-88cf-11ca7fdb544b](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/e0334b08-19b0-40e6-a714-e371a95aaf51)

Profit Prediction for a population of 35000: 

![267988692-43f982a1-bbcc-4910-9ef0-794ff2421d33](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/fd317f84-b2da-4bd2-b2b9-dd36908724ad)

Profit Prediction for a population of 70000 :

![267988729-f1cf50b4-0a6e-4d34-bb8f-683c9b6923ab](https://github.com/vaishnavishaji/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/151444759/d423f4fb-dd5d-4d73-98b6-06d94ca76ffa)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
