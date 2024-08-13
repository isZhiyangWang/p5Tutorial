# Module 6 - Arrays

## Summary
- Arrays
- Arrays of Objects

## Arrays
- Basic Arrays
    - <b>Creating Arrays</b>: Store multiple values in a single variable

            function setup() {
                createCanvas(400, 200);
                let numbers = [10, 20, 30, 40];
                for (let i = 0; i < numbers.length; i++) {
                    textSize(32);
                    text(numbers[i], i * 50 + 10, 100);
                }
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/q6tZMdsKt" width="400px" height="250px"></iframe>

    - <b>Array Functions</b>: Use built-in functions to manipulate arrays

            function setup() {
                createCanvas(400, 200);
                let colors = [color(255, 0, 0), color(0, 255, 0), color(0, 0, 255)];
                colors.push(color(255, 255, 0)); // Add yellow
                for (let i = 0; i < colors.length; i++) {
                    fill(colors[i]);
                    rect(i * 100, 50, 100, 100);
                }
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/CgoMjXwf7" width="400px" height="250px"></iframe>


- Arrays of Objects
    - Using Arrays with Custom Objects
    - <b>Arrays of Custom Objects</b>: Manage multiple instances of custom objects

            class Particle {
                constructor(x, y) {
                    this.x = x;
                    this.y = y;
                }

                move() {
                    this.x += random(-5, 5);
                    this.y += random(-5, 5);
                }

                display() {
                    ellipse(this.x, this.y, 10, 10);
                }
            }

            let particles = [];

            function setup() {
                createCanvas(400, 200);
                for (let i = 0; i < 10; i++) {
                    particles.push(new Particle(random(width), random(height)));
                }
            }

            function draw() {
                background(220);
                for (let i = 0; i < particles.length; i++) {
                    particles[i].move();
                    particles[i].display();
                }
            }
        
        <iframe src="https://editor.p5js.org/JimmyXwtx/full/-hmmcqewb" width="400px" height="250px"></iframe>