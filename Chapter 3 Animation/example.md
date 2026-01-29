# Animation Chapter
## Animation 1

```py
class Animation1(Scene):
    def construct(self):
        s = RoundedRectangle(fill_opacity = 0.2, color = RED, corner_radius = 1).shift(LEFT * 3)
        t = Triangle(fill_opacity = 0.2, color = BLUE).scale(2).shift(RIGHT * 3)
        self.wait(1)
        self.play(Write(s), Create(t))
        self.wait(2)
```
---
## Animation 2
### Create a circle
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10).set_color("#FF00FF")
```

### Surrounding Rectangle
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        self.play(Write(s), Write(r))
        self.wait(1)
```

### Positioning objects next to each other
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = "Manim"
        self.play(Write(s),Write(r),Write(t))
        self.wait(1)
```

### Moving objects to specific coordinates
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(s,UP, buff = 0.5)
        self.play(Write(s),DrawBorderThenFill(r),Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4,0,0]), sr.animate.move_to([4,0,0]))
        self.wait()
```

### Creating an arrow
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip)
        self.play(Write(arrow))
        self.wait()
```

### Indicating text
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip)
        self.play(Write(arrow))
        self.play(Indicate(t, 1.5, color = ORANGE))
        self.wait()
```
### Rotation
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip)
        self.play(Write(arrow))
        self.play(Indicate(t, 1.5, color = ORANGE))
        self.play(Rotate(r,angle = -PI/2), ScaleInPlace(s, 2))
        self.wait()
```

### Updating position of an arrow
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = always_redraw(lambda: Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip))
        self.play(Write(arrow))
        self.play(Indicate(t, 1.5, color = ORANGE))
        self.play(Rotate(r,angle = -PI/2), ScaleInPlace(s, 2))
        self.wait()
```

### Moving VGroup
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = always_redraw(lambda: Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip))
        self.play(Write(arrow))
        self.play(Indicate(t, 1.5, color = ORANGE))
        self.play(Rotate(r,angle = -PI/2), ScaleInPlace(s, 2))
        self.play(sr.animate.move_to([0,0,0]))
        self.wait()
```

### Finishing up
```py
class Animation2(Scene):
    def construct(self):
        s = Circle(radius = 0.5, stroke_width = 10, color = RED, fill_opacity = 0.3)
        r = SurroundingRectangle(s, color = BLUE, corner_radius = 0.1)
        t = Text("Manim").next_to(r, UP, buff = 0.5)
        self.play(Write(s), DrawBorderThenFill(r), Write(t))
        sr = VGroup(s,r)
        self.play(t.animate.move_to([-4, 0, 0]), sr.animate.move_to([4, 0, 0]))
        arrow = always_redraw(lambda: Line(buff = 0.4, start = sr.get_left(), end = t.get_right()).add_tip(tip_shape = StealthTip).add_tip(at_start = True, tip_shape = StealthTip))
        self.play(Write(arrow))
        self.play(Indicate(t, 1.5, color = ORANGE))
        self.play(Rotate(r,angle = -PI/2), ScaleInPlace(s, 2))
        self.play(sr.animate.move_to([0,0,0]))
        self.play(FadeOut(arrow), FadeOut(t), run_time = 0.25)
        self.play(ShrinkToCenter(r), ScaleInPlace(s, 30))
        self.play(FadeOut(s))
        self.wait()
```
