<!--
.. title: Databases - the next day
.. slug: 2013-10-09-database-followup.md
.. date: 2013-10-09
.. tags: 
.. type: text
-->


Two days ago I asked the students, in small groups, to come up with a design to store a school (or school district) database.

Yesterday we discussed the designs.

All the students took our brand of AP Computer Science last year - a
superset of the old AB curriculum and in that class they implemented a
number of data structures such as binary search trees and hash tables,
but they really didn't have an opportunity to design something more
comprehensive.

At the start, suggestions were based around simple monolithic
designs. A class to represent a student, an array or hash table of
these classes and in each object, an array of grades or something like
that. 

Soon the discussion turned to optimizing search based on different
"keys." Searching by student id or searching by name. This led to the
idea of indices. For example, if our main data set is sorted by name, we can make auxiliary lists sorted by id or grades and use those to point into our main data set.


<div align="center">
<a href="/img/2013-10-09-database-part2/indices.png" rel="lightbox">
<img width="50%" src="/img/2013-10-09-database-part2/indices.png" class="" alt="" />
</a>
</div>


This was followed by less monolithic ideas -- essentially ideas behind
linking different tables using key fields. For example, a student
table with student id and a transcript table where each line has a
student id, a class, grade, teacher, and date.

<div align="center">
<a href="/img/2013-10-09-database-part2/links.png" rel="lightbox">
<img width="50%" src="/img/2013-10-09-database-part2/links.png" class="" alt="" />
</a>
</div>

Pretty sophisticated ideas.

From there we talked about assorted data structures that we could use with these ideas. 

I think it was a productive day.
