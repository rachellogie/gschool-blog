---
title: Front-end fabulous
date: 2014-04-21 19:03 UTC
tags: HTML, CSS, front-end
---

Up until now, we have been making some pretty cool apps using Ruby and Sinatra.
They work great, which is awesome, but they look like something straight out of the 90's.
Luckily for us, this past Friday we had a front-end expert come in and give us a talk
on how to add a little visual flair to our apps using HTML and CSS.

####Stretched Layout

Stretched layouts are all the rage. They're the pages you see where the content
goes all the way to the edge of the page.
The way you can achieve the stretched layout look is by using a div within a div. In
your html, put a div inside your header:

```
<header>
  <div id="header_container">
    Header Stuff
  </div>
</header>
```

And in your CSS:

```
#header_container {
  margin: auto;
  width: 980px;
}
```
The reason you put the inside "header_container" div is so that you can center it on the page,
which is what margin:auto is doing.  Basically,
you are making two boxes.  You are telling the inside box to have a width of 980px and be
centered within the outer one.  This is useful, because if you keep this pattern throughout
your html and css, the inside boxes of different sections will line up.

####Columns

Columns are another cool trick.  Check out <a href="http://solopine.com/">this page</a> and scroll down to see the
sections that have three or four images/blurbs across.  How can we recreate that look,
where everything is in horizontal alignment?  Columns!  Let's say we want to do
a layout with three columns across.

In your html, make three divs (one for each column) and give it a class of one_third:

```
<div id="container">
  <div class="one_third">
    Column 1
  </div>
  <div class="one_third">
    Column 2
  </div>
  <div class="one_third">
    Column 3
  </div>
</div>
```

And in your css do something like this:

```
/*columns -----------------*/

.one_third {
    width: 300px;
}

.one_fourth {
    width: 220px;
}

.one_third, .one_fourth {
    position: relative;
    margin-left: 10px;
    margin-right: 10px;
    margin-bottom: 20px;
    float: left;
}
```
The top line is just a comment so you can easily spot the column section in your css.
And I added in the one_fourth so you can see how you could also use a section with
four columns somewhere else on your page.

So there you have it!  Stretched layouts and columns: two tricks to make your life a
little easier and you pages look less 90's and more 2014!





