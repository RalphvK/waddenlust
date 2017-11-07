# Waddenlust

[Checkout the demo.](http://dev.ralphvankruiselbergen.nl/waddenlust)

This educational project served as a demonstration of the interesting new opportunities the then new SVG support provided for simple and efficient dynamic content. In this case, I used this technology to create a moving, zoomable map as part of a proposed publicity campaign for the Dutch *Waddenvereniging* who sought to raise awareness of the unique qualities of the Wadden Sea area among young adults.

## Controls

Map movement can be controlled in the following ways:

* Scroll wheel

* Swipe up/down

* Arrow keys

------

## Important Functions

```javascript
map_resize()
```

Scales map to appropriate size for screen format.

```javascript
map_zoom( waypointID, zoom )
```

Moves map and adjusts zoom-level. The first parameter sets the new waypoint id (string) the second parameter sets the zoom factor, relative to the initial zoom level (decimal).

```javascript
map_attach( elementID, targetID, offsetx, offsety, corrx, corry )
```

Attaches an element to a map element. The first and second parameter define the selectors of the element and the target to attach it to, respectively. The ```offsetx``` and ```offsety``` arguments provide a relative way of offsetting the attached objects that is scaled proportionately with map-scale, while the correction arguments ```corrx``` and ```corry``` offset the position in absolute pixels, applied at the very end of the positioning process.

```javascript
map_waypoint( action )
```

Shifts to either the next/previous waypoint, or to a given waypointID. When the ```action``` argument equals ```'next'``` or ```'previous'```, the function will automatically switch to the next/previous waypoint. If any other string is given, it will be used as the selector. For example: ```"#waypoint8"``` moves to waypoint 8.

Zoom-levels can also be coded into the map_waypoint function.

------

## Adding additional waypoints

After modifying the SVG graphic, some code must be updated to add new waypoints.

1. Ensure each waypoint object has a defined ```id``` attribute
```html
<circle id="waypoint8" class="st0" cx="54.5" cy="979.8" r="9.7"/>
```

2. Update total number of waypoints ```line 302```
```javascript
var numberOfWaypoints = 8 // total number of waypoints
```

3. Bind the labels ```line 296```
```javascript
// attaching labels
map_attach('#label8','#waypoint8',16,0,0,0);
```

4. Preset a zoom level (optional) ```line 345```
```javascript
 else if (current_waypoint == '#waypoint8') {
    current_zoom = 1.5;
}
```

5. Add a corresponding information panel
```html
<div id="info8" class="infopanel right">
    <h2>Waypoint Title<span class="arrow">&#10093;</span></h2>
    <div>
        <p>Content, information, stories, videos and images go here.</p>
    </div>
</div>