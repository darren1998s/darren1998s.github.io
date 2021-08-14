---
sort: 5
---
Here we would explore how one would be able to plot scatter graphs, histograms and bar charts.

For the first example, we would utilise code in the Act 1 where we plot 2 array against one another using standard plot function and simulated it in a scatter graph and a bar graph

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
![WorkshopImage13](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop13.png)



source: `{{ page.path }}`