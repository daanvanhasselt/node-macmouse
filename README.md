# macmouse

A node.js module that enables you to create virtual mouse input on Mac OS X.

## Credits
Uses [NodObjC](https://github.com/TooTallNate/NodObjC) to hook into the Cocoa framework. The macmouse module is merely a wrapper around mouse control commands to the Cocoa framework via NodObjC.

## Installation

Install using `npm`,

``` bash
$ npm install macmouse
```

## Usage Example
``` javascript
var mouse = require('macmouse');

mouse.init();

var ptX = 800;
var ptY = 600;

var doThings = function() {
    mouse.Place(ptX, ptY);
    setTimeout(pressAndHold, 250);
}

var pressAndHold = function() {
    mouse.LeftButtonPress();
    setTimeout(doDragStuff, 250);
}

var doDragStuff = function() {
    ptX += 2;
    ptY += 2;
    mouse.DragPlace(ptX, ptY);
    setTimeout(doDragStuff, 250);
}


doThings();

mouse.quit();

```

## List of functions

And a small description for each function.

```
// Desc:   Imports the macmouse module as mouse
// Before: nothing
// After:  mouse is an uninitialized macmouse
var mouse = require('macmouse');
```

### init

```
// Desc:   Initializes the macmouse module
// Before: mouse is an uninitialized macmouse
// After:  mouse is an initialized macmouse
mouse.init();
```

### getRealPos

```
// Desc:   Sends request for real mouse position, more expensive than getPos
// Before: mouse is an initialized macmouse
// After:  pos holds x and y numbers representing the system mouse position
var pos = mouse.getRealPos();
var x = pos.x;
var y = pos.y;
```

### getPos

```
// Desc:   Returns mouse position currently stored in the mouse module
// Before: mouse is an initialized macmouse
// After:  pos holds x and y numbers representing the system mouse position currently stored in the
//         mouse module
var pos = mouse.getPos();
var x = pos.x;
var y = pos.y;
```

### Place

```
// Desc:   Sends mouse event message to place the system mouse at a specific position
// Before: mouse is an initialized macmouse, x and y are numbers representing a specific position
// After:  mouse event has been sent to move the system mouse to position defined by x and y
mouse.Place(x, y);
```

### DragPlace

```
// Desc:   Sends mouse event message to place the system mouse at a specific position while in a 
//         dragging state
// Before: mouse is an initialized macmouse, x and y are numbers representing a specific position, the 
//         system mouse currently has (or thinks it has) the left mouse button pressed
// After:  mouse event has been sent to move the system mouse to position defined by x and y with left 
//         mouse button pressed
mouse.DragPlace(x, y);
```

### Move

```
// Desc:   Sends mouse event message to move the system mouse (from current stored position in the mouse 
//         module) by a vector defined by dx and dy
// Before: mouse is an initialized macmouse, dx and dy are numbers representing our moving vector 
// After:  mouse event has been sent to move the system mouse by a vector defined by the numbers dx and dy
mouse.Move(dx, dy);
```

### DragMove

```
// Desc:   Sends mouse event message to move the system mouse (from current stored position in the mouse 
//         module) by a vector defined by dx and dy while in a dragging state
// Before: mouse is an initialized macmouse, dx and dy are numbers representing our moving vector, the 
//         system mouse currently has (or thinks it has) the left mouse button pressed
// After:  mouse event has been sent to move the system mouse by a vector defined by the numbers dx and dy 
//         with left mouse button pressed
mouse.Move(dx, dy);
```

### LeftButtonPress

```
// Desc:   Sends mouse event message to press and hold down the left button of the system mouse
// Before: mouse is an initialized macmouse
// After:  mouse event has been sent to press and hold the left button on the system mouse
mouse.LeftButtonPress();
```

### LeftButtonRelease

```
// Desc:   Sends mouse event message to release a pressed left button of the system mouse
// Before: mouse is an initialized macmouse
// After:  mouse event has been sent to release a pressed left button on the system mouse
mouse.LeftButtonRelease();
```

### RightButtonPress

```
// Desc:   Sends mouse event message to press and hold down the right button of the system mouse
// Before: mouse is an initialized macmouse
// After:  mouse event has been sent to press and hold the right button on the system mouse
mouse.LeftButtonPress();
```

### RightButtonRelease

```
// Desc:   Sends mouse event message to release a pressed right button of the system mouse
// Before: mouse is an initialized macmouse
// After:  mouse event has been sent to release a pressed right button on the system mouse
mouse.LeftButtonRelease();
```

### quit

```
// Desc:   Does garbage collection some on objective c stuff, be a good lad and call this when 
//         you're done using the macmouse module
// Before: mouse is an initialized macmouse
// After:  mouse is an uninitialized macmouse
mouse.quit();
```

## License
(MIT License)
