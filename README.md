# SLIC (Simple Linear Iterative Clustering) Superpixels

Paper: https://www.cs.jhu.edu/~ayuille/JHUcourses/VisionAsBayesianInference2022/4/Achanta_SLIC_PAMI2012.pdf

## Background

Superpixels are just small regions of an image.

Superpixels-based algorithms group pixels based on color and spatial proximity into perceptually meaningful regions while respecting potential object contours, and thereby can replace the rigid pixel grid structure. They serve as a more meaningful and efficient representation of images compared to individual pixels, and can reduce the complexity of image processing tasks.

Used in computer vision stuff like object detection, image segmentation, image editing, etc.

## SLIC Superpixels
SLIC (Simple Linear Iterative Clustering) is an efficient algorithm for generating superpixels. It is based on a modified k-means clustering approach, considering both color and spatial information.

![image](https://github.com/milton-lopez/SLIC-Superpixels/assets/26948607/f435dca7-c974-453d-9d09-565bb0978b0a)

## Distance function

The minimized distance function considers both color similarity and spatial proximity:

$D=\sqrt{\left(\frac{d_c}{m}\right)^2+\left(\frac{d_s}{S}\right)^2}$

Where:
- $D$ is the combined distance.
- $d_c$ is the color distance in the CIELAB color space.
- $d_s$ is the spatial distance.
- $m$ is a compactness parameter that controls the trade-off between color and spatial proximity.
- $S$ is the grid interval, approximately equal to the square root of the image area divided by the desired number of superpixels.

## Algorithm

- **Initialization**: Cluster centers are formed at grid intervals and moved to lowest gradient position within some neighborhood.
- **Assignment**: Pixels are assigned to the nearest cluster center applying the distance function.
- **Update**: Update cluster centers to pixels mean.
- **Iteration**: Repeat until convergence.
