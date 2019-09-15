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

