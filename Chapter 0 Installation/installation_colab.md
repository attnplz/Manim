# Setting up Colab
```py
!sudo apt update
!sudo apt install libcairo2-dev \
    texlive texlive-latex-extra texlive-fonts-extra \
    texlive-latex-recommended texlive-science \
    tipa libpango1.0-dev
!pip install manim
!pip install IPython==8.21.0
```
Import Manim's libraries
```py
import manim as mn
from manim import *

config.media_width = "75%"
config.verbosity = "WARNING"

print(mn.__version__)
```
Scratch Cell
```py
%manim -qm CodeFromString
```
```py
from IPython.display import Video
video_path = "/content/media/videos/content/720p30/CodeFromString.mp4"
Video(video_path, embed=True, width=600, height=400)
```