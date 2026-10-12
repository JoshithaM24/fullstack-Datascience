# Matplotlib --- Quick Revision Notes

## 1. What is Matplotlib?

-   **Data visualization:** Representing data using charts, plots, and
    graphics to make it easier to understand and analyze.
-   **Matplotlib:** A Python plotting library used to create
    visualizations.
-   Created by **John Hunter in 2002**.
-   Supports line plots, scatter plots, histograms, bar charts, pie
    charts, box plots, and more.
-   Can save plots in formats such as PNG, JPG, PDF and SVG.
-   Pandas and Seaborn can use Matplotlib for visualization.

Other visualization tools mentioned in the source notes: Seaborn,
Pandas, Bokeh, Plotly, ggplot and pygal.

## 2. Importing Matplotlib

``` python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
```

-   `matplotlib.pyplot` provides plotting functions.
-   `plt` is the common shorthand for `matplotlib.pyplot`.
-   NumPy helps create numerical arrays and sequences.
-   Pandas is used for working with tabular data.

## 3. Displaying and saving plots

  -----------------------------------------------------------------------
  Function                            Purpose
  ----------------------------------- -----------------------------------
  `plt.show()`                        Displays the plot

  `fig.savefig("plot.png")`           Saves a specific figure

  `%matplotlib inline`                Displays static plots inside a
                                      Jupyter Notebook

  `%matplotlib notebook`              Enables interactive plots in a
                                      Jupyter Notebook
  -----------------------------------------------------------------------

Example:

``` python
plt.plot([1, 2, 3, 4])
plt.show()
```

## 4. Matplotlib object hierarchy

-   **Figure:** The outer container that can hold one or more plots.
-   **Axes:** The area where an individual plot is drawn.
-   **Subplot:** One plot within a figure containing multiple plots.
-   Plot elements include lines, ticks, labels, titles and legends.

## 5. Two Matplotlib interfaces

  -----------------------------------------------------------------------
  Pyplot API                          Object-Oriented API
  ----------------------------------- -----------------------------------
  Simple and convenient               Gives more control

  Uses `plt.plot()`                   Uses `ax.plot()`

  Good for quick plotting             Useful for complex plots

  Tracks the current figure and axes  Uses explicit Figure and Axes
                                      objects
  -----------------------------------------------------------------------

### Pyplot example

``` python
plt.plot([1, 2, 3], [2, 4, 6])
plt.title("My Plot")
plt.show()
```

### Object-Oriented example

``` python
fig, ax = plt.subplots()

ax.plot([1, 2, 3], [2, 4, 6])
ax.set_title("My Plot")

plt.show()
```

-   `plt.gcf()` gets the current figure.
-   `plt.gca()` gets the current axes.

## 6. Important plotting functions

  ----------------------------------------------------------------------------
  Plot type               Function                     Purpose
  ----------------------- ---------------------------- -----------------------
  Line plot               `plt.plot()`                 Shows trends or changes
                                                       over values

  Scatter plot            `plt.scatter()`              Shows individual points
                                                       and relationships

  Histogram               `plt.hist()`                 Shows the frequency
                                                       distribution of
                                                       numerical data

  Vertical bar chart      `plt.bar()`                  Compares values using
                                                       vertical bars

  Horizontal bar chart    `plt.barh()`                 Compares values using
                                                       horizontal bars

  Error bar chart         `plt.errorbar()`             Shows data points with
                                                       error or uncertainty
                                                       ranges

  Stacked bar chart       `plt.bar(..., bottom=...)`   Displays one set of
                                                       bars on top of another

  Pie chart               `plt.pie()`                  Shows proportions of a
                                                       whole

  Box plot                `plt.boxplot()`              Summarizes a
                                                       distribution using
                                                       quartiles, median and
                                                       whiskers

  Area chart              `plt.fill_between()`         Fills the area between
                                                       a line and a baseline

  Contour plot            `plt.contour()`              Shows contour lines for
                                                       values across two
                                                       dimensions
  ----------------------------------------------------------------------------

### Quick code examples

``` python
# Line plot
plt.plot(x, y)

# Scatter plot
plt.scatter(x, y)

# Histogram
plt.hist(data)

# Vertical and horizontal bars
plt.bar(x, y)
plt.barh(x, y)

# Pie chart
plt.pie(values, labels=labels)

# Box plot
plt.boxplot(data)

# Area chart
plt.fill_between(x, y)

# Contour plot
plt.contour(matrix)
```

## 7. Figure and subplots

Create a figure with two plotting areas:

``` python
fig, ax = plt.subplots(2)
```

This creates two Axes objects, accessible as `ax[0]` and `ax[1]`.

Create a 2 × 2 layout:

``` python
fig = plt.figure()

ax1 = fig.add_subplot(2, 2, 1)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(2, 2, 3)
ax4 = fig.add_subplot(2, 2, 4)
```

