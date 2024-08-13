# Task-1 

## Summary

We have learned a lot basic information about the p5.js, what about let's have a pratical task to make a solid understanding of it!

## Prompt: 

- Draw a round face in a 500x500 canvas.
- The face should include eyes, a nose, and a mouth.
- The eyes should look in the direction of the mouse.
- When we <b>click</b> the face, the eyes should toggle between open and closed. 
- If we press the <b>space key</b>, the mouth should open or close.

Before you see the solution, Let's do it on the [online editor](https://editor.p5js.org/) ourselves!


## Showcase:

<iframe src="https://editor.p5js.org/JimmyXwtx/full/O8Ri_sZQK" width="500px" height="550px"></iframe>

## Let's Get Started:

- Create Canvas: 
    - We can use the `createCanvas()` function inside the `setup()` function to create a 500x500 canvas

            function setup() {
                createCanvas(500, 500); 
            }

            function draw(){
                // nothing here yet
            }

- Draw the Face
    - We can use the `ellipse()` function to draw a round face. Let's set the fill color to yellow. scss

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220); // Light gray background
                fill(255, 204, 0); // Yellow fill
                ellipse(250, 250, 400, 400); // Draw the face
            }


- Draw the Eyes
    - We can add two eyes using the `ellipse()` function. Position them relative to the face center.

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220);
                fill(255, 204, 0);
                ellipse(250, 250, 400, 400); // Draw the face
                
                fill(255); // White fill for the eyes
                ellipse(180, 200, 50, 50); // Left eye
                ellipse(320, 200, 50, 50); // Right eye
            }


- Draw the Nose and Mouth
    - Add a nose using the `triangle()` function and a mouth using the `arc()` function.

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220);
                fill(255, 204, 0);
                ellipse(250, 250, 400, 400); // Draw the face
                
                fill(255); // White fill for the eyes
                ellipse(180, 200, 50, 50); // Left eye
                ellipse(320, 200, 50, 50); // Right eye
                
                fill(255, 153, 51); // Orange fill for the nose
                triangle(250, 220, 230, 280, 270, 280); // Draw the nose
                
                fill(255, 51, 51); // Red fill for the mouth
                arc(250, 320, 100, 50, 0, PI); // Draw the mouth
            }

- Make the Eyes Look at the Mouse
    - Use `mouseX` and `mouseY` to make the eyes look in the direction of the mouse.

            //put the variable outside function is a global variable
            let eyeSize = 50;
            let eyeOffsetX = 70;
            let eyeOffsetY = 50;
            //put the variable outside function is a global variable

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220);
                fill(255, 204, 0);
                ellipse(250, 250, 400, 400); // Draw the face
                
                fill(255); // White fill for the eyes
                ellipse(250 - eyeOffsetX, 200, eyeSize, eyeSize); // Left eye
                ellipse(250 + eyeOffsetX, 200, eyeSize, eyeSize); // Right eye
                
                fill(255, 153, 51); // Orange fill for the nose
                triangle(250, 220, 230, 280, 270, 280); // Draw the nose
                
                fill(255, 51, 51); // Red fill for the mouth
                arc(250, 320, 100, 50, 0, PI); // Draw the mouth

                // Draw pupils based on mouse position
                fill(0); // Black fill for the pupils
                let pupilOffsetX = (mouseX - 250) / 20;
                let pupilOffsetY = (mouseY - 200) / 20;
                ellipse(250 - eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Left pupil
                ellipse(250 + eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Right pupil
            }


- Toggle Eyes Open/Closed on Click
    - Use the <b>mousePressed()</b> function to toggle the eyes between open and closed.

        
            let eyeSize = 50;
            let eyeOffsetX = 70;
            let eyeOffsetY = 50;

            // add a global condition to detect if the eye is open or closed
            let isEyesClosed = false;

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220);
                fill(255, 204, 0);
                ellipse(250, 250, 400, 400); // Draw the face
                
                fill(255); // White fill for the eyes
                if (isEyesClosed) {
                    rect(250 - eyeOffsetX - eyeSize / 2, 200 - 5, eyeSize, 10); // Left closed eye
                    rect(250 + eyeOffsetX - eyeSize / 2, 200 - 5, eyeSize, 10); // Right closed eye
                } else {
                    ellipse(250 - eyeOffsetX, 200, eyeSize, eyeSize); // Left eye
                    ellipse(250 + eyeOffsetX, 200, eyeSize, eyeSize); // Right eye
                    fill(0); // Black fill for the pupils
                    let pupilOffsetX = (mouseX - 250) / 20;
                    let pupilOffsetY = (mouseY - 200) / 20;
                    ellipse(250 - eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Left pupil
                    ellipse(250 + eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Right pupil
                }
                
                fill(255, 153, 51); // Orange fill for the nose
                triangle(250, 220, 230, 280, 270, 280); // Draw the nose
                
                fill(255, 51, 51); // Red fill for the mouth
                arc(250, 320, 100, 50, 0, PI); // Draw the mouth
            }

            function mousePressed() {
                let d = dist(mouseX, mouseY, 250, 250);
                if (d < 200) {
                    isEyesClosed = !isEyesClosed; // Toggle eye state
                }
            }


- Toggle Mouth Open/Closed on Space Key
    - Use the <b>keyPressed()</b> function to toggle the mouth between open and closed when the space key is pressed.

            let eyeSize = 50;
            let eyeOffsetX = 70;
            let eyeOffsetY = 50;
            let isEyesClosed = false;

            // add a condition to determine whether the mouth is open or closed
            let isMouthOpen = false;

            function setup() {
                createCanvas(500, 500);
            }

            function draw() {
                background(220);
                fill(255, 204, 0);
                ellipse(250, 250, 400, 400); // Draw the face
                
                fill(255); // White fill for the eyes
                if (isEyesClosed) {
                    rect(250 - eyeOffsetX - eyeSize / 2, 200 - 5, eyeSize, 10); // Left closed eye
                    rect(250 + eyeOffsetX - eyeSize / 2, 200 - 5, eyeSize, 10); // Right closed eye
                } else {
                    ellipse(250 - eyeOffsetX, 200, eyeSize, eyeSize); // Left eye
                    ellipse(250 + eyeOffsetX, 200, eyeSize, eyeSize); // Right eye
                    fill(0); // Black fill for the pupils
                    let pupilOffsetX = (mouseX - 250) / 20;
                    let pupilOffsetY = (mouseY - 200) / 20;
                    ellipse(250 - eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Left pupil
                    ellipse(250 + eyeOffsetX + pupilOffsetX, 200 + pupilOffsetY, eyeSize / 2, eyeSize / 2); // Right pupil
                }
                
                fill(255, 153, 51); // Orange fill for the nose
                triangle(250, 220, 230, 280, 270, 280); // Draw the nose
                
                fill(255, 51, 51); // Red fill for the mouth
                if (isMouthOpen) {
                    arc(250, 320, 100, 50, 0, PI); // Open mouth
                } else {
                    rect(200, 320, 100, 10); // Closed mouth
                }
            }

            function mousePressed() {
                let d = dist(mouseX, mouseY, 250, 250);
                if (d < 200) {
                    isEyesClosed = !isEyesClosed; // Toggle eye state
                }
            }

            function keyPressed() {
                if (key === ' ') {
                    isMouthOpen = !isMouthOpen; // Toggle mouth state
                }
            }
