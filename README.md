# DIR TREE

- *mcndp* : contains mosel models and data for the __MCNDP__ problem

	- *cg*   : column generation approach
	- *raw*  : raw approach
	- *data* : data file folder
		- *easy*  : easy instances
		- *hard*  : hard instances
		- *small* : contains a small instance of the __MCNDP__ problem and its network representation to help understanding the *.dat* file format

	- *lib*  : reusable code folder

- *pdf*   : contains the assignment sheet, the report, the __Mosel User Guide__ and papers on the subject of the  __MCNDP__ problem

- *sp*    : contains mosel models and data for the __SP__ problem


- *test*  : __mosel__ examples

	- *data* : data for the test models
	- *mos*  : test models

- *init*  : quick environment initialization for __mosel__
- *run* : shortcut for model execution



# USAGE

## INIT MOSEL

	source ./init


## RUN MODEL

	./run <model_path> [params..]


## EXAMPLES FOR mcndp/cg AND mcndp/raw

	time ./run mcndp/cg  < mcndp/data/p33.dat

	time ./run mcndp/raw < mcndp/data/p33.dat


## BENCHMARK

	./bench/run <inp> <out> <*alg>

	./bench/run mcndp/data/easy/ bench/data/ mcndp/raw mcndp/cg


## BENCHMARK LATEX TABLES

	./bench/b2l <inp> <precision> <alg1> <alg2>

	./bench/b2l bench/data/ 2 mcndp/raw mcndp/cg



# DATA

Data is contained in *.dat* files inside the *data* directory (for __MCNDP__ see *mcndp/data*).
Information is splitted in 3 parts:

1. Info on the instance size;
2. Info on source-destination pairs;
3. Info on product supply/demand.


## Info on the instance size

The first line contains all the info on the instance size. 
You can read the 3 following values:

- *N* = number of nodes;
- *M* = number of edges;
- *K* = number of products.


## Info on source-destination pairs

Starting from the second line you can read info on source-destination pairs. 
For each of the *M* couples we have a first line with values.

-      *j* = destination;
-      *i* = source;
- *f_{ij}* = fixed costs;
- *u_{ij}* = total capacity;
-      *k* = number of products. 

After that we have a line for each of the *k* products with values

-        *k* = product index; 
- *c^k_{ij}* = cost on edge (*i*,*j*) for product *k*;
- *b^k_{ij}* = bound on edge (*i*,*j*) for product *k*.


## Info on product supply/demand

Finally there is the section on product supply and demand. 
For each product we have a line containing values:

-     *k* = product index;
-     *i* = destination node index;
- *d^k_i* = amount of product *k* supplied (positive value) or demanded (negative value) by node *i*.


__To have a better understanding see example *mcndp/data/small/small.dat* and *mcndp/data/small/small.pdf*.__

__/!\ Error in *mcndp/data/small/small.pdf*, *u* and *b* swapped.__ 

