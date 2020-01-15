+++
title = "Lecture #1"
author = ["Kostas Andreadis"]
description = "An overview of the class..."
lastmod = 2020-01-15T17:01:45-05:00
tags = ["lectures"]
draft = false
+++

## Course logistics {#course-logistics}

-   Office hours

    **Tue 10:00-12:30**, 18C Marston Hall
    (or by appointment, [kandread@umass.edu](mailto:kandread@umass.edu))

-   No textbook

-   Grading

|               |     |
|---------------|-----|
| Homework      | 60% |
| Final project | 40% |


## Course objectives {#course-objectives}

<ul>
<li class="fragment"> Understand basic programming abstractions and data structures</li>
<li class="fragment"> Load, parse, process, and store various scientific datasets</li>
<li class="fragment"> Produce publication-quality plots and visualizations</li>
<li class="fragment"> Implement statistical and algorithms for engineering problems</li>
<li class="fragment"> Understand basic parallelization techniques</li>
<li class="fragment"> Deploy algorithms on cloud architectures</li>
<li class="fragment"> Learn good software engineering practices</li>
</ul>


## Course schedule {#course-schedule}

-   Week 1: Introduction and programming basics
-   Week 2: Python basics
-   Week 3: Data structures
-   Week 4: Numerical Python
-   Week 5/6: Plotting and visualization
-   Week 6/7: Time series analysis

<!--listend-->

-   Week 8: No class
-   Week 9: Statistical modeling
-   Week 10: Spatial analysis
-   Week 11: Databases
-   Week 12: Parallel and cloud computing
-   Week 13: Version control
-   Week 14: Coding best practices


## Machine architecture {#machine-architecture}

{{< figure src="/ox-hugo/architecture.png" >}}


## Computer programming {#computer-programming}

-   Sequence of instructions built from set of predefined <font color="blue">primitives</font>
-   Interpreter executes each instruction in order and completes program
-   **Programming languages** can abstract methods to create new primitives
-   Set of instructions forms the program's source code


## What can go wrong? {#what-can-go-wrong}

Syntactic errors

```ipython
printfd("hello")
```

Semantic errors

```ipython
print("hello" + 3)
```

Algorithmic errors

```ipython
c = 2.998e6
m = 60
E = m * c**3
E
```


## Choosing a programming language {#choosing-a-programming-language}

| **Mainstream PL**        | **Technical Computing**  |
|--------------------------|--------------------------|
| static checking          | experimental computation |
| classes, single dispatch | complex operators        |
| data hiding              | manipulation of data     |
| parametric polymorphism  | ad hoc polymorphism      |

<style>
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>
<img src="https://www.ibm.com/ibm/history/ibm100/images/icp/C854721S34852J03/us__en_us__ibm100__punched_card__hand_cards__940x727.jpg"
  alt="cards" style="width:80%;">


## Expressiveness vs Performance {#expressiveness-vs-performance}

{{< figure src="https://pbs.twimg.com/media/Dv8k-qpWwAAHRtg.jpg" >}}


## And the winner is... {#and-the-winner-is-dot-dot-dot}

{{< figure src="https://2s7gjr373w3x22jf92z99mgm5w-wpengine.netdna-ssl.com/wp-content/uploads/2016/08/python%5Flogo%5F1.png" >}}

Java

\`\`\`java
public class Main {
      public static void main(String[] args) {
          System.out.println("hello umass");
      }
  }
\`\`\`

Python

```ipython
  print("hello umass")
```


## Libraries {#libraries}

-   **Numpy**
-   **Scipy**
-   **Pandas**
-   **Xarray**
-   **Scikit-Learn**
-   **Matplotlib**
-   **Statsmodels**

Wealth of Python libraries allow us to be productive with complex tasks

Let's look at an example!

```ipython
import folium
import vincent
import pandas as pd
from climata.usgs import DailyValueIO
datelist = pd.date_range(end=pd.datetime(2019, 12, 31), periods=365)
data = DailyValueIO(start_date=datelist[0], end_date=datelist[-1],
                    station="01175500", parameter="00060")
flow = pd.DataFrame({'flow': [r[1] for r in data[0].data]}, index=datelist)
m = folium.Map(location=[42.4, -72.3], zoom_start=7, tiles='Stamen Terrain')
vis = vincent.Line(flow, width=550, height=250).axis_titles(x='Date', y='Flow')
folium.Marker(
    location=[42.267778, -72.333056],
    popup=folium.Popup(max_width=vis.width+75).add_child(
        folium.Vega(vis, width="100%", height="100%"))
).add_to(m)
```

```ipython
m
```

<h1 align="center">Let's install Python!</h1>
