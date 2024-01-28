[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/FgMJElkj)
# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.

Add your answers to this markdown file.

# My answers

Question 1)

- You could have two algorithms that both have an asymptotic runtime of $O(n^3)$ but one algorithm might have a constant factor such as $5n^3$ whereas the other algorithm might just be $n^3$. Although asymptotically both of these algorithms have the same $O(n^3)$ the one with a constant factor in practice will run much slower than the second algorithm without any constants.
- Additionally two algorithms could both have a runtime complexity of $O(n^3)$ but exploring further you might find that one of the algorithms is $n^3$ while the other is $5n^3 + 3n^2 + 2n$ in this case the big O is the same but in practice the algorithm with extra lower order terms will run much slower than the algorithm which only runs in $O(n^3)$
- Asymptotic analysis doesn't account for differences or limitations in hardware. Therefore you could have an algorithm with a seemingly fast asymptotic runtime that in practice can't make full use of its implementation because of hardware limitations, this could especially be true in the case of asynchronous algorithms that may not have as many threads or cores as it needs to maximize it's effeciency.

Question 2)

- Since the runtime to traverse a binary search tree is $log_2(n)$ we can use this to estimate the difference between $log_2(1000)$ and $log_2(10000)$.

- $log_2(1000)$ is approximately 9.966 and $log_2(10000)$ is approximately 13.288, thus 13.288/9.966 is roughly 1.333 repeating. Using these values we can conclude that if the time to search 1000 elements is 5 seconds, then the time to search 10000 would be 5 * 1.333 or 6.666 seconds as that is the growth rate we found from $log_2(1000)$ to $log_2(10000)$

Question 3)

- The algorithm might be implemented in such a way that the slowness isn't apparent until the input size is large enough. For example a brute force implementation to solve the traveling salesperson problem will run fine with an input smaller than say 10, but attempting to search among 100 or even 50 and the algorithm will likely run out of memory before finishing. Perhaps this binary search algorithm is implemented similarly. 
- It could simply be a hardware issue, or different data sets as input. If the programmer tested the runtime for 1000 elements with a different input than when testing 10000 elements this could account for such a large change in runtime, or merely testing in one environment, and then testing again in a different environment.
- The data structure the algorithm uses doesn't scale well with larger inputs. Even if the algorithm logically works, an ineffecient choice of data structure could be increasing the runtime beyond what the typical traversal of a binary tree suggests.