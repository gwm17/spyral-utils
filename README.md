# spyral-utils

![testing workflow](https://github.com/gwm17/spyral-utils/actions/workflows/test-actions.yml/badge.svg)
[![PyPI version shields.io](https://img.shields.io/pypi/v/ansicolortags.svg)](https://pypi.python.org/pypi/spyral-utils/)
[![PyPI license](https://img.shields.io/pypi/l/ansicolortags.svg)](https://pypi.python.org/pypi/spyral-utils/)

spyral-utils is a utility library that contains some of the  core functionality of [Spyral](https://github.com/turinath/Spyral.git). These utilities were found to be useful not just within Spyral but also continuing analysis after using Spyral. Some key utilities include:

- Nuclear masses from the AMDC AME 2020 masses
- Some histogramming and gating/cuting tools using matplotlib
- Basic four vector tools for creating and boosting momentum four vectors using numpy
- Energy loss analysis for gas and solid targets using pycatima

spyral-utils is still in very early development, so all mileage may vary!

## Installation

spyral-utils can be installed using `pip install spyral-utils`

## System requirements

spyral-utils requires Python >= 3.10 and  < 3.13

spyral-utils is cross-platform and tested for MacOS 13, Windows 11, and Ubuntu 22.04.

## Formats

Several parts of the utilities allow for saving and creating objects from JSON. Below is an outline of the expected formats for each of these

### Targets

The JSON description of a target is as follows:

For a gas target:

```[json]
{
    "compound": [
        [1, 1, 2]
    ],
    "pressure(Torr)": 300.0,
    "thickness(ug/cm^2)": null
}
```

For a solid target:

```[json]
{
    "compound": [
        [6, 12, 1]
    ],
    "pressure(Torr)": null,
    "thickness(ug/cm^2)": 50.0
}
```

The indication of a `null` pressure or thickness tells spyral-utils if that JSON is for a solid or gas target. Compound specifications are lists of elements where each element is an array of `[Z, A, S]`. `S` is the stoichiometry of that particular element in the compound. spyral-utils does not support target layers at this time (but layered targets can be built from the building blocks provided by spyral-utils). In the above examples the gas target is for <sup>1</sup>H<sub>2</sub> gas at 300 Torr pressure and the solid target is for <sup>12</sup>C<sub>1</sub> foil with a thickness of 50 &mu;g/cm<sup>2</sup>.

### 2D-Cuts

The JSON description of a 2D-Cut (or 2D-gate) on data is as follows:

```[json]
{
    "name": "test_cut",
    "vertices": [
        [0.0, 0.0],
        [1.0, 0.0],
        [1.0, 1.0],
        [0.0, 1.0],
        [0.0, 0.0]
    ]
}
```

`name` is a identifier given for that particular cut. `verticies` is a list of `[x,y]` coordinates which define the polygon. Note that the polygon must be closed (the final vertex must be the same as the first vertex).

## References

- [CAtima](https://github.com/hrosiak/catima)/[pycatima](https://github.com/hrosiak/pycatima)
- [AMDC Mass Evaluation](https://www-nds.iaea.org/amdc/): W.J. Huang et al 2021 Chinese Phys. C 45 030002
- [scipy](https://scipy.org/)
- [numpy](https://numpy.org/)
- [matplotlib](https://matplotlib.org/)
- [polars](https://www.pola.rs/)

## Authors

- Gordon McCann
- Nathan Turi
