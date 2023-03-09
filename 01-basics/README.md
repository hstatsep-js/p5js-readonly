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