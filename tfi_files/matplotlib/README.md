---
sort: 0
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
Supposed that we would like to make a plot between 2 variables, we would required the usage of two arrays. For this example, we would have array X and Y containing three variables each. The image generated on the right showcase the points generated from the arrays of the two variables which gives their cartisan co-ordinates. 
```python
x = [1,2,3]
y = [4,2,0]
plt.plot(x,y)
plt.show()
```
![WorkshopImage 1](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop1.png)

