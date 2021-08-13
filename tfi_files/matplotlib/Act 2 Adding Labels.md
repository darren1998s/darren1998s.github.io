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
![WorkshopImage4](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop4.png) 

next we would be modifying the graphs with their necessary labels with a legend 
![WorkshopImage 6](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage6.png)

```python
#Right graph
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y,color='black')
plt.set_xlabel('x-axis of newly formatted line')
plt.set_ylabel('y-axis of newly formatted line'')
plt.set_title('This is a title of newly formatted line!')
plt.legend()

plt.show()
```
We would be able to modify the code further to change the location and size of the legend,labels and ticks.
![WorkshopImage 7](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage7.png)
```python
#The generated graph on the middle
font={'family': 'cursive',
        'color':  'darkred',
        'weight': 'normal',
        'size': 16,
        }
plt.set_xlabel('x-axis of different colored sized labelled line',fontdict=font)
plt.set_ylabel('y-axis of different colored sized labelled line',fontdict=font)
plt.set_title('This is a title of different colored sized labelled line !',size=18)
plt.plot(x,y, color='black',label='Different color and size labels')
plt.legend()
plt.show()
#The generated graph on right
plt.plot(x,y, color='black')
plt.set_xlabel('x-axis of Different legend location with colored ticks')
plt.set_ylabel('y-axis of Different legend location with colored ticks')
plt.set_title('Different legend location with colored ticks!',size)
plt.legend(['Different legend location with colored ticks'], loc='lower left',prop={'size': 6})
plt.tick_params(direction='in', length=6, width=2, colors='r',
               grid_color='r', grid_alpha=0.5)
plt.show()
```
Finally, we are able to modify the basic error bars on the graph, we would be able to illustrate the error propagated by the uncertainity of the value
```python
x = [1,2,3]
y = [1,2,3]
font={'family': 'cursive',
        'color':  'black',
        'weight': 'normal',
        'size': 16,
        }
fig, ax = plt.subplots(nrows = 1, ncols = 2, figsize = (16,8))
ax[0].plot(x,y, color='black',label='Original',)
ax[0].set_xlabel('x-axis of original graph',fontdict=font)
ax[0].set_ylabel('y-axis of original graph',fontdict=font)
ax[0].set_title('This is a title of Original graph!',size=18)
ax[0].legend()


ax[1].plot(x,y, color='black',label='Different color and size labels')
ax[1].set_xlabel('x-axis of graph with error bars',fontdict=font)
ax[1].set_ylabel('y-axis of graph with error bars',fontdict=font)
ax[1].set_title('This is a title of graph with error bars !',size=18)
ax[1].errorbar(x,y,yerr=0.1,color='black',capsize=5,elinewidth=2,markeredgewidth=2)
ax[1].legend()
plt.show()
```
![WorkshopImage 12](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage12.png)

source: `{{ page.path }}`
