<!--
.. title: Stuyablo II
.. slug: 2013-10-27-stuyabloII.md
.. date: 2013-10-27
.. tags: 
.. type: text
-->


Last week in my AP classes, we were working on inheritance.

So, what to do?

Last time around I had my classes work on a "speed dating" program -
StuyDater. Back then JonAlf had his classes work on Stuyablo, that
classic dungeon crawl.

I still plan on reworking the StuyDater project, but first I decided
to do my take on Stuyablo. Of course, we've improved on it. This time
it's **Stuyablo II**. The next guy will have to do **Stuyablo III - in
3D**.

We used the concept of a base class **Character**:


    public class Character {
      private int health;
      private String name;
      
      public String toString() {
        return Name;
      }

      // etc
    }
And then some derived classes such as:


    public class Wizard extends Character {
     private int mana;
     // etc
    } 

We spend time dealing with public vs private vs protected, issues with
constructors, super and the like but then the weekend was upon us.

So, what was the assignment - we broke up into groups. Each group had
to design one aspect of the project. Some groups had to decide on what
would make up a player character. Perhaps a fighter or a wizard. What
base level attributes are needed? What methods? What do they need as
parameters and what do they return? What will the combat system look
like? 

Another groups had to work on non player characters. Yet others
designed the game driver.

None of them were supposed to actually write finished code. 

I asked them to bounce around ideas on our mailing list over the
weekend.

It's been amazing to watch the discussion. It's now Saturday evening
and throughout the day there's been a constant flow of ideas and
discussion. I love it when the classes are into the projects. 

Monday we're going to sync up, finalize the design, and then start
writing this thing.

It's going to be fun.
