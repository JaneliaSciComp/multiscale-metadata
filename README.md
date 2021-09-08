# multiscale-metadata
Guidelines for metadata for multiscale images stored in hierarchical storage schemes (e.g., Zarr / N5)

# Motivation
It is convenient for both computation and visualization to store a single image as a collection of sub-images, where each sub-image has coarser sampling than the previous one (known as a [multiresolution pyramid](https://en.wikipedia.org/wiki/Pyramid_(image_processing)), or a [mipmap](https://en.wikipedia.org/wiki/Mipmap)). Because each multiscale image has a unique size, they cannot be conveniently stored as a contiguous array, and hierarchical array formats are often used (e.g., [HDF5](https://www.hdfgroup.org/solutions/hdf5/), [Zarr](https://zarr.readthedocs.io/en/stable/), [N5](https://github.com/saalfeldlab/n5))

Applications consuming multiscale images must infer the following details, usually via convention or image metadata:

- Which images comprise the multiscale collection, and in what order?
- How does each image in the multiscale collection get mapped to a shared coordinate space? Coarsening reduces the grid spacing of an image by some (possibly anisotropic) amount, and common coarsening schemes also introduce a small translation. 

# Existing implementations

Historically different applications have taken varied approaches to creating / inferring these metadata elements, leading to a fragmentation of multiscale metadata schemes. 

## Neuroglancer: 
[Neuroglancer](https://github.com/google/neuroglancer/) displays multiresolution N5 groups if the following conditions are met:
- Group metadata contains `downSamplingFactors`, an array of arrays of numbers defining the per-axis downsampling per image.
- Group metadata contains `resolution`, an array of numbers specifying the grid spacing of the base image per axis.
- Group metadata contains `units`, an array of strings specifying the units of each axis.
- The group contains arrays with magic names: `s0` is the image with base sampling, `s1` is the first coarsened image, down to `sN` for the `Nth` coarsening
