---
layout: post
title: Proposed NodeSchool Workshopper
---

# A New NodeSchool Workshopper

As I mentioned before, I mentored a NodeSchool on 5/23/2015 in Reno.  We presented the Learnyounode and Javascripting
workshoppers.  I want to start off by saying `thanks` to the writers of those workshoppers.  It was clear that they
worked hard on them and they certainly serve the purpose of teaching programming concepts to beginning programmers.

However, while we were at the event, we did get feedback from the students and the mentors noticed a number of patterns
that we feel deserve to be addressed.  Immediately after the workshop we talked and we chatted on Slack in the days
following and we came up with a number of ideas that we thought might help students learn better.

This post begins to outline a new NodeSchool workshopper for beginner to novice JavaScript developers that will attempt
to address the feedback we received.

## Reference
[Authoring Node.js workshopper lessons](http://lin-clark.com/blog/2014/07/01/authoring-nodejs-workshopper-lessons/)

## Goals
The goal of this workshopper is to introduce students to JavaScript using a story-driven approach.  A number of criticisms
and feedback comments were noted during the 5/23/2015 NodeSchool in Reno.  One criticism of existing workshoppers is that 
they do not provide 
context to the student about *why* they should be learning to program; they only describe the *how*.  The mentors of
the event noted that many of the students struggled with the exercises in the same way, indicating a possible problem
with the exercise itself.  Common sources of confusion were syntax and using the example in the program when the example
was leading to the wrong answer.

## Concept for Workshopper
The student is presented with a storyline that puts them in the position of a programmer that is organizing a 
JavaScript conference.  Naturally, as a programmer, the student will be using programming exercises to help them solve
many of the logistical issues of planning a conference.  

Possible sources of exercises will include:  
* printing name tags  
* counting guests  
* counting speakers  
* scheduling speakers  
* calculating budgets  
* meal planning  
* etc.

## Language
The workshopper will take the form of a story-based series of exercises.  The exercises should start with the assumption
that the student has never programmed before.  Exercises will build on each other in complexity and should serve to push
the narrative.  Spaced repetition will be uses to present common programming structures multiple times to the student 
(spaced repetition is a technique where concepts are repeated back to the student but not necessarily one right after another.
I think there's a lot of research about this but we could probably simplify it by occasionally bringing back a topic from
earlier in the course).

As the workshopper is story driven and we don't want to alienate any students, all stories should prefer the second person
(you) to keep the story gender neutral.  Additional characters in the story and names in data should represent a broad range of genders,
ethnicities, ages, etc.  There are online character generators that will generate random names/identities to help with
this.

## Structure of exercises
One of the criticisms of other workshoppers was that they were confusing to read.  Info about the exercise was mixed with
an example.  The example might have been similar to the exercise but confused the exercise because it had extraneous
statements in it.  Syntax wasn't given much attention so syntax errors were common.  The validation system was expecting
a very specific output but that wasn't clear from the exercise.

To help this issue, we'll try to organize each exercise using a very regular format with clearly defined headers.  An
example of this format, would be:  
* Introduction - the story that introduces the exercise  
* Code Example and Hints  
* Syntax to watch for  
* Expected output of the student's program  

Additionally, the results of each pass or fail should also follow a regular format:  
* Pass/fail message  
* Output from the student's program  
* If fail, possibly parse the error or from the failed test provide feedback on what may be wrong  
* If pass, present the official answer along with comments about it's structure & syntax

## Next steps
The next step will be to start outlining the story and matching up coding concepts with each point of the outline.
After that, we can start writing exercises and the long-form story to go with each exercise.

## Repo
Here's the repo where this project will live:  
[https://github.com/gwmccull/javascript-workshopper]
