---
sort: 1
---

# Matplotlib: Basic Plotting
## Introduction to plot function of Matplotlib

Matplotlib is a mathematical library which allow us to bring life to data and translate them into graphs which tells us a story.

Some of these graphs are more complex compared to others and depending on what you would like to show would imply different items.

*need nice graphs here*

First, we would need to import the library into our python interpreter which allows us to utilise it:

```python
import matplotlib.pyplot as plt
```
Supposed that we would like to make a plot between 2 variables, we would required the usage of two arrays. For this example, we would have array X and Y containing three variables each. 
```python
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y)
plt.show()
```
![WorkshopImage 1](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage1.png)


We would be able to modify several parameters in code to format what would be generated. 
Colour, Markers, Line type, sizes are what we can modify in the presented format.
```python
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y , marker='.',linestyle='dashed',color='#008000')
plt.show()
```
![WorkshopImage 2](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage2.png)


The displayed graph produced has a marker style of '.', linestyle of dashed and a color of green. However, we are still not done as the illustrated diagram lacks labels,title and legend 
```python
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y , marker='.',linestyle='dashed',color='#008000')
plt.xlabel('x-axis')
plt.ylabel('y-axis')
plt.title('This is a title!')
plt.legend()
plt.show()
```
![WorkshopImage 3](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage3.png)

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

Similarly, we can format it such that we would be able to plot 2 graphs on separate plots.
```python
X = [1,2,3]
Y = [1,2,3]
Z = [2,3,4]
fig, ax = plt.subplots(nrows = 1, ncols = 2, figsize = (16,9))
ax[0].plot(X,Y , marker='.',linestyle='dashed',color='r', label='Red')
ax[1].plot(X,Z , marker='.',linestyle='dashed',color='b', label='Blue')
ax[0].set_xlabel('x-axis of Red')
ax[0].set_ylabel('y-axis of Red')
ax[0].set_title('This is a title of Red!')
ax[0].legend()
ax[1].set_xlabel('x-axis of Blue')
ax[1].set_ylabel('y-axis of Blue')
ax[1].set_title('This is a title of Blue!')
ax[1].legend()
plt.show()
```
![WorkshopImage 5(https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage5png)

Take note that these aestatics could be modified easily, however it would be discussed in the core visualistaion part of the workshop.
