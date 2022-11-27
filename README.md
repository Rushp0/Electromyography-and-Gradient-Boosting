# Basics of Gradient Boosting

Gradient boosting is the technique of using many weak learners to create a model that makes better predictions than any of the weak learners could individually. This is done by not adjusting the weights of the model but by adding a new weak learner that tries to fit the residual error. In other words the new weak learner in each interation see what the previous ensemble model got wrong and tries to spot correct those areas.

## Walkthrough of Gradient Boosting using Equations

You can think of the equation of the final predictor model as the summation of many weak learners or written simply: 

\begin{align}F_M(x) = Σh_n(x)\end{align}

Where $h_n(x)$ is a model that fits the residuals errors of the previous function. 

First we create a initial model where $F(x)_1 = \hat{y}$. This crappy model will get some points right but will have much more error points.

 We take the error points and calculate the residual error by finding $y-F_1(x)$. We will then takes these residual errors and fit a model to them, and we will call it $h(x)$.

\begin{align}h(x) = y-F_1(x)\end{align}

Using this second model $h(x)$ and the inital model $F_1(x)$, we will create a composite model. This compsoite model will fix some of the errors of the inital singular model. The composite model is written as:
\begin{align} F_2(x) = F_1(x) + h(x) \end{align}

Continuing this step an M number of times will result in a model $F_m(x)$ which can much more accurately predict the target values of y. The result from repeating the previous steps an $M$ number of times can be written as:

\begin{align} F_{m+1}(x) = F_M(x) + h_M(x) \end{align}

The above equation expanded would look like:
\begin{align} F_{m+1}(x) = (F_{M-1}(x) + h_{M-1}(x)) + h_M(x) \end{align}
This equation would expand recursively until $M = 1$.
