---
sort: 2
---

# Visualisation of Data using Python
**Authors**: [Darren Teo](https://www.linkedin.com/in/darren-teo-3125871a1/), [Ervin Chia](https://www.linkedin.com/in/ervin-chia-194080214/)

**About the Authors**: Year 3 student in NUS in Special Programme in Science, Darren and Ervin are currently majoring in Life Sciences and Physics respectively.

**About this tutorial**: This is essentially the same example of the R tutorial but repurposed to make use of Python, the `seaborn` and `matplotlib` package.

# Importing relevant packages
For this tutorial, we would need to import a few things.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

# Loading in iris dataset

For the purposes of this tutorial, we are going to be using the _Iris_ flower dataset introduced by Ronald Fisher in his 1936 paper _The use of multiple measurements in taxonomic problems_.

There are various ways of loading in the iris dataset in python, but let us load in our own csv file to simulate actually loading our own data from a csv file!

```python
#I hosted the same dataset exported from R onto my github for easy access
iris = pd.read_csv('https://raw.githubusercontent.com/darren1998s/darren1998s.github.io/1e6564c4a3f501a980b0dc64f943457928b47d8a/iris.csv', index_col=None)
```

## Inspecting the dataset
This dataset contains Sepal and Petal length / width of different Species of flowers _Iris setosa_, _versicolor_, and _virginica_

We can thus inspect the dataset like this:

```python
print(iris)
```

|  | Sepal.Length  | Sepal.Width  | Petal.Length  | Petal.Width  | Species  |
| -- | ------------- | ------------ | ------------- | ------------ | -------- |
| 1  | 5.1           | 3.5          | 1.4           | 0.2          | setosa   |
| 2  | 4.9           | 3.0          | 1.4           | 0.2          | setosa   |
| 3  | 4.7           | 3.2          | 1.3           | 0.2          | setosa   |
| 4  | 4.6           | 3.1          | 1.5           | 0.2          | setosa   |
| 5  | 5.0           | 3.6          | 1.4           | 0.2          | setosa   |
| 6  | 5.4           | 3.9          | 1.7           | 0.4          | setosa   |


The next step in exploring datasets is to know and understand what the different variables are referring to, such as Sepal Length, Sepal Width, Petal Lengths and Petal Width!

### Optional Information
The dataset numbers are all in centimeters (cm), and the different variables should look foreign to people not well versed in plant morphology. Luckily for us, since this is a well-known dataset, the internet should have figures explaining what each variables mean.

![iris_variable_explain](https://static.packt-cdn.com/products/9781789539462/graphics/9cede6e3-0932-430a-a17e-d30025eb2b02.png)

How handy! [This website](https://subscription.packtpub.com/book/big_data_and_business_intelligence/9781789539462/3/ch03lvl1sec17/text-classification) contains an image on what Sepal / Petal length and widths mean for each row!

## Testing some variable
Perhaps you have this dataset, you think `Sepal.Length` and `Petal.Width` are related in someway, we can visualise this quickly by using the `plt.plot()` function:

```python
plt.plot(iris['Sepal.Length'],iris['Petal.Width'], '.')
plt.show()
```
![SLvsPw](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/irisSepalvsPetal.jpg)

Awesome! There seems to be some sort of association. What if we want to explore other combinations of our variables, such as `Sepal.Length` vs `Petal.Length` and so on and so forth? Luckily for us Python's `seaborn` has a function called `sns.pairplot()` to help us! 

```python
sns.pairplot(iris)
plt.show()
``` 
![irisPairsPlot](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/pairsiris.jpg)

It seems that `Petal.Length` and `Petal.Width` has the strongest positive association from each other. This is to be expected as we would expect a flower with a longer petal length to have a longer petal width as well.

It also seems that `Sepal.Length` and `Petal.Length` have some sort of correlation as well. Lets use these two variables for our examples later!

## Solidifying our research question
Before we proceed any further, it is important in any experiment that we have a solid research question in mind. This is because the type of data presented will help answer your research question. 

Lets say we had a basic research question "Are the lengths of the petals associated with the lengths of sepal in _I. setosa_, _I. versicolor_, and _ I. virginica_?" So while we're doing data collection, we collected other variables as well (see table above).

After data collection, we can casually plot `Sepal.Length` against `Petal.Length` using `plt.plot()`.

```python
plt.plot(iris['Sepal.Length'],iris['Petal.Length'], '.')
plt.show()
```
![SLvsPL](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/irisSepalLvsPetalL.jpg)

It seems to me that Petal Length and Sepal Length have a linear positive correlation with each other!

## Beautifying the graphs

If you were Ronald Fisher and wanted to present about the positive correlation of Sepal Length with Petal Length by using the graph presented above, you will probably not succeed in getting your point across.

We are going to make use of the various functions in `seaborn` to plot. So be sure to check closely! 

We already have our base syntax, where our x-axis is `Sepal.Length` and y-axis is `Petal.Length`.

```python
sns.set_theme(style="darkgrid") #This just makes the graph dark and shiny
sns.scatterplot(x = 'Sepal.Length',y = 'Petal.Length', data = iris)
plt.show()
```
![geompointExample](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PetalLengthvsSepalLength.jpg)


Great, this is the exact same graph as above. Except this has **COLOUR**. There are a few things we can do to make this graph look more presentable.

- [ ] Label size for the numbers
- [ ] Naming of X- and Y-axis
- [ ] Title / subtitle


### Changing the label size & Naming of X- and Y-axis
The first issue that is very obvious is that the labels on the x- and y-axis are very small and may not be readable by people. So let us change that using functions found in `matplotlib`:

```python
sns.scatterplot(x = 'Sepal.Length',y = 'Petal.Length', data = iris)
plt.xlabel("Length of Sepal (cm)", fontsize = 20)
plt.ylabel("Length of petal (cm)", fontsize = 20)
plt.xticks(fontsize = 15)
plt.yticks(fontsize = 15)
plt.show()
```
![Change_Label_Size](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/PLvsSLChangeSize.jpg)


`plt.xticks(fontsize = 15)` and `plt.yticks(fontsize = 15)` changes the numbers on the x- and y-axis whereas `plt.xlabel("Length of Sepal (cm)", fontsize = 20)` and `plt.ylabel("Length of petal (cm)", fontsize = 20)` changes the size and name of the x- and y-axis labels!

So to look at our checklist real quick
- [x] Label size for the numbers
- [x] Naming of X- and Y-axis
- [ ] Title / subtitle

Awesome, now with one look, readers can guess what the graph is about. But to make it even clearer, we will need to add a title to the graph:

```python
sns.scatterplot(x = 'Sepal.Length',y = 'Petal.Length', data = iris).set(title='Length of Petals (cm) vs Length of Sepals (cm)\nof various $\it{Iris}$ flowers')
plt.xlabel("Length of Sepal (cm)", fontsize = 20)
plt.ylabel("Length of petal (cm)", fontsize = 20)
plt.xticks(fontsize = 15)
plt.yticks(fontsize = 15)
plt.show()
```
![Added_TitlenSubtitle](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PLvsSLTitle.jpg)

The code snippet `.set(title='Length of Petals (cm) vs Length of Sepals (cm))` allows each individual graph to have their own titles! and the snippet `\nof various $\it{Iris}$ flowers'` allows for a new line, and in that new line, italacise the word _Iris_ using `$\it{Iris}$`.

Cool, our checklist is done!
- [x] Label size for the numbers
- [x] Naming of X- and Y-axis
- [x] Title / subtitle

### Giving meaning to the graph

Ok we have a decent graph generated, but it does not really tell the reader anything. Linking back to our research question, we want to show that there is a linear association between length of petal and length of sepal of various _Iris_ flower species. The easiest way we can do this is by adding a best-fit linear regression line!

```python
sns.regplot(x = 'Sepal.Length',y = 'Petal.Length', data = iris).set(title='Length of Petals (cm) vs Length of Sepals (cm)\nof various $\it{Iris}$ flowers')
plt.xlabel("Length of Sepal (cm)", fontsize = 20)
plt.ylabel("Length of petal (cm)", fontsize = 20)
plt.xticks(fontsize = 15)
plt.yticks(fontsize = 15)
plt.show()
```
![Added_stat_smooth_line](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PLvsSLLMline.jpg)

Let us compare with our base graph from earlier to the one we have now!

![comparison_base_ggplot](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/comparisonggplotbase.png)

Awesome! With one look, readers can tell exactly what they are looking at and what message you would want them to takeaway! In this case, as `Sepal Length` increases, `Petal Length` increases. 

## Visualising Categorical Variables
In the previous section, both variables shown are continuous variables. Meaning they could take any number. What if one of the variables is categorical, like `Species`?

In the `sns.pairplot()` plot that is provided all the way to the top, you would notice that the `Species` of _Iris_ has some form of correlation with both `Sepal.Length` and `Petal.Length`.

So, if our research question was to investigate the `Sepal.Length` and `Petal.Length` (continuous variable) between `Species` (categorical variables), we can modify some of our code from the previous section to work!

One of the ways to visualise continous variables against categorical variables, is to use a boxplot.

For the sake of simplicity of the tutorial, I would not be changing much of the aesthetics such as label size, label names, tile, etc.
```R
#Plotting Petal length vs Species
sns.boxplot(x="Species", y="Petal.Length", data=iris)
sns.boxplot(x="Species", y="Sepal.Length", data=iris)
plt.show()
```

### Plotting 2 ggplot graphs in the same window

Oh no! The boxplots seemed to have merged together! This calls for a new way of defining graphs by using subplots!

We are going to use the `plt.subplots()` function to define our figure size (if needed), and the number of rows and columns we need! Thankfully, `sns.boxplot()` takes in an argument of `ax = ` as well, allowing us to specify which `ax` is for which box!

The `fig.suptitle()` allows us to define the biggest title for these graphs while `.set(title='')` allows us to define the title for each graph!

```python
#Plotting these two boxplots together in 1 graph
fig, ax = plt.subplots(figsize=(10,12), nrows = 2, ncols = 2)
ax1, ax2 = ax.ravel()


fig.suptitle('Length of Petals (cm) vs Species of various $\it{Iris}$ flowers')
sns.boxplot(x="Species", y="Petal.Length", data=iris, ax = ax1).set(title = 'This is ax1')
sns.boxplot(x="Species", y="Sepal.Length", data=iris, ax = ax2).set(title = 'This is ax2')
sns.boxplot(x="Species", y="Petal.Length", data=iris, ax = ax3).set(title = 'This is ax3')
sns.boxplot(x="Species", y="Sepal.Length", data=iris, ax = ax4).set(title = 'This is ax4')
plt.show()
```
![grid_arrange_boxplots](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PetalvsSpeciesvsSepal.jpg)

It is clear that there is some form of association between both `Sepal.Length` and `Petal.Length` and `Species`, with _I. virginicca_ having the longest `Petal.Length` and `Sepal.Length` and _I. Setosa_ having the shortest.

how do we combine all these information together into a single graph?

## Visualising a continuous variable vs continous variable grouped by categorical variable data

From two sections ago, we could see, on average across all species of _Iris_ flowers, `Sepal.Length` is positively associated with `Petal.Length`. However, we have to be careful with this conclusion as it is prone to **ecological fallacy**. As we are making conclusions on a group and we might conclude this same trend **within** each species of _Iris_ flowers.

So, you might be asking, how do we visualise this when we only have x- and y-axis on a graph? The secret lies in the **COLOR** or **SHAPE** of each data point!


```python
#Grouping
sns.lmplot(x = 'Sepal.Length',y = 'Petal.Length', hue = 'Species', aspect = 1.5, data = iris).set(title='Length of Petals (cm) vs Length of Sepals (cm)\nof various $\it{Iris}$ flowers')
plt.xlabel("Length of Sepal (cm)", fontsize = 20)
plt.ylabel("Length of petal (cm)", fontsize = 20)
plt.show()                           
```
![group_by_species](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PLSL_col.jpg)

Wow! It seems like all three species of _Iris_ are positively associated. With red being _I. Setosa_, green being _I. Versicolor_ and blue being _I. virginica_. There is one thing left! 

Amazing! With this graph, this looks beautiful. At first glance, anyone can immediately understand the following points:

- Each species of _Iris_ flower, the `Petal Length` and `Sepal Length` are positively associated
- Weak association for _I. setosa_ 
- Strong association for _I. versicolor_ and _I. virginica_
- _I. virginica_ have the longest Petal and Sepal on average as compared to the other three species

### Addtional information
Do note, that there can be **TOO MUCH** information on a single graph. Generally, representing the data on x- and y- axis and grouping the points accordingly by colour is the maximum I would go for any graph.

If I would want to explore another variable that I have collected, I would generate another graph at that point.


#### Bad examples of graphs

To illustrate this point, I added another grouping factor of `Sepal.Width` for colour and shifted `Species` to shape.

![bad_too_much_sepal_width](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PLSL_col_bad.jpg)


On first glance, you cannot instantly tell many information. This example serves to show that "more isn't always better" and that the way the data is presented would aid in the readability of your point.

Now, this is a really exagerrated example of what **NOT** to do...
![Why_Did_I_do_dis](https://raw.githubusercontent.com/nus-sps/workshops-R/main/assets/images/iris_PLSL_col_ascinine.jpg)

Theres just too much text / useless information which could have been in a table and it distracts the reader from the main point of the graph...

# End


Text can be **bold**, _italic_, or ~~strikethrough~~. [Links](https://github.com) should be blue with no underlines (unless hovered over).


There should be whitespace between paragraphs. There should be whitespace between paragraphs. There should be whitespace between paragraphs. There should be whitespace between paragraphs.

There should be whitespace between paragraphs. There should be whitespace between paragraphs. There should be whitespace between paragraphs. There should be whitespace between paragraphs.

> There should be no margin above this first sentence.
>
> Blockquotes should be a lighter gray with a gray border along the left side.
>
> There should be no margin below this final sentence.

# Header 1

This is a normal paragraph following a header. Bacon ipsum dolor sit amet t-bone doner shank drumstick, pork belly porchetta chuck sausage brisket ham hock rump pig. Chuck kielbasa leberkas, pork bresaola ham hock filet mignon cow shoulder short ribs biltong.

## Header 2

> This is a blockquote following a header. Bacon ipsum dolor sit amet t-bone doner shank drumstick, pork belly porchetta chuck sausage brisket ham hock rump pig. Chuck kielbasa leberkas, pork bresaola ham hock filet mignon cow shoulder short ribs biltong.

### Header 3

```
This is a code block following a header.
```

#### Header 4

- This is an unordered list following a header.
- This is an unordered list following a header.
- This is an unordered list following a header.

##### Header 5

1. This is an ordered list following a header.
2. This is an ordered list following a header.
3. This is an ordered list following a header.

###### Header 6

| What    | Follows  |
| ------- | -------- |
| A table | A header |
| A table | A header |
| A table | A header |

---

There's a horizontal rule above and below this.

---

Here is an unordered list:

- Salt-n-Pepa
- Bel Biv DeVoe
- Kid 'N Play

And an ordered list:

1. Michael Jackson
2. Michael Bolton
3. Michael Bublé

And an unordered task list:

- [x] Create a sample markdown document
- [x] Add task lists to it
- [ ] Take a vacation

And a "mixed" task list:

- [ ] Steal underpants
- ?
- [ ] Profit!

And a nested list:

- Jackson 5
  - Michael
  - Tito
  - Jackie
  - Marlon
  - Jermaine
- TMNT
  - Leonardo
  - Michelangelo
  - Donatello
  - Raphael

Definition lists can be used with HTML syntax. Definition terms are bold and italic.

<dl>
    <dt>Name</dt>
    <dd>Godzilla</dd>
    <dt>Born</dt>
    <dd>1952</dd>
    <dt>Birthplace</dt>
    <dd>Japan</dd>
    <dt>Color</dt>
    <dd>Green</dd>
</dl>

---

Tables should have bold headings and alternating shaded rows.

| Artist          | Album          | Year |
| --------------- | -------------- | ---- |
| Michael Jackson | Thriller       | 1982 |
| Prince          | Purple Rain    | 1984 |
| Beastie Boys    | License to Ill | 1986 |

If a table is too wide, it should condense down and/or scroll horizontally.

<!-- prettier-ignore-start -->

| Artist            | Album           | Year | Label       | Awards   | Songs     |
|-------------------|-----------------|------|-------------|----------|-----------|
| Michael Jackson   | Thriller        | 1982 | Epic Records | Grammy Award for Album of the Year, American Music Award for Favorite Pop/Rock Album, American Music Award for Favorite Soul/R&B Album, Brit Award for Best Selling Album, Grammy Award for Best Engineered Album, Non-Classical | Wanna Be Startin' Somethin', Baby Be Mine, The Girl Is Mine, Thriller, Beat It, Billie Jean, Human Nature, P.Y.T. (Pretty Young Thing), The Lady in My Life |
| Prince            | Purple Rain     | 1984 | Warner Brothers Records | Grammy Award for Best Score Soundtrack for Visual Media, American Music Award for Favorite Pop/Rock Album, American Music Award for Favorite Soul/R&B Album, Brit Award for Best Soundtrack/Cast Recording, Grammy Award for Best Rock Performance by a Duo or Group with Vocal | Let's Go Crazy, Take Me With U, The Beautiful Ones, Computer Blue, Darling Nikki, When Doves Cry, I Would Die 4 U, Baby I'm a Star, Purple Rain |
| Beastie Boys      | License to Ill  | 1986 | Mercury Records | noawardsbutthistablecelliswide | Rhymin & Stealin, The New Style, She's Crafty, Posse in Effect, Slow Ride, Girls, (You Gotta) Fight for Your Right, No Sleep Till Brooklyn, Paul Revere, Hold It Now, Hit It, Brass Monkey, Slow and Low, Time to Get Ill |

<!-- prettier-ignore-end -->

---

Code snippets like `var foo = "bar";` can be shown inline.

Also, `this should vertically align` ~~`with this`~~ ~~and this~~.

Code can also be shown in a block element.

```
var foo = "bar";
```

Code can also use syntax highlighting.

```javascript
var foo = "bar";
```

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```javascript
var foo =
  "The same thing is true for code with syntax highlighting. A single line of code should horizontally scroll if it is really long.";
```

Inline code inside table cells should still be distinguishable.

| Language   | Code               |
| ---------- | ------------------ |
| Javascript | `var foo = "bar";` |
| Ruby       | `foo = "bar"`      |

---

Small images should be shown at their actual size.

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

Large images should always scale down and fit in the content container.

![Branching](https://guides.github.com/activities/hello-world/branching.png)

```
This is the final element on the page and there should be no margin below this.
```