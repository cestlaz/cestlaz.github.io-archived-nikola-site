<!--
.. title: Change the data
.. slug: 2014-02-26-change-the-data.md
.. date: 2014-02-26
.. tags: 
.. type: text
-->


> Patient: "Doctor, it hurts when I do this."

> Doctor: "So, don't do that."

We've been spending time on
[State Space Search](http://en.wikipedia.org/wiki/State_space_search). It's
a great topic. We deal with or at least introduce:

 * Recursion
 * Blind search
 * Heuristic search
 * foreshadowing things like A* and Dijkstra's algorithm.

and more. Today, however. I want to talk about something else.

We started by developing a maze solver. It reads a text file
representing the maze and then proceeds to find an exit. One version
of the source code can be found
[here](https://github.com/stuycs-apcs-z/classcode/tree/master/3/maze).

It's really cool to see how such a short program, about 10 lines of
work code, can solve such an open sounding problem. From there we talk
about state spaces, graphs, etc. We then moved on to the
[Knight's tour](https://github.com/stuycs-apcs-z/classcode/tree/master/3/maze). By
viewing it as a state space problem we can look at it just like the
maze.

We represented a state as a board with the knight's current position and where it's been. An easy way to do this is to use an array of ints. So we have an empty 5x5 board:

    0 0 0 0 0
    0 0 0 0 0
    0 0 0 0 0
    0 0 0 0 0
    0 0 0 0 0

Or a board after a few moves:

    1 0 0 0 0
    4 0 2 0 0
    0 0 5 0 0
    0 3 0 0 6
    0 0 0 0 0

The kids saw three base cases:

 1. When our count got up to n^2 (and in fact, we're done)
 2. When we land on a non-zero space (when we just return or backtrack)
 3. When we try to move off the board, for an index out of bounds error.

I wanted to look at that third one. We talked for a bit about using an
if or a try/catch but I pointed out that I didn't like either. Looking
at our maze code, we never checked bounds there. Why not. Well it
turns out that our maze had wall all around. It was stored in a 2D
array but the entire outer edge was wall. Why not do the same for the chess board:

    -1 -1 -1 -1 -1 -1 -1 -1 -1
    -1 -1 -1 -1 -1 -1 -1 -1 -1
    -1 -1  0  0  0  0  0 -1 -1 
    -1 -1  0  0  0  0  0 -1 -1 
    -1 -1  0  0  0  0  0 -1 -1 
    -1 -1  0  0  0  0  0 -1 -1
    -1 -1  0  0  0  0  0 -1 -1 
    -1 -1 -1 -1 -1 -1 -1 -1 -1
    -1 -1 -1 -1 -1 -1 -1 -1 -1

Now, as long as we start on the board, if the Knight jumps off the
edge, it will end on a -1 square and backtrack. By modifying our data
structure and data to contain a border, we've eliminated the special
case of index out of bounds.

I always like doing that.



####Some Links

[Source code for Knight's tour](https://github.com/stuycs-apcs-z/classcode/tree/master/3/knights)

