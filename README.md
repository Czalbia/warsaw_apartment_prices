<div style="text-align: right"> By Jan Czałbowski </div>

# **You want to predict the price for renting an apartment in Warsaw?** 
Check out this apartment price prediction script that utilizes linear regression and a simple database to predict the price of an apartment.
For explanation of all the mathematics scroll down.

## **How does it work?**

To predict the price of an apartment, linear regression has to be used. Linear regression is easy to employ when 2 variable functions are used; therefore, in this script the area of an apartment is presented as $X$ and price as $Y$.

To calculate the optimal line of regression, minimizing the total sum of squares of $Y$ is required. $SSy$ shows how big is the sum of all the differences of $Yi$ and $\overline{Y}$, how precise is the linear function. The parameters of the linear function are $\hat{\beta_0}$ and $\hat{\beta_1}$. The optimal parameters can be calculated in 3 steps.

1. Deriving the formula for partial derivatives of $\hat{\beta_0}$ and $\hat{\beta_1}$ <br>
    -> It is done to determine the slope of the function at a given moment
2. Calculating zeroes of the two derivatives <br>
    -> $\frac{\partial f}{\partial x} = 0$ is a local minimum of a function  
3. Solving the simultanious equations for $\hat{\beta_0}$ and $\hat{\beta_1}$ <br>
    -> To derive the complete forumla for the linear regression $Y = \hat{\beta_1}X + \hat{\beta_0}$

Formulas for calculating the mean: <br>

$\overline{X} = \frac{\sum_{i = 0}^{n} Xi}{n}$

$\overline{Y} = \frac{\sum_{i = 0}^{n} Yi}{n}$

### **Step 1.** <br>

**For $\hat{\beta_0}$** <br>

$\frac{\partial }{\partial \beta_0} \sum_{i = 0}^{n} (Yi - \hat{Y})^2 = \sum_{i = 0}^{n} \frac{\partial }{\partial \beta_0}  (Yi - \hat{\beta_0} - \hat{\beta_1}Xi)^2 = -2\sum_{i = 0}^{n} (Yi - \hat{\beta_0} - \hat{\beta_1}Xi)$

**For $\hat{\beta_1}$** <br>

$\frac{\partial }{\partial \beta_1} \sum_{i = 0}^{n} (Yi - \hat{Y})^2 = \sum_{i = 0}^{n} \frac{\partial }{\partial \beta_1}  (Yi - \hat{\beta_0} - \hat{\beta_1}Xi)^2 = -2\sum_{i = 0}^{n} Xi(Yi - \hat{\beta_0} - \hat{\beta_1}Xi)$

### **Step 2.** <br>

$-2\sum_{i = 0}^{n} (Yi - \hat{\beta_0} - \hat{\beta_1}Xi = 0$<br>
$-2\sum_{i = 0}^{n} Xi(Yi - \hat{\beta_0} - \hat{\beta_1}Xi) = 0$

To simplify $\sum_{i = 0}^{n}$ => $\sum$

$\sum(Yi - \hat{\beta_0} - \hat{\beta_1}Xi) = 0$<br>
$\sum Xi(Yi - \hat{\beta_0} - \hat{\beta_1}Xi) = 0$

### **Step 3.** <br>

Now derive the formula for $\hat{\beta_0}$ from the first equation to then substitute in the second equation

$\sum Yi - \sum \hat{\beta_0} - \sum \hat{\beta_1}Xi = 0$<br>

$\hat{\beta_0}$ and $\hat{\beta_1}$ are treated as constants 

$\sum Yi - \hat{\beta_0}\sum 1 - \hat{\beta_1}\sum Xi = 0$<br>

$\sum Yi - \hat{\beta_0}n - \hat{\beta_1}\sum Xi = 0$ <br>

$\sum Yi - \hat{\beta_1}\sum Xi = \hat{\beta_0}n$<br>

$\hat{\beta_0} = \frac{\sum Yi - \hat{\beta_1}\sum Xi}{n}$

<br>

$\hat{\beta_0} = \hat{Y} - \hat{\beta_1}\overline{X}$


We take the second equation and substitue $\hat{\beta_0}$

$\sum Xi(Yi - \hat{Y} - \hat{\beta_1}\overline{X} - \hat{\beta_1}Xi) = 0$<br>

$\sum Xi((Yi - \hat{Y}) - \hat{\beta_1}(\overline{X} - Xi)) = 0$

$\sum Xi(Yi - \hat{Y})  - \sum Xi \hat{\beta_1}(\overline{X} - Xi) = 0$

$\sum Xi(Yi - \hat{Y})  - \hat{\beta_1}\sum Xi (\overline{X} - Xi) = 0$

$\sum Xi(Yi - \hat{Y}) = \hat{\beta_1}\sum Xi (\overline{X} - Xi)$

$\hat{\beta_1} = \frac{\sum Xi(Yi - \hat{Y})}{\sum Xi (\overline{X} - Xi)} = \frac{\sum (Xi-\overline{X})(Yi - \overline{Y})}{\sum (\overline{X} - Xi)^2}$

<br>

$\hat{\beta_1} = \frac{\sum (Xi-\overline{X})(Yi - \overline{Y})}{\sum (\overline{X} - Xi)^2}$

$\hat{\beta_0} = \hat{Y} - \hat{\beta_1}\overline{X}$
<br>

<br>

$Y = X\hat{\beta_1} + \hat{\beta_0}$

This is the optimal linear regression formula.