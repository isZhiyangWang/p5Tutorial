# Module 4 - Functions
## Summary
- Modularize Your Code

## Modularize Your Code

- Basic Functions
    - <b>Creating Functions</b>: Define reusable blocks of code

            function setup() {
                createCanvas(400, 200);
                drawRectangle(50, 50, 100, 100, color(0, 255, 0)); // Green rectangle
                drawRectangle(200, 50, 100, 100, color(255, 0, 0)); // Red rectangle
            }

            function drawRectangle(x, y, w, h, col) {
                fill(col);
                rect(x, y, w, h);
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/QGb8_39na" width="400px" height="250px"></iframe>
    
    - <b>Function Parameters</b>: Pass values to functions for flexible behavior

            function setup() {
                createCanvas(400, 200);
                drawEllipseAndRect(100, 100, 50, 50); // Draw an ellipse at (100, 100)
                drawEllipseAndRect(300, 100, 75, 75); // Draw a larger ellipse at (300, 100)
            }

            function drawEllipseAndRect(x, y, w, h) {
                ellipse(x, y, w, h);
                rect(x,y,w,h)
            }
        
        <iframe src="https://editor.p5js.org/JimmyXwtx/full/ioC8FE0SP" width="400px" height="250px"></iframe>

