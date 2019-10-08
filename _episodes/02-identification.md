---
title: "Identification"
teaching: 0
exercises: 0
questions:
- "What is ."
objectives:
- "Learn what parts of your code can be effectively vectorised."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
Start by looking for loops in your code. The more iterations the better.

the loop should have a pre-defined number of iterations with no premature exit condition. for loops can more easily be vectorised than while loops.
each iteration should not depend on any previous iteration. One should be able to execute the iterations in any order.
it is best not to have if statements inside the loop as these could cause some iterations to take longer than others
Good candidates are loops where the same function is applied to each element. Reduction operations (for example sum or product of all array elements) are also good candidates.

When considering nested loops, start by vectorising the innermost loop, unless the innermost loop only performs very few iterations.

Array operations are available through the numpy Python module. numpy arrays in many respects behave like lists with the following caveats:

all array elements must have the same type (integer, float, etc.)
array elements cannot be added or removed (without having to recreate the array)
On the other hand, numpy arrays support elementwise operations.

Vectorised Python code using large numpy arrays should almost always run much faster than plain Python code with loops, and it can run as fast as C code in some cases. If your algorithm has high “algorithmic intensity”, where many operations are done on the same piece of data, you may find that implementing loops with Numba or a low-level language like C provides yet better performance - these methods can often use fast processor caches more efficiently, avoiding the cost of repeatedly fetching data form memory. They also avoid temporary arrays that numpy code sometimes requires.

{% include links.md %}

