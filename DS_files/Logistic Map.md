---
sort: 1
---

# Modelling Population Dynamics of Organisms and negative density dependence
**Authors**: [Darren Teo](https://www.linkedin.com/in/darren-teo-3125871a1/)

**About the Authors**: Year 3 student in NUS in Special Programme in Science, I am currently majoring in Life Sciences.

**About this page**: This is essentially a simple project coded in python that explores chaotic behaviors in dynamical systems. More specifically, the logistic map. This page was meant to serve as a sample project for a NUS module SP2273, "Working on Interdisciplinary Science, Pythonically".

## Introduction

When looking at organisms in the wild, we often have to build models in order to make predictions about changes in their population[$^{[1]}$](#References). Many different factors can drive changes in the population of organisms. In this example, we will be considering the effects of finite resources on the growth of the number of rabbits or crabs in a toy model

This entire project is going to explore a simple mathematical equation and how it can give insights into ecological systems. Such mathematical equations are often referred to as models. There are two types of models in mathematical biology, a discrete time model and continuous time model[$^{[2]}$](#References). For the purposes of this project, we are only going to be looking at discrete time models.

### Discrete Time model

A discrete time model is essentially a model that has time at set intervals. You can think of this as the model having a finite number of data points starting from the initial time to some final time taking steps of some time interval. For example, if we choose a time interval is 1 second, there will be a data point at 1 second, then the next at 2 seconds, but not at 1.5 seconds.

Oftentimes, discrete time models use something called a difference equation[$^{[3]}$](#References) (not to be confused with its mathematical older brother, differential equations) which have this form (assuming $A_t$ is a certain species population at time $t$):

$$A_{t+1} = kA_t$$

Where the species population at time $t+1$ is directly affected by the species population at time $t$.

## Why it is important to study this?

Mathematical models that predict biological systems will give us insights and predictions on future systems. Assuming we are an employee of NParks, and we would want to predict if a certain environmental measure is helping with improving the ecosystem. We would then have a mathematical model of how certain species of animals are growing and see if various populations of species would die out.

An example of this would be the tree types and populations in Singapore mangroves affecting the population of Tree-climbing crabs (_Episesarma spp._). Studying these crabs are particularly important because they recycle carbon on the mangrove floors and aid in decomposition, which makes them a keystone species[$^{[4]}$](#References). The loss of habitat could result in potential threat to them[$^{[5]}$](#References), which would be really bad!


## Fibonacci Model

So let's take a look at a very simple model first.
A simple model is the Fibonacci rabbit problem[$^{[6]}$](#Reference). Assuming a population of adult rabbits, $A$, juvenile rabbits, $J$ at time, $t$, where it follows this formula: $$A_{t+1} = J_{t} + A_t$$

This is because the number of adult rabbits is governed by how many adult rabbits there are and number of juvenile rabbits that will mature to become adult rabbits. However, the number of juvenile rabbits are also governed by how many adult rabbits there are too!


| $$t$$   |  $$A_t$$            |   $$J_t$$ |
|---------|:-------------------:|:-------------------:|
| $$t_0$$ | 2                   |1                    |
| $$t_1$$ | 3                   |2                    |
| $$t_2$$ | 5                   |3                    |
| $$t_3$$ | 8                   |5                    |
| $$t_4$$ | 13                  |8                    |
| $$t_n$$ | $$A_{t-1} + A_{t}$$ |$$J_{t-1} + J_{t}$$  |

This means that, we start with 2 rabbits and these 2 rabbits would produce 1 rabbit. Then these 3 rabbits would produce 2 additional rabbits and so on.

We can actually simplify the equation to this for ease of modelling later!

$$A_{t+1} = A_{t-1} + A_t$$

As you can already tell, it is tedious to generate a table like this, so let us do it in code instead!

### Putting this into context

Now, what if we **ARE** a manager of NParks and we want to track the population of _Episesarma spp._ over time in Singapore? We can employ the same model and assume the population of crabs follow the fibonacci sequence.


```python
# Import things
import numpy as np
import matplotlib.pyplot as plt
```


```python
# Simulate a timeframe
ts = np.arange(0,10)

# Initialize a list to store our As
As = [1]*len(ts)

# Let us run a loop to simulate our model
for t in ts:
    # The formula of our model
    As[t] = As[t-2] + As[t-1]
```

Now that we have the results from the model, we can plot them using `ts` as our x-axis and `As` as our `y-axis`.


```python
plt.plot(ts, As,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$A_t$', size = 20)
plt.show()
```


![png](https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/main/assets/images/Logistic%20Map/output_4_0.png)


### Simplifying the workflow
Since we would be exploring more models today, it would be nice to simulate these models easily. Hence, we can push all of these code into 1 function, `simulate_func`.

If we inspect our modelling code from before, we can point out some things:
```python
ts = np.arange(0,10) #<-- Array of time steps with 10 being max_t
As = [1]*len(ts)
for t in ts:
    As[t] = As[t-2] + As[t-1] #<-- Func to calc A_t+1 using A_t & A_t-1
```


`simulate_func` will take in arguments, the modelling function `func` and, `max_t` for the maximum time frame.

We then need to make a function to calculate A_t of the next time step, we can easily do this by passing in the time t and a list of As so we can use list indexing:

```python
def fibo_func(As,t):
    return As[t-2] + As[t-1]
```


```python
def simulate_func(func, max_t, A0 = 1):
    ts = np.arange(0,max_t)
    As = [A0]*len(ts)
    for t in ts:
        As[t] = func(As,t)
    return As

def fibo_func(As,t):
    return As[t-2] + As[t-1]

# Yep this works for us!
simulate_func(fibo_func, 10)
```




    [2, 3, 5, 8, 13, 21, 34, 55, 89, 144]



If you think about the previous crab model, it is a little unrealistic. This is because if the crab population did follow that curve, there would be infinite crabs in the world and every tree would be filled with CRABS! Regardless of how great that would be, we know this is not true in the real world because we are not surrounded by crabs.

So what is going on here?

## Negative Density Dependence

Every biological system has limited resources (carrying capacity `K`) such as limited space and food sources. Hence the population of species in every environment would be limited in some way! Thus, we would need to introduce it in some way.

I would not go into the details as to how this model came about[$^{[7]}$](#References), just... magic. Let `N` be the number of individuals and `r` to be a reproductive rate.

$$N_{t+1} = \left(1+r\left(1-\frac{N_t}{K}\right)\right)N_t$$

This system is modelled below using our previously defined function.


```python
r = 0.5
K = 100
def density_dependence(Ns,t):
    y = (1 + r*(1-(Ns[t-1]/K)))*Ns[t-1]
    return y


max_t = 25
Ns = simulate_func(density_dependence, max_t)
ts = np.arange(0,max_t)

plt.plot(ts, Ns,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$N_t$', size = 20)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_8_0.png?raw=true)


If we relate this new crab model to the original fibonacci crab model, intuitively we know that this is more realistic.

Let us plot this new graph with the previous one and see the difference!


```python
max_t = 25
Ns = simulate_func(density_dependence, max_t)
ts = np.arange(0,max_t)

As = simulate_func(fibo_func, max_t)

ts = np.arange(0,max_t)

plt.plot(ts, Ns,'o-', label = 'Density Dependence')
plt.plot(ts, As,'o-', label = 'Fibonacci Problem')

plt.ylim(0,300)
plt.xlabel('$t$', size = 20)
plt.ylabel('$N_t$ or $A_t$', size = 20)
plt.legend()
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_10_0.png?raw=true)


Just like how intuition has told us, the fibonacci crab model predicts the population to grow geometrically and there would be infinite crabs given infinite time. Whereas, according to the density dependence model, given infinite time, the population of crabs would stay constant.

This model is more in-line with what we see in reality! Let us explore this model further.

### Equilibrium
Let us see what happens if we forcefully decrease the population of crabs at `time = 20`. This could be due to mass poaching by the locals or rising sea levels which submerges a significant number of trees which decreases the available trees that crabs can climb on to avoid predators. 


```python
def density_dependence_perturb(Ns,t):
    y = (1 + r*(1-(Ns[t-1]/K)))*Ns[t-1]
    
    # At time t = 20, forcefully drop the population by 50
    if t == 20:
        y -= 50
    return y

max_t = 40
Ns = simulate_func(density_dependence_perturb, max_t)
ts = np.arange(0,max_t)

plt.plot(ts, Ns,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$N_t$', size = 20)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_12_0.png?raw=true)


This is interesting. It seems like if we introduce a change in population (pertubation), the system still grows to a certain point. This is called a stable equilibrium!

## Logistic Map

The previous model: $$N_{t+1} = \left(1+r\left(1-\frac{N_t}{K}\right)\right)N_t$$

We can get rid of both `K` and `r` by doing cool math and replace them with `a`. This is important because it makes the analysis simpler as we went from a model with two parameter to a model with one[$^{[8]}$](#References)!

$$x_t = \frac{r}{1+r}\frac{N_t}{K}, a = 1+r$$

And thus:

$$x_{t+1} = ax_t(1-x_t)$$

An important thing about this model is that the maximum number $x$ can be is `1.0` and thus the population of crabs now is a PROPORTION of the carrying capacity ($K$) instead of an absolute number.


```python
a = 1.5

def log_map(xs,t):
    y = a*xs[t-1]*(1-xs[t-1])
    return y

max_t = 20
xs = simulate_func(log_map, max_t, A0 = 0.01)
ts = np.arange(0,max_t)

plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_14_0.png?raw=true)


An interesting thing we can do now is to vary the value of `a` and check the dynamics!


```python
a = 2.9
max_t = 50
xs = simulate_func(log_map, max_t, A0 = 0.01)
ts = np.arange(0,max_t)

plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_16_0.png?raw=true)


Cool, by increasing the value of `a = 2.9`, we can see some interesting oscilations. However, these oscilations do not last forever. As we increased `max_t = 50`, we can see that these oscilations start to **dampen** and eventually reach the state previously explored :)

### What this means for our model?

This model somewhat follows real-life biological systems more closely than our other models so far. This is because there are some sort of variation being introduced before equilibrium is reached!

### Increasing `a`

Let us increase `a` to 3.1 and see what happens


```python
max_t = 70
a = 3.1
xs = simulate_func(log_map, max_t, A0 = 0.01)
ts = np.arange(0,max_t)

plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_18_0.png?raw=true)


At `a = 3.1` it seems that the system will exhibit some sort of cyclical behaviour after a period of time. If we zoom in to this area of the graph, we can inspect it more closely!


```python
plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)

# Setting Limits
plt.xlim(50,70)
plt.ylim(0.5,0.8)

# Plotting cool lines
plt.hlines(xs[-2:], xmin = 50, xmax = 70, 
           linestyle = 'dashed', color = 'orange', alpha = 0.75)

# Giving a nice grid 
plt.grid(alpha = 0.25)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_20_0.png?raw=true)


This is remarkable. At this value of `a = 3.1`, there seems to be a stable limit cycle. More specifically, a stable two-cycle. We can conclude that this is a stable two-cycle system because as plotted above, the points on the graph fall into 1 of the two lines.

More importantly, these cycles / oscillations do not dampen like the case of when `a = 2.9` seen earlier. The next interesting question would be, what would now happen if we increased `a` further?

### a = 3.5


```python
max_t = 70
a = 3.5
xs = simulate_func(log_map, max_t, A0 = 0.01)
ts = np.arange(0,max_t)

plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)

# Setting Limits
plt.xlim(50,70)
plt.ylim(0.35,0.9)

# Plotting cool lines
plt.hlines(xs[-4:], xmin = 50, xmax = 70, 
           linestyle = 'dashed', color = ['orange', 'k', 'red','green'], alpha = 0.75)

# Giving a nice grid 
plt.grid(alpha = 0.25)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_22_0.png?raw=true)


Now instead of 1 stable equilibrium or a stable 2-cycle system, we are presented with a stable 4-cycle system! We can tell this is the case as all the points will intersect with one of the 4 horizontal lines in this order:

$$black \rightarrow red \rightarrow green \rightarrow orange$$

As always, we can tell from these lines, the cycles do not dampen as time goes on as well. Hence it is a stable 4-cycle!

Here comes the super interesting thing. What happens if we continue to increase the value of `a`?


```python
max_t = 70
a = 3.9
xs = simulate_func(log_map, max_t, A0 = 0.01)
ts = np.arange(0,max_t)

plt.plot(ts, xs,'o-')
plt.xlabel('$t$', size = 20)
plt.ylabel('$x_t$',size = 20)

# Lines 
plt.hlines([0.8312549282779312, 0.8124735248492181], 
           xmin = [xs.index(0.8124735248492181)-5,xs.index(0.8312549282779312)-5], 
           xmax = [xs.index(0.8124735248492181)+5,xs.index(0.8312549282779312)+5],
          color = 'orange', linestyle = 'dashed')

plt.vlines([xs.index(0.8124735248492181), xs.index(0.8312549282779312)], 
           ymin = 0.4, ymax = 1,color = 'orange', linestyle = 'dashed')

# Giving a nice grid 
plt.grid(alpha = 0.25)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_24_0.png?raw=true)


On first glance, there does not seem to be any stable system seen. Maybe if we try to align these points denoted in dashed-orange lines together, we would see something.


```python
## Splitting the X axis into 2
## First set of X-axis
xs_2 = xs[xs.index(0.8124735248492181)-2:]
xs_1 = xs[xs.index(0.8312549282779312)-2:]
xs_1 = xs_1[:len(xs_2)]

plt.plot(np.arange(0,len(xs_2)), xs_1,'o-', label = 'First Set')
plt.plot(np.arange(0,len(xs_2)), xs_2,'o-', label = 'Second Set')

# Giving a nice grid 
plt.grid(alpha = 0.25)
plt.legend(loc = 'lower left')
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_26_0.png?raw=true)


This is very interesting, it does not seem that at `a = 3.9` exhibits any stable cycle even after increasing `max_t`. We see similar patterns being repeated then they are no longer observed. Let us recap all the graphs we have generated so far!


```python
a_s = [1.5, 3.1, 3.5, 3.9]
max_t = 40
ts = np.arange(0,max_t)

figure, ax = plt.subplots(nrows = 2, ncols = 2, figsize = (9,9))
ax1, ax2, ax3, ax4 = ax.ravel()
axes = [ax1, ax2, ax3, ax4]
all_xs = [] # For the next part :)
for i in range(len(a_s)):
    a = a_s[i]
    xs = simulate_func(log_map, max_t, A0 = 0.01)
    all_xs.append(xs)
    axes[i].plot(ts, xs, 'o-')
    axes[i].set_xlabel('$t$', size = 20)
    axes[i].set_ylabel('$x_t$',size = 20)
    axes[i].set_title(f'a: {a}', size = 15)

plt.tight_layout()
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_28_0.png?raw=true)


We have seen these graphs where 3 out of 4 values of `a` generated a stable equilibrium / cycles. Let us explore, if the inital conditions `A0` would affect anything.

I am going to plot the graphs with identical values of `a` with just a slight change in `A0`, from 0.01 to 0.0101.


```python
figure, ax = plt.subplots(nrows = 2, ncols = 2, figsize = (9,9))
ax1, ax2, ax3, ax4 = ax.ravel()
axes = [ax1, ax2, ax3, ax4]
for i in range(len(a_s)):
    a = a_s[i]
    xs = simulate_func(log_map, max_t, A0 = 0.0101)
    axes[i].plot(ts, xs, 'o-', label = 'A0 = 0.0101')
    axes[i].plot(ts, all_xs[i], 'o-', label = 'A0 = 0.01')
    axes[i].legend()
    axes[i].set_xlabel('$t$', size = 20)
    axes[i].set_ylabel('$x_t$',size = 20)
    axes[i].set_title(f'a: {a}', size = 15)

plt.tight_layout()
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_30_0.png?raw=true)


As expected, for the three out of four systems, the system equilibriated at their stable equilibrium or stable-cycles.

Interestingly, the last graph (`a = 3.9`) does not seem to equilibriate at any value! So what is actually going on here?

## Chaos

A chaotic system has the following properties:

- By definition, Chaos is loosely defined as sensitivity to initial conditions!
- Similar structures appear over and over, but never perfectly repeat themselves
- The behaviour looks stochastic, but it is completely deterministic
- Can be hard to distinguish stochasticity and chaos from time series alone



### Bifurcation Plot

Since we know that changing `a` changes the dynamic of the system, more specifically, the equilibrium or stable cycles of the system. We can plot these equilibrium states against values of `a`.

The way we can do this is to do the following:

1. Simulate the time series plot for `max_t = 10000` to ensure the system reaches equilibrium.
2. Store the last 100 points from the time series.
3. Repeat steps 1 & 2 for all values of `a`.


```python
max_t = 10000
all_xs = []
all_as = np.arange(2.5,4,0.001)
ts = np.arange(0,max_t)

for a in all_as:
    xs = simulate_func(log_map, max_t, A0 = 0.01)
    all_xs.append(xs[-100:])

plt.figure(figsize = (12,12))
plt.plot(all_as, all_xs, '.', markersize = 1)
plt.xlabel('$a$', size = 25)
plt.ylabel(r'$\bar N$', size = 25)
plt.xticks(size = 15)
plt.yticks(size = 15)
plt.title(r'Bifurcation plot of $\bar N$ vs $a$', size = 30)
plt.show()
```


