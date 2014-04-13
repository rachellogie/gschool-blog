---
title: Regular Expressions Fun Time! Part 1
date: 2014-04-08 23:30 UTC
tags: regular expressions, ruby, rubular
---

Who wants to learn about regular expressions! That wasn't a question.
A few days ago I was pretty scared of
regular expressions, and I avoided them at all costs. Luckily I did
a bit of research and gave a lightning talk on the topic, so I am
feeling a little bit better about them.  I will now impart my
regular expressions knowledge onto you all.

A regular expression is a pattern that can be matched against a string.
We can use them in several scenarios, such as validating the format of
input, like credit card numbers, phone numbers, email addresses, or
urls.  We can also use them to extract data from a string, or replace
complex patterns in strings.

You build regular expressions from special characters that have
certain meanings.  For example, the . (period) refers to any character,
while \s means whitespace.  I like to use rubular.com, which is a
great way to test out your regular expressions, and see what the
matches would be.  It also has a cheat sheet with way more special
characters than I care to list here.

This won't make sense until I do an example.
Let's say I am filtering a document and
I want to match all the occurrences of the word "color."  But wait,
this document has collaborators from many different countries,
and some of them spell the word color as "colour." How could I write
a regular expression that matches both? Well, let's hop on over to
rubular.com and take a quick look at their cheat sheet. Hmm, it seems
that the ? (question mark) means "0 or 1 of whatever is before it."
So perhaps we could do something like this...

<img src="/images/foundation/orbit/rubular.png">

This is a screen shot from rubular.com.  See how it shows you
what the matches would be? Pretty awesome tool. So now that we have
our regular expression, what do we do with it?  How do we use
it in our ruby code? I will cover ruby methods that can be used with
regular expressions in part two of this series. So stay tuned
 for more regular expression fun times next week!