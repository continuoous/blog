---
layout: post
title: Logistic Regression
description: Quickest implementation of Logistic Regression in MS Excel
summary: Logistic regression isn't a native functionality in Excel. Its implementation is rather quick with Excel's Solver capability.
tags: [Tech]
img: https://source.unsplash.com/K1NObYzL86k/200x150/
---

![Unsplash](https://source.unsplash.com/K1NObYzL86k/800x450/ "Source: unsplash.com/@persnicketyprints")

1. Many free online resources<sup>1</sup> explain Logistic regression far better than I ever could in a single post. At the outset, I'll assume you are *very* familiar with Logistic regression.

2. I love that Logistic regression can be implemented so simply in a Spreadsheet. My intent is to post about, what in my opinion is, the quickest implementation of Logistic regression in MS Excel with this [Exercise](http://openclassroom.stanford.edu/MainFolder/DocumentPage.php?course=DeepLearning&doc=exercises/ex4/ex4.html) published by Stanford. 

3. **Input**: The dataset represents scores of Exam1 (x₁) and Exam2 (x₂) of 40 students admitted (y = 1) to college and 40 students who were not admitted (y = 0).

4. You can download the [dataset](https://raw.githubusercontent.com/continuoous/Spreadsheets/main/Logistic_regression.txt) or the entire [excel file](https://github.com/continuoous/Spreadsheets/blob/main/Logistic_Regression_OneStep.xlsx?raw=true) to follow along. ![SSolution](http://openclassroom.stanford.edu/MainFolder/courses/MachineLearning/exercises/ex4materials/ex4regression.png)

5. **Insert x₀**: To begin. Copy input data (x₁, x₂ and y) to excel and then insert a column x₀ before x₁ in which all rows equal 1.
  
6. **Name Ranges** <sup>2</sup>: create 4 Name ranges. 
  * columns x₀, x₁ and x₂ together become $$x$$. 
  * column y is named $$y$$.
  * create a 3 cell range called $$w$$
  * finally name a single cell $$j$$

7. **Cost Function**: Next, we'll implement the Cost Function<sup>3</sup> in name range $$j$$.
$$\frac{{1}}{m}\sum\left[
 -y \log(\frac{{1}}{1+e^{-w^{T}x}}) -
 (1-y)\log(1-\frac{{1}}{1+e^{-w^{T}x}})\right]$$

8. Since **LET formula** <sup>4</sup> un-nests excel formula to make them more readable. We'll use it to implement cost function. 
 ```
  =LET(
  m,COUNTA(y),
  w,TRANSPOSE(w),
  z,MMULT(X,w),
  h,1/(1+EXP(-z)),
  cost0,(1-y)*-LN(1-h),
  cost1,y*-LN(h),
  j,SUM(cost0+cost1)/m,
  j)
  ```
  I posted earlier about LET<sup>4</sup> function which is linked below.

9. At this point, we could implement *gradient descent* using VBA or MS Excel's *iterative calculations*. Instead, we'll use Excel's solver function which is quicker to implement and faster in calculation. 
  * Since the cost function is non-linear - we use the Generalized Reduced Gradient (GRG) Nonlinear Solving method.

10. Here's how you implement Solver (you must have solver Add-in enabled)
![solver](https://support.content.office.net/en-us/media/5f471432-a239-4b8f-b664-0c34a16c9aa9.png)
  * Navigate *Data > Solver*
  * *Set Objevtive* = **J** 
  * TO **Min**
  * *by changing variable cells* = **w**
  * uncheck *Make unconstrained variables non-negative*
  * *Select a solving method* = **GRG NonLinear**
  * Click *Solve*
  * Click *OK*

11. Excel's solution for the weights (w₀, w₁, w₂) is identical to the result at [orginal source](http://openclassroom.stanford.edu/MainFolder/DocumentPage.php?course=DeepLearning&doc=exercises/ex4/ex4.html)
  * w₀ = -16.375
  * w₁ = +00.148
  * w₂ = +00.158

So, there it is. Logistic regression implemented with **One** formula and solver function.

**References**
  * <sup>1</sup> [Andrew NG's Youtube playlist](https://www.youtube.com/watch?v=-la3q9d7AKQ&list=PLNeKWBMsAzboR8vvhnlanxCNr2V7ITuxy)
  * <sup>2</sup> [Using Named Cells in Excel - Youtube](https://www.youtube.com/embed/eEFbCBCLLFM)
  * <sup>3</sup> [Andrew NG's Simplified cost function from YT](https://www.youtube.com/watch?v=TTdcc21Ko9A)
  * <sup>4</sup> [My earlier post about LET function](http://www.continuoous.com/2021/04/25/01)