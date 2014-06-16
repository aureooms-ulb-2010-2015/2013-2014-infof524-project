# DIR TREE

- *data*  : contains instances of the __MCNDP__ problem

- *mos*   : contains mosel models for the __MCNDP__ problem

- *pdf*   : contains the assignment sheet, the __Mosel User Guide__ and papers on the subject of the  __MCNDP__ problem

- *small* : contains a small instance of the __MCNDP__ problem and its network representation to help understanding the *.dat* file format

- *test*  : __mosel__ examples

	- *data* : data for the test models
	- *mos*  : test models

- *init*  : quick environment initialization for __mosel__
- *run* : shortcut for model execution


# USAGE

## INIT MOSEL

	source ./init


## RUN MODEL

	./run mos/model_name [params..]



# DATA

Data are contained in *.dat* files inside the *data* directory.
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


__To have a better understanding see example *small/small.dat* and *small/small.pdf*.__

__/!\ Error in *small/small.pdf*, *u* and *b* swapped.__ 

