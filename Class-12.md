# Class-12

Charts are used to display data and it looks better than table, JavaScript and HTML5 provide such a tool to produce a good looking and colorful charts.

[Chart.js](https://www.chartjs.org/) a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page.

![chartjs](https://marketplace-cdn.atlassian.com/files/images/39451ee7-deb8-4adb-99c1-cd4479d4e8c5.png)



[Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) element `<canvas>` in HTML is looks like the `<img>` element except it does not use src and alt attributes; however it use width and height attributes.

![canvas](https://www.wikitechy.com/step-by-step-html-tutorials/html5-canvas/img/canvas-images/code-explanation-linewidth-property-in-html5-canvas.png)


By using the `<canvas>` element we could draw different shapes like;

1. `Rectangle` and there are three functions that draw rectangles on the canvas:
* `fillRect(x, y, width, height)`
* `strokeRect(x, y, width, height)`
* `clearRect(x, y, width, height)`

2. `Arcs or circle` in order to draw arcs or circles, we use the `arc()` or `arcTo()` methods.

3. `Triangle` by using `moveTo(x, y)` method.


#### Drawing paths:
Path is a list of points that are connected by lines and as a resultyou could have a different shapes.
These are the functions that are used to draw a path:

1. `beginPath()` Creates a new path. Once created, future drawing commands are directed into the path and used to build the path up.

2. `Path methods` Methods to set different paths for objects.

3. `closePath()` Adds a straight line to the path, going to the start of the current sub-path.

4. `stroke()` Draws the shape by stroking its outline.

5. `fill()` Draws a solid shape by filling the path's content area.

In order to  apply colors you can use two properties `fillStyle` and `strokeStyle`.

In addition canvas rendering context provides two methods to render a text:

1. `fillText(text, x, y [, maxWidth])`
Fills a given text at the given (x,y) position. Optionally with a maximum width to draw.

2. `strokeText(text, x, y [, maxWidth])`
Strokes a given text at the given (x,y) position. Optionally with a maximum width to draw.




