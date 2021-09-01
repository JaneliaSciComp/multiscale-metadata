# multiscale-metadata
Guidelines for metadata for multiscale images stored in hierarchical storage schemes (e.g., Zarr / N5)

# Motivation
It is convenient for both computation and visualization to store a single image as a collection of sub-images, where each sub-image has coarser sampling than the previous one (known as a [multiresolution pyramid](https://en.wikipedia.org/wiki/Pyramid_(image_processing)), or a [mipmap](https://en.wikipedia.org/wiki/Mipmap)).  
