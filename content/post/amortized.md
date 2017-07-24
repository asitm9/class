+++
date = "2017-07-24T14:14:49+05:30"
title = "AMORTIZED ANALYSIS"

+++

### What is Amortized Analysis?

 Amortized analysis means analyzing time-averaged cost for a sequence of operations. It doesn't provide any information of a single operation int that sequence.

 __Purpose:__ To have a better idea of total running time of a longer job.  Calculated in relation to a batch of calls to the process.

__Note:__ This is different from our usual notion of "average case anyalysis" -- we are not making any input being chosen at random. Here we're just averaging over total time.

There are going to be three approaches that we call:

__Aggregate method__

__Accounting method(Banker's method)__

__Potential method(physicist's method)__

### Aggregate method
____

In aggregate analysis, there are two steps. First, we must show that a sequence of `n` operation takes `T(n)` time in the worst case. Then, we show that each operation takes `T(n)/n`.

A common example of aggregate analysis is stack's operations. Stack have two `O(n)` operations. `Push(elel)` puts an element on the top and `pop()` takes the top element off of the stack. As the operations are both constant time, so a total of `n` operations will result in `O(n)` total time.

Now, a new operation is added to the stack. `multipop(k)` will either pop the top `k` elements int the stack or if it runs out of elements before that it will pop all the elements in the stack and stop.

```
multipop(k):
    while stack not empty and k>0:
        k = k-1
        stack.pop()

```
The worst-case cost of a `multipop` operation in the sequence is `O(n)`, since the stack size is at most `n`. The worst case time of any stack operation is `O(n)`, and hence a sequence of `n` operations cost `O(n^2)`.

However that's not the case. `multipop` cannot function unless there's been a push to the stack because it would have nothing to pop off. So After pushing `n` elements to the stack, the number of times `pop` can be called including calls within `multipop` is `n`. For any value of `n`, any sequence of `n`   `push, pop` and `multipop` takes a total time of `O(n)` time.

The amortized cost of an operation is the average : `O(n)/n=O(1)`
