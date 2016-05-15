<!--
.. title: Shell Games - an introduction
.. slug: 2014-02-04-shellgames-1-intro.md
.. date: 2014-02-04
.. tags: 
.. type: text
-->




A few weeks ago, I noticed this Twitter conversation between <a href="http://twitter.com/alfredtwo">Alfred Thompson</a>  and <a href="http://twitter.com/keinath">Steve Keinath</a>

<p></p>

<blockquote class="twitter-tweet">I&#39;d love to see an Intro to Linux (way more than just install) as a 3-hour workshop at <a href="https://twitter.com/search?q=%23CSTA14&amp;src=hash">#CSTA14</a> <a href="https://twitter.com/csteachersa">@csteachersa</a></p>&mdash; Steve Keinath (@keinath) <a href="https://twitter.com/keinath/statuses/400333558603997184">November 12, 2013</a></blockquote><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><a href="https://twitter.com/alfredtwo">@alfredtwo</a> <a href="https://twitter.com/csteachersa">@csteachersa</a> Right. I know very little &amp; would love a &quot;zero to hero&quot; Linux workshop.</p>&mdash; Steve Keinath (@keinath) <a href="https://twitter.com/keinath/statuses/400335634297937920">November 12, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<p></p>

I briefly considered proposing a session for the conference but it was just a day or two before the deadline, I don't know if I'm going to be able to attend the conference, and besides, who said anything I proposed would be accepted.

<p></p>

Still, I liked the idea - I've been an educator for 23 years, a Linux user for most of that time and an  Unix user for longer. I'm a firm believer in operating system as toolkit and so I think I'll take Steve and Alfred's suggestion and try to put together a series of posts on using Linux from a CS educators point of view.
<p></p>


So, before we begin - a little background.

<p></p>

I can proudly say that I've been Windows free since about 2000. That's when I decided to wipe the lat traces of Microsoft from my hard drives. Prior to that I just booted up MS-DOS or Windows to play games or to use a Excel or Word.
<p></p>

Since the early days of Linux - back before Slackware, I dual booted. Before Linux, I dialed into public Unix systems such as <a href="http://www.panix.com">Panix</a> or <a href="http://en.wikipedia.org/wiki/The_Big_Electric_Cat">The Big Electric Cat</a>. At home, I tried to make MS-DOS as Unix like as I could. I ran the <a href="http://en.wikipedia.org/wiki/MKS_Toolkit">MKS Toolkti</a>, and used my own shell (a project every young programmer should attempt).
<p></p>


Why am I posting this now? It's a new semester and I find myself, as usual, leveraging the Linux shell. It was time to set up a mailing list for the class.

<p></p>

I'm able to go to our school's data system and grab a tab delimited file that looks something like this:
<p></p>

  <blockquote><pre>
Code	Section	Period	Last	First	ID	Official	Advisor	OSIS	Email
grY22tBs	01	6	Hxk	Blu GFy	9272	7rr	gEs	274989649	zlu3lxk@QylKR.oqy
grY22tBs	01	6	HiQqvlRu	Blku	9918	7PP	YHZHm	200878353	zzl8@yu.oqy
grY22tBs	01	6	plxk	ClSKv	9226	7II	PHXrNY	274661826	olxkvl@QylKR.oqy
grY22tBs	01	6	pxKk	BqVxFl	9026	7II	PHXrNY	224608174	zo6461@lqR.oqy
grY22tBs	01	6	pqxuk	NRK	9234	7dd	gHAMmNd	270217219	uRKo90@QylKR.oqy
  </pre>  </blockquote>

<p></p>

It's tab delimited but I scrambled the letters so as to not reveal any student info.
<p></p>

Oh, how did I do that scrambling? Easy. First, I combined some basic utilities to make a random permutation of the upper and lower case letters and stored them in a shell variable. Don't worry, I'll explain these commands in upcoming posts:
<p></p>

<blockquote>
perm=`echo "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ | sed "s/\(.\)/\1\n/g" | sort -R | tr -t "\\n" ":" | sed "s/[^a-zA-Z0-9,@]//g"`
</blockquote>

<p></p>

Then I used tr (translate) to exchange the real letters for the matching letter in the random permutation:
<p></p>

<blockquote>
cat students.tsv | tr a-zA-Z $perm > students.scrambled
</blockquote>
<p></p>


So back to the real work. I needed to isolate the students email addresses. The process:
<p></p>

  <ol>
    <li>convert the tabs to commas</li>
	<li>Pull out the students in my AP class (code MKX22X) from the list of all students</li>
    <li>Pull out the 10th column</li>
    <li>These are the emails, save them to a file</li
  </ol>
<p></p>

So, I typed:
<p></p>

<blockquote>
cat students.tsv | grep MKS22X | sed "s/\t/,/g" | cut -d, -f10 > emails
</blockquote>
<p></p>

grep filters out lines that have MKS22X in them and sed replaces the tabs (\t) with commas and cut pulls out the email addresses. It's all stored in a file named emails.
<p></p>

Now, I just have to import these into my maillist software (mailman).
<p></p>

  <blockquote>
    add_members -r emails myclasslist
  </blockquote>
<p></p>

So, that's it, easy peasy.
<p></p>

I'll be away for most of this week at the Tapia conference and then I'll be playing catch up, but I'm hoping to do a series of posts talking about my Linux toolset and how I use it.
<p></p>

I hope you all find it interesting and maybe even useful.
<p></p>
