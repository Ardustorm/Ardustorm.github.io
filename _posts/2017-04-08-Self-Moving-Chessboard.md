---
layout: post
title:  Introduction to the Self Moving Chessboard
category: Chess
tag: Chess wip
---


We have started working on an automatic Chessboard that will
be able to sense pieces (using hall effect sensors) and move them
(using an electromagnet).

To sense the pieces, we are going to embed magnets in each of them
and place hall effect sensors under each square. This will not give
us the whole information, only that some piece is on a square. To
know which piece is which will be done in software. Since the board
will be set up the same at the begining of each game, we will know
which pieces are which. Then it is a matter of updating this representation
every time a piece moves. (Some special care will have to be given when
a piece takes another piece.)



To move the pieces, we are going to have an electromagnet underneath
the board, that way the board looks almost magical. We then brainstormed
and researched ideas for a xy system. We wanted to make it cheap, light,
and small, so a conventional xy system with linear rods was out.
We eventually came across the hbot design and then the CoreXY design.

The benefit of both of these designs is that they do not require linear
rods or bearings, and both motors are stationary. They are also easy to
implement. The CoreXY system requires 8 pulleys and a horizontal bar.
That's it.

![CoreXY Design](/img/CoreXY_Design.png)

The kinematics are also pretty simple. Each motor controls a diagonal,
so to get a horizontal or vertical line, both motors are run together.
The equations for which are included in the image above. [This post ](https://www.marginallyclever.com/2015/01/adapting-makelangelo-corexy-kinematics/)
from Marginally Clever provides some great information about the CoreXY
system and how to drive it. He has [another post ](https://www.marginallyclever.com/2013/08/how-to-build-an-2-axis-arduino-cnc-gcode-interpreter/)
where he goes over the basics of a simple gcode interpreter and how to
move in straight lines. I found both of these posts very useful in creating
a simple program that takes in an xy position in steps, and then moves there.



So Where are we now?
=============

We are currently working on the 3rd-ish prototype.

The first one consisted of cardboard and milk jug handles and
was just a proof of concept to us that the CoreXY system
would work.

The second prototype, also made of cardboard (can you tell that
I'm a fan of Cardboard Aided Design (CAD) ). This one had motors and actual
pulleys and we were able to see that it worked. It eventually fell apart
and so we started work on the 3rd revision.

This one will be made of aluminum angle stock and will last much longer
then the others. We are planing to use the 28byj-48 stepper motors
because they are cheap (a bit over a dollar each), small, and quite.
One downside of these motors though is that they are quite slow.
We might have to eventually move to a different motor but for now
these should work just fine.

![Stepper Motor](/img/28byj-48_StepperMotor.jpg)

I'm also planing on controlling the whole board with an esp8266,
that way the board could connect to the internet. Driving
the motors will be taken care of with a shift register and a Darlington
array on a custom pcb, and reading the state of the board will be
handled by additional shift registers.


There is still a lot left to do but I think we have a pretty solid start.
We might run into some problems such as the electromagnet being to weak,
the b, and reading the state of the board will be
handled by additional shift registers.


There is still a lot left to do but I think we have a pretty solid start.
We might run into some problems such as the electromagnet being to weak,
the motors being to slow, etc. but we'll cross those bridges when we get
there.

Next time, I'll talk a little bit about where we see the project going
and where we are then.