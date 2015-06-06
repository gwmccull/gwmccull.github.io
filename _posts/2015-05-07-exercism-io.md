---
layout: post
title: Exercism.io
---

I started working through the [Exercism.io](http://exercism.io) exercises yesterday.  
Exercism is a site where people can complete coding challenges and have their work reviewed by other users of the site.
It's offered in a number of different languages and I understand that the exercises will start easy and get harder.

I completed the Javascript 'Bob' exercise tonight.  It wasn't too difficult and it was kinda fun.  It involved a lot of
string manipulation which I don't really do at work so that exercised a few muscles I don't often use.

I took what I thought was a pretty straightforward approach.  I didn't really read ahead on the tests.  I simply enabled
each test, one by one, and coded to meet that test.  After the first 5 or so tests, I did a small refactor.  Then another
refactor after about 12 tests.

Once I uploaded my version, I was able to see other people's code.  That was pretty interesting.  A number of people came up
with totally different code.  I didn't test any of them so I don't know if they worked or not but it was interesting
to see all of the variations.  There were a few that "cheated" by simply coding the input/responses directly into their
programs.  

Here's my final code:
{% highlight javascript %}
var Bob = function() {};

Bob.prototype.hey = function(input) {
    var response = "Whatever.",     // default response
        lastChar = input.charAt(input.length - 1),
        isSilence = input.trim() === '',
        isShouting = input.toUpperCase() === input && !isSilence,
        isAllNumbers = input.search(/(\d+,?\s?)+[\.!\?]*/) != -1,
        isQuestion = lastChar === '?',
        isExcl = lastChar === '!';

    if (isShouting && !isAllNumbers) {
        response = 'Whoa, chill out!';
    } else if (isQuestion) {
        response = 'Sure.';
    } else if (isAllNumbers) {
        if (isExcl) {
            response = 'Whoa, chill out!';
        } else {
            response = "Whatever.";
        }
    } else if (isSilence) {
        response = "Fine. Be that way!";
    }

    return response;
};

module.exports = Bob;
{% endhighlight %}

Exercism seems like a fun way to practice some coding.  It also gives me an excuse to commit some stuff to Github, which
I need to do more of if I'm ever going to qualify for a profile on [Stack Overflow Careers](https://careers.stackoverflow.com/) ;-)
