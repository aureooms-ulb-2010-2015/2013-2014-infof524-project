# 1

>    1. Comment génère-t-on une base initiale pour le problème? Quels chemins
>    doit-on choisir?

Vous pouvez soit ajouter un arc artificiel avec un très grand coût pour
chaque commodité et l'utiliser comme chemin initial, ou bien calculer un
chemin de départ, par exemple avec un algorithme de plus court chemin.

>    2. Dans le livre *Network Flows Theory : Algorithms and Applications *les
>    coûts fixes sont inexistants, comment doit-on les intégrer?

Les coûts fixes sont liés aux variables d'installation des arcs:
celles-ci restent telles quelles dans le problème mère, donc elles
n'interfèrent pas avec la génération de colonne.

>    3. Dans le livre *Network Flows Theory : Algorithms and Applications *les
>    bornes supplémentaires par produit par arc sont inexistantes, comment
>    doit-on les intégrer?
>
>    4. On ne voit pas bien de quelles variables de la modélisation en flot
>    viennent les contraintes de types conditions d'optimalité du plus court
>    chemin.

Je répons à 3 et 4 ensemble: il faut remplacer les variables x par des
variables de chemin, et une fois que vous avez fait ça, vous pouvez
utiliser la même technique que dans le livre pour en déduire la formule
des coûts réduits.

>    5. On doit générer des chemins reliant pour chaque produit k sa source à
>    sa destination au fur et à mesure en résolvant k problèmes de plus court
>    chemin. Mais que doit-on faire avec ces k plus cours chemins, les intégrer
>    un par un dans la base ou ne prendre que le meilleur (pour autant que sont
>    coût réduit soit non nul)?

Le plus efficace est de les ajouter toutes au modéle.


# 2

> 1) Pourquoi les coûts fixes n'interfèrent-ils pas avec la génération
> des variables chemin à ajouter ? Nous pourrions en calculant des plus
> court chemin avoir des couts fixes sur ces chemins monstrueux, alors
> que d'autres chemins avec un cout unitaire plus important auraient des
> couts fixes qui compenseraient ce cout unitaire supérieur. Les couts
> fixes doivent-ils donc jouer dans le critère d'arrêt ?

Les coûts fixes sont implicitements pris en charge via les variables
duales, mais ils n'interviennent pas dans le pricing.

> 2) Comment choisir "efficacement" les variables chemin à ajouter ?
> Pour le moment nous en sommes à penser qu'il faut trouver des "plus
> court" chemin entre chaque offre et chaque demande, plus court en le
> sens où on additionne le coût d'ouverture du chemin (donc la somme des
> coûts d'ouverture des arêtes) + le coût unitaire pour parcourir ce
> chemin multiplié par la demande du produit correspondant. Deux
> problèmes se posent : est ce que c'est efficace (c'st à dire va-t-on
> trouver "rapidement" les chemins que la solution optimale utilise) et

Vous devez trouver un chemin de coût réduit négatif, il faut donc que
vous écriviez ce coût réduit pour voir quel est le problème de + courts
chemins correspondants (voir le chapitre de Ahuja et al.)

> 2') comment faire en sorte que la recherche d'un tel chemin ne donne
> pas un chemin déjà ajouté dans la liste des variables ? Une idée
> brutale serait de brancher (il faut au moins une arête différente avec
> chaque chemin déjà existant) mais bon... (pour l'ajout de la 4e
> variable chemin d'une commodité, il faut brancher sur les arêtes de
> chaque chemin déjà existant pour dire "au moins une différence avec
> chaque chemin", ça devient vite gros)

Le critère d'arrêt est que tous les coûts réduit sont positifs ou
nuls. Quand on résoud le master, par les propriétés d'optimalité une
variable déjà générée a un coût réduit positif ou nul, donc on a la
certitude qu'elle ne sera pas générée une seconde fois.

> 3) Comment trouver un critère d'arrêt ? Nous sommes parti sur
> l'utilisation d'arcs factices à gros couts comme première base, et une
> première idée de critère serait d'arrêter lorsque plus aucun de ces
> arcs-chemins n'est utilisé, mais cela semble fort peu robuste. Comment
> utiliser le problème dual ici comme critère d'arrêt ? En ajoutant les
> contraintes liées aux variables ajoutées ?

Voir ci-dessus.
