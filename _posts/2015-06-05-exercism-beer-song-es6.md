---
layout: post
title: Solving the Exercism Beer Song exercise with ES6
---

# Solving the Exercism Beer Song exercise with ES6

The most recent exercise from Exercism was to write code that generates the Beer Song (ie, "99 bottles of beer on the wall...").
This exercise was somewhat similar to the last exercise, which was another song generator.

I chose to write this exercise using ES6 and used it as an excuse to try out some of the new features of ES6 including string templates,
static functions, classes, and default and rest variables for functions.

I'm sure there are a few more that I could have thrown in but I'm pretty happy how it turned out.  The string templates
were especially helpful in this exercise.

It was also interesting to note how my ES6 code ended up much different than the ES5 code submitted by other developers.
Part of it is style, of course, but the new features made a big difference.  Other developers ended up with a lot more string
concatenation, for loops and if statements.  While mine does some of that, I feel like it ended up being cleaner.


```JavaScript
class BeerSong {
    constructor() { }

    sing(start, end = 0) {
        return this.verse(start) + ((start !== end)?"\n" + this.sing(start - 1, end):"");
    }

    verse(num) {
        let verse = this.replace`${num} ${BeerSong.bottles(num)} of beer on the wall, ${num} ${BeerSong.bottles(num)} of beer.\n`;

        if (num) {
            verse += this.replace`Take ${(num === 1) ? 'it' : 'one'} down and pass it around, ${num - 1} ${BeerSong.bottles(num - 1)} of beer on the wall.\n`;
        } else {
            verse += "Go to the store and buy some more, 99 bottles of beer on the wall.\n";
        }

        return verse;
    }

    replace(strings, ...subs) {
        let result = "";

        subs.forEach(function(sub, index, subs) {
            let str = sub;
            if (str === 0) {
                if (index === 0) {
                    str = 'No more';
                } else {
                    str = 'no more';
                }
            }

            result += strings[index] + str;
        });

        result += strings[strings.length - 1];

        return result;
    }

    static bottles(num) {
        return (num === 1) ? "bottle" : "bottles";
    }
}

module.exports = new BeerSong();
```
