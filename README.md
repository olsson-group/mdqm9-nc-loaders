# Data Loaders for the MDQM9-nc dataset

## Description
This dataset contains MD simulations of 12,506 non-cyclic molecules from the QM9 dataset in vacuum and room temperature using the GAFF force field. We carried out these simulations using the openmmforcefields and OpenMM packages. All initial conditions were generated by energy minimizing the QM9 geometry in the corresponding GAFF force field. We sampled different molecules proportionally to their number of heavy atoms with a median sampling time of 36.5 ns. Moreover, for 100 molecules from the test set (10 %), we run longer 100 ns Replica Exchange (RE) simulations.

## Prerequisites
* Anaconda or Miniconda with Python 3.9.

### Setting the environment
The [./environment.yml](./environment.yml) file lists all the packages required for this environment. A virtual environment can be easily created using the YAML file and conda by typing into the terminal:

```
conda env create -f environment.yml
```

### Usage
The MDQM9-nc dataset is available [here](https://zenodo.org/records/10579242?token=eyJhbGciOiJIUzUxMiJ9.eyJpZCI6ImY1MjMyZTY2LWYwMzUtNDg3NC05ODFhLWQ3ODE1M2QyYTdjMiIsImRhdGEiOnt9LCJyYW5kb20iOiI1ZWNkNjQ2Mzg2NThjNzFlYjk0YmE3MmNiOTZlM2IyNSJ9.V1BbyB7fINU4wEiht5l19B0JpDyWpA2OGaAbO1wbNAM3jwFEUM_Us13Y7bjRPPcP8S3q9OjSrS2_o41Sx0VCXg). It contains mdqm9-nc.sdf, a sdf file with the molecules and mdqm9-nc.hdf5 with conformational data. Random splits are also provided.
mdqm9-nc.hdf5 is distrubuted in 10 files mdqm9_nc_0{0 to 9}. After downloadig the 10 files, run 
```
cat parts/mdqm9-nc_* > parts/mdqm9-nc.hdf5
```
to merge the files. To instantiate a class of the mdqm9-nc dataset, import MDQM9Dataset from [mdqm9_loader.py](./mdqm9_loader.py):
```
from mdqm9_loader import MDQM9Dataset
sdf_path = "datasets/mdqm9-nc/mdqm9-nc.sdf" #path to mdqm9-nc.sdf
hdf5_path = "datasets/mdqm9-nc/mdqm9-nc.hdf5" #path to mdqm9-nc.hdf5
dataset = MDQM9Dataset(sdf_path, hdf5_path)
first_mol = dataset[0]
```


## Contributors
[@JuanViguera](https://www.github.com/JuanViguera) and [@psolsson](https://github.com/psolsson).

## Contributions
Contributions are welcome in the form of issues or pull requests. To report a bug, please submit an issue. Thank you to everyone who has used the code and provided feedback thus far.

### Publications
If you use MDQM9-nc in your research, please reference our [paper](https://doi.org/10.26434/chemrxiv-2023-sx61w).

The reference in BibTex format are available below:

```
 @article{viguera diez_romeo atance_engkvist_olsson_2023, place={Cambridge}, title={Generation of conformational ensembles of small molecules via Surrogate Model-Assisted Molecular Dynamics}, DOI={10.26434/chemrxiv-2023-sx61w}, journal={ChemRxiv}, publisher={Cambridge Open Engage}, author={Viguera Diez, Juan and Romeo Atance, Sara and Engkvist, Ola and Olsson, Simon}, year={2023}} This content is a preprint and has not been peer-reviewed.
```

### Related work
```
@article{qm9,
author={Ramakrishnan, Raghunathan
and Dral, Pavlo O.
and Rupp, Matthias
and von Lilienfeld, O. Anatole},
title={Quantum chemistry structures and properties of 134 kilo molecules},
journal={Scientific Data},
year={2014},
month={8},
day={05},
volume={1},
number={1},
pages={140022},
abstract={Computational de novo design of new drugs and materials requires rigorous and unbiased exploration of chemical compound space. However, large uncharted territories persist due to its size scaling combinatorially with molecular size. We report computed geometric, energetic, electronic, and thermodynamic properties for 134k stable small organic molecules made up of CHONF. These molecules correspond to the subset of all 133,885 species with up to nine heavy atoms (CONF) out of the GDB-17 chemical universe of 166 billion organic molecules. We report geometries minimal in energy, corresponding harmonic frequencies, dipole moments, polarizabilities, along with energies, enthalpies, and free energies of atomization. All properties were calculated at the B3LYP/6-31G(2df,p) level of quantum chemistry. Furthermore, for the predominant stoichiometry, C7H10O2, there are 6,095 constitutional isomers among the 134k molecules. We report energies, enthalpies, and free energies of atomization at the more accurate G4MP2 level of theory for all of them. As such, this data set provides quantum chemical properties for a relevant, consistent, and comprehensive chemical space of small organic molecules. This database may serve the benchmarking of existing methods, development of new methods, such as hybrid quantum mechanics/machine learning, and systematic identification of structure-property relationships.},
issn={2052-4463},
doi={10.1038/sdata.2014.22},
url={https://doi.org/10.1038/sdata.2014.22}
}
```

## License
MDQM9-nc is licensed under the MIT license and is free and provided as-is.

## Link
[https://github.com/olsson-group/mdqm9-nc-loaders](https://github.com/olsson-group/mdqm9-nc-loaders)
