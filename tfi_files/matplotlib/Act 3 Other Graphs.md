---
sort: 3
---
## Subplots
### Second graph generation
Here we would be exploring how one would be able to plot two graphs side by side independent of one another.
First, we would be able to generate two different plots on the same graph by plotting twice on the same graph.

```python
X = [1,2,3]
Y = [1,2,3]
Z = [1,2,3]
fig, ax = plt.subplots(nrows = 1, ncols = 2)
ax[0].plot(X,Y,label='first plot',color='r')
ax[1].plot(X,Z,label='second plot',color='b')
plt.show()
```
![WorkshopImage 8](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop8.png)

### Title and label generation  
In a single plot, one would only need to utilise plt.xlabel,plt.ylabel and plt.title to generate labels for the x-axis, y-axis and title representively. However, for one to generate the respective labels in a subplot, we would need to utilise set_xlabel, set_ylabel and set_title for the individual plots as seen below. Additionally,we would be able to include the final title of all graphs here.

```python
X = [1,2,3]
Y = [1,2,3]
Z = [1,2,3]
fig, ax = plt.subplots(nrows = 1, ncols = 2)
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
plt.suptitle('Title of Figure')
plt.show()
```
![WorkshopImage 9](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop9.png)

### Additional formatting
As seen from the previous graph, the formatting of the space between figures requires some fixing as y-axis label of second label overlaps with the area of the first graph.
Thus, we would be required to format the figures by inputting constrained_layout. Additionally, we would be able to modify the size of the figure from figsize.
```python
X = [1,2,3]
Y = [1,2,3]
Z = [1,2,3]
fig, ax = plt.subplots(nrows = 1, ncols = 2,constrained_layout=True,figsize=(16,9))
ax[0].plot(X,Y , marker='.',linestyle='dashed',color='r', label='Red')
ax[1].plot(X,Z , marker='.',linestyle='dashed',color='b', label='Blue')
ax[0].set_xlabel('x-axis of Red',fontsize=18)
ax[0].set_ylabel('y-axis of Red',fontsize=18)
ax[0].set_title('This is a title of Red!',fontsize=24)
ax[0].legend()
ax[1].set_xlabel('x-axis of Blue',fontsize=18)
ax[1].set_ylabel('y-axis of Blue',fontsize=18)
ax[1].set_title('This is a title of Blue!',fontsize=24)
ax[1].legend()
plt.suptitle('Title of Figure',fontsize=36)
plt.show()
```
![WorkshopImage10](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop10.png)

