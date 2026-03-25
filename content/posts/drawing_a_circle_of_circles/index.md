+++
date = '2026-02-03T21:04:00-05:00'
draft = false
title = 'Drawing_a_circle_of_circles'
p5 = true
+++


# Drawing a circle of circles

Lying awake in bed one night, the image of a circle of circles popped into my head. Take a single circle and then keep repeating the same circle and placing it next to the prior circle until you create a perfect circle of circles. 

What I thought next was, this is maybe an interesting math problem... at least for me. See I've been out of school for over a decade now, and it's not every day that I am thinking about a specific math problem. For this situation, I thought of a few associated problems:
  * Given a circle of radius l, how many circles do you need to make a perfect circle?
    * What would be the radius of the central circle, say r, given a circle of circles of radius l?
    * Are there different solutions for larger circles?
  * Flipping it somewhat, given a central circle of radius r, what are the possible radius' of outer circles that could make an outer circle of circles border?


I stumbled upon this Math Stack Exchange [post](https://math.stackexchange.com/questions/12166/numbers-of-circles-around-a-circle) which is relevant, but doesn't generalize solutions for the above.

I haven't totally worked out a general solution yet. I'm not sure it is possible, but this sparked my interest in computer rendering which has rarely happened to me!

I'd like to draw circles of circles and since I know very little about rendering, I'm going to ask Claude Code to help me out. Here we go...

Looks decent for the inner ring, but the outer ring doesn't border the inner ring all the way around.

First I'll define common functions defined to assist in making multiple drawings. I'm probably not doing this right, since it seemed harder than necessary, but then again I *rarely* use javascript.

  {{< p5sketch >}}
  /////////////////////
  // COMMON FUNCTIONS
  /////////////////////

  // This is the right way to draw a circle of circles where they all intersect given inner circle large radius r and the number of circles
  if (!window.computeRingCircleRadius) {
    window.computeRingCircleRadius = function(r, n) {
      let l = r * Math.sin(Math.PI / n)
      return l;
    }
  }

  if (!window.drawRingCircle) {
    window.drawRingCircle = function(p, outerRadius, numCircles, centerX, centerY, color=200) {
    p.circle(centerX, centerY, outerRadius * 2);
    for (let i = 0; i < numCircles; i++) {

      let circleRadius = window.computeRingCircleRadius(outerRadius, numCircles);
      let angle = (360 / numCircles) * i; 
      let rad = p.radians(angle);
      let x = centerX + p.cos(rad) * outerRadius;
      let y = centerY + p.sin(rad) * outerRadius;

      p.fill(color, 0, 0);
      p.circle(x, y, circleRadius*2);
    }
    }
  }

  {{< /p5sketch >}}


Now let's draw some circles. This took me a couple attempts to get the math and code right.

  {{< p5sketch >}}
  p.setup = function() {
    p.createCanvas(1200, 1200);
    p.noLoop();
  }

  p.draw = function() {
    p.background(255);

    // Variables
    let centerX = p.width / 2;
    let centerY = p.height / 2;
    let outerRadius = 100;
    let numCircles = 4;

    // Central circle
    p.circle(centerX, centerY, outerRadius * 2);

    // Iterate and draw circles around center that all intersect with one another
    for (let i = 0; i < numCircles; i++) {
      // Math operations: +, -, *, /
      let circleRadius = window.computeRingCircleRadius(outerRadius, numCircles);
      let angle = (360 / numCircles) * i; 
      let rad = p.radians(angle);
      let x = centerX + p.cos(rad) * outerRadius;
      let y = centerY + p.sin(rad) * outerRadius;

      p.circle(x, y, circleRadius*2);
    }
  }
  {{< /p5sketch >}}

That looks good for one ring of circles! Javascipt ain't so bad! More direct than a Jupyter notebook. Now can I clean up the code a little bit?


  {{< p5sketch >}}
  p.setup = function() {
    p.createCanvas(1200, 1200);
    p.noLoop();
  }

  p.draw = function() {
    p.background(255);

    // Variables
    let centerX = p.width / 2;
    let centerY = p.height / 2;
    let outerRadius = 100;
    let numCircles = 4;

    // Central circle
    p.circle(centerX, centerY, outerRadius * 2);

    //     window.drawRingCircle = function(outerRadius, numCircles, centerX, centerY, color=200) {

    // Iterate and draw circles around center that all intersect with one another, but with a function
    drawRingCircle(p, outerRadius, numCircles, centerX, centerY);

  }
  {{< /p5sketch >}}


Ok I was able to do that, now can I draw a second circle? To do that then we need to pass in a different
outerRadius, but now that will depend on the number of circles we want to draw. centerX and centerY will not change.
The new outer Radius is going to be the old outer Radius plus the radius of one of the circles in the outer ring.


  {{< p5sketch >}}
  p.setup = function() {
    p.createCanvas(1200, 1200);
    p.noLoop();
  }

  p.draw = function() {
    p.background(255);

    // Variables
    let centerX = p.width / 2;
    let centerY = p.height / 2;
    let outerRadius = 100;
    let numCircles = 4;

    // Central circle
    p.circle(centerX, centerY, outerRadius * 2);

    // Iterate and draw circles around center that all intersect with one another, but with a function
    drawRingCircle(p, outerRadius, numCircles, centerX, centerY);

    // Now for a second

  }
  {{< /p5sketch >}}