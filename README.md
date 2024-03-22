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
- Asymptotic analysis doesn't account for differences in hardware. Insertion sort for example has an average-case runtime of $O(n^2)$ but in practice running insertion sort on large inputs on a raspberry pi will be slower than running it on a gaming desktop or a supercomputer. Even though the runtime complexity doesn't change the actual runtimes will vary because of the difference in faster/slower CPU performance. 

Question 2) 

- Since the runtime to traverse a binary search tree is $log_2(n)$ we can use this to estimate the difference between $log_2(1000)$ and $log_2(10000)$.

- $log_2(1000)$ is approximately 9.966 and $log_2(10000)$ is approximately 13.288, thus 13.288/9.966 is roughly 1.333 repeating. Using these values we can conclude that if the time to search 1000 elements is 5 seconds, then the time to search 10000 would be 5 * 1.333 or 6.666 seconds as that is the growth rate we found from $log_2(1000)$ to $log_2(10000)$

Question 3)

- The testing environments might have just been entirely different. Our smaller input test might've been done on a supercomputer, and our test with $10,000$ elements might've been done on an old slower machine like a raspberry pi. 

- When testing the algorithm with $1,000$ elements perhaps no software was running in the background, whereas when testing with $10,000$ elements other software was running, such as another program that was eating up RAM and which would then cause the algorithm to slow down the actual time beyond what we estimated from the assumed time complexity.

- Lastly the type of input could also account for such a large difference in our estimate compared to the actual runtime. If our first test with $1,000$ elements was merely comparing integers but our test with $10,000$ elements was doing string comparisons, this would change each comparison per recursive call from a constant operation (integer comparison) and turn it into some $k$ runtime, where $k$ is the length of the string being compared. 
