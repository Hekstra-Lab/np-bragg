# np-bragg
A very simplistic x-ray diffraction simulator for teaching purposes. 

### nanobragg in numpy
The goal of this project was to implement something akin to James Holton's authoritative nanobragg x-ray diffraction simulator in numpy. 
This was undertaken mostly as a learning exercise and a feasibility study. 
However, they do accurately model basic diffraction physics with multi-wavelength support as well as a gaussian radial basis function mosaicity model. 
Long term, this code may form the basis of a tensorflow or pytorch implementation of diffraction simulation. 

### limitations
These notes do not attempt to implement many of the features supported by nanobragg and related packages. 
However, these can be added simply in future iterations either by a pixelwise multiplicative correction to the diffraction simulation (eg polarization and Debye-Waller Factors) or additive in the case of background scatter or detector noise. 
They need not change the core simulation routine for bragg diffraction. 

* Polarization correction
* Debye-Waller factors
* Solvent scatter
* Detector artifacts
* Poisson noise


### list of notebooks
At the moment there are 3 notebooks in this repository which represent 3 increasing levels of algorithmic complexity. 
#### np-bragg.ipynb
This is a very simplistic, first stab at diffraction simulation using numpy. 
It implements calculation of monochromatic still images. 
It is perhaps the clearest of the 3 notebooks. 
It suffers from being painfully slow and very memory hungry. 

#### np-bragg-laue.ipynb
This notebook extends the basic ideas in the first to multiple wavelengths. 
As production code, it is hopelessly resource intensive, but it is much simpler than more optimized implementations. 


#### np-bragg-sparse.ipynb
This is the only implementation in this repository which is close to being applicable to real use-cases. 
It implements a sparse approximation of the diffraction equation which works by assigning sets of pixels to each reciprocal lattice point. 
Essentially, it knows it shouldn't spend time and memory computing the contribution of every HKL to every pixel.
Instead it works by building up a list of which HKL is likely to have a significant contribution to which pixel and only summing over that list. 
This algorithm is probably good enough to use in production if it can be ported to tensorflow or torch in a way that preserves its memory saving advantages. 
