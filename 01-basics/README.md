# 01-basics

## Intro
```js
// runs once in the beginning
function setup() {
    createCanvas(800, 600); // width, height
}

// runs continually
// Default: 60 frames (times) per second
// Basically an infinite loop (that doesn't crash your browser)
function draw() {

}
```

## Shapes

### Points and Lines

```js
point(x,y); // default: only 1 pixel thick; very difficult to see!

line(x1,y1,x2,y2); // from (x1,y1) to (x2,y2)
```

### Rectangles and Ellipses

| Mode | Syntax | Default |
| --- | --- | --- |
| `rectMode(CORNER)` | `rect(x,y,width,height)` | yes |
| `rectMode(CENTER)` | `rect(x,y,width,height)` |  |
| `rectMode(CORNERS)` | `rect(x1,y1,x2,y2)` |  |
| `ellipseMode(CORNER)` | `ellipse(x,y,width,height)` |  |
| `ellipseMode(CENTER)` | `ellipse(x,y,width,height)` | yes |
| `ellipseMode(CORNERS)` | `ellipse(x1,y1,x2,y2)` |  |

Note: you can also use `ellipse(x,y,diameter)` to draw a perfect circle.

## Text, Layers, Comments, Thickness

### Text

```js
textSize(32); // (any number)             
text("word", x, y);
```
Note: `x` and `y` are the BOTTOM-LEFT corner of the text
You can change this by putting 
```js
textAlign(CENTER); // (or LEFT or RIGHT)
```
before your text.

If you want to wrap text in a box, use:
```js
text(str,x,y,w,h)
```
where:
* `str` is your string
* (`x`,`y`) represents the top-left corner of the box
* `w` and `h` represent the size of your box, respectively

Bonus: you can import a Google Font like you normally would into an HTML file, then use `textFont('Your font here')` to set the p5js font.

### Layers

The order of your code matters. If your code is:
```js
ellipse(100,100,200,200);
line(0,0,200,200);
rect(0,0,200,200);
```
You actually won't see the `ellipse` or the `line` because the `rect` is drawn **after** and thus is on "top" of those shapes.

### Comments

* A comment above a chunk of code describes that chunk of code
* A comment next to a line of a code describes that line of code
* Use `//` to comment out a single line of code.
* Use `/* code */` to comment out multiple lines of code

```js
function draw() {
    // body
    rect(80,100,40,70);

    // feet
    line(90,170,70,200); // left
    line(110,170,130,200); // right

    /*
    // head
    ellipse(100,75,60,50); 

    // eyes
    ellipse(85,75,10,30); // left
    ellipse(115,75,10,30); // left

    // nose 
    point(100, 80);
    */
}
```

### Thickness

```js
strokeWeight(10); // Sets the thickness of your shape to however many pixels you want
```

### Debugging

```js
console.log(mouseX,mouseY); // Helpful for locating a shape
```

## Color

### Color Theory

* Grayscale
  * `0` is black (no "light")
  * `1-244` is gray (dark to light)
  * `255` is white (all "light")
* Color
  * RGB = red/green/blue (think "Roy-G-Biv")
  * Each color also goes 0-255
  * `0` means NONE of that color
  * `255` means MAX of that color
  * Ex: `(255,0,0)` is all red, no green, no blue
* Mixing
  * `(0,0,0)` is black
  * `(num,num,num)` is grayscale (if they're all the same)
  * `(255,255,255)` is white
  * Red + Green = Yellow
  * Red + Blue = Purple
  * Green + Blue = Cyan (blue-green)
  * _^you don't need to memorize these^_
* Alpha (opacity)
  * How solid the color is
  * `0`: empty
  * `1-254`: translucent (see-through)
  * `255`: solid
* Functions
  * `fill(r,g,b,[a])`
    * Example: `fill(255,0,0)` = red fill (inside)
  * `stroke(r,g,b,[a])`
    * Example: `fill(0,255,0,)` = red fill (inside)
  * `noFill()`: same as setting opacity to 0
  * `noStroke()`: same as setting `strokeWeight(0)`
  * `background(r,g,b,[a])`: set the background to a color