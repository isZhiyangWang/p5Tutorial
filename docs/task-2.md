# Task-1 

## Summary

After we Learn the Classes and Objects in the p5.js, what about let's have a pratical task to make a solid understanding of it!

## Prompt: 

Now that we have learned the basics of Object-Oriented Programming (OOP) in p5.js, let's put that knowledge into practice!
Task:

- Create a Face class:
    - Define properties such as position (x, y), size (size), and states (isEyesClosed, isMouthOpen).
    - Add a draw method to draw the face, eyes, nose, and mouth with the current states.
    - Add methods to toggle the eyes and mouth states (toggleEyes, toggleMouth).
    - Add a method to check if the mouse is inside the face (isMouseInside).

- Use the Face class:
    - Create a 500x500 canvas.
    - Create an array of Face instances arranged in a 3x3 grid.
    - Implement the draw function to draw all the faces.
    - Implement the mousePressed function to toggle the eyes of a face when clicked.
    - Implement the keyPressed function to toggle the mouths of all faces when the space key is pressed.

Before you see the solution, Let's do it on the [online editor](https://editor.p5js.org/) ourselves!


## Showcase:


<iframe src="https://editor.p5js.org/JimmyXwtx/full/xVd9ozS9y" width="500px" height="550px"></iframe>

## Let's Get Started:

- Creating a Class

    <em>A class is a blueprint for creating objects. It defines the properties and behaviors that the objects created from the class will have.</em>

    - We can use the `createCanvas()` function inside the `setup()` function to create a 500x500 canvas
        - class `Face { ... }`: This defines a new class named Face.
        - `constructor(x, y, size) { ... }`: The constructor is a special function that is called when a new object is created. It initializes the object's properties.

                class Face {
                    constructor(x, y, size) {
                        this.x = x;
                        this.y = y;
                        this.size = size;
                        this.eyeSize = size * 0.2;
                        this.eyeOffsetX = size * 0.35;
                        this.eyeOffsetY = size * 0.25;
                        this.isEyesClosed = false;
                        this.isMouthOpen = false;
                    }
                }

- Add a Method to Draw the Face
    - Drawing the Face

        <em>We define a method inside the class to handle drawing the face. Methods are functions defined inside a class that operate on objects created from the class.</em>

        - `draw() { ... }`: This defines a method named draw inside the Face class. It will be used to draw the face on the canvas.
        - `fill(255, 204, 0); and ellipse(this.x, this.y, this.size)`: These commands set the color and draw the face.

                class Face {
                    constructor(x, y, size) {
                        this.x = x;
                        this.y = y;
                        this.size = size;
                        this.eyeSize = size * 0.2;
                        this.eyeOffsetX = size * 0.35;
                        this.eyeOffsetY = size * 0.25;
                        this.isEyesClosed = false;
                        this.isMouthOpen = false;
                    }

                    draw(){
                        // Draw face
                        fill(255, 204, 0);
                        ellipse(this.x, this.y, this.size);
                    }
                }

