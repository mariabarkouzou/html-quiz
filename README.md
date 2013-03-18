
Jeopardy-like quiz script
=========================

Copyright 2013 Google Inc.
Written by [Michał Nazarewicz](mailto:mina86@mina86.com).
This is not a Google product.

Overview
--------

This is a Jeopardy-like quiz game with the difference that it
currently supports only two players (or teams) and there are no
negative points.

The idea is that teams get questions alternately and if one does not
answer the other gets a chance.  If neither answers correctly, it's
a tie.  Another way to play is to have teams use buzzers of some kind
to determine which gets the first try at the question.  The way I've
used the script is by having two asymmetric teams and the smaller one
always getting the first chance.

Configuration
-------------

Configuration is rather simple.  Most of the things to modify is in
the `index.html` file and they include content of:
* the TITLE element which determines the title text shown at the top
  of the page, and
* the #questions DIV which determines categories and list of
  questions.

Categories are determined by the H2 elements and each question and
answer is specified as two DIV or P elements.  If either question or
answer is just a single paragraph a single P element can be used,
otherwise a DIV element is necessary.  Because of some scripts
limitations, there must be at least two categories.  And there must be
exactly five questions per category – if any are missing, a greyed out
box will be displayed.

You can put almost any kind of HTML in either a question or an answer
so this includes images, embedded audio or video, etc.  Beware that
you may need to add some styling for the elements to show up properly
on the question board and when printing.

Secondly, there is a `teams` variable in the `jeo.js` file.  It
contains the names of the two teams that participate (and yes, there
must be two teams).  Finally, if you want to localise the script to
a different language, you may change the value of `strTie` and
`strClose` variables.

Usage
-----

First of all, you should check print preview and print the web page as
it will give you list of questions and answers for each category.  If
your questions are not too long you should get one-page per category
printout.  This may be helpful when hosting the game.

Controls of the game itself are rather simple.  As you open the site,
a grid should show up with category names at the top and boxes indexed
from 100 to 500 for each question in the category.  Clicking on such
a box brings up the question board with the question, an “x” link in
top right corner and three links at the bottom: “Team 1”, “Tie” and
“Team 2” (the text obviously depends on values of configuration
variables in `jeo.js` file).

Pressing “x” hides the question board in case you've clicked on it by
mistake.  “Team 1” and “Team 2” links will hide the question board,
add appropriate amount of points to given team, and disable the
question.  The “Tie” button shows the answer to the question and
replaces bottom links with a single “Close” link, which disables the
question without adding points to either team.  Disabling the
questions greys corresponding box out and makes it impossible to
display the question board again.

Lastly, team scores are displayed on the bottom.  If there was any
kind of mix-up and scores need to be altered it's enough to click on
the number and a prompt will show up where one can enter new score for
given team.

And that's about it, when it comes to usage – not very complicated.