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

Next, we would try to plot two different plots on the same graph.
```python
X = [1,2,3]
Y = [4,2,0]
Z = [6,2,4]
plt.plot(X,Y, marker='*',markersize=12,linestyle='dashed',linewidth =1,color='#ff0000')
plt.plot(X,Z,marker='.',markersize=10,linestyle='-',linewidth =1,color='#00ff00'
plt.show()
```
![WorkshopImage4](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/tfi/basics%20plt/workshop4.png)