- Add Methods to Draw the Eyes, Nose, and Mouth

    <em> We add the logic to draw the eyes, including their states (open or closed). </em>

    - Drawing the Eyes
        - `if (this.isEyesClosed) { ... } else { ... }`: This checks if the eyes are closed and draws them accordingly. The this keyword refers to the current object instance.

    - Drawing the Nose and Mouth

        - `if (this.isMouthOpen) {...}else{...}` used for control the mouse

                class Face {
                        constructor(x, y, size) {
                            this.x = x;
                            this.y = y;
                            this.size = size;
                            this.eyeSize = size * 0.2;
                            this.eyeOffsetX = size * 0.35;
                            this.eyeOffsetY = size * 0.25;
                            this.isEyesClosed = false;
                            this.isMouthOpen = false;
                        }

                        draw(){
                            // Draw face
                            fill(255, 204, 0);
                            ellipse(this.x, this.y, this.size);
                            // Draw eyes
                            fill(255); // White fill for the eyes
                            if (this.isEyesClosed) {
                            rect(this.x - this.eyeOffsetX - this.eyeSize / 2, this.y - this.eyeOffsetY - 5, this.eyeSize, 10); // Left closed eye
                            rect(this.x + this.eyeOffsetX - this.eyeSize / 2, this.y - this.eyeOffsetY - 5, this.eyeSize, 10); // Right closed eye
                            } else {
                            ellipse(this.x - this.eyeOffsetX, this.y - this.eyeOffsetY, this.eyeSize, this.eyeSize); // Left eye
                            ellipse(this.x + this.eyeOffsetX, this.y - this.eyeOffsetY, this.eyeSize, this.eyeSize); // Right eye
                            fill(0); // Black fill for the pupils
                            let pupilOffsetX = (mouseX - this.x) / 20;
                            let pupilOffsetY = (mouseY - this.y) / 20;
                            ellipse(this.x - this.eyeOffsetX + pupilOffsetX, this.y - this.eyeOffsetY + pupilOffsetY, this.eyeSize / 2, this.eyeSize / 2); // Left pupil
                            ellipse(this.x + this.eyeOffsetX + pupilOffsetX, this.y - this.eyeOffsetY + pupilOffsetY, this.eyeSize / 2, this.eyeSize / 2); // Right pupil
                            }
                            // Draw nose
                            fill(255, 153, 51); // Orange fill for the nose
                            triangle(this.x, this.y - this.size * 0.1, this.x - this.size * 0.05, this.y + this.size * 0.1, this.x + this.size * 0.05, this.y + this.size * 0.1);

                            // Draw mouth
                            fill(255, 51, 51); // Red fill for the mouth
                            if (this.isMouthOpen) {
                                arc(this.x, this.y + this.size * 0.2, this.size * 0.5, this.size * 0.25, 0, PI); // Open mouth
                            } else {
                                rect(this.x - this.size * 0.25, this.y + this.size * 0.2, this.size * 0.5, 10); // Closed mouth
                            }
                        }
                    }

- Add Methods to Toggle Eye and Mouth States
    - Toggling States
        - `toggleEyes()` and `toggleMouth()`: These methods change the state of the eyes and mouth between open and closed.
        - `isMouseInside()`: This method checks if the mouse is inside the face.

                class Face {
                        constructor(x, y, size) {
                            this.x = x;
                            this.y = y;
                            this.size = size;
                            this.eyeSize = size * 0.2;
                            this.eyeOffsetX = size * 0.35;
                            this.eyeOffsetY = size * 0.25;
                            this.isEyesClosed = false;
                            this.isMouthOpen = false;
                        }

                        draw(){
                        ....
                        //all draw() functions
                        }

                        toggleEyes() {
                            this.isEyesClosed = !this.isEyesClosed;
                        }

                        toggleMouth() {
                            this.isMouthOpen = !this.isMouthOpen;
                        }

                        isMouseInside() {
                            let d = dist(mouseX, mouseY, this.x, this.y);
                            return d < this.size / 2;
                        }

                    }



- Use the Face Class
    - Creating and Drawing Faces

        <em> We create an array of Face instances and draw them on the canvas. </em>

        - `let faces = [];`: This creates an empty array to store the face objects.
        - `for (let i = 0; i < 3; i++) { ... }`: This nested loop creates a 3x3 grid of face objects.
        Drawing Faces
        - We call the draw method of each Face instance in the draw function.

                let faces = [];

                function setup() {
                    createCanvas(500, 500);
                    let size = 100;
                    for (let i = 0; i < 3; i++) {
                        for (let j = 0; j < 3; j++) {
                            faces.push(new Face(150 * i + 100, 150 * j + 100, size));
                        }
                    }
                }

        - `for (let face of faces) { ... }`: This loop iterates through each face in the array and calls its draw method.
        Interacting with Faces
        - We add interactions to toggle the eyes and mouth states using mouse and keyboard events.

                function draw() {
                    background(220);
                    for (let face of faces) {
                        face.draw();
                    }
                }

        - mousePressed() { ... }: This function checks if the mouse is inside any face and toggles the eyes if true.
        - keyPressed() { ... }: This function toggles the mouth of all faces when the space key is pressed.

                function mousePressed() {
                    for (let face of faces) {
                        if (face.isMouseInside()) {
                            face.toggleEyes();
                        }
                    }
                }

                function keyPressed() {
                    if (key === ' ') {
                        for (let face of faces) {
                            face.toggleMouth();
                        }
                    }
                }

