# MNIST Sequence Generator

## Library used 

Tensorflow 1.5.0

Numpy 1.14.0

Scikit-Image 0.13.1

OpenCV 3.3.1

## About the Main Function

The algorithm was designed to meet the following specifications:

- Select a sequence of MNIST digits

- generate a spacing to separate the digits, chosen from a uniform random distribution

- crop, or grow, the digits in accordance with a user-defined width parameter

- combine the digits, and the spacings between them, into a single image

The intention is to provide an API/command-line module which takes as parameters:

digits: the list of numbers to select from MNIST

spacing_range: a minimum, maximum pair used to provide an interval for the generated spacings

image_width: used to either crop or widen the images

The main function to call is the following:

def generate_numbers_sequence(digits, spacing_range, image_width):
    
		"""
    Generate an image that contains the sequence of given numbers, spaced
    randomly using a uniform distribution.
    """
So, for example, if we had

digits = [2,3,4]

spacing_range = (0,9)

width = 20

then

generate_numbers_sequence(digits, spacing_range, image_width)

would read through and randomly select MNIST images corresponding to each of the numbers provided, create arrays of spacings between each of the digits, and concatenate them into a single np.array. Each MNIST image would be either cropped or grown, according to the width parameter; in this case, image_width = 27, so each MNIST image would be cropped by 1 pixel (or, rather, one column of the np.array).

The function would return a floating point 32-bit numpy array representing the sequence of digits. Each float in the array represents a colour value for the pixel, such that 1 == white and 0 == black.

In addition, the generated image is saved in the current directory as a .png.
