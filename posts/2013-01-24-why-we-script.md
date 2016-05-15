<!--
.. title: Why we script
.. slug: 2013-01-24-why-we-script.md
.. date: 2013-01-24
.. tags: cli, shell
.. type: text
-->


I tell my students "the cool thing about what we do is that if we're not happy with the way something works, we've got a shot at fixing it."

That came up this morning so I thought I'd share.

I
recently <a href="http://cestlaz.github.com/2012/12/09/real-projects.html#.UQFhh1L6s7x">posted</a>
about the in-term projects my Software Development kids were working
on. Well, now it's time to grade their final projects.

The code is up on GitHub. This morning I was faced with independently
going to every project page and cloning each one:

<div align="center">
<a href="http://cestlaz.github.com/img/github-projects.png" rel="lightbox">
<img width="50%" src="/img/github-projects.png" class="" alt="" />
</a>
</div>

Not fun!!!!

There had to be a better way. Fortunately all the projects were under a single "organization" and a little digging into the GitHub API reminded me that I could use this url:

<pre>
https://api.github.com/orgs/stuycs-ml7-projects/repos 
</pre>

which brought up all this nice JSON data.

<div align="center">
<a href="/img/github-api.png" rel="lightbox">
<img width="50%" src="/img/github-api.png" class="" alt="" />
</a>
</div>


A little poking around in the data finds that each project url is part of a line that starts with "ssh_url." 

a little wget, sed, grep and  sh magic later:

<pre>
urls=`wget --quiet -O - https://api.github.com/orgs/stuycs-ml7-projects/repos | grep ssh_url | sed "s/.*\(git.*\.git\).*/\1/g"`

for url in $urls 
do
  git clone git@$url
done
</pre>

Now, as long as all the projects are under a single Github organization I can easily clone or pull them without having to navigate the Github web site. 

Commandline FTW!!!!!!

