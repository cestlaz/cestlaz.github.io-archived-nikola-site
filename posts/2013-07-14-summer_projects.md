<!--
.. title: Summer Project 1 - Citibike Data
.. slug: 2013-07-14-summer_projects.md
.. date: 2013-07-14
.. tags: misc
.. type: text
-->


So, the Citibike program has been running for a bit. I like the idea,
but I have some reservations -- it's great for getting around in the
zone - I've been using it for short shopping trips - run cross town to
[Fairway](http://www.fairwaymarket.com/) or take a quick trip from
work to [Porto Rico Importers](http://www.portorico.com/store/) or
[Rocco's Pastries](http://pasticceriarocco.com/). On the other hand,
the zone doesn't get to the residential neighborhoods of upper
Manhattan or the boroughs and the price per day is way too expensive
for regular working class joes, particularly on top of a subway trip.

In any event, I was curious about station use patterns. Cool thing is
that you can get live data from
[here](http://citibikenyc.com/stations/json). This was a great
opportunity to play with some tools to see if I want to use them in
class next year. In particular, [backbone.js](http://backbonejs.org)
and [d3.js](d3js.org). 

So, I'm grabbing the station data every 5 minutes, storing it in a
Mongo database, and threw together a little map and graph app:

<div align="center">
<a href="http://cb.zamansky.net">
<img width="50%" src="/img/2013-07-14-summer-projects/citibike-1.png" class="" alt="" />
</a>
</div>

You can check it out [here](http://cb.zamansky.net). 

The code is up on GitHub:
[citibike-1](http://github.com/zamansky/citibike-1).

I might play around and add more graphs as I collect more data or
maybe I'll just move on to the next project.

