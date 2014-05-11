---
title: Gettin cray with APIs
date: 2014-05-11 01:57 UTC
tags: API, google, VCR, faraday
---

APIs are awesome, although until Monday of this week I wasn't entirely sure what they were.
I had heard the term thrown around a lot and I had read less-than-clear Wikipedia articles, but
all I knew was that it stood for Application Programming Interface.  Which, frankly, meant nothing
to me.  But, like most things, once I actually got in there and started using APIs, the confusion
as to what they are cleared right up.  I am going to go through, step by step, how to make API calls
from your own app, and you will see how awesome they are.

Ok, so let's think.  What kind of data do we want to get?  Do we want some weather data for our app? If so,
we could use a weather API such as AccuWeather to get the current weather, and then we could display it on
our website. For my personal app, I wanted to pull in restaurant information from google, so I went
to see what APIs google had available.  Turns out, they have a lot.  I needed google places API.  If you
go to the docs, you can see an example of what your api call should look like:

```
https://maps.googleapis.com/maps/api/place/nearbysearch/json?
location=-33.8670522,151.1957362&radius=500&types=food&name=harbour
&sensor=false&key=AddYourOwnKeyHere
```

In this example you would be searching for food places that are within a 500 meter (how many meters
 in a mile?) radius of the latitude and longitude listed and whose name matches with harbour.
 What is that thing on the end, you ask?  The key? Well,
it turns out, some APIs require you to have some sort of authentication.  In this case, after you sign up to
use the places api, google gives you a key that you must use in all your requests.  This is so that
they can keep tabs on how many calls you are making, and limit you.  For example, the places API courtesy
limit is 1,000 API calls a day.  You might also see authentication done through headers- it just
depends on the API.

But, you protest, the courtesy limit doesn't seem sufficient, especially since I am running my test
suite and it is making tons of api calls just to test. This is where a ruby gem called VCR will come in
handy.  VCR allows you to wrap each test in a "cassette," and when you run the test the VCR will record
the results of the API call in that cassette and refer to that cassette
the next time you run your test, so that you don't have to keep making the API calls.

So, I have looked at the docs and know what to type in, but how do I see what I'm going to get back?
Postman is a useful tool, available from the chrome web store. Once you have it open, you can put in your
api request and it return a nicely formatted response, so you can see exactly what data
it is returning and what the data structure looks like.  You can experiment in Postman until you
feel comfortable.

Then, when you know exactly what your API call should look like, and what you are going to get back,
you can put it in your rails app.  I have been using the faraday gem.  Straight from
the faraday docs, it can be as simple as this:

```
response = Faraday.get 'http://sushi.com/nigiri/sake.json'
```
And its just a couple more lines if you want to do more complicated things, like add headers.


#####So, to recap:

1. Do some research on the API that you want to use.
2. Look at the docs for that API so you know how to write your request.
3. Include your key, if needed.
4. Put your request into Postman, so you can see what the response will look like.
5. Write a test, using VCR, to test your API calls.
6. Write your API calls using the faraday gem.


