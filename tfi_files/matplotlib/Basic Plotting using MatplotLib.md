---
sort: 1
---

# Matplotlib: Basic Plotting
## Introduction to plot function of Matplotlib




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
