---
title: How to approach a problem
description: Algo test
---

Algorithmic Thinking
Make sure you understand the problem
get  constraints,
Best way to prove correctness is to find counter examples
Counterexamples have two important properties
Verifiability: Calculate answer, and display a better one
Simplicity: Once a counterexample has been found make it as simple as possible
Tips for finding Counterexamples:
Think small: When something fails it's usually on a simple example
Think Exhaustively: Find the cases where your algorithm can fail
Take intervals: they can be disjoint, overlapping or nested, all counter examples can be constructed with three intervals
Hunt for the weakness: Say for a greedy algorithm, think why that might be wrong
Go for a tie: Best way to break a greedy heuristic is to provide instances where everything is the same size
Seek extremes: Many Counter-Examples are mixtures of huge and tiny, left and right, few and many, near and far.
Incremental Correctness
Start with smallest interesting case
Corner cases typically occur at extreme values such as N = 0, N = 1, negative values, final (and/or intermediate) values that does not fit 32-bit signed integer, etc.

Do I really understand the problem?
What does the input consist of?
What exactly are the desired results or output?
Can I construct an input example small enough to solve by hand? What happens when I try to solve it?
How important is it to my application that I a;wyas find the optimal answer? Might I settle for something close to the best answer?
How large is a typical instance of my problem? Will I be working on 10? 10k? 1M?
How important is speed in my applications?
How much time and effort can I invest in implementaion?
What type of problem is it?
2. Can I find a simple algorithm or heuristic for my problem?
   Will brute force solve my problem correctly by searching through all subsets or arrangements and picking the best one?
   If so, why am I sure that this algorithm always gives the correct answer?
   How do I measure the quality of a solution once I construct it?
   Does this simple, slow solution run in polynomial or exponential time? Is my problem small enough that a brute-force solution will suffice?
   Am I certain that my problem is sufficiently well defined to actually have a correct solution?
   Can I solve my problem by repeatedly trying some simple rule, like picking the biggest item first? The smallest item first? A random item first?
   If so, on what types of inputs does this heuristic work well? Do these correspond to the data that might arise in my application?
   On what inputs does this heuristic work badly? If no such examples can be found, can I show that it always works well?
   How fast does my heuristic come up with an answer? Does it have a simple implementation?
   Is my problem in the catalog of algorithmic problems in the back of this book?
   What is known about the problem? Is there an available implementation that I can use?
   Did I look in the right place for my problem? Did I browse through all the pictures? Did I look in the index under all possible keywords?
   Are there relevant resources available on the World Wide Web? Did I do a Google Scholar search? Did I go to the page associated with this book: www.algorist.com?
   Are there special cases of the problem that I know how to solve?
   Can I solve the problem efficiently when I ignore some of the input parameters?
   Does the problem become easier to solve when some of the input parameters are set to trivial values, such as 0 or 1?
   How can I simplify the problem to the point where I can solve it efficiently? Why can’t this special-case algorithm be generalized to a wider class of inputs?
   Is my problem a special case of a more general problem in the catalog?
   Which of the standard algorithm design paradigms are most relevant to my problem?
   Is there a set of items that can be sorted by size or some key? Does this sorted order make it easier to find the answer?
   Is there a way to split the problem into two smaller problems, perhaps by doing a binary search? How about partitioning the elements into big and small, or left and right? Does this suggest a divide-and conquer algorithm?
   Does the set of input objects have a natural left-to-right order among its components, like the characters in a string, elements of a permutation, or the leaves of a rooted tree? Could I use dynamic programming to exploit this order?
   Are there certain operations being done repeatedly, such as searching, or finding the largest/smallest element? Can I use a data structure to speed up these queries? Perhaps a dictionary/hash table or a heap/priority queue?
   Can I use random sampling to select which object to pick next? What about constructing many random configurations and picking the best one? Can I use a heuristic search technique like simulated annealing to zoom in on a good solution?
   Can I formulate my problem as a linear program? How about an integer program?
   Does my problem resemble satisfiability, the traveling salesman problem, or some other NP-complete problem? Might it be NP-complete and thus not have an efficient algorithm? Is it in the problem list in the back of Garey and Johnson [GJ79]?







Max Value of N
Algorithm needed
10^9
O log n or sqrt n
10^8
O(n) border probably need faster
10^7
O(n) might work need faster
10^6
O(n)
10^5
O(n log n)
10^4
O(n^2)
10^2
O(n^3)

KEEP THINGS SIMPLE! DONT OMIT DETAILS! DONT SKIP STEPS!!
Dont understand this: Can questioning move up to more complex problem solving?

SCRIPT!!!!
Ask clarifying questions (bounds, types, edge cases)
Propose a brute force solution (and describe its runtime)
Propose an optimized solution (and describe its runtime)
Do the optimized on a small example (this will also help you find logical errors)
Code the optimized solution
Throw out some edge cases that your solution will handle




Design and test solution before coding.
Why? Interviewer might be thinking?
State a solution and work through optimizing solutions (naive to optimal)
Prove that your idea works with examples and walk through them
Multiple examples, bulletproof!
Mind edge cases
Analyze time and space complexity  
How?
Design
Can I combine a sufficient number of characteristics and match to a known pattern/algo/DS?
Generate Skeleton and fill in details
Look at substeps. Can We Optimize anything?
Test
Tests things that matter
Simple tests before complex checks
Null, empty, conditionals
Try? Ascending, descending, skipping, null,
Tests should be independent of each other
Code according to the design.
Troubleshooting
Design is flawed
Code does not reflect design
Bug while coding


Consider asking the following questions.

How big is the size of the input?
How big is the range of values?
What kind of values are there? Are there negative numbers? Floating points? Will there be empty inputs?
Are there duplicates within the input?
What are some extreme cases of the input?
How is the input stored? If you are given a dictionary of words, is it a list of strings or a trie?


Follow ups :

Input too large to fit in memory?
Data arrives as a stream?

The answer is usually a divide-and-conquer approach — perform distributed processing of the data and only read certain chunks of the input from disk into memory, write the output back to disk and combine them later.

Always validate input first. Check for inputs that are invalid, empty, negative, or different. Never assume you are given the valid parameters. Alternatively, clarify with the interviewer whether you can assume valid input (usually yes), which can save you time from writing code that does input validation.

ou should have at least one:

example of an interesting technical problem you solved
example of an interpersonal conflict you overcame
example of leadership or ownership
story about what you should have done differently in a past project
piece of trivia about your favorite language, and something you do and don't like about said language
question about the company's product/business
question about the company's engineering strategy (testing, Scrum, etc)

Get unstuck.
Sometimes you'll get stuck. Relax. It doesn't mean you've failed. Keep in mind that the interviewer usually cares more about your ability to cleverly poke the problem from a few different angles than your ability to stumble into the correct answer. When hope seems lost, keep poking.
Draw pictures. Don't waste time trying to think in your head—think on the board. Draw a couple different test inputs. Draw how you would get the desired output by hand. Then think about translating your approach into code.
Solve a simpler version of the problem. Not sure how to find the 4th largest item in the set? Think about how to find the 1st largest item and see if you can adapt that approach.
Write a naive, inefficient solution and optimize it later. Use brute force. Do whatever it takes to get some kind of answer.
Think out loud more. Say what you know. Say what you thought might work and why it won't work. You might realize it actually does work, or a modified version does. Or you might get a hint.
Wait for a hint. Don't stare at your interviewer expectantly, but do take a brief second to "think"—your interviewer might have already decided to give you a hint and is just waiting to avoid interrupting.
Think about the bounds on space and runtime. If you're not sure if you can optimize your solution, think about it out loud. For example:


