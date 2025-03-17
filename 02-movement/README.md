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

### Constrain

There are times when you want to restrict the value of a variable to stay between a set of **minimum** and **maximum** values. For that, we have:

`constrain(val,min,max)`

Here's what gets returned:
* If `val` is within `[min,max]`, `val` gets returned
* If `val` is greater than `max`, `max` gets returned
* If `val` is less than `min`, `min` gets returned

The most common usage of this is to then _save_ (overwrite) that return value, i.e:

`val = constrain(val,min,max)`

For example, suppose you wanted to prevent your ellipse from leaving the canvas (i.e. "constrain" it). The code would look like this:

```js
var circleX; 

function setup() {
    createCanvas(800,600);
    circleX = 0; 
}

function draw() {
    background(200); 
  
    circleX++; // move to the right
    circleX = constrain(circleX,0,width); // prevent circle from leaving the canvas
    ellipse(circleX,100,50,50);

    console.log("circleX: " + circleX);
}
```

Behind the scenes, as soon as the value of `circleX` reaches 801, `constrain(circleX,0,width)` returns `800` (the width of our canvas), which then gets saved back into `circleX`.

[Here](https://p5js.org/reference/#/p5/constrain) is another example.

### Fun with variables

Variable can hold all kinds of data (numbers, strings, booleans, etc). But for now, the fun part of storing **numbers** is that numbers are used _all over_ the place in P5js. Here are some reminders of where you see numbers:
* `point(#,#)`
* `line(#,#,#,#)`
* `rect(#,#,#,#)`
* `ellipse(#,#,#,#)`
* `background(#,#,#,[#])`
* `fill(#,#,#,[#])`
* `stroke(#,#,#,[#])`
* `strokeWeight(#)`
* `textSize(#)`
* `text("Hello World",#,#)`
