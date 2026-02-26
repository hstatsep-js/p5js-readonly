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

## Loops

Remember that there are three kinds of loops we've learned: `while`, `for`, and `forEach`.

```js
// while
var i = 0;
while(i < 3) {
    console.log(i);
    i++;
}

// for
for(var i = 0; i < 3; i++) {
    console.log(i);
}

// forEach
var foods = ["apples", "bananas", "carrots"];
foods.forEach(function(food){ // remember you could write `function(food, i)` to have access to `i`
    console.log(food);
});

```

The most common usage is a `for` loop. Here is an example that draws `10` vertical lines in a `100`x`100` canvas:
```js
function setup() {
    createCanvas(100, 100);
}

function draw() {
    background(255);
  
    for(var x = 0; x < 100; x += 10) {
        line(x, 0, x, 100); // vertical lines, drawn LEFT to RIGHT
    }
}
```

If we add in another loop, we can draw the horizontal lines as well.
```js
for(var x = 0; x < 100; x += 10) {
    line(x, 0, x, 100); // vertical lines, drawn LEFT to RIGHT
}
for(var y = 0; y < 100; y += 10) {
    line(0, y, 100, y); // horizontal lines, drawn TOP to BOTTOM
}
```

Hopefully you noticed that the headers are exactly the same for both loops, so we could combine them into one loop. But we should probably change our variable name.
```js
for(var i = 0; i < 100; i += 10) {
    line(i, 0, i, 100); // vertical lines, drawn LEFT to RIGHT
    line(0, i, 100, i); // horizontal lines, drawn TOP to BOTTOM
}
```

As a fun extension, try to create the SAME result using `rect()` instead of `line()`. Hint, use a `for` loop _inside_ a `for` loop.

## Arrays

As a reminder, here are some common array methods:
| method | purpose |
| --- | --- |
| `.push()` | add to the end |
| `.pop()` | remove from the end |
| `.shift()` | remove from the beginning |
| `.unshift()` | add to the beginning |

You can access an element by doing `arrName[i]` where `i` is the index number. This is useful for reading or (over)writing.

```js
var people = ["Alice", "Bob"];
console.log(people[0]); // "Alice"
people.push("Carter");
console.log(people); // ["Alice", "Bob", "Carter"]
people[1] = "Brenda";
console.log(people); // ["Alice", "Brenda", "Carter"]
```

Remember that there are two commons ways to loop through an array: `for` and `forEach`. Also, keep in mind that the `i` is optional in the `forEach`.

```js

var foods = ["apples", "bananas", "carrots"];

// for
for(var i = 0; i < foods.length; i++) {
    console.log(foods[i]); // `foods[i]` is the current food
}

// forEach
foods.forEach(function(food,i){ 
    // not using `i`, but could if we needed to
    console.log(food); // `food` is the current food
});
```

In P5js, arrays can be used for all kinds of things. Here is a quick example:

```js
var shades;
var i;

function setup() {
    createCanvas(400, 400);
    shades = [0, 127, 255];
    i = 0;
}

function draw() {
    background(220);
    fill(shades[i]);
    ellipse(width/2,height/2,100)
}

function mousePressed() {
    i++;
}
```

How could we make the pattern repeat, so that it goes black, gray, white, black, gray, white, ...

There are multiple ways! Here are two hints:
* `if()` to reset
* use mod (`%`)

## Objects

Objects are a way of wrapping data together, i.e. variables. We can use JSON (JavaScript Object Notation) syntax.

For example, instead of having two separate variables:

```js
var ballX = 400;
var ballY = 300;
```

... we can wrap those two variables together inside an object:

```js
var ball = {
    x: 400,
    y: 300
}
```

We call `x` and `y` "properties", whereas `400` and `300` are their respective "values". Notice the `:` that separates properties/values, and the `,` that separates each pair (you can have has many pairs as you want!).

We can then read/write the values of those properties using _dot notation_:

```js
console.log(ball.x); // 400 (read)
ball.x = 401; // (over)write
```

You can use this idea in P5js just like you would with any variable:

```js
var ball;

function setup() {
    createCanvas(800, 600);
    ball = {
        x: 400,
        y: 300
    }
}

function draw() {
    background(220);
    ellipse(ball.x, ball.y, 50, 50);
}
```

For more information about objects, here are some resources:
* [w3schools](https://www.w3schools.com/js/js_objects.asp)
* [freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/#basic-javascript), starting at [Build JavaScript Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/build-javascript-objects)
* [dot notation vs bracket notation](https://medium.com/@prufrock123/js-dot-notation-vs-bracket-notation-797c4e34f01d)

## Classes

We've seen how objects can wrap variables together. You can even include functions! The best way to do this is to shift to object-oriented programming, where you define a **class** which acts as a blueprint (or a template) for creating multiple instances of that class (i.e. objects). 

That probably sounds like a bunch of vocab jargon, but it'll make more sense as we go, and we'll recap at the end.

Here is the generic code:

```js
class MyClassName {

    
    // how to make a NEW instance of this class
    constructor() {
        // variables are often setup here
        // each instance of the class gets their own copy of the variable
    }

    // functions
    // each instance can also perform these functions

}
```

Notice the convention for classes: they start with a capital letter. This is important for distinguishing from other variables/functions!

Here is an example of the code in action:

```js
class Bubble {

    constructor(x,y) {
        this.x = x; // `this` refers to the instance you are currently working on
        this.y = y; // which helps us distinguish from parameters in the constructor
    }

    move() {
        this.x += random(-2, 2);
        this.y += random(-2, 2);
    }

    display() {
        ellipse(this.x, this.y, 50, 50);
    }

}
```

By itself, this code does nothing, much like defining a function. But just like you can call a function, you can create a new instance of a class.

```js

var bubble1;

function setup() {
    createCanvas(800, 600);
    bubble1 = new Bubble(width/2, height/2); // activate the constructor and pass in arguments
}

function draw() {
    background(220);

    bubble1.move(); // call that instance's functions
    bubble1.display(); // to make them run
}
```

Now, with a single line of code, we can create a new instance of the `Bubble` class. Then we call functions as we want them to run!

Here is a recap of some vocabulary:
* `Class`: the template/blueprint for making similar things.
* `Constructor`: a special function that runs once when `new` is used.
* `Instance`: usually followed by a classname, i.e. "a new instance of the Bubble class". Basically the template was used to create something.
* `Object`: the generic word for any instance of any class. In Javascript, is even more generic to include basic objects like property-value pairs.