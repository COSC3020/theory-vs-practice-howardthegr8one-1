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

- Our time estimate was based on our assumption that the runtime complexity is $log(n)$, however the actual time it takes to run could be slower than estimated due to a constant of some kind, perhaps the actual runtime is closer to $10 log(n)$ or $100 log(n)$ which would account for a much slower runtime in practice. 

- When testing the algorithm with 1000 elements better hardware could've been used, or no software was running in the background, whereas when testing with 10,000 elements slower hardware with other software running could slow down the actual time beyond what we estimated from the assumed time complexity.

- The actual implementation may not be $log(n)$ as we would assume for a binary search. The implementation might be poorly written and thus perform much slower, although this would mean that the runtime is NOT actualy $log(n)$.