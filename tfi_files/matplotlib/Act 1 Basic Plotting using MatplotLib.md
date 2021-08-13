---
sort: 1
---

# Matplotlib: Basic Plotting
## Utilizing arguments in matplotlib
### Using Markers, Linestyle and Color

Now that we have presented the idea that we can plot with elements of basic aestatics with such as markers, linestyle, color and labels we can try plotting two plots on the same graph. For illustration purposes, we will be using the following plot to present the ideas using a Star shaped marker, a Dashed linestyle in Red.
```python
X = [1,2,3]
Y = [4,2,0]
plt.plot(X,Y, marker='.',linestyle='dashed',color='r')
plt.show()
```
![WorkshopImage2](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop2.png)

We would be able to modify these elements further by changing its size, line width and colour in the hexadecimal format.
```python
X = [1,2,3]
Y = [4,2,0]
plt.plot(X,Y , marker='*',markersize=12,linestyle='dashed',linewidth =5,color='#ff0000')
plt.show()
```
![WorkshopImage3](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop3.png)
Take note that these aestatics could be modified easily, however it would be discussed in the core visualistaion part of the workshop.


