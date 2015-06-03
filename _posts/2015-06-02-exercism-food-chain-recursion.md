---
layout: post
title: Solving the Exercism Food Chain exercise with Recursion
---

# Solving the Exercism Food Chain exercise with Recursion

I've always been a big fan of recursion.  I enjoyed it in college when I was programming in C++ and lately, I've been
working on a number of JavaScript recursion exercises.  A number of the problems that I've done so far from the NodeSchool 
Functional JavaScript workshopper use recursion.

So when this problem came up on Exercism, programming a song with repeating lyrics that build on top of each other, my first
thought was to turn to recursion.

My answer is below.  It's pretty straightforward.  I wrote it in ECMAScript 6.  The entry point is through `verse()` or
`verses()`.  The verses and the refrains are built up using recursion rather than loops.  Note: I'm not a musician, so
it's very likely that those are the wrong terms.

If you're not familiar with recursion, a recursive function is one that calls itself.  Often, a recursive function will
pass some sort of counter variable that is incremented or decremented so that the function can tell when it's done.  In
my code, the verse number or refrain number serves that purpose.

When solving the exercise, I decided to take the most direct line possible without a whole lot of pre-planning or 
premature optimization.  The test suite tests each individual verse so I started with a single function (verse) with
a big switch/case that simply returned the exact phrase requested.  From there, I refactored by moving the intro
into it's own function, moving the closing line into another function, and built a third function to return each repeated
refrain.  

Rather than call the `getRefrain()` function repeatedly for each verse, I built a recursive function to build up the 
series of refrains.

The final tests involve getting multiple, sequential verses.  For that, I just created a recursive wrapper, `verses()`, 
for the `verse()` function.


{% highlight javascript %}
class FoodChain {
    constructor() {}

    verses(start, end) {
        if (start > end) return "";

        return this.verse(start) + '\n' + this.verses(start + 1, end);
    }

    verse(num) {
        let result = this.intro();

        switch (num) {
            case 1:
                result += "fly.\n";
                break;
            case 2:
                result += "spider.\nIt wriggled and jiggled and tickled inside her.\n";
                break;
            case 3:
                result += "bird.\n" +
                "How absurd to swallow a bird!\n";
                break;
            case 4:
                result += "cat.\n" +
                "Imagine that, to swallow a cat!\n";
                break;
            case 5:
                result += "dog.\n" +
                "What a hog, to swallow a dog!\n";
                break;
            case 6:
                result += "goat.\n" +
                "Just opened her throat and swallowed a goat!\n";
                break;
            case 7:
                result += "cow.\n" +
                "I don't know how she swallowed a cow!\n";
                break;
            case 8:
                result += "horse.\n" + "She's dead, of course!\n";
                break;
        }

        if (num > 1 && num < 8) {
            result += this.getRefrains(num - 1);
        }

        if (num < 8) {
            result += this.flyEnding();
        }

        return result;
    }

    intro() {
        return "I know an old lady who swallowed a ";
    }

    flyEnding() {
        return "I don't know why she swallowed the fly. Perhaps she'll die.\n";
    }

    getRefrains(num) {
        if (num === 0) return "";

        return this.getRefrain(num) + this.getRefrains(num - 1);
    }

    getRefrain(num) {
        let result = "";

        switch (num) {
            case 1:
                result = "She swallowed the spider to catch the fly.\n";
                break;
            case 2:
                result = "She swallowed the bird to catch the spider that wriggled and jiggled and tickled inside her.\n";
                break;
            case 3:
                result = "She swallowed the cat to catch the bird.\n";
                break;
            case 4:
                result = "She swallowed the dog to catch the cat.\n";
                break;
            case 5:
                result = "She swallowed the goat to catch the dog.\n";
                break;
            case 6:
                result = "She swallowed the cow to catch the goat.\n";
                break;
        }

        return result;
    }
}

module.exports = new FoodChain();
{% endhighlight %}
