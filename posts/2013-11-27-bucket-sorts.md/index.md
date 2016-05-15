<!--
.. title: Bucket Sorting
.. slug: 2013-11-27-bucket-sorts.md
.. date: 2013-11-27
.. tags: 
.. type: text
-->


In spite of the Java based annoyances I mentioned last time, I decided
to go ahead and do Radix sort with my AP students. I usually don't
cover it in AP Computer Science, but I like getting the kids to think
about using arrays as buckets as it's a new way of thinking for them and it does give a non-trivial application that combines ararys and ArrayLists.

It's a nice little algorithm. You start with an Array of integers:

<div align="center">
<a href="/img/radix/array1.png" rel="lightbox">
  <img width="50%" src="/img/radix/array1.png" class="" alt="" />
</a>
</div>


Then, place them in buckets based on the least significant digit:

<div align="center">
<a href="/img/radix/buckets1.png" rel="lightbox">
  <img width="50%" src="/img/radix/buckets1.png" class="" alt="" />
</a>
</div>

We then copy the numbers from the buckets back into the original array, keeping the order of the buckets (0->9).

<div align="center">
<a href="/img/radix/array2.png" rel="lightbox">
  <img width="50%" src="/img/radix/array2.png" class="" alt="" />
</a>
</div>

We then repeat this process on the 2nd least significant digit:

<div align="center">
<a href="/img/radix/step2.png" rel="lightbox">
  <img width="50%" src="/img/radix/step2.png" class="" alt="" />
</a>
</div>

And so on until we're done:

<div align="center">
<a href="/img/radix/step3.png" rel="lightbox">
  <img width="50%" src="/img/radix/step3.png" class="" alt="" />
</a>
</div>

It's a nice algorithm to teach on a number of fronts. 

First, we get to combine Arrays and ArrayLists. Since we'll always
have 10 digits, the "bucket list" is of fixed size, while the
individual bucket lengths vary. This leads to the Array of ArrayLists
and we've got a single platform to compare and contrast the two. Which
is better when and why?

The algorithm itself is also worth talking about. 
 
 * It's relatively simple - we did it by hand before implementing it.
 * It's got some history worth discussing.
 * There are a number of other questions we can approach
  * How can we deal with negatives?
  * What about strings?
  * Will it always work (what about floating point numbers).
 
Finally, we can talk about speed -- they're testing that now and we'll discuss our Radix sort vs the built in Arrays.sort() on Monday.

We'll do the n^2 and nLog(n) sorts a little later, but I think this
was a detour well worth taking.


