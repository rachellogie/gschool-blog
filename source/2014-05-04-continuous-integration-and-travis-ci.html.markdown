---
title: Continuous Integration and Travis CI
date: 2014-05-04 19:32 UTC
tags: continuous integration, travis ci
---

Remember when I talked about pair programming as a tenet of extreme programming?  Well,
I have another extreme programming practice for you-- continuous integration.  Ideally, you
would be integrating your code every few hours, as opposed to holding onto it for extended periods
of time and then finding yourself in integration hell when you discover everyone's code is
incompatible.

Travis CI is a continuous integration service that hooks up to your github repos, and best of
all its free! Let's go through how to get this working with your app, including using the
CCMenu.

1.  Go to https://travis-ci.org/ and sign in with your github login.

2.  You will see a list of all your repos.  They will initially all say "off," but you
should pick one that you want and flip it to "on."

3. Open up that project in RubyMine (or whatever text editor you like) and add a .travis.yml
file to the root.  Mine looks like this:

```
language: ruby
rvm:
  - "2.1.1"
script:
  - RAILS_ENV=test bundle exec rake --trace db:create db:migrate
```

If you look at the docs, it will say something about jruby and rbx. I did not need to include these
for my personal project, but you might need them for yours.

4. Make a commit, and as soon as you push to github, it will trigger travis ci to start the build.
You can go to the homepage and view your build happening under "My Repositories."

But how do you know when it gets done?  Do you have to keep flipping back over to the webpage? The
answer is no! There is something called the CCMenu.

5. Go to the app store and search for CCMenu.  Download it.

This app provides you with a little square in your toolbar, which will be green if your
build passes!

6. Click on the little square, go to preferences, and then at the bottom there should be a plus
button.  Click that, and then add your project.

Voila!  That's all there is to it.