## Complete Code:

        class Face {
            constructor(x, y, size) {
                this.x = x;
                this.y = y;
                this.size = size;
                this.eyeSize = size * 0.2;
                this.eyeOffsetX = size * 0.35;
                this.eyeOffsetY = size * 0.25;
                this.isEyesClosed = false;
                this.isMouthOpen = false;
            }

            draw() {
                // Draw face
                fill(255, 204, 0);
                ellipse(this.x, this.y, this.size);

                // Draw eyes
                fill(255); // White fill for the eyes
                if (this.isEyesClosed) {
                    rect(this.x - this.eyeOffsetX - this.eyeSize / 2, this.y - this.eyeOffsetY - 5, this.eyeSize, 10); // Left closed eye
                    rect(this.x + this.eyeOffsetX - this.eyeSize / 2, this.y - this.eyeOffsetY - 5, this.eyeSize, 10); // Right closed eye
                } else {
                    ellipse(this.x - this.eyeOffsetX, this.y - this.eyeOffsetY, this.eyeSize, this.eyeSize); // Left eye
                    ellipse(this.x + this.eyeOffsetX, this.y - this.eyeOffsetY, this.eyeSize, this.eyeSize); // Right eye
                    fill(0); // Black fill for the pupils
                    let pupilOffsetX = (mouseX - this.x) / 20;
                    let pupilOffsetY = (mouseY - this.y) / 20;
                    ellipse(this.x - this.eyeOffsetX + pupilOffsetX, this.y - this.eyeOffsetY + pupilOffsetY, this.eyeSize / 2, this.eyeSize / 2); // Left pupil
                    ellipse(this.x + this.eyeOffsetX + pupilOffsetX, this.y - this.eyeOffsetY + pupilOffsetY, this.eyeSize / 2, this.eyeSize / 2); // Right pupil
                }

                // Draw nose
                fill(255, 153, 51); // Orange fill for the nose
                triangle(this.x, this.y - this.size * 0.1, this.x - this.size * 0.05, this.y + this.size * 0.1, this.x + this.size * 0.05, this.y + this.size * 0.1);

                // Draw mouth
                fill(255, 51, 51); // Red fill for the mouth
                if (this.isMouthOpen) {
                    arc(this.x, this.y + this.size * 0.2, this.size * 0.5, this.size * 0.25, 0, PI); // Open mouth
                } else {
                    rect(this.x - this.size * 0.25, this.y + this.size * 0.2, this.size * 0.5, 10); // Closed mouth
                }
            }

            toggleEyes() {
                this.isEyesClosed = !this.isEyesClosed;
            }

            toggleMouth() {
                this.isMouthOpen = !this.isMouthOpen;
            }

            isMouseInside() {
                let d = dist(mouseX, mouseY, this.x, this.y);
                return d < this.size / 2;
            }
        }

        let faces = [];

        function setup() {
            createCanvas(500, 500);
            let size = 100;
            for (let i = 0; i < 3; i++) {
                for (let j = 0; j < 3; j++) {
                    faces.push(new Face(150 * i + 100, 150 * j + 100, size));
                }
            }
        }

        function draw() {
            background(220);
            for (let face of faces) {
                face.draw();
            }
        }

        function mousePressed() {
            for (let face of faces) {
                if (face.isMouseInside()) {
                    face.toggleEyes();
                }
            }
        }

        function keyPressed() {
            if (key === ' ') {
                for (let face of faces) {
                    face.toggleMouth();
                }
            }
        }
