---
title: Regular Expressions Fun Time! Part 2
date: 2014-04-13 16:25 UTC
tags: regular expressions, ruby
---

So last week we talked about regular expressions, and we did a little example
using rubular.com.  So now that you have tested out your regular expression, what
do you do with it? How do you put it into your code? Well, it really depends on
what you want to do with it.  Ruby gives us several
methods that work with regular expressions, and I am going to go over a few
of them here.

#####=~
Ruby gives us the =~ operator, which matches a string against a pattern. A quick
example:

```
"bananas" =~ /bananas/
```
Now what do you think that's going to return? Perhaps you think that the =~ looks
similar to the ==, and so it would return true, since there is a match here. Well,
you would be wrong. What it actually returns is the index of where the match
occurred (0 in this case), or nil if no match occurred. But, you protest, I don't
need the index, I need true or false! How could we coax a true or false out of
this situation? Well, let's remember that nil is falsy, and numbers are truthy,
so we could do something like this:

```
if "bananas" =~ /bananas/
  true
else
  false
end
```
If you type that into irb, it will give you true.
#####!~
Alternatively, we could use
the !~ operator, which tests whether a string does NOT match against a pattern.
For example:

```
"i love bananas!" !~ /pineapple/
```
This is basically saying that the string ("i love bananas!") does not match against
the pattern(/pineapple/).  So what do you think this would return to us? Now you're
probably scared to venture forth true or false,
 but that is exactly what it returns.  This example
would return true, since they don't match.  If we had something like this:

```
"i love bananas!" !~ /bananas/
```
it would return false, since there obviously is a match.

#####.scan
Ruby also gives us an awesome scan method, which scans a string and
returns an array of matches:

```
"001_foo.rb 002_foo.rb 003_foo.rb".scan(/\d{3}/)
>>> ["001", "002", "003"]
```
In this particular case, it is looking for exactly 3 digits.

#####.gsub
The last one I'll talk about is gsub, which means "global substitution" --
it goes through a string and substitutes all the occurrences of the match with
whatever your seconds argument is.  Back to our color/colour example from last
week:

```
"i like this color but not that colour".gsub(/colou?r/, "red")
>>> "i like this red but not that red"
```
And we can see that it returns to us a string, with all the matches for
/colou?r/ substituted with the word "red" because that's what we told it to do.

There are also some other ones, like match, that I won't go into.  I think that's enough
for right now.  Perhaps you still don't think that regular expressions are a fun time,
but hopefully you do feel a little more comfortable with using them in Ruby.