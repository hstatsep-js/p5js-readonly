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

### Example: Bouncing Ball

#### Step 0: Make it move

```js
var x;
var xSpeed;

function setup() {
    createCanvas(800, 600);
    x = width/2; // position
    xSpeed = 5; // speed
}

function draw() {
    background(220);

    ellipse(x,height/2,50);
    x += xSpeed;
    console.log(x)    
}
```

#### Step 1: Make it reset

```js
if(x >= width-25){ // past the right edge
    x = 0; // reset
}
```

#### Step 2: Make it bounce off right edge

```js
if(x >= width-25){ // past the right edge
    xSpeed = -5; // bounce
}
```

#### Step 3: Make it bounce off left edge

```js
if(x <= 25){ // past the left edge
    xSpeed = 5; // bounce
}
```

#### Step 4: Refactor to make it bounce off either edge

```js
if(x >= width-25 || x <= 25){ // if past either edge
    xSpeed *= -1 // reverse direction
}
```
