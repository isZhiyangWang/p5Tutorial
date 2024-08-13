# Module 5 - Classes and Objects
## Summary
- Object Oriented Programming

## Object Oriented Programming

- Basic Classes and Objects
    - <b>Creating Classes</b>: Define custom objects with properties and methods.

            class Ball {
                constructor(x, y, r,col) {
                    this.x = x;
                    this.y = y;
                    this.r = r;
                    this.col = col;
                }

                display() {
                    fill(this.col);
                    ellipse(this.x, this.y, this.r * 2, this.r * 2);
                }
            }

            function setup() {
                createCanvas(400, 200);
                let ball = new Ball(200, 100, 50, color(255,0,0));
                ball.display();
            }
        
        <iframe src="https://editor.p5js.org/JimmyXwtx/full/TdOR5FdfV" width="400px" height="250px"></iframe>
    
    - <b>Adding Methods</b>: Methods define behavior for objects

            class Ball {
                constructor(x, y, r) {
                    this.x = x;
                    this.y = y;
                    this.r = r;
                }

                move() {
                    this.x += random(-5, 5);
                    this.y += random(-5, 5);
                }

                display() {
                    ellipse(this.x, this.y, this.r * 2, this.r * 2);
                }
            }

            let ball;

            function setup() {
                createCanvas(400, 200);
                ball = new Ball(200, 100, 50);
            }

            function draw() {
                background(220);
                ball.move();
                ball.display();
            }

        <iframe src="https://editor.p5js.org/JimmyXwtx/full/Nhk4DAcBL" width="400px" height="250px"></iframe>