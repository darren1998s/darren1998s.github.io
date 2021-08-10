---
sort: 3
---
## Other Graphical Visualisation

Here we would be exploring the different plot that could be done using mathplotlib in the section.

We will begin with the elementary plots that we can do with Mathplotlib:
* Multi-plots 
* Subplots
* Scatter
* Line
* Histograms
* Bar

First, we would be able to generate two different plots on the same graph by plotting twice on the same graph.


```python
X = [1,2,3]
Y = [1,2,3]
Z = [2,3,4]
plt.plot(X,Y,label='first plot')
plt.plot(X,Z,label='second plot')
plt.show()
```
![WorkshopImage 8](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage8.png)

## Subplots

However, it would be impossible to generate 2 plots on the same figure without utilizing the subplot function as the final line of code which uses plot would overwrite the previous line. Thus, we would be able to plots on the same graph.


```python
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
![WorkshopImage 9](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage9.png)


Similarly, we would be able to make a plot for a secondary axis by cloning the x-axis which allows one to do a quick comparsion between the datasets
```python
X = [1,2,3]
Y = [1,2,3]
Z = [4,3,2]
fig, ax = plt.subplots(figsize=(8,8))
axd = ax.twinx()
ax.plot(X, Y, 'black')
axd.plot(X, Z, 'blue')
ax.set_xlabel('X axis')
ax.set_ylabel('Y data', color='black')
axd.set_ylabel('Z data', color='blue')
plt.show()
```
![WorkshopImage 10](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage10.png)
## Scattered graphs and Bar charts

Based on the graphical output that have been discussed in this section, we would be able to illustrate how other graphs would look if we were to plot them out.

For the first example, we would be using scattered plot and bar graphs.
```python
x = [1,2,3]
y = [1,2,3]
fig, ax = plt.subplots(nrows = 1, ncols = 3, figsize = (24,8))
ax[0].plot(x,y, color='black',label='Original')
ax[0].set_xlabel('x-axis of original graph')
ax[0].set_ylabel('y-axis of original graph')
ax[0].set_title('This is a title of Original graph!')
ax[0].legend()


ax[1].scatter(x,y, color='black',label='scattered graph')
ax[1].set_xlabel('x-axis of scattered graph')
ax[1].set_ylabel('y-axis of scattered graph')
ax[1].set_title('This is a title of scattered graph!')
ax[1].legend()

ax[2].bar(x,y, color='black')
ax[2].set_xlabel('x-axis of Bar Graph')
ax[2].set_ylabel('y-axis of Bar Graph')
ax[2].set_title('Bar Graph!')
ax[2].legend()

plt.show()
```
source: `{{ page.path }}`
