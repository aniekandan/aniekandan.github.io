---
layout: post
title: "How many Multiples of a number exist below a limit?"
subtitlte: "Abstract goes here"
background: 'posts/how_to_list_k_multiples/we-in-rest.jpg'
img: 'posts/how_to_list_k_multiples/we-in-rest.jpg'
katex: True
---


A multiple of any number is the product of that number with a whole number. For example, $$3 \times 4$$ is a multiple of $$3$$ (which equals $$12$$ when simplified), and $$3 \times 9$$, which equals $$27$$, is another multiple of $$3$$. The numbers $$12$$ and $$27$$ are multiples of $$3$$ because we get them by multiplying $$3$$ by the whole numbers $$4$$ and $$9$$ respectively.

We said earlier that a multiple of a number is that number multiplied by a whole number. Since $$0$$ is a whole number, $$3 \times 0$$ would also be a multiple of $$3$$. This means that $$0$$ is a multiple of $$3$$, and of any other number for that matter.

There are infinitely many whole numbers. Consequently, for any given number, we could potentially have an infinite amount of multiples for it. So, how do we even begin to list them?

## Listing the Multiples of a Number
To help our case, we can start by limiting the whole numbers to the non-negative numbers $$\{0, 1, 2, 3, 4, 5, 6, 7 \dots\}$$. Then, to get the multiples of a number $$x$$, we  multiply $$x$$ by each non-negative number in the set. The result of this will be the infinite list $$\{0, x, 2x, 3x, 4x, 5x, 6x, 7x \dots\}$$.

Our operation is actually an endless one, as we will always have a multiple of $$x$$ to list. To be more concrete, if $$x = 3$$, then the multiples of $$3$$ would be:

$$0, 3, 6, 9, 12, 15, 18, 21 …$$

We were just listing them on and on (the non-negative numbers are endless, remember?). We need to look for a way to get a finite number of multiples. This would make it easy to write a program that actually executed, and terminated, providing us with the results we need.

In this article, we will discuss how to **list $$k$$ multiples of a number**, where $$k = 1, 2, 3, $$ and so on. In a future article, we will consider how to **list the multiples of a number below a limit**. We will also include Python code that generates a list of multiples of a number.

## List $$k$$ multiples of a number
In order to have a clearer idea of this problem, we could try yo be more specific:

> **List $$10$$ multiples of $$3$$**

Solving this query is as simple as listing 10 numbers

$$0, 3, 6, 9, 12, 15, 18, 21, 24, 27$$

And we're done!

Notice something about the multiples we listed earlier; the $$1st$$ multiple was $$3 \times 0$$, and the $$10th$$ multiple was $$3 \times 9$$. To get the last multiple in the list, we did not multiply $$3$$ by $$10$$; we multiplied $$3$$ by $$(10−1)$$.

Let us test our strategy on another problem:

> **List $$5$$ multiples of $$3$$**

The $$1st$$ multiple will be $$0$$ (that is, $$3 \times 0$$), and the $$5th$$ multiple will be $$12$$ (that is, $$3 \times (5−3)$$, or $$3 \times 4$$). Thus, the $$5$$ multiples of $$3$$ we are looking for are:

$$0, 3, 6, 9, 12$$

---

Generally, the problem:

> **List $$k$$ multiples of $$x$$**

where $$k$$ is a non-negative number, can be resolved as follows:

$$0, x, 2x, 3x, …, (k-2)x, (k-1)x$$

The first element in the list is $$0 \times x$$, and the last element is $$(k-1)\times x$$. 

## Python Implementation
Now that we have a way to generate a fixed number of multiples, we can now try to experiment with how to code it in Python. I am making use of Python 3.8.8 in this article. The code snippet below defines a function that generates $$k$$ multiples of $$3$$, and then calls that function to first generate $$5$$ multiples, and then $$10$$ multiples of $$3$$.

```python
def k_multiples_of_3(k):
    return [3 * i for i in range(0, k)]

# print 5 multiples of 3
print("5 multiples of 3: ", k_multiples_of_3(k=5))

# print 10 multiples of 3
print("10 multiples of 3: ", k_multiples_of_3(k=10))
```

The function `k_multiples_of_3` accepts only one argument, `k`, which represents the number of multiples to produce. `k` should be a non-negative integer. The function returns a list containing multiples of $$3$$ only. When the code is run, the output looks like the one below:

```
5 multiples of 3:  [0, 3, 6, 9, 12] 
10 multiples of 3:  [0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
```

What if we wanted to generate multiples of another number, say $$5$$? We will make some changes to the previous code to make it generate only multiples of $$5$$.

```python
def k_multiples_of_5(k):
    return [5 * i for i in range(0, k)]

# print 5 multiples of 5
print("5 multiples of 5: ", k_multiples_of_5(k=5))

# print 10 multiples of 5
print("10 multiples of 5: ", k_multiples_of_5(k=10))
```

The modified function is now called `k_multiples_of_5`, and now returns a list containing only multiples of $$5$$. However, the parameter `k` means the same as the one in the previous `k_multiples_of_3` function. We can see from the output below that we are getting the correct multiples of $$5$$.

```
5 multiples of 5:  [0, 5, 10, 15, 20] 
10 multiples of 5:  [0, 5, 10, 15, 20, 25, 30, 35, 40, 45]
```

---

What we just did was to create special functions each time we needed to generate $$k$$ multiples of a particular number. However, we now have an idea of how to define a general function that produces multiples for any number we specify. We will call our general function `k_multiples_of_x`, and this time, we will need to specify an additional parameter `x`. The `x` parameter specifies the number we want to generate multiples for.

```python
def k_multiples_of_x(k, x):
    return [x * i for i in range(0, k)]
```

The next code snippet calls the `k_multiples_of_x` function four different times to get multiples of $$3$$, $$5$$, and $$7$$.

```python
# print 5 multiples of 3
print("5 multiples of 3: ", k_multiples_of_x(k=5, x=3))

# print 10 multiples of 3
print("10 multiples of 3: ", k_multiples_of_x(k=10, x=3))

# print 10 multiples of 5
print("10 multiples of 5: ", k_multiples_of_x(k=10, x=5))

# print 10 multiples of 7
print("10 multiples of 7: ", k_multiples_of_x(k=10, x=7))
```

Our output looks like what follows.

```
5 multiples of 3:  [0, 3, 6, 9, 12] 
10 multiples of 3:  [0, 3, 6, 9, 12, 15, 18, 21, 24, 27] 
10 multiples of 5:  [0, 5, 10, 15, 20, 25, 30, 35, 40, 45] 
10 multiples of 7:  [0, 7, 14, 21, 28, 35, 42, 49, 56, 63]
```

---

That's it for this article on **listing a fixed numer of multiples**. In the next article, we will discuss how to **list multiples below a limit**.


### image for section goes here
### image for section goes here
### image for section goes here
