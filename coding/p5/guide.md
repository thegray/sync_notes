---

Tags : 
Back Links :
Date : {{13-04-2022}} 17:19

---

# p5 Guide

## Online Editor
https://editor.p5js.org/


## Base
```javascript
// initialisation function
// executed at start
function setup() {
	//...
}

// executed each frame
function draw() {
	//...
}
```


```javascript
/* simple example */

function setup() {
	// create render area called canvas with width and height as param
	createCanvas(400, 400);
	
	// set canvas' background color
	background(220);
	
	// draw an ellipse with its center 
	// 50 pixels over from the left (x axis) and 
	// 50 pixels down from the top  (y axis),
	// with a width and height of 80 pixels
	ellipse(50,50,80,80);
}

function draw() {
	//...
}
```

```javascript
/* draw and mouse press input example */

function setup() {
  createCanvas(400, 400);
  background(220);
}

function draw() {
	// detect if there's a mouse pressed event
	if (mouseIsPressed) {
		// set fill color
		fill(255);
		// draw ellipse on current mouse cursor's position
		ellipse(mouseX, mouseY, 80, 80);
	}
}
```

