## Plotting Secondary Y axis on the same graph 
Here, we would explore how one would plot a secondary axis on a separate graph which can be done by utilising subplot function.

For the first example, we would be utilising a duplicate of the x-axis to plot the range of second y values.
```python
X = [1,2,3]
Y = [1,2,3]
Z = [4,2,0]
fig, ax1 = plt.subplots(nrows = 1, ncols = 1, figsize=(8,8))
ax1.plot(X,Y,label='first plot',color='r')
ax2 = ax1.twinx()
ax2.plot(X,Z,label='second plot',color='b')
ax1.set_xlabel('X axis')
ax1.set_ylabel('First y-axis created from (X,Y)', color='red')
ax2.set_ylabel('Secondary y-axis created from (X,Z)', color='b')
ax1.legend()
ax2.legend()
plt.suptitle('Combination graph')
plt.show()
```

![WorkshopImage11](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop11.png)

For the second example, we would be utilising a duplicate of the y-axis to plot the range of second y values.
```python
X = [1,2,3]
Y = [1,2,3]
Z = [4,2,0]
fig, ax1 = plt.subplots(nrows = 1, ncols =1,figsize=(16,8))
ax2 = ax1.twiny()
ax1.plot(X,Y,label='first plot',color='r')
ax2.plot(X,Z,label='second plot',color='b')
ax1.set_xlabel('First x-axis created from (X,Y)')
ax1.set_ylabel('Y-axis', color='red')
ax2.set_xlabel('Secondary x-axis created from (X,Z)', color='b')
ax1.legend()
ax2.legend(loc=7)
plt.suptitle('Combination graph')
plt.show()
```
![WorkshopImage12](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop12.png)
