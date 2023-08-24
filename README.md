<h1 align="center">Continuous Style Control</h1>
<p align="center"><strong>Image morphing using Stable Diffusion</strong></p>
<br/>
<div align="center"><img src="results/draw-vangogh.png"></img>
</div>
<h2>About</h2>

Unlike text-conditioned models like Stable Diffusion, common unconditional
GANs such as StyleGAN allow for style control of the generated images by manipulating
the input latent code. It is possible to discover latent directions that
correlate with certain characteristics, such as hair color, skin tone, lighting, and
pose (in the particular example of faces). Since the latent space is continuous, it
is also possible to smoothly interpolate between these factors of variation while
preserving the identity of the generated image. It would be interesting to see if
such interpolation can also be achieved using diffusion models.
<br><br>
Our attempt to achieve this uses a combination of CLIP embedding interpolation and attention map interpolation (based on <a href="https://prompt-to-prompt.github.io/">Prompt-to-Prompt</a>).
We also tried comparing it to another technique based on <a href="https://github.com/ml-research/semantic-image-editing">Semantic Guidance</a>. These methods are then used to interpolate between text prompts, which allows continuous style control (eg. between prompts like "a red car" and "a green car"), but also more complex morphs (eg. "a squirrel eating a burger" and "a lion eating a burger").
<br><br>
Our findings are described in our [final report](report.pdf).

<h2>Try it out yourself</h2>

To experiment with our code and see how it works, you can take a look at the Jupyter Notebook. The [CSC-all-in-one.ipynb](CSC-all-in-one.ipynb) notebook can simply be uploaded to Google Colab and should just work without any extra setup. You can also find this notebook <a href="https://colab.research.google.com/drive/1TU4SkCyWEjO-nZOs4q4PW0FDy_TrRstK?usp=sharing">here</a>. To run our main interpolation method (AttentionFullInterpolation) locally, a GPU with 16GB+ VRAM is required.

<h2>A few results </h2>
"A charcoal drawing of a squirrel eating a burger"  &rarr;  "A painting by Van Gogh of a squirrel eating a burger"
<img src="results/draw-vangogh.png"></img>
<br>
"A painting of a squirrel eating a burger"  &rarr;  "A painting of a lion eating a burger"
<img src="results/squirrel-lion.png"></img>
<br>
"A portrait of a Roman Emperor" &rarr; "A portrait of a Chinese Empress"
<img src="results/emperor-empress.png"></img>
<br>
"A children's painting of a large castle on a hill in the distance" &rarr; "A drawing of a large fantasy castle on a hill in the distance"
<img src="results/castles.png"></img>
<br>
"A realistic painting of a white boy" &rarr; "A realistic painting of a black girl"
<img src="results/boy-girl.png"></img>


<h2>Credits</h2>

This project was developed by Jonathan Swinnen, Patrick Eppensteiner and Yannick Biehl for the 'Generative Visual Models' seminar at ETH Zürich during the spring semester of 2023. 
<br> We would like to thank Prof. Thomas Hofmann and his team of TA's for their support, without whom this project would not have been possible.
<br><br>
The code & notebook is heavily based on the one provided in the 'Prompt-to-Prompt' project. <br> You can find their work here:
https://prompt-to-prompt.github.io/
<br><br>
The alternative semantic guidance technique was taken from the 'semantic-image-editing' project. <br> You can find their work here:
https://github.com/ml-research/semantic-image-editing
