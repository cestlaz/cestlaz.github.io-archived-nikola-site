<!--
.. title: Build it first
.. slug: 2013-11-19-build_it.md
.. date: 2013-11-19
.. tags: 
.. type: text
-->


The subtitle of this post is:

>
> and why my students are going to hate me tomorrow.

When my good friend Gerry Seidman talks to my classes, he frequently
says "never use a data structure or algorithm you couldn't build yourself."

This doesn't mean that you have to write everything from scratch, just
that you should have some knowledge as to what's going on under the
hood. I find that all too often young programmers just rely on APIs
and libraries and really don't know how their computers and programs are working.

And it's never too early to start.

We've been spending time talking about arrays recently. Now, most of
my students have some exposure to Python and so we started talking
about the flexibility and power of the Python list vs the limited
facilities of the Java array.

How to solve the problem and make Java easier to work with? Let's
write our own list class. We started simple:


    public class myList {
      private int[] data;
      private int numItems;
    
      public myList() {
        data = new int[5];
    	numItems = 0;
      }
    
      // append to the end of the list
      public add(int d) {
        if (numItems >= data.length) {
    	  tmp = new int[data.length+data.length/2];
    	  for (int i=0;i<numItems;i++)
    	    tmp[i]=data[i];
    	  data = tmp;
    	}
    
        data[numItems]=d;
    	numItems = numItems + 1;
      }
    }

from there we added functionality such as:

 * Inserting in arbitrary locations
 * Removing items from the list
 * Searching for an item
 * Setting the item at a location to a value

And of course we were also able to talk about things like refactoring
out growing the array into a private method.

And tonight the classes are changing the internal array from int[] to String[].

Of course, what we're building is an ArrayList. Tomorrow we'll reveal
that little fact and of course the classes will all hate me, but then,
they'll really understand what's going on under the hood.
