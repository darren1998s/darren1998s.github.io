---
sort: 2
---

## Adding labels to the graph to give meaning to plot 

Adding onto the introduction, we would be able to add labels and modify basic aestatics on the plot as it is being generated from python. 
The general paramaters that we could modify are namely:
* Labels
* Legends
* Error bars

First we would add Title and axis labels with Legend onto the previous graphs generated from section 1.

```python
X = [1,2,3]
Y = [4,2,0]
plt.plot(X,Y, marker='.',linestyle='dashed',color='r',label='plot')
plt.xlabel('x-axis of plot')
plt.ylabel('y-axis of plot')
plt.title('Title of Plot')
plt.legend()
plt.show()
```
![WorkshopImage5](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop5.png) 
### Exploring different sized Labels
Next, we would explore how one could change the sizes of the labels
```python
X = [1,2,3]
Y = [4,2,0]
plt.plot(X,Y, marker='.',linestyle='dashed',color='r',label='plot')
plt.xlabel('x-axis of plot', fontsize=4)
plt.ylabel('y-axis of plot',fontsize=8)
plt.title('Title of Plot',fontsize=12)
plt.legend()
plt.show()
```
![WorkshopImage6](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop6.png) 

### Adding Error bars 
In this section, we would explore adding error bars for the plot to showcase the range of error presented in the graph. One would have to make the connection between points transparent by making the errorbar plot linestyle blank as seen in the code.
```python
X = [1,2,3]
Y = [4,2,0]
plt.plot(X,Y, marker='.',linestyle='dashed',color='black',label='plot')
plt.errorbar(X,Y,yerr=0.1,color='black',capsize=5,elinewidth=2,markeredgewidth=2)
plt.xlabel('x-axis of plot', fontsize=4)
plt.ylabel('y-axis of plot',fontsize=8)
plt.title('Title of Plot',fontsize=12)
plt.legend()
plt.show()
```

![WorkshopImage7](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop7.png) 


source: `{{ page.path }}`
