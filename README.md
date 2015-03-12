# MNISTDataset

[![Build Status](https://travis-ci.org/Elzair/MNISTDataset.jl.svg?branch=master)](https://travis-ci.org/Elzair/MNISTDataset.jl)

**MNISTDataset** helps you work with the [MNIST Database of handwritten digits](http://yann.lecun.com/exdb/mnist/) in [Julia](http://julialang.org/). Many machine learning experts have used this database to test how well their algorithms can classify handwritten digits. I have included the database in this package, so you have everything you need to work with the data.

## API

**MNISTDataset** has two functions

### parseImages(name; useDecimal=true, addBias=false)

This function parses the files containing the image data. It returns a two-dimensional MxN matrix (of type `UInt8` or `Float64`) containing the pixel data for each image in its own column. Since the images are 28x28 pixels, the number of columns will be either 28*28=784 or 785 (depending on the value of `addBias`).

* **name**: Either "train" or "test"
* **useDecimal**: Convert the pixel data from [0-255] to [0.0-1.0]
* **addBias**: Add a column of ones (or 255) to the left-side of the resulting matrix

### parseLabels(name; multi=true, useBetterValues=false)

This function parses the files containing the digit classification (i.e 0, 1, 2, ..., 9) of the corresponding image in the image file. It returns either a vector of type `UInt8` or a two-dimensional Nx10 matrix of type `Float64` (depending on the value of `multi`).

* **name**: Either "train" or "test"
* **multi** Whether to split each row into a vector of length 10 (ex: 7 becomes `[0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0]`)
* **useBetterValues**: Instead of using `0.0` and `1.0`, as in the previous option, use `0.1` and `0.9`; this value only has an effect when `multi=true`
