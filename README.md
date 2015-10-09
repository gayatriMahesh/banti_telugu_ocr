# Comprehensive OCR System for Telugu Language
## The Banti Framework

This framework relies on the ability of a segmentation algorithm to break the
text in to glyphs. Hence it can be extended to other scripts with well 
seperated images like Malayalam, Oriya, Tamil, Kannada, Thai etc.

# Features
+ Opens box files generated by banti (segmentation program)
+ Passes them to a neural network trained by [theanet](https://github.com/rakeshvar/theanet)
+ n-gram modelling of the language
+ Ability to stich broken glyphs (using the language model).

# Dependencies
1. Python3
1. Numpy, Scipy, Nose etc.
1. [Theano](https://github.com/Theano/Theano)
1. [banti segmenter](https://github.com/rakeshvar/banti)
1. [Theanet](https://github.com/rakeshvar/theanet)

# Installation Instructions

1. Install python3

  You might already have it. Just type ```which python3``` and  check. Make sure you also have ```pip3```. Python3.4 comes with ```pip3```. Python3.3 and older need additional installation of ```pip3```.

1. Install ```Theano``` after installing its dependencies. Here are the [General](http://deeplearning.net/software/theano/install.html) and  the 
[Ubuntu-specific](http://deeplearning.net/software/theano/install_ubuntu.html#install-ubuntu) instructions. 

  You just need to install numpy, scipy, nose etc.

1. Install [Theanet](https://github.com/rakeshvar/theanet) by running the setup.py

1. Clone [telugu_ocr_banti](https://github.com/rakeshvar/telugu_ocr_banti).

1. Set the following theano flag(s). I just put the following in my .bashrc file.

```sh
export THEANO_FLAGS='floatX=float32'
```

1. Get the required files to load the neural network and the ngram library.

```sh
# change to cloned project directory
mkdir library
wget http://stanford.edu/~rakesha/banti/library/4hidaux_252611_01.pkl -O library/nn.pkl
wget http://stanford.edu/~rakesha/banti/library/mega.123.pkl -P library/
```

1. Run the ocr program 

```sh
python3 ocr.py sample_images/praasa.box 
# Run without arguments to see complete list of available arguments.
```

Here you are running on the provided sample image ```praasa.box``` genereated from ```praasa.tif``` (both in the ```sample_images``` directory)

1. To run on your own images.

Note that ```ocr.py``` accepts only images in the ```.box``` format. These 
files are genereated by [banti segmenter](https://github.com/rakeshvar/banti). You 
can install that to genereate box files from your own tiff files.
