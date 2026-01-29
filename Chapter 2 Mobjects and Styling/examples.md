# Examples
## Example 1
```py
class Example_1(Scene):
  def construct(self):
    circle_1 = Circle(radius=1.0,color='RED')
    circle_2 = Circle(radius=1.0,color='GREEN')
    circle_3 = Circle(radius=1.0,color='BLUE')

    circles = Group(circle_1,circle_2,circle_3).arrange(buff=1)

    # circle.stroke_width = 20
    self.add(circles)
    # self.add(circle_2)
    # self.add(circle_3)
    self.wait(5)
```
Example 1 is a Manim scene that demonstrates creating and arranging colored circles:

Creates 3 circles — each with a radius of 1.0 and different colors (RED, GREEN, BLUE).
Groups them together — uses ```Group()``` to combine all three circles into a single unit.
Arranges with spacing — ```.arrange(buff=1)``` distributes them horizontally with 1 unit spacing between them.
Adds to scene — ```self.add(circles)``` renders all circles on screen.
Wait duration — ```self.wait(5)``` holds the animation for 5 seconds.

## Example 2
```py
class Example_2(Scene):
  def construct(self):
    rect_1 = Rectangle(color='RED',width=2,height=2,grid_xstep=1,grid_ystep=1)
    rect_2 = Rectangle(color='GREEN',width=2,height=2,grid_xstep=1,grid_ystep=1)
    rect_3 = Rectangle(color='BLUE',width=2,height=2,grid_xstep=1,grid_ystep=1)
    rect_2.next_to(rect_1,RIGHT)
    rect_3.next_to(rect_2,RIGHT)
    self.add(rect_1,rect_2,rect_3)
```
Example 2 creates and positions three colored rectangles in a horizontal line:

Creates 3 rectangles — each with width=2, height=2, and different colors (RED, GREEN, BLUE)
Grid parameters — grid_xstep=1 and grid_ystep=1 add internal grid lines to each rectangle at 1-unit intervals
Positions side by side — uses .next_to() to place rectangles horizontally:
rect_2 is positioned to the RIGHT of rect_1
rect_3 is positioned to the RIGHT of rect_2
Renders all three — self.add(rect_1,rect_2,rect_3) displays them on screen
This example demonstrates object positioning and the next_to() method for relative placement. Unlike Example 1 which uses .arrange() for automatic spacing, this shows manual positioning with explicit direction (RIGHT).

## Example 3
```py
class Example_3(Scene):
  def construct(self):
    circle = Circle()
    square = Square()
    square.flip(RIGHT)
    square.rotate(-3*TAU/8)
    circle.set_fill(PINK,opacity=0.5)

    # self.add(square)
    self.play(Create(square))
    self.play(Transform(square,circle))
    self.play(FadeOut(square))
```
Example 3 demonstrates transformations and animations between shapes:

Creates shapes — creates a circle and a square

Modifies the square:

```.flip(RIGHT)``` mirrors it horizontally
```.rotate(-3*TAU/8)``` rotates it by -3/8 of a full turn (135 degrees counterclockwise)
Styles the circle — ```.set_fill(PINK,opacity=0.5)``` fills it with semi-transparent pink

Animations:

```self.play(Create(square))``` — draws the square with an animation
```self.play(Transform(square,circle))``` — morphs the square into the circle
```self.play(FadeOut(square))``` — fades out the transformed object

This example shows core Manim animation techniques: object transformations, shape morphing with ```Transform()```, and fade effects. The commented-out ```self.add(square)``` suggests testing static display before applying animations.
## Example 4
```py
class Example_4(Scene):
  def construct(self):
    first_line = Text('Piyawat Neammalai')
    second_line = Text('Department of Mathematics')
    third_line = Text('Welcome to Manim')

    second_line.next_to(first_line,DOWN)

    self.wait(1)
    self.play(Write(first_line), Write(second_line))
    self.wait(1)
    self.play(ReplacementTransform(first_line,third_line),FadeOut(second_line))
    self.wait(2)
```
Example 4 demonstrates text animation and replacement transformations:

Creates 3 text objects:

```first_line``` — "Piyawat Neammalai" \
```second_line``` — "Department of Mathematics" \
```third_line``` — "Welcome to Manim" \
Positions text — ```second_line.next_to(first_line,DOWN)``` places the second line below the first

Animation sequence:

```self.wait(1)``` — 1 second pause
```self.play(Write(first_line), Write(second_line))``` — writes both lines simultaneously with a typewriter effect 
```self.wait(1)``` — 1 second pause
```self.play(ReplacementTransform(first_line,third_line),FadeOut(second_line))``` — morphs the first line into the third line while fading out the second line
```self.wait(2)``` — 2 second pause at the end
This example shows how to create introductory text animations, run multiple animations simultaneously, and use ReplacementTransform() to smoothly transition between text objects.
## Example 5
```py
class Example_5(Scene):
  def construct(self):
    first_line = Tex('$y = ax^2+bx+c$')
    second_line = Tex('$x = \\dfrac{-b \\pm \\sqrt{b^2-4ac}}{2a}$')
    self.wait(1)
    self.play(Write(second_line))
```
- **Creates 2 LaTeX equations**:
  - `first_line` — quadratic equation: $y = ax^2+bx+c$
  - `second_line` — quadratic formula: $x = \dfrac{-b \pm \sqrt{b^2-4ac}}{2a}$
- **Animation sequence**:
  - `self.wait(1)` — 1 second pause
  - `self.play(Write(second_line))` — writes the quadratic formula with animation

**Note**: `first_line` is defined but never displayed or animated, suggesting this might be incomplete code or intentionally showing only the quadratic formula. The `Tex()` class renders LaTeX math notation, allowing professional mathematical typesetting in animations.

