# module-3 Interaction

## Summary

- Conditionals
- Loops
- Applications with Mouse and Keyboard Events

## Conditionals
- Basic Conditionals
    - <b>if()</b>: Executes a block of code if the specified condition is true.

            function setup() {
                createCanvas(400, 200);
                let x = 50;
                if (x < 100) {
                    fill(0, 255, 0); // Green fill
                } else {
                    fill(255, 0, 0); // Red fill
                }
                rect(50, 50, 100, 100); // Draw a rectangle
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/uHemka35l" width="400px" height="250px"></iframe>

    - <b>if...else if...else</b>: Executes different blocks of code based on multiple conditions.

            function setup() {
                createCanvas(400, 200);
                let y = 150;
                if (y < 100) {
                    fill(0, 255, 0); // Green fill
                } else if (y < 200) {
                    fill(255, 255, 0); // Yellow fill
                } else {
                    fill(255, 0, 0); // Red fill
                }
                rect(50, 50, 100, 100); // Draw a rectangle
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/iBIpP9-U_" width="400px" height="250px"></iframe>

## Loops
- Basic Loops
    - <b>for()</b>: Repeats a block of code a specified number of times.

            function setup() {
                createCanvas(400, 200);
                for (let i = 0; i < 10; i++) {
                    fill(0, 0, 255); // Blue fill
                    rect(i * 40, 50, 30, 30); // Draw a rectangle
                }
            }

    <iframe src="https://editor.p5js.org/JimmyXwtx/full/kARk1zkVu" width="400px" height="250px"></iframe>

    - <b>while()</b>: Repeats a block of code while a specified condition is true.

            function setup() {
                createCanvas(400, 200);
                let x = 0;
                while (x < 400) {
                    fill(255, 0, 255); // Magenta fill
                    ellipse(x, 100, 30, 30); // Draw a circle
                    x += 40;
                }
            }

    <iframe src="https://editor.p5js.org/JimmyXwtx/full/v0RFaVu0_" width="400px" height="250px"></iframe>

## Applications with Mouse and Keyboard Events
- Basic Mouse and Keyboard Functions
    - <b>mousePressed()</b>: Executes a block of code when the mouse is pressed.

            function setup() {
                createCanvas(400, 200);
            }

            function draw() {
                if (mouseIsPressed) {
                    fill(0, 255, 0); // Green fill when mouse is pressed
                } else {
                    fill(255, 0, 0); // Red fill when mouse is not pressed
                }
                rect(50, 50, 100, 100); // Draw a rectangle
            }

    You can try it! Click the red square!

    <iframe src="https://editor.p5js.org/JimmyXwtx/full/AhmpfgCE4" width="400px" height="250px"></iframe>

    - <b>mouseDragged()</b>: Executes a block of code when the mouse is dragged.
    
            function setup() {
            createCanvas(400, 200);
            background(255);
            }

            function mouseDragged() {
            fill(0, 0, 255); // Blue fill
            ellipse(mouseX, mouseY, 20, 20); // Draw a circle at the mouse position
            }
    
    You can try it! Click on the canvas to see what's happening! 

    <iframe src="https://editor.p5js.org/JimmyXwtx/full/b5etr7Nk2" width="400px" height="250px"></iframe>

    - <b>keyPressed()</b>: Executes a block of code when a key is pressed.

            function setup() {
                createCanvas(400, 200);
            }

            function draw() {
                background(255);
                if (keyIsPressed) {
                    if (key === 'r' || key === 'R') {
                        fill(255, 0, 0); // Red fill when 'r' is pressed
                    } else if (key === 'g' || key === 'G') {
                        fill(0, 255, 0); // Green fill when 'g' is pressed
                    } else if (key === 'b' || key === 'B') {
                        fill(0, 0, 255); // Blue fill when 'b' is pressed
                    } else {
                        fill(0); // Black fill for any other key
                    }
                    rect(50, 50, 100, 100); // Draw a rectangle
                }
            }

    <iframe src="https://editor.p5js.org/JimmyXwtx/full/f3jGdeeNZ" width="400px" height="250px"></iframe>