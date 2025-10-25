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
