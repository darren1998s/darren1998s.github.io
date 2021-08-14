## Plotting Secondary Y axis on the same graph 
Here, we would explore how one would plot a secondary axis on a separate graph which can be done by utilising subplot function.


```python
X = [1,2,3]
Y = [1,2,3]
Z = [1,2,3]
fig, ax1 = plt.subplots(nrows = 1, ncols = 2)
ax2 = ax1.twinx()
ax1.plot(X,Y,label='first plot',color='r')
ax2.plot(X,Z,label='second plot',color='b')
ax1.set_xlabel('X axis')
ax1.set_ylabel('First y-axis created from (X,Y)', color='red')
ax2.set_ylabel('Secondary y-axis created from (X,Z)', color='b')
plt.show()
```

![WorkshopImage11](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop11.png)
