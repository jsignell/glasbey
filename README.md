When visualizing categorical data we often want to encode each category with a
distinct color. The set of colors may be generated randomly, however more
visually pleasing results can be achieved if special care is taken to generate
a maximally distinct set of colors.

This repository contains an implementation of a method proposed by Glasbey et
al. [1] that is capable of identifying such a set. Dissimilarity between colors
is computed in the state-of-the-art perceptually uniform color space CAM02-UCS
[2].

Examples
--------

A palette with 30 colors, based on the "Set1" palette from [ColorBrewer2](http://bl.ocks.org/mbostock/5577023), with colors similar to black excluded.

![30 colors, based on "Set1"](https://raw.github.com/taketwo/glasbey/master/images/palette-set1-30.png)

A palette with 30 colors. First one was fixed to be white; no restrictions
regarding similarity to black.

![30 colors, starting with white](https://raw.github.com/taketwo/glasbey/master/images/palette-white-30.png)

Requirements
------------

Mandatory:

* [`colorspacious`](https://github.com/njsmith/colorspacious)

Optional:

* [`python-progressbar`](https://code.google.com/p/python-progressbar/) to show
  a progress bar during palette generation
* [`python-pillow`](https://github.com/python-pillow/Pillow) to visualize
  generated palettes

Usage
-----

```
usage: glasbey.py [-h] [--base-palette BASE_PALETTE] [--no-black] [--view]
                  [--format FORMAT]
                  size output

    Generate a palette with maximally disticts colors using the sequential
    method of Glasbey et al.¹

    (Dis)similarity between colors is computed in the state-of-the-art
    perceptually uniform color space CAM02-UCS.²

    This script needs an RGB to CAM02-UCS color lookup table. Generation of
    this table is a time-consuming process, therefore the first run of this
    script will take some time. The generated table will be stored in the
    working directory of the script and automatically used in next invocations
    of the script. Note that the approximate size of the table is 363 Mb.

    The palette generation method allows the user to supply a base palette. The
    output palette will begin with the colors from the supplied set. If no base
    palette is given, then white will be used as the first base color. The base
    palette should be given as a text file where each line contains a color
    description in RGB255 format with components separated with commas. (See
    files in the 'palettes/' folder for an example.)

    If having black (and colors close to black) is undesired, then `--no-black`
    option may be used to prevent the algorithm from inserting such colors into
    the palette.

    ¹) Glasbey, C., van der Heijden, G., Toh, V. F. K. and Gray, A. (2007),
       Colour Displays for Categorical Images.
       Color Research and Application, 32: 304-309

    ²) Luo, M. R., Cui, G. and Li, C. (2006),
       Uniform Colour Spaces Based on CIECAM02 Colour Appearance Model.
       Color Research and Application, 31: 320–330

positional arguments:
  size                  number of colors in the palette
  output                output palette filename

optional arguments:
  -h, --help            show this help message and exit
  --base-palette BASE_PALETTE
                        file with base palette
  --no-black            avoid black and similar colors
  --view                view generated palette
  --format FORMAT       output format (byte or float)
```

References
----------

1) Glasbey, C., van der Heijden, G., Toh, V. F. K. and Gray, A. (2007),
   [Colour Displays for Categorical Images](http://onlinelibrary.wiley.com/doi/10.1002/col.20327/abstract).
   Color Research and Application, 32: 304-309

2) Luo, M. R., Cui, G. and Li, C. (2006),
   [Uniform Colour Spaces Based on CIECAM02 Colour Appearance Model](http://onlinelibrary.wiley.com/doi/10.1002/col.20227/abstract).
   Color Research and Application, 31: 320–330
