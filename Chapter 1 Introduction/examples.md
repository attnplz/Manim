# Examples

## Animating a circle
```py
class CreateCircle(Scene):
  def construct(self):
    circle = Circle()  # create a circle
    circle.set_fill(PINK, opacity=0.5)  # set the color and transparency
    self.play(Create(circle))  # show the circle on screen
```
## Transform a square into circle
```py
class SquareToCircle(Scene):
  def construct(self):
    circle = Circle()  # create a circle
    circle.set_fill(PINK, opacity=0.5)  # set color and transparency

    square = Square()  # create a square
    square.rotate(PI / 4)  # rotate a certain amount

    self.play(Create(square))  # animate the creation of the square
    self.play(Transform(square, circle))  # interpolate the square into the circle
    self.play(FadeOut(square))  # fade out animation
```
## Positioning Mobjects
```py
class SquareAndCircle(Scene):
  def construct(self):
    circle = Circle()  # create a circle
    circle.set_fill(PINK, opacity=0.5)  # set the color and transparency

    square = Square()  # create a square
    square.set_fill(BLUE, opacity=0.5)  # set the color and transparency

    square.next_to(circle, RIGHT, buff=0.5)  # set the position
    self.play(Create(circle), Create(square))  # show the shapes on screen
```
## Using .animate syntax to animate methods
```py
class AnimatedSquareToCircle(Scene):
  def construct(self):
    circle = Circle()  # create a circle
    square = Square()  # create a square

    self.play(Create(square))  # show the square on screen
    self.play(square.animate.rotate(PI / 4))  # rotate the square
    self.play(Transform(square, circle))  # transform the square into a circle
    self.play(
        square.animate.set_fill(PINK, opacity=0.5)
    )  # color the circle on screen
```
```py
class DifferentRotations(Scene):
  def construct(self):
    left_square = Square(color=BLUE, fill_opacity=0.7).shift(2 * LEFT)
    right_square = Square(color=GREEN, fill_opacity=0.7).shift(2 * RIGHT)
    self.play(
        left_square.animate.rotate(PI), Rotate(right_square, angle=PI), run_time=2
    )
    self.wait()
```
```py
class TwoTransforms(Scene):
  def transform(self):
    a = Circle()
    b = Square()
    c = Triangle()
    self.play(Transform(a, b))
    self.play(Transform(a, c))
    self.play(FadeOut(a))

  def replacement_transform(self):
    a = Circle()
    b = Square()
    c = Triangle()
    self.play(ReplacementTransform(a, b))
    self.play(ReplacementTransform(b, c))
    self.play(FadeOut(c))

  def construct(self):
    self.transform()
    self.wait(0.5)  # wait for 0.5 seconds
    self.replacement_transform()
```
```py
class TransformCycle(Scene):
  def construct(self):
    a = Circle()
    t1 = Square()
    t2 = Triangle()
    self.add(a)
    self.wait()
    for t in [t1,t2]:
        self.play(Transform(a,t))
```
## Create and display MObject
```py
class CreatingMobjects(Scene):
  def construct(self):
    circle = Circle()
    self.add(circle)
    self.wait(1)
    self.remove(circle)
    self.wait(1)
```
## Placing MObject
```py
class Shapes(Scene):
  def construct(self):
    circle = Circle()
    square = Square()
    triangle = Triangle()

    circle.shift(LEFT)
    square.shift(UP)
    triangle.shift(RIGHT)

    self.add(circle, square, triangle)
    self.wait(1)
```
```py
class MobjectPlacement(Scene):
  def construct(self):
    circle = Circle()
    square = Square()
    triangle = Triangle()

    # place the circle two units left from the origin
    circle.move_to(LEFT * 2)
    # place the square to the left of the circle
    square.next_to(circle, LEFT)
    # align the left border of the triangle to the left border of the circle
    triangle.align_to(circle, LEFT)

    self.add(circle, square, triangle)
    self.wait(1)
```
## MObject styling
```py
class MobjectStyling(Scene):
  def construct(self):
    circle = Circle().shift(LEFT)
    square = Square().shift(UP)
    triangle = Triangle().shift(RIGHT)

    circle.set_stroke(color=GREEN, width=20)
    square.set_fill(YELLOW, opacity=1.0)
    triangle.set_fill(PINK, opacity=0.5)

    self.add(circle, square, triangle)
    self.wait(1)
```
## MObject on-screen order
```py
class MobjectZOrder(Scene):
  def construct(self):
    circle = Circle().shift(LEFT)
    square = Square().shift(UP)
    triangle = Triangle().shift(RIGHT)

    circle.set_stroke(color=GREEN, width=20)
    square.set_fill(YELLOW, opacity=1.0)
    triangle.set_fill(PINK, opacity=0.5)

    self.add(triangle, square, circle)
    self.wait(1)
```
## Animation
```py
class SomeAnimations(Scene):
  def construct(self):
    square = Square()

    # some animations display mobjects, ...
    self.play(FadeIn(square))

    # ... some move or rotate mobjects around...
    self.play(Rotate(square, PI/4))

    # some animations remove mobjects from the screen
    self.play(FadeOut(square))

    self.wait(1)
```
## Animating methods
```py
class AnimateExample(Scene):
  def construct(self):
    square = Square().set_fill(RED, opacity=1.0)
    self.add(square)

    # animate the change of color
    self.play(square.animate.set_fill(WHITE))
    self.wait(1)

    # animate the change of position and the rotation at the same time
    self.play(square.animate.shift(UP).rotate(PI / 3))
    self.wait(1)
```
## Animation run time
```py
class RunTime(Scene):
  def construct(self):
    square = Square()
    self.add(square)
    self.play(square.animate.shift(UP), run_time=3)
    self.wait(1)
```
## First scene
```py
class CircleToSquare(Scene):
  def construct(self):
    blue_circle = Circle(color=BLUE, fill_opacity=0.5)
    green_square = Square(color=GREEN, fill_opacity=0.8)
    self.play(Create(blue_circle))
    self.wait()

    self.play(Transform(blue_circle, green_square))
    self.wait()
```
## Positioning Mobjects and moving them around
```py
class HelloCircle(Scene):
  def construct(self):
    # blue_circle = Circle(color=BLUE, fill_opacity=0.5)
    # We can also create a "plain" circle and add the desired attributes via set methods:
    circle = Circle()
    blue_circle = circle.set_color(BLUE).set_opacity(0.5)

    label = Text("A wild circle appears!")
    label.next_to(blue_circle, DOWN, buff=0.5)

    self.play(Create(blue_circle), Write(label))
    self.wait()
```
## Animating Method calls: the .animate syntax
```py
class CircleAnnouncement(Scene):
  def construct(self):
    blue_circle = Circle(color=BLUE, fill_opacity=0.5)
    announcement = Text("Let us draw a circle.")

    self.play(Write(announcement))
    self.wait()

    self.play(announcement.animate.next_to(blue_circle, UP, buff=0.5))
    self.play(Create(blue_circle))
```
```py
class AnimateSyntax(Scene):
  def construct(self):
    triangle = Triangle(color=RED, fill_opacity=1)
    self.play(DrawBorderThenFill(triangle))
    self.play(triangle.animate.shift(LEFT))
    self.play(triangle.animate.shift(RIGHT).scale(2))
    self.play(triangle.animate.rotate(PI/3))
```
```py
class DifferentRotations(Scene):
  def construct(self):
    left_square = Square(color=BLUE, fill_opacity=0.7).shift(2*LEFT)
    right_square = Square(color=GREEN, fill_opacity=0.7).shift(2*RIGHT)
    self.play(left_square.animate.rotate(PI), Rotate(right_square, angle=PI), run_time=2)
    self.wait()
```
## Typesetting Mathematics
```py
class CauchyIntegralFormula(Scene):
  def construct(self):
    formula = MathTex(r"[z^n]f(z) = \frac{1}{2\pi i}\oint_{\gamma} \frac{f(z)}{z^{n+1}}~dz")
    self.play(Write(formula), run_time=3)
    self.wait()
```
```py
class TransformEquation(Scene):
  def construct(self):
    eq1 = MathTex("42 {{ a^2 }} + {{ b^2 }} = {{ c^2 }}")
    eq2 = MathTex("42 {{ a^2 }} = {{ c^2 }} - {{ b^2 }}")
    eq3 = MathTex(r"a^2 = \frac{c^2 - b^2}{42}")
    self.add(eq1)
    self.wait()
    self.play(TransformMatchingTex(eq1, eq2))
    self.wait()
    self.play(TransformMatchingShapes(eq2, eq3))
    self.wait()
```
```py
class FormulaEmphasis(Scene):
  def construct(self):
    product_formula = MathTex(
        r"\frac{d}{dx} f(x)g(x) =",
        r"f(x) \frac{d}{dx} g(x)",
        r"+",
        r"g(x) \frac{d}{dx} f(x)"
    )
    self.play(Write(product_formula))
    box1 = SurroundingRectangle(product_formula[1], buff=0.1)
    box2 = SurroundingRectangle(product_formula[3], buff=0.1)
    self.play(Create(box1))
    self.wait()
    self.play(Transform(box1, box2))
    self.wait()
```
## Plotting
```py
class PlotExample(Scene):
  def construct(self):
    plot_axes = Axes(
        x_range=[0, 1, 0.05],
        y_range=[0, 1, 0.05],
        x_length=9,
        y_length=5.5,
        axis_config={
            "numbers_to_include": np.arange(0, 1 + 0.1, 0.1),
            "font_size": 24,
        },
        tips=False,
    )

    y_label = plot_axes.get_y_axis_label("y", edge=LEFT, direction=LEFT, buff=0.4)
    x_label = plot_axes.get_x_axis_label("x")
    plot_labels = VGroup(x_label, y_label)

    plots = VGroup()
    for n in np.arange(1, 20 + 0.5, 0.5):
        plots += plot_axes.plot(lambda x: x**n, color=WHITE)
        plots += plot_axes.plot(
            lambda x: x**(1 / n), color=WHITE, use_smoothing=False
        )

    extras = VGroup()
    extras += plot_axes.get_horizontal_line(plot_axes.c2p(1, 1, 0), color=BLUE)
    extras += plot_axes.get_vertical_line(plot_axes.c2p(1, 1, 0), color=BLUE)
    extras += Dot(point=plot_axes.c2p(1, 1, 0), color=YELLOW)
    title = Title(
        r"Graphs of $y=x^{\frac{1}{n}}$ and $y=x^n (n=1, 1.5, 2, 2.5, 3, \dots, 20)$",
        include_underline=False,
        font_size=40,
    )

    self.play(Write(title))
    self.play(Create(plot_axes), Create(plot_labels), Create(extras))
    self.play(AnimationGroup(*[Create(plot) for plot in plots], lag_ratio=0.05))
```
```py
import networkx as nx

nxgraph = nx.erdos_renyi_graph(14, 0.5)

class ErdosRenyiGraph(Scene):
  def construct(self):
    G = Graph.from_networkx(nxgraph, layout="spring", layout_scale=3.5)
    self.play(Create(G))
    self.play(*[G[v].animate.move_to(5*RIGHT*np.cos(ind/7 * PI) +
                                      3*UP*np.sin(ind/7 * PI))
                for ind, v in enumerate(G.vertices)])
    self.play(Uncreate(G))
```
```py
class CodeFromString(Scene):
  def construct(self):
    code = '''
    from manim import Scene, Square

    class FadeInSquare(Scene):
      def construct(self):
        s = Square()
        self.play(FadeIn(s))
        self.play(s.animate.scale(2))
        self.wait()
    '''
    rendered_code = Code(
        code_string=code, tab_width=4, background="window",
        language="python", paragraph_config=dict(font="Monospace")
    )
    self.play(Write(rendered_code))
    self.wait(2)
```
