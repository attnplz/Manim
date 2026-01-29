# Calculus Area
```py
from manim import *

class CalculusArea(Scene):
    def construct(self):
        axes = Axes(
            x_range=[-3, 3, 1],
            y_range=[-1, 5, 1],
            axis_config={"color": GREEN},
        )

        func = axes.plot(lambda x: 0.5 * x**2 + 1, color=BLUE)
        area = axes.get_area(func, x_range=[-2, 2], color=YELLOW, opacity=0.5)

        self.play(Create(axes))
        self.play(Create(func))
        self.play(FadeIn(area))
        self.wait()
```


## Explanation

This is a Manim animation that visualizes the concept of area under a curve in calculus.

### Setup

- Creates a coordinate plane with axes ranging from -3 to 3 on the x-axis and -1 to 5 on the y-axis, styled in green
```py
axes = Axes(
    x_range=[-3, 3, 1],
    y_range=[-1, 5, 1],
    axis_config={"color": GREEN},
)
```
### Graph

- Plots the function $f(x) = 0.5x^2 + 1$ (a parabola) in blue
```py
func = axes.plot(lambda x: 0.5 * x**2 + 1, color=BLUE)
```

### Area

- Fills the region under the curve between $x = -2$ and $x = 2$ with yellow color at 50% opacity
```py
area = axes.get_area(func, x_range=[-2, 2], color=YELLOW, opacity=0.5)
```
## Animation Sequence

1. Creates the axes with a drawing animation
2. Draws the function curve
3. Fades in the shaded area under the curve
4. Waits for 1 second
```py
self.play(Create(axes))
self.play(Create(func))
self.play(FadeIn(area))
self.wait()
```
### Purpose

The scene demonstrates how to visualize definite integrals by shading the area beneath a curve between two x-values, which is a fundamental concept in calculus.
