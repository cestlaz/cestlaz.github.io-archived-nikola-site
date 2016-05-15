<!--
.. title: Teaching Languages
.. slug: 2013-11-23-teaching-languages.md
.. date: 2013-11-23
.. tags: 
.. type: text
-->


Java's never been my favorite language either for using or for
teaching.

As a programmer, after starting with languages like Fortran
and Pascal, I really cut my teeth with C. More recently, Python has
been my go to language to get real work done. 

From a teaching point of view most languages have good points
and bad ones. When the AP class went from Pascal to C++ I lamented
losing the simplicity and the low cost of entry. On the other hand,
C++ gave us objects (not that I'm a big OOP guy), separate files, the
ability to use tons of real world libraries and more.

Moving to Java simplified things in a number of ways but removed
memory management. If we didn't teach that along with the stack frame
in our Systems class, I think our kids would be missing something very
important.


I was reminded of some of Java's limitations as a teaching language over the past couple of days.

As posted earlier, I had my AP students create their own class to
mimic the Java ArrayList. Before introducing the ArrayList in Java, I
wanted to introduce generics:


    public class myList<T> {
      T[] data;
      public myList() {
        data = new T[10];
      }
      // much more not shown 
    }


Turns out, you can no longer do this.

After doing some searching, there does appear to be a way to get this
effect but it was certainly not something I wanted to do with my
classes. I was looking for something more pedagogically sound - an
easy way to show the concept and a way to springboard to an ArrayList.

Oh well...

So, we finished ArrayLists and I was mapping out a plan for Monday. I
thought Radix sort would be cool -- we already introduced using an
array to tally votes when we did the mode. This seemed to be a natural
extension. It would combine Arrays and ArrayLists and illustrate when each is appropriate.

First the kids would set up an array of 10 buckets, each being an ArrayList:

    public class Buckets {
      ArrayList<Integer>[] buckets;
      public Buckets() {
        buckets = new ArrayList<Integer>[10];
		for (int i=0;i<10;i++)
		  buckets[i] = new ArrayList<Integer>();
      }
      // much more not shown 
    }

Unfortunately, Java type safety once again reared its ugly head. OK,
maybe not ugly to a programmer, but ugly to a teacher. You can't do
it. You can do it with an old school ArrayList without the generic:
```ArrayList[] buckets = new Arraylist[10];``` but of course, this
leaves you open to type mismatch problems.

Once again, Java provides a convoluted workaround that might be fine
for a professional programmer, but for a student, it would be nuts.

I might go ahead with the Radix sort lesson anyway, we'll see, but it
would be nice if I could teach this level of course without having to
fight the implementation language.
