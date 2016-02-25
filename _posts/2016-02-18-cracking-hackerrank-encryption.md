---
layout:   post
comments: true
title:    Cracking Hackerrank - Encryption
---

As a friend of mine loves to say, "The best way to learn a programming language is to start writing algorithms in it".
While that most probably won't make you the language expert, there's a high chance that you will face most of the data
structures it provides as well as feel the power of it's unique language constructs.

There're lots of good resources to help you get started, but I prefer to spend my spare time on
[Hackerrank](https://www.hackerrank.com/). It's free, has pleasant user interface and a solid selection of algorithmic
problems conveniently broken down into categories and difficulty levels.

After solving each problem, the whole analyzing part is usually getting thrown out. And that pointed me to the idea of
writing the way of thinking into blog posts. Always good to look back and see how good you were and how bad was your
English. So let's get it started!

Our today's problem - "Encryption" ([link to the challenge](https://www.hackerrank.com/challenges/encryption)).

<!--more-->

## Step 1. Detect the grid size

The problem defines a handful of conditions to detect the grid size:

- `floor(sqrt(L)) <= rows <= columns <= ceil(sqrt(L))`
- `rows * columns >= L`

If multiple grids satisfy the above conditions, we will choose the one with the minimum area, i.e. `rows * columns`.

Let's use the sample input and output provided by Hackerrank for the sake of clarity in the decision we will make. More
concrete, the string `haveaniceday` should produce `hae and via ecy`.

To have some base for the manual calculations, we are going to start by resolving the conditions:

- `L = len("haveaniceday") = 12`
- `sqrt(L) = sqrt(12) = 3.46`
- `floor(sqrt(L)) = floor(3.46) = 3`
- `ceil(sqrt(L)) = ceil(3.46) = 4`

By placing these values into the first condition,

{% highlight text %}
3 <= rows <= columns <= 4
{% endhighlight %}

we get the idea of the grid sizes available to us. Let's analyze each of them in the ascending order:

- `3 * 3 = 9` - the condition `rows * columns >= L` is not satisfied
- `3 * 4 = 12` - the condition is satisfied
- `4 * 4 = 16` - the condition is satisfied, but the area is larger than the one of the previous grid

Based on the knowledge we've got, let's write our solution to the first step:

{% highlight text %}
1. rows = columns = floor(sqrt(L))
2. if rows * columns < L then columns = ceil(sqrt(L))
3. if rows * columns < L then rows = ceil(sqrt(L))
{% endhighlight %}

And the actual code in [Go](https://golang.org/):

{% highlight go %}
func detectGridSize(l int) (int, int) {
    s := math.Sqrt(float64(l))

    f := int(math.Floor(s))
    if f * f >= l {
        return f, f
    }

    c := int(math.Ceil(s))
    if f * c >= l {
        return f, c
    }

    return c, c
}
{% endhighlight %}


## Step 2. Populate the grid

Using the values we calculated (`rows = 3` and `columns = 4`), let's represent our initial string in the form of a grid:

{% highlight text %}
have
anic
eday
{% endhighlight %}

Populating the grid is fairly simple:

{% highlight text %}
1. iterate i from 0 to rows
2.   iterate j from 0 to columns
3.     if i*N+j is less than string length, equal G[i][j] to S[i*N+j]
{% endhighlight %}

And the code in Go:

{% highlight go %}
func populateGrid(g [][]byte, s string) {
    for i := range g {
        for j := range g[i] {
            if k := i * len(g[i]) + j; k < len(s) {
                g[i][j] = s[k]
            }
        }
    }
}
{% endhighlight %}


## Step 3. Print the grid columns

The remaining piece of the problem is to display the resulted grid. The first column constructs the first word, followed
by a space, followed by the word constructed from the second column, and so on:

{% highlight text %}
1. iterate j from 0 to columns
2.   iterate i from 0 to rows
3.     if G[i][j] is set then print G[i][j]
4.   print " "
{% endhighlight %}

The code implementation:

{% highlight go %}
func printGridColumns(g [][]byte) {
    for j := range g[0] {
        for i := range g {
            if (g[i][j] != 0) {
                fmt.Print(string(g[i][j]))
            }
        }
        fmt.Print(" ")
    }
}
{% endhighlight %}


## Getting everything together

{% highlight go %}
package main

import (
    "fmt"
    "math"
)

func main() {
    var s string
    fmt.Scanln(&s)

    m, n := detectGridSize(len(s))
    g := make([][]byte, m)
    for i := range g {
        g[i] = make([]byte, n)
    }

    populateGrid(g, s)
    printGridColumns(g)
}

func detectGridSize(l int) (int, int) {
    s := math.Sqrt(float64(l))

    f := int(math.Floor(s))
    if f * f >= l {
        return f, f
    }

    c := int(math.Ceil(s))
    if f * c >= l {
        return f, c
    }

    return c, c
}

func populateGrid(g [][]byte, s string) {
    for i := range g {
        for j := range g[i] {
            if k := i * len(g[i]) + j; k < len(s) {
                g[i][j] = s[k]
            }
        }
    }
}

func printGridColumns(g [][]byte) {
    for j := range g[0] {
        for i := range g {
            if (g[i][j] != 0) {
                fmt.Print(string(g[i][j]))
            }
        }
        fmt.Print(" ")
    }
}
{% endhighlight %}


## Further steps

The solution we have already passes all the test cases prepared by the Hackerrank team. But can we do even better?

It's easy to spot how inefficient last two steps are, as both of them are iterating through all the elements inside our
grid. Do we really need to do it twice? Do we need to have the grid populated? Do we need to initialize the grid at all?

If you answered "No" to all of the questions - fantastic! And let's see what our optimized solution looks like:

{% highlight go %}
package main

import (
	"fmt"
	"math"
)

func main() {
	var s string
	fmt.Scanln(&s)

	m, n := detectGridSize(len(s))
	encodeString(m, n, s)
}

func detectGridSize(l int) (int, int) {
	s := math.Sqrt(float64(l))

	f := int(math.Floor(s))
	if f * f >= l {
		return f, f
	}

	c := int(math.Ceil(s))
	if f * c >= l {
		return f, c
	}

	return c, c
}

func encodeString(m, n int, s string) {
	for j := 0; j < n; j++ {
		for i := 0; i < m; i++ {
			if k := i * n + j; k < len(s) {
				fmt.Print(string(s[k]))
			}
		}
		fmt.Print(" ")
	}
}
{% endhighlight %}

And now it is almost twice as fast with 16 lines of code saved. Isn't that great?
