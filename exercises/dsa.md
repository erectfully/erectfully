> Introduction to Algorithms, Fourth Edition
> Cormen, Thomas H., Leiserson, Charles E., Rivest, Ronald L., Stein, Clifford

> 1.1-1 Describe your own real-world example that requires sorting. Describe one that requires finding the shortest distance between two points.

Student have decided to use unix timestamps to organize his notes, he would like to browse them chronically and in order to archive such one would use  **sorting algorithm**.

There is imaginary grid with squares where two specific points are marked, with a virtual need to find shortest path between two points on such grid.

> 1.1-2 Other than speed, what other measures of efficiency might you need to consider in a real-world setting?

Computational complexity.
Parallelism of tasks.
Input size (as allowance of inefficient algorithms)

> 1.1-3 Select a data structure that you have seen, and discuss its strengths and limitation

**Binary Search Tree**, have strength of reduced computational cost when it comes to lookups and queries yet inserts are more costly due to necessary sorting. I am not aware of exact computational complexity measures, alternative implementations (BST can be replaced with Vector) and limitations associated with my data structure of choice.

> 1.1-4 How are the shortest-path and traveling-salesperson problems given above similar? How are they different?

**Traveling-salesperson problem** is NP-complete complete problem which means there are no efficient solution for such, while it's possible to determine efficient algorithm for shortest-path problem.

> 1.1-5 Suggest a real-world problem in which only the best solution will do. Then come up with one in which "approximately" the best solution is enough.

I can't recall nor imagine problem where only best solution will be a solve, by intuition it would be every problem except **NP-complete** ones, there we can include anything requiring *sorting*, *path-finding*, *clustering* etc.

In every real-world application which includes **NP-complete** problem (like **travelling-salesman problem**) there is no known efficient solution, however **approximation** algorithms can be used which would be not necessarily best but would solve.

> 1.1-6 Describe a real-world problem in which sometimes the entire input is available before you need to solve the problem, but other times the input is not entirely available in advance and arrives over time.

Imagine grocery store where every client coming to shop receives a number and shop is open so new customers may come at any time and we don't know how many customers may come in future, such problem is called **online problem** and can be solved with use of **scheduling algorithm**.

## Algorithms as Technology

> **1.2-1** Give an example of an application that requires algorithmic content at the application level, and discuss the function of algorithms involved.

Navigation (maps) application wouldn't be possible without implementation of various different algorithms for calculation of geographic distance, path-finding and many others algorithms involved. I am not capable of discussing their function and implementation on lower level.

> **1.2-2** Suppose that for inputs of size *n* on a particular computer, insertion sort runs in 8n^2 steps and merge sort runs in 64n log(n) steps. For which values of *n* does insertion sort beat merge sort?

While I was not capable to estimate complexity in mathematical way to establish cross-over point for *insertion sort* and *merge sort*. I decided to find Least Common Multiple (LCM) between `8(n^2)` and `64(n)` which was **2** and use increment powers until cross-over point where `mergeSort < insertionSort`

```
n = 2^15
i = 8(n^2)
m = 64(n) * log(n)
m  = 9 469 584,862
i  = 8 589 934 592
```

```
n = 2^16
i = 8(n^2)
m = 64(n) * log(n)
m  = 20 201 781,0389
i  = 34 359 738 368
```

By such technique I estimate cross-over point between those two algorithms is between `2^15` and `2^16`. Even through results of those are correct it's figurative method rather than technical one which should include calculation of time complexity of functions, my knowledge about Big O notation is weak.

Answering question stated... *insertion sort beats merge sort for approximately n <= `2^15`*.

> **1.2-3** What is the smallest value of *n* such that an algorithm whose running time is `100(n^2)` runs faster than algorithm whose running time is `2^n` on same machine.

Let’s name algorithms we’re comparing into single letters: **100(n^2)** as **A** and **2^n** as **B** while **n** is a number exponentially powered from number 2 to approach problem with direct trial and seek for breakthrough point.

```
N = 2^3
A = (100 * (N^2))
B = 2^N

A  = 6 400
B  = 256
```

Observe A > B isn’t condition we’re looking for therefore we’re continuing with incrementation exponential of _n_.

```
N = 2^4
A = (100 * (N^2))
B = 2^N

A  = 25 600
B  = 65 536
```

Observe **A < B** which means we found approximate number, yet is this a smallest number which satisfy condition? I don’t know. In order to find out, lookup table can be used where we would store calculations done to find smallest n.

| N   | Algorithm A | Algorithm B |
| --- | ----------- | ----------- |
| 2   | 400         | 4           |
| 4   | 1 600       | 16          |
| 8   | 6 400       | 256         |
| 16  | 25 600      | 65 536      |

Figuratively, observe **A > B** doesn’t answer question “What is the smallest value of n where algorithm A would be faster than algorithm B”, yet we can estimate N we’re looking for is in enclosed within rage 8..16.

Let’s start looking from upper boundary towards lower boundary of established range and recalculate time cost of algorithms for each step.

```
N = 15
A = (100 * (N^2))
B = 2^N

A  = 22 500
B  = 32 768
```

We can evaluate a(n=15) < a(n=16) therefore it’s closer to answering initially asked question, with additional iteration where we check a(n=14) and b(n=14) we find out it no longer satisfies A<B therefore we estimate number 15 as smallest value of n that where algorithm A is faster than algorithm B.

| N      | Algorithm A | Algorithm B |
| ------ | ----------- | ----------- |
| 16     | 25 600      | 65 536      |
| **15** | **22 500**  | **32 768**  |
| 14     | 19 600      | 16 384      |

Within time of solving exercise I was not aware of any other method that would allow calculation of exact smallest number where A<B.
