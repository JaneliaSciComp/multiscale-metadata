# multiscale-metadata
Guidelines for metadata for multiscale images stored in hierarchical storage schemes (e.g., Zarr / N5)

# Motivation
It is convenient for both computation and visualization to store a single image as a collection of sub-images, where each sub-image has coarser sampling than the previous one (known as a [image pyramid](https://en.wikipedia.org/wiki/Pyramid_(image_processing)), or a [mipmap](https://en.wikipedia.org/wiki/Mipmap)). The creation of multiresolution image has several degrees of freedom, including:

- The method used for coarsening the image (e.g., subsampling, windowed averaging, smoothing -> resampling) 
- The amount of coarsening per coarsening step. Coarsening by a factor of 2 in each dimension is most common, but there are enough exceptions to this trend that  

# Conc

# E: 
```json
```
