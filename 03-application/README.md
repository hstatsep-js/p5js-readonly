# 03-application

## Conditionals

You can use conditionals in P5js just like you normally would in JS:

```js
if(condition) {
    // code to run
} else if(condition) {
    // code to run
} else {
    // code to run
}
```

As always, you _must_ have an `if`, as many `else if`s as you want, and at most _one_ `else`.

## Functions

Remember that there are special functions in P5js:

| name | defined | called |
| --- | --- | --- |
| `setup()` | by programmer | by P5js |
| `draw()` | by programmer | by P5js |
| `mousePressed()` | by programmer | by P5js |
| `keyPressed()` | by programmer | by P5js |
| `rect()` | by P5js | by programmer |
| `ellipse()` | by P5js | by programmer |
| `random()` | by P5js | by programmer |
etc.

But the programmer can also both **define** and **call** their own functions.

Take a look at the following example:
```js
function setup() {
    createCanvas(800,600);
    textAlign(CENTER);
    noStroke();
    
    // WITHOUT A FUNCTION
    fill(255,0,0); // candy color: red
    ellipse(75,200,100,100); // medium-sized
    fill(0); // prep text to be black
    textSize(25); // text size 1/4 of diameter
    text("m", 75,200); // draw the M
    
    // CALLING A FUNCTION (defined below)
    mnm(200,200,50,255,255,0); // yellow, small
    mnm(350,200,150,0,255,0); // green, large
    
}

// DEFINING THE FUNCTION
// (teaching the computer how to draw an M&M)
function mnm(x,y,size,r,g,b){
    fill(r,g,b); // candy color
    ellipse(x,y,size,size);
    fill(0); // prep text to be black
    textSize(size/4); // text size 1/4 of diameter
    text("m",x,y); // draw the M
}

function draw() {
    
}
```
