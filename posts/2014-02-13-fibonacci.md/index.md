<!--
.. title: Fibonacci by the tail
.. slug: 2014-02-13-fibonacci.md
.. date: 2014-02-13
.. tags: pedagogy, algorithms
.. type: text
-->


We're ramping up for recursion in my junior classes - state space
search, nlg(n) sorts, etc. As a refresher, we took a quick look at the
Fibonacci numbers.

Now, some people seem to think that it's a tired problem. It's mathy,
it's played out, it's boring etc.. They just might be missing the
point.


The beauty isn't in the problem itself, but rather, that it's a
platform on which you can look at many problem solving techniques.

We can look at the basic, straightforward , imperative solution:


>{% highlight java %}
public int fib1(int n) {
  int a=1,b=1;
  for (int i=0;i<n;i++){
    int c=a+b;
    a=b;
    b=c;
  }
  return a;
}
{% endhighlight %}


It's straightforward and fast - no recursion needed.

Next, we can look at the basic recursive version:


>{% highlight java %}
public int fib2(int n) {
 if (n<=1)
   return 1;
 else
	return fib2(n-1)+fib2(n-2);
}
{%endhighlight%}

The advantages (of recursive solutions in general):

 * It's a direct translation from the recursive mathematical formula.
 * It's elegant, clean, and concise.
 * It can make hard problems much easier (see: [Towers, Hanoi](http://cestlaz.github.io/2010/01/10/towers-of-hanoi.html#.Uv1m4N_EvZ8)).
 * We can use same thought process that led to this solution to solve
   problems like finding our way out of a maze.

The downside:

 * It can be VERY slow.

So, how do we address this?

One way is via **memoization** - when we find a value, store it in a
table, then we can use the look up table instead of recalculating over
and over:
 

> ```java
public int[] fibnums = new int[100000]; 
public int fib3(int n) {
 if (n<=1)
   return 1;
 else if (fibnums[n] != 0)
	return fibnums[n];
 else {
   fibnums[n] fib3(n-1)+fib3(n-2);
   return fibnums[n];
   }
}
```

This is a terrific thing to show a class since it's easy for students
to wrap their heads around, it really speeds things up, and it's a
precursor to lots of neat algorithms.

Finally, we can look at re-writing Fibonacci using tail
recursion. This one can be a little hard for students to grasp. I like
building it up from the iterative solution. In that solution, we use
**a**, and **b** to "walk down" the list of Fibonacci numbers. At any point in time, **a** and **b** represent where we are in the sequence. We also use **c** but that's really just a temporary place to add a and b together.

The problem with doing this in a recursive solution is that we can't
have **a** and **b** as local variables as each recursive call will
have new **a** and **b**s and no information will be transferred.

Since we're working in Java, it doesn't take long for some students to come up with the idea of using instance variables to store a and b and just use the recursion for the "loop.":

>{% highlight java %}
public int a=1, b=1
public int fib4(int n) {
	if (n==1)
		return a;
	else {
		int c=a+b;
		a=b;
		b=c;
		return fib4(n-1)
	}
}
{% endhighlight %}


Great, but using instance variables in this way is very inelegant and messy. Better, use extra parameters to store the values from call to call:

>{% highlight java %}
public int fib5(int n,int a, int b) {
	if (n==1)
		return a;
	else
		return fib4(n-1,b,a+b)
}
{% endhighlight %}

Looking at Fib5(5) we get for n, a, and b:

 * 5,1,1
 * 4 1,2
 * 3,2,3
 * 2,3,5
 * 1,5,8

At which point we just return the 8

Clean, elegant, fast, and easy to understand.

Each of these four techniques are important and will be used time and time again and here we have one simple problem that allows us to explore them all.

#### Some Links

[Project Euler: Problem #2 - Even Fibonacci numbers](http://maikolsolis.wordpress.com/2014/01/18/project-euler-problem-2-even-fibonacci-numbers/)

[Memoized Fibonacci Numbers with Java 8](http://java.dzone.com/articles/memoized-fibonacci-numbers)

[The quadratic formula and Fibonacci numbers](http://mikesmathpage.wordpress.com/2014/02/07/the-quadratic-formula-and-fibonacci-numbers/)

[Monte Carlo Simulations, Fibonacci Numbers, and Other Number Tests: Why Developers Still Need The Basics](http://blog.smartbear.com/programming/why-developers-
still-need-the-basics/)

[TED: Arthur Benjamin: The magic of Fibonacci numbers - Arthur Benjamin (2013)](http://www.ted.com/talks/arthur_benjamin_the_magic_of_fibonacci_numbers.html)

[Fibonacci Numbers in the Real World](http://lee-phillips.org/lispmath/)
