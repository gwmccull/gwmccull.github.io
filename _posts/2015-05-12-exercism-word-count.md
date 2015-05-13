---
layout: post
title: Exercism.io - Word Count
---

I did the JavaScript Word Count exercise on [Exercism.io](http://exercism.io) tonight.  It was a pretty interesting
little exercise.

I ended up solving it this way:
{% highlight javascript %}
var words = function(input) {
    var subStrings = input.replace(/\s+/, ' ').split(' ');
    var total = Object.create(null);

    subStrings.forEach(function(string) {
        if (typeof total[string] === 'undefined') {
            total[string] = 0;
        }

        total[string]++;
    });

    return total;
};

module.exports = words;
{% endhighlight %}

Pretty straightforward, I thought.

Other folks on the site had some good feedback.  Initially, I was using `var total = {}` which led to some additional
complexity in the forEach loop to test invalid types.  Based on some comments, I switched to `Object.create(null)` which
allows you to create an object with no prototype.

Other people on the site used `Array.reduce()` to solve the problem.  That was interesting to see.  I haven't really used
`Array.reduce()` before; I'll have to look into it more.

One person commented on the use of `Array.forEach()` citing issues with legibility and backwards compatibility.  I feel
that it's pretty easy to read, and easier in some ways than a normal for loop.  And it's supported by IE9 and up, which
is plenty of backwards compatibility for a demo exercise.  I think we need to push ahead with newer capibilities of JavaScript
and not let support for old browsers hamper the evolution of the language, unless backwards compatibility really is a 
deal breaker.