Remember: `add_subplot(rows, columns, position)`.

## 8. Multiline plots

Display multiple lines on the same figure by calling the plot function
several times before showing the figure.

``` python
plt.plot(x, y1)
plt.plot(x, y2)
plt.plot(x, y3)
plt.show()
```

## 9. Plot customization

  Task                Function or parameter
  ------------------- ------------------------------
  Add a title         `plt.title()`
  Label X-axis        `plt.xlabel()`
  Label Y-axis        `plt.ylabel()`
  Add a legend        `plt.legend()`
  Add grid lines      `plt.grid(True)`
  Set axis limits     `plt.axis()`
  Set X-axis limits   `plt.xlim()`
  Set Y-axis limits   `plt.ylim()`
  Set X-axis ticks    `plt.xticks()`
  Set Y-axis ticks    `plt.yticks()`
  Set figure size     `plt.figure(figsize=(7, 7))`
  Select plot style   `plt.style.use()`

Example:

``` python
plt.plot([1, 2, 3], [2, 4, 6], label="Sales")
plt.title("Sales Report")
plt.xlabel("Month")
plt.ylabel("Sales")
plt.grid(True)
plt.legend()
plt.show()
```

## 10. Colors and line styles

### Color abbreviations

  Code   Color
  ------ ---------
  `b`    Blue
  `c`    Cyan
  `g`    Green
  `k`    Black
  `m`    Magenta
  `r`    Red
  `w`    White
  `y`    Yellow

### Line styles

  Style   Meaning
  ------- ---------------
  `-`     Solid line
  `--`    Dashed line
  `-.`    Dash-dot line
  `:`     Dotted line

Examples:

``` python
plt.plot(x, y, 'r--')  # Red dashed line
plt.plot(x, y, 'bo')   # Blue circles
plt.plot(x, y, 'g^')   # Green triangles
```

The default format string in the source notes is `'b-'`, meaning a solid
blue line.

## 11. Axes, ticks and legends

-   `plt.axis([xmin, xmax, ymin, ymax])` sets both axes' limits.
-   `plt.xlim([1, 4])` sets the X-axis limits.
-   `plt.ylim([0, 12])` sets the Y-axis limits.
-   `plt.xticks()` and `plt.yticks()` control tick positions and labels.
-   A **legend** explains what each line represents.
-   Using `label=` in the plot and then calling `plt.legend()` helps
    match labels to lines.

Example:

``` python
plt.plot(x, y1, label="Normal")
plt.plot(x, y2, label="Fast")
plt.legend()
```

## 12. Other important concepts

-   **Histogram bins:** Intervals into which numerical data are grouped.
-   **Pie chart wedges:** Sectors proportional to each value relative to
    the total.
-   **Box plot median:** The middle value of the ordered data.
-   **Interquartile range (IQR):** Upper quartile minus lower quartile.
-   **Contour lines:** Join locations with equal values; closer lines
    indicate a steeper change in the represented function.
-   **Stacked bar chart:** The `bottom` parameter positions one bar
    series above another.
-   **Grid:** Provides reference lines that make values easier to read.
-   **Plot styles:** Change the overall appearance of visualizations.

## 13. Last-minute revision cheat sheet

1.  Matplotlib is a Python library for data visualization.
2.  `import matplotlib.pyplot as plt` imports the plotting interface.
3.  `plt.show()` displays a plot.
4.  `Figure` is the overall container; `Axes` is an individual plotting
    area.
5.  Pyplot is convenient for simple plots; Object-Oriented API offers
    more control.
6.  `plt.plot()` creates line plots.
7.  `plt.hist()` displays frequency distributions.
8.  `plt.bar()` creates vertical bars; `plt.barh()` creates horizontal
    bars.
9.  `plt.title()`, `plt.xlabel()`, `plt.ylabel()` customize plot text.
10. `plt.legend()`, `plt.grid()`, and `fig.savefig()` add a legend,
    grid, and save a figure.

## 14. Self-test questions

Try answering these without looking at the notes.

1.  Which function displays a plot?
2.  Which object represents the entire figure?
3.  Which function creates a histogram?
4.  Which function creates a horizontal bar chart?
5.  What does `'r--'` mean?
6.  Which function adds a legend?
7.  What does `plt.gca()` return?
8.  Which parameter stacks bars above another series?

### Answers

1.  `plt.show()`
2.  Figure
3.  `plt.hist()`
4.  `plt.barh()`
5.  Red dashed line
6.  `plt.legend()`
7.  Current Axes
8.  `bottom`

------------------------------------------------------------------------

## Revision plan

1.  Read Sections 1--5.
2.  Memorize the plotting functions in Section 6.
3.  Type the code examples into a Python notebook.
4.  Finish by answering the self-test questions without looking.