![png](https://github.com/darren1998s/darren1998s.github.io/blob/main/assets/images/Logistic%20Map/output_32_0.png?raw=true)


## References

\[1\] Torres, N. V.; Santos, G. The (Mathematical) Modeling Process in Biosciences. Frontiers in Genetics, 2015, 6. https://doi.org/10.3389/fgene.2015.00354.
<br>
\[2\] Motta, S.; Pappalardo, F. Mathematical Modeling of Biological Systems. Briefings in Bioinformatics, 2012, 14, 411–422. https://doi.org/10.1093/bib/bbs061.
<br>
\[3\] Discrete-Time Models with Difference Equations https://math.libretexts.org/@go/page/7782.
<br>
\[4\] Lee, S. Potential Trophic Importance of the Faecal Material of the Mangrove Sesarmine Crab Sesarma Messa. Marine Ecology Progress Series, 1997, 159, 275–284. https://doi.org/10.3354/meps159275.
<br>
\[5\] Sivasothi, N. Niche Preferences of Tree-climbing Crabs in Singapore Mangroves. Crustaceana, 2000, 73, 25–38. https://doi.org/10.1163/156854000504093.
<br>
\[6\] Sigler, L. Fibonacci's Liber Abaci, Springer 2002.
<br>
\[7\] Density Dependence, Regulation and Variability in Animal Populations. Philosophical Transactions of the Royal Society of London. Series B: Biological Sciences, 1990, 330, 141–150. https://doi.org/10.1098/rstb.1990.0188.
<br>
\[8\] Logistic Population Growth https://bio.libretexts.org/@go/page/14190.
