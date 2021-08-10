---
sort: 3
---
## Other Graphical Visualisation

Here we would be discussing the different plot that could be done using mathplotlib.

We will begin with the elementary plots that we can do with Mathplotlib:
* Scatter
* Line
* Histograms
* Bar


Similarly, we can format it such that we would be able to plot 2 graphs on separate plots.
```python
X = [1,2,3]
Y = [1,2,3]
Z = [2,3,4]
fig, ax = plt.subplots(nrows = 1, ncols = 2, figsize = (16,9))
ax[0].plot(X,Y , marker='.',linestyle='dashed',color='r', label='Red')
ax[0].errorbar(X,Y,xerr=0.1,yerr=0.1, fmt=' ',ecolor='black')#errors could be an array format as well
ax[1].plot(X,Z , marker='.',linestyle='dashed',color='b', label='Blue')
ax[1].errorbar(X,Z,xerr=0.1,yerr=0.1, fmt=' ',ecolor='black')
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
![WorkshopImage 5](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage5.png)




source: `{{ page.path }}`
