---
sort: 2
---

## Adding labels

Adding onto the introduction, we would be able to add labels and modify basic aestatics on the plot as it is being generated from python. 
The general paramaters that we could modify are namely:
* Line Width
* Line Style
* Markers Type
* Marker Size
* Positons
* Labels
* Legends

First we would modify Linestyle and Line Width to illustrate the difference that one could see from the following images.

![WorkshopImage 2](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage2.png)

Next, we would be able to see the difference by changing the Markers Types and Sizes 
```python
#Second graph code
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,linestyle='dashed')

```
 

```python
#Third Graph Code
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y,linewidth='4')    
```
Next we would be modifying the difference between marker types and sizes 
![WorkshopImage 3](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage3p1.png)

```python
#Middle Graph

x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,marker='.')
plt.show()
#Final Graph
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,marker='+',markersize='10')       
plt.show()
```
Next we would be able to modify the color of both markers and line plot by formatting the code used.
![WorkshopImage 4](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage4.png)
```
python
#Middle graph
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y, color='red')
#Final Graph
plt.plot(x,y,color='black',marker='.', markerfacecolor='r',markersize='10')  
```



We can adjust the range of the plot by shifting the limits imposed on the range of the diagrams
![WorkshopImage 5](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/WorkshopImage5.png)
```python
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y,color='black')
plt.show()


plt.plot(x,y,color='black')
plt.set_xlim([0,3])
plt.set_ylim([0,3])
plt.show()
```
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
plt.set_title('Different legend location with colored ticks!')
plt.legend(['Different legend location with colored ticks'], loc='lower left')
plt.tick_params(direction='in', length=6, width=2, colors='r',
               grid_color='r', grid_alpha=0.5)
plt.show()
```
we could update the parameters of the library so that the changes would be done on all graphs.


source: `{{ page.path }}`
