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
x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,linestyle='dashed')

```
 

```python
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y,linewidth='4')    
```
Next we would be modifying the difference between marker types and sizes
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y)
plt.show()

x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,marker='.')
plt.show()

x = [1,2,3]
y = [1,2,3]
plt.plot(x,y,marker='.',markersize='10')       
plt.show()

Next we would be able to modify the color of both markers and line plot by formatting the code used.



We can adjust the range of the plot by shifting the limits imposed on the range of the diagrams
```
python
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
```
python
x = [1,2,3]
y = [1,2,3]

plt.plot(x,y,color='black')
plt.show()


plt.plot(x,y,color='black')
plt.set_xlabel('x-axis of newly formatted line')
plt.set_ylabel('y-axis of newly formatted line'')
plt.set_title('This is a title of newly formatted line!')
plt.legend()

plt.show()
```
Suppose that we would like to modify the labels sizes and title sizes,
we could update the parameters of the library so that the changes would be done on all graphs.


source: `{{ page.path }}`
