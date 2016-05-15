<!--
.. title: Rot13 - Gateway <s>Drugs</s> Techniques
.. slug: 2014-01-07-rot13-gateway.md
.. date: 2014-01-07
.. tags: 
.. type: text
-->


I've written before about [That One Inspirational Curriculum](
http://cestlaz.github.io/2013/08/07/That_One_Inspirational_Curriculum.html#.UsyYlN_EvZ8) -
the idea that it's not the topic in the syllabus but rather what the
teacher does with it.

Some times a simple problem can lead to some really neat concepts.

Take what we did in my AP classes over the past couple of days. 

I wanted a nice little warm up after the break so we wrote a simple
[rotation cipher](http://www.rot-n.com/). We started with a little
encode routine - take a string and rotate the letters by some
offset. For example if we use an offset of 3, 'hello' becomes
'khoor' - each letter being shifted over thee places.

Pretty easy for the class but even a simple problem like this lets us
talk about a few things, including:

 * we can exploit the ASCII ordering but have to remember to deal with
   the offsets. That is in ASCII, an  'a' is 97, we can't just calculate c =
   (c+offset)%26. We have to first shift the letter down to 0, add and
   mod, and then shift back c = ((c-'a') +offset)%26 + 'a'
* We can talk about neat Internet history such as how
  (rot13)[http://en.wikipedia.org/wiki/ROT13] was used to hide
  spoilers and offensive material on the internet.

I then ran a program that broke the encryption. I also showed the
students how it didn't work on single words but did on full sentences.

By hand, decodingn even a simple cipher is a pain.

With computer assist, it's easy - just print out all 26 possible rotations and pull out the right one.

Our question was how do we have the computer do it all on its own?

I asked them to think about how they might write a program to
accomplish this -- and that's when the magic starts.


They came up with a few interesting ideas:

 1. For each of the 26 rotations, choose the one with the most vowels.
 2. For each word in each rotation, give a point for each word with a vowel and choose the rotation with the highest score.
 3. Look for common short words in each rotation and then check other words against a dictionary.
 4. Do the letters appear with the same frequencies as in the English language
 
We noticed that all of these suggestions are based on our knowledge of
English. What if the message was in a different language or even a
different alphabet?

We decided to use choice 4 - the letter frequencies.

**Magic part 1 - using known data to figure out a pattern for unknown data**

Even if we don't know the frequencies, if we can get a sample document in our language, we can figure them out. We downloaded a text from Project Gutenberg and used it to build
an array of 26 elements called *CorpusFreqs*. CorpusFreqs[0] would hold the
frequency of the letter 'a' in our sample document (that is, how many
times 'a' appears over the total number of letters in our document),
CorpusFreqs[1] the frequency of 'b' etc.

Now we have a model that we can use to compare our rotations to.

**Magic part 2 - wow, that 9th grade math is actually useful**

At this point, it usually isn't clear how to compare our rotations to
the model frequencies we calculated. Time to simplify,

We can look at another problem: Selecting a house.

>**Me:**  if we can only have one criteria, what would it be?

>**Class:** Neighborhood

>**Me:** Ok, let's rate each neighborhood between 0 and 100 

>**Me:** We can draw two houses on a line, which is better?

>**Class:** The one with the larger value!

>**Me:** What if we add a third house? Which is it more similar to?

>**Class:** The one it's closer to.

Next:

>**Me:** Well, what if we add another feature? Cost - let's map low cost to 100 and high cost to 0 and all the other costs in between.

>**Me:** If we want to visualize a house, how can we do it?

>**Class:** We can use a graph - like x,y points use location,cost points.

So we do it.

>**Me:** This is the least desirable house (0,0) and this is the best one (1,1).
I plot two houses and ask

>**Me:** Which is more desirable?

>**Class:** That one (they indicate the one closer to 1,1).

>**Me:** How can you tell

>**Class:** It's closer

>**Me:** How do we figure it out?

>**Class:** The Distance Formula!!!!!

So now we add a third feature - size. It's pretty easy to show that
the distance formula extends to three-space and in fact to even higher
dimensions.

**Magic part 3 - from 3 dimensions to 26**

So now, we bring it back to our cipher. For the house example, we used
points in 1,2, and 3 dimensions (and we actually talked about it in
4D) so we used 1 through 4-space vectors to represent the points and
used Euclidean distance formula to see what houses were similar to
each other, or what points where near to each other

From there, it's easy to see that the frequency array we built from ou sample text is a
26-space vector and that we can build a similar vector for each
rotation.

From there we can use the distance formula to see how close each
rotation is to the sample document vector. The rotation with the
closest vector is pobably our solution.


So from a simple warm up problem we're at the gateway to some serious techniques that will come back time and time again as the students move through their CS education and careers.

Fun!



