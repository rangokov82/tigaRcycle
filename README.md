![](https://img.shields.io/badge/language-R_and_python-orange.svg) ![version](https://img.shields.io/badge/GiHub_version-1.1.0-519dd9) ![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/viktormiok/tigaRcycle) ![GitHub issues](https://img.shields.io/github/issues/viktormiok/tigaRcycle)

![dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-orange)  	![commit](https://img.shields.io/github/last-commit/viktormiok/tigaRcycle) ![GitHub](https://img.shields.io/github/license/viktormiok/tigaRcycle)

[![Edit with Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/viktormiok/tigaRcycle) 



# tigaRcycle

- [Overview](#overview)
- [Installation](#installation)
- [Docker](#docker)
- [Data](#data)
- [Tutorials](#tutorials)
- [License](#license)
- [References](#references)



## Overview

The R-package __`tigaRcycle`__ performs integrative detection of circadian signals in time series omics data, both sequencing counts RNAseq and continuous microarray data. The package offers a broad range of functions for visualisation of rithmic signals and comparison between different diets and time points. Also, pathway enrichment analysis and visualisation using different repositories can be performed comparing different conditions.

**Note:** if you have a choice to use either Windows or Unix/Linux, opt for the latter. __`tigaRcycle`__ runs more efficiently under Unix/Linux than under Windows. NOTE:  when running __`tigaRcycle`__ you may see *** WARNINGS ***  from [__`INLA`__](https://www.r-inla.org/) (e.g. on eigenvalues, or on convergence, or even something like 18500 Aborted...). They can currently not be surpressed, because they are produced by C-code. Please ignore them. 

![image](https://user-images.githubusercontent.com/22052679/150277203-646d6d85-482a-44ab-8e30-c20d260179fe.png)


## Installation

The package __`tigaRcycle`__ depends on [__`tigaR`__](https://github.com/viktormiok/tigaR) and on [R >= 3.0.0](https://cran.r-project.org/) and is available from GitHub. This requires the package [__`devtools`__](https://cran.r-project.org/web/packages/devtools/index.html):

``` r
devtools::install_github("viktormiok/tigaRcycle", build_vignettes=TRUE)
```

Please restart R before loading the package and its documentation:

``` r
library(tigaRcycle)
utils::help(tigaRcycle)
utils::vignette("tigaRcycle")
```

## Docker

If your system configuration is making it difficult to install __`tigaRcycle`__ natively, an alternative way to get __`tigaRcycle`__ running is through a docker container.

**Note:** On Mac OS X, Docker Machine has Memory and CPU limits. To control it, please check instructions either for [CLI](https://stackoverflow.com/questions/32834082/how-to-increase-docker-machine-memory-mac/32834453#32834453) or for [Docker Desktop](https://docs.docker.com/docker-for-mac/#advanced).

For building Docker image from the Dockerfile, download the [Dockerfile](https://github.com/viktormiok/tigaRcycle/blob/main/Dockerfile) (available in this repo) and run to following command to build it:
```
docker build -t tigaRcycle .
```
This will create a __`tigaRcycle`__ docker image on your system (please be patient, as the build could take approximately 30-50 minutes to finish).
You can then run it using the following command:
```
docker run -d -p 8787:8787 -e PASSWORD=pass --name tigaRcycle -it tigaRcycle
```

## Data
Data required for identifying cicardian rithms in transcriptomics data have been deposited in the National Center for Biotechnology Information Gene Expression Omnibus (GEO) and are accessible through the GEO Series accession numbers:
| Data type     | GEO number |
| ------------- | ------------- |
| mRNA Arrays  | [__`GSE138079`__](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE138079) |
| RNA-Seq      | Not available yet |


In order to access one of the data set for instance GSE138079 you need to run the code bellow. Unpacking the data requires tar and gunzip, which should already be available on most systems.

```
cd ../  #To get to the main github repo folder
mkdir -p data/tigaRcycle_data_analysis/
cd data/tigaRcycle_data_analysis/
wget ftp://ftp.ncbi.nlm.nih.gov/geo/series/GSE13nnn/GSE138079/suppl/GSE138079_RAW.tar
mkdir GSE138079_RAW
tar -C GSE138079_RAW -xvf GSE138079_RAW.tar
gunzip GSE138079_RAW/*_Regional_*
```

## Tutorials

Please see the following tutorials for detailed examples of how to use __`tigaRcycle`__: 

### tigaRcycle walkthrough:
* [Notebook](https://github.com/viktormiok/tigaRcycle/blob/main/notebooks/circadian_analysis_v2.ipynb)

## License

__`tigaRcycle`__ is distributed under the MIT license. Please read the license before using __`tigaRcycle`__, which it is distributed in the `LICENSE` file.


## References

Publication related to __`tigaRcycle`__ include:

- Miok, V., Yi, C., Gonzalez Garcia, I., Lutter, D., García-Cáceres, C.,"Circadian transcriptomics of different brain regions reveals system-wide coordination and communication between clocks", *In preparation*

- Miok, V., Wilting, S.M., Van de Wiel, M.A., Jaspers, A., van Noort, P.I., Brakenhoff, R.H., Snijders, P.J.F., Steenbergen, R.D.M., Van Wieringen, W.N. (2014), "[tigaR: integrative significance analysis of temporal differential gene expression induced by genomic abnormalities](https://doi.org/10.1186/1471-2105-15-327)", *BMC Bioinformatics*, 15, 327. 

Please cite the relevant publication if you use __`tigaRcycle`__.
