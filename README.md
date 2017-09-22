# Partitioning methods for phylogenomic studies of UCE markers 

The accuracy of phylogenetic inferences often depends on choosing an appropriate model of molecular evolution. In Tagliacollo & Lanfear (submitted), we evaluated the performance of two new partitioning methods for phylogenomics studies of UCES, and conclude that automatic selection of partitions through the SWSC-EN method considerably improve model-fit and parameter estimates. This new method is computational efficient and a viable alternative to partitioning large UCE alignments. Below we describe the SWSC-EN method and explains how to run it on personal computers  


**Partitioning method: _Sliding-Window Site Characteristics_** (SWSC-EN)

The SWSC-EN partitioning method uses a sliding-window approach and entropy rates of molecular evolution across DNA sites to automatically select partitions that account for heterogeneity in rates and patterns of molecular evolution within UCE alignments. The SWSC-EN method is graphically summarized below. For further information, see [Tagliacollo & Lanfear, 2018](www.paper.com.br) 

![SWSC-EN](/png/Figure2.png)

The diagram above includes three hypothetical alignments: UCE-1 (green), UCE-2 (yellow), and UCE-3 (blue). The alignments include the same patterns of molecular evolution (i.e. entropies) as seen in the UCE markers. The SWSC-EN algorithm includes three steps. First, it proposes all combinations of three-window models in the alignments. It delimitates windows by locating every conceivable pairs of nucleotide sites in the alignments. Second, it counts nucleotide proportions and estimates site-wise rates of entropies. Third, it calculates the Sum of Squared Errors (SSE) statistics across windows and sum them up to obtain the sum of SSEs for every three data block model. The SWSC-EN algorithm selects the best models by minimizing the squared residuals among three windows. For further information, see [Tagliacollo & Lanfear, 2018](www.paper.com.br)

# Installing and Running Python 3.6.x and SWSC-EN

### Install Python and its dependencies

SWSC-EN needs Python 3.6.x or higher (but not 2.x!) and some additional libraries to run on personal computers. The simplest way to set this up is to install the Anaconda Python distribution, which can be downloaded from here:

[http://continuum.io/downloads](http://continuum.io/downloads)   

Follow the link for the Python 3.6 graphical installer, then open it and follow the prompts. You need to make sure that you have version 4.4.0 or higher of the Anaconda Python distribution. In addition, install the following dependencies:

[collections](https://docs.python.org/3/library/collections.html)
[io](https://docs.python.org/3/library/io.html)
[itertools](https://docs.python.org/3/library/itertools.html) 
[os](https://docs.python.org/3/library/os.html)
[subprocess](https://docs.python.org/3/library/subprocess.html)
[time](https://docs.python.org/3/library/time.html) 

If you don’t want to install with Anaconda, you can install Python 3.6.x and then install the following dependencies:

[Bio](https://pypi.python.org/pypi/biopython)
[collections](https://docs.python.org/3/library/collections.html)
[io](https://docs.python.org/3/library/io.html) 
[itertools](https://docs.python.org/3/library/itertools.html) 
[math](https://docs.python.org/3/library/math.html) 
[numpy](https://pypi.python.org/pypi/numpy)
[os](https://docs.python.org/3/library/os.html)
[pathlib2](https://pypi.python.org/pypi/pathlib2/) 
[subprocess](https://docs.python.org/3/library/subprocess.html)
[time](https://docs.python.org/3/library/time.html)
[tqdm](https://pypi.python.org/pypi/tqdm)


### Installing SWSC-EN

To install SWSC-EN, 

	1. Download the latest version of SWSC-EN from [here](https://github.com/Tagliacollo/PFinderUCE-SWSC-EN/blob/master/py_script.zip)
	2. Double-click the .zip file, and it will automatically unzip. You will get a folder called something like ‘PFinderUCE-SWSC-EN’
	3. Move it to wherever you want to store PFinderUCE-SWSC-EN (e.g. in /Applications)
	

### Running SWSC-EN

The instructions below describe how to run the `example/example_dataset.nex` using SWSC-EN method. This is a nexus DNA alignment with 15 concatenated UCEs  

	1. Open Terminal (on most Macs, this is found in Applications/Utilities) 
	2. In the Terminal, you need to tell the computer where to find Python, SWSC-EN, and your input files. The easiest way to do this is as follows:
		a. Type “python“ followed by a space (remember, it needs to be python 3.6.x or higher)
		b. Drag and drop the “analysis.py” file (which is in the PFinderUCE-SWSC-EN folder you just unzipped) onto the command prompt. The path to will be added automatically.
		c. Type another space
		d. Drag and drop the blue `example_dataset/example_dataset.nex` folder (in the PFinderUCE-SWSC-EN folder) onto the command prompt
	3. Hit Enter/Return to run PFinderUCE-SWSC-EN



## Input File
SWSC-EN needs oonly a single input file, which is a concatenated nexus alignment (.nex) comprised of UCE markers and including charsets with the locations of the UCEs (example input is in the `/example_dataset` folder of this repository) .


## Output Files

All of the output is contained in a folder called `PFinderUCE_output` which appears within the folder created to store SWSC-EN (e.g. FinderUCE-SWSC-EN) . There are two output, which are a PartitionFinder 2 configuration file (.cfg) to be used as the input file for [PartitionFinder 2](https://academic.oup.com/mbe/article/34/3/772/2738784/PartitionFinder-2-New-Methods-for-Selecting), and a csv file (.csv) with values of entropy (SWSC-EN) for each site of the UCEs (example outputs are in the `/PFinderUCE_output/example_dataset` folder of this repository). 


