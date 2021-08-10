---
sort: 1
---

# Matplotlib: Basic Plotting
## Introduction to plot function of Matplotlib

First, we would need to import the library into our python interpreter which allows us to utilise it:

```python
import matplotlib.pyplot as plt
```
Supposed that we would like to make a plot between 2 variables, we would required the usage of two arrays. For this example, we would have array X and Y containing three variables each. The image generated on the right showcase the points generated from the arrays of the two variables which gives their cartisan co-ordinates. 
```python
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y)
plt.show()
```
![WorkshopImage 1](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage1.png)
![WorkshopImage 1 part 2](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage1part2.png)



Now that we have presented the idea that we can plot a graph using two arrays, we can try plotting two plots on the same graph. For illustration purposes, we will use blue and red for the diagrams. 
```python
X = [1,2,3]
Y = [1,2,3]
Z = [2,3,4]
plt.plot(X,Y , marker='.',linestyle='dashed',color='r', label='red')
plt.plot(X,Z , marker='.',linestyle='dashed',color='b', label='Blue')
plt.xlabel('x-axis')
plt.ylabel('y-axis')
plt.title('This is a title!')
plt.legend()
plt.show()
```
![WorkshopImage 4](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage4.png)


Take note that these aestatics could be modified easily, however it would be discussed in the core visualistaion part of the workshop.
