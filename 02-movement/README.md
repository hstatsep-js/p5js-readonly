# 02-movement

## Variables

### User Variables

You can use JS variables just like you normally do! The one thing to keep in mind is the **scope** of the variable.
* **Local**: declared _inside_ a function definition, only viewable to _that_ function.
* **Global**: declared _outside_ of functions, viewable _everywhere_.

Here is a working example:

```js
var circleX; // variable declared globally
// circleX = 0; // could also be initialized here.

function setup() {
    createCanvas(800,600);
    circleX = 0; // initializes variable
}

function draw() {
    background(200); // don't want to see the trail of circles
  
    circleX++; // move to the right
    ellipse(circleX,100,50,50); // circleX is able to vary (vari-able!)

    console.log("circleX: " + circleX);
}
```

Understanding scope prevents errors such as these:

```js
function setup() {
    createCanvas(800,600);
    var circleX = 0; // declared locally, only viewable to setup()
}

function draw() {
    background(200);
  
    circleX++; // ReferenceError: circleX is not defined
    ellipse(circleX,100,50,50);
}
```

For now, we get around this problem by using global variables. But just know that you can run into problems with having _all_ of your variables be global. It can get very technical, but if you're interested, [here](http://wiki.c2.com/?GlobalVariablesAreBad) is a list of reasons.

[Variables video](https://www.youtube.com/watch?v=dRhXIIFp-ys)


### System Variables

You can generally name your own variables whatever you want, with a few exceptions: **system variables**. Two commonly-used system variables that are _already defined_ in P5js are:

* `width`
* `height`

These essentially _automatically_ save whichever numbers you write in `createCanvas(#,#)`. This can be useful for all kinds of things, for example, centering something on your canvas.

```js
function setup() {
    createCanvas(800,600);
}

function draw() {
    ellipse(width/2, height/2, 50, 50); // center of the canvas
}
```

This is essentially calculating the position based on the dimensions of the canvas:
* `x`: `width/2` = `800`/`2` = `400`
* `y`: `height/2` = `600`/`2` = `300`

So why not just type in `ellipse(400, 300, 50, 50);`? The magic happens when you change the size of the canvas. Go ahead, try it!
