

# INIT MOSEL

	source ./init



# RUN MODEL

	./solve mos/model_name



# DATA

Les données sont contenues dans des fichiers *.dat* a l’intérieur du dossier *data*.
Les informations sur les instances sont structurées en trois parties:

1. Infos sur la taille de l'instance; 
2. Infos sur les couples source-destination;
3. Infos sur le demande des produits.

1)
La premier ligne contient les infos sur la taille de l'instance. 
En particulier il y a le valeurs:
n = nombre des nodes;
m = nombre des arcs;
#k = nombre des produit.

2)
A partir de la deuxième ligne il y a les info sur le couples source-destination. 
Pour chaque couple  nous avons une première ligne avec les valeurs 
j = destination;
i = source;
f_ij = coûts fixes;
b_ij = capacité mutuelle;
#k = nombre des produits. 

Après nous avons un ligne pour chaque produit qui contient les valeurs: 
k = indice du produit; 
c_{ij} = coût sur l'arc (i,j);
u_{ij} = capacité sur l'arc (i,j).

3)
Finalement il y a la section sur la demande produit. 
Pour chaque produit nous avons un ligne qui contient les valeurs:
k = indice du produit;
i = indice du node destination;
d^k_i = quantité de produit k demandé par le node i.


Pour mieux comprendre, voir l’exemple “small.dat” et “small.pdf” .

