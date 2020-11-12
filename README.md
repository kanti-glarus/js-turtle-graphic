# JavaScript Turtle Graphic

This is an attempt to recreate the famous Python Turtle Graphics  in JavaScript, using the canvas.  
For the moment the only available commands are `forward`, `backward` `right` and `left`.

## Include Turtle.js

You can include `turtle.js` directly from GitHub:

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/kanti-glarus/js-turtle-graphic@master/turtle.js"></script>
```

Or by a specific commit:
```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/kanti-glarus/js-turtle-graphic@0189037/turtle.js"></script>
```

## HTML-Setup
See our two examples:

- [Minimal Setup](./minimal.html)
- [Sierpinski Triangle](./index.html)


## Example
We can use this to draw a spiral recursively with this simple code:

```javascript
  function drawSpiral(turtle, lineLen) {
    if (lineLen > 0) {
      turtle.forward(lineLen);
      turtle.left(90);
      drawSpiral(turtle, lineLen-5);
    }
  }
  drawSpiral(turtle, 100);
  turtle.draw();
```

You can also draw a fractal tree with this sample:

```javascript
function tree(branchLen, turtle) {
  if (branchLen > 5) {
    turtle.forward(branchLen);
    turtle.right(20);
    tree(branchLen-15, turtle);
    turtle.left(40);
    tree(branchLen-15, turtle);
    turtle.right(20);
    turtle.backward(branchLen);
  }
}
tree(75, turtle);
turtle.draw();
```

You can even draw a Sierpinski Triangle:

```javascript
function drawTriangle(l, x, y, myTurtle) {
  // Not done yet?
  if (l > min) {
      // scale down by 2
      l = l/2;
      // bottom left triangle
      drawTriangle(l, x, y, myTurtle);
      // bottom right triangle
      drawTriangle(l, x+l, y, myTurtle);
      // top triangle
      drawTriangle(l, x+l/2, y-l*pf, myTurtle);
  }
  // Done recursing
  else {
      // start at (x,y)
      myTurtle.goto(x, y);
      myTurtle.down();
      // prepare to fill triangle
      myTurtle.beginFill();
      // triangle base
      myTurtle.forward(l);
      myTurtle.left(120);
      // triangle right
      myTurtle.forward(l);
      myTurtle.left(120);
      // triangle left
      myTurtle.forward(l);
      myTurtle.endFill();
      // face East
      myTurtle.setHeading(-90);
      // finish at (x,y)
      myTurtle.up();
      myTurtle.goto(x, y);
    }
}
```
