# Résumé recherche sur l'état de l'art

1. Lecture d'un premier papier "de base" sur le scheduling multiproc : 
[A New Configurable and Parallel Embedded Real-time Micro-Kernel for Multi-core platforms](./refs/ospert15-p25.pdf) 
<details>
  <summary>Commentaires actuels</summary>
   <p>Explique l'implémentation de HIPPEROS. Plusieurs éléments restent flous pour moi, notamment l'usage d'un coeur maître et de coeurs esclaves. Le coeur maître envoie des systèmes à scheduler aux slaves ?! Pas sûre de voir comment ça marche.</p>
   <p>   Inter-Process Communication : IPC</p>
   <p> Il me semble important aussi de comprendre comment fonctionne cet OS pour implémenter un scheduler dessus... </p>
   <p>(cette question m'a été confirmée par J. Goossens, ça semble important, donc. Noter compte-rendu après réunion chez HIPPEROS.</p>
</details>

2. Le papier 2 renvoie à deux standards:
    * [ARINC 653](https://fr.wikipedia.org/wiki/ARINC_653):
    * [AUTOSAR](https://fr.wikipedia.org/wiki/AUTOSAR)
    * On apprend que malgré le fait qu'ils soient très souvent utilisés, ce ne sont pas les plus efficaces.
3. [U-EDF: An Unfair but Optimal Multiprocessor Scheduling Algorithm for Sporadic Tasks](https://github.com/subsib/Scheduling/blob/master/refs/U-EDF-ECRTS2012.pdf)
<details>
  <summary>Commentaires sur la lecture</summary>
   <p>u-edf est optimal en global MAIS pas fair.</p>
   <p>Deux types de généralisation EDF, un horizontal, un vertical. Il faut bien lire les exemples. Ils montrent des comportements très différents.</p>
   <p>Démonstrations d'optimalité, lemmes, etc.</p>
   <p>Accessoirement, comparaison de performances. RUN a l'air plutôt efficace à première vue.</p>
</details>

4. [Multiprocessor scheduling by reduction to uniprocessor(RUN): an original optimal approach](https://github.com/subsib/Scheduling/blob/master/refs/RUN-ExtVers.pdf)
<details>
<summary>Commentaires sur la lecture</summary>
  <p>
    RUN : Reduction to UNiprocessor
  </p>
  <p>
    m >= 1 procs identiques + rate identiques, global scheduling = 1 seul dispatcher,
    (rien de nouveau avec realease time (r) et deadline (d)), 
    Les tâches ne sont pas "périodiques" mais on pose qu'elles sont "fixed rate", 
    le "rate" est la fraction de temps d'utilisation par un proc (ça revient pas un peu au même ?)
    Du coup, forcément, le rate <= 1, sinon ça rentre pas sur un proc.
  </p>
  <p>
    À retenir : rho est le taux, un job va nécessiter <b>rho(d-r)</b> execution time.
  </p>
  <h3>Dual</h3>
  <p>
    On sélectionne tau*, un ensemble de tâches qui ont la même deadline (ou auxquelles on attribue la même, pas sûre),  
  on leur attribut un temps d'exec (nb_proc - 1) (ou nb de tâches, suis pas sûre), en complément.<br>
  C'est normal, car on va finalement attribuer les procs aux tâches complémentaires dans le primal.<br>
  On reprend : on calcule le dual, et on schedule le "vrai" set qui est le primal, sauf le job géré par le dual. 
  Ça permet de prioritiser. Voir pour ça <it>Dual Scheduling Equivalence<it>. 
  Donc en gros, Tau* représente les idle de Tau.
  </p>
  <p> 
    Dans l'exemple présenté, c'est avantageux, car on réduit le nombre de procs.
    Cela dit, avec un primal qui aurait des high rate, on gagnerait pas vraiment. 
    (Question : pourquoi ?... ) Pour éviter ça, on met des low rate tasks avec des high rate, 
    et on créé des <it>serveurs</it> qui gèrent moins de mrocs pour les <it>clients</it>. (??)
  </p>
  <p>Ça, c'est en gros la partie offline de RUN, je crois. 
  En gros, on procède à une réduction à un uniproc pour diminuer par le dual le nb de procs au total (??).
  La partie online, c'est en gros EDF. 
  </p>
  <p>
    Ensuite, il y a un tas de définitions, que je connais, mais qui se trouvent vers les pages 6-7, et qui serviront sans doute
    pour l'état de l'art.
  </p>
  <h3>Servers</h3>
  <p>
    RUN utilise des agrégats de tâches dan des serveurs.
    Dans cette partie, on explique en quoi consiste ce truc de "serveur".
  </p>
  <p>
    En fait, dans un serveur, y a une seule tâche "virtuelle". Comme c'est one-to-one, les 
    concepts sont interchangeables.
    Le packing se fait hors ligne (offline) et reste statique durant l'exécution.
    Execution requirement est en fait l'équivalent du execution time, 
  rho(S)(ri+1 - ri), quoi.
  </p>
  <p>
    L'intérêt de prouver qu'EDF est optimal revêt son importance ici, puisque si on ne l'utilise 
    pas, on n'a pas d'optimalité pour scheduler les serveurs. Du coup, EDF, du coup, preuve EDF.
  </p>
  <p>
    L'intérêt majeur de RUN est de réduire le nb de préemptions. Comme habituellement, on pose que le temps de 
    préemption est négligeable, on ne les compte pas mais en pratique, c'est faux.
    RUN réduit ça, ça a l'air de s'en ressentir sur le résultat.

    Mais attention à un détail d'importance : on considère une certaine classe de tâches.
  </p>
  <p>
    
  </p>

<h3>Question</h3>
<p>
  À ce stade, une des questions que je me pose, c'est : est-ce que c'est très courant, des tâches qui partagent la même deadline ?
  Parce que si ça n'apporte rien... ?! de faire des sous-ensembles...
</p>
</details>

5. [Recap on RUN](http://www.math.unipd.it/~tullio/RTS/2016/RUN_Impl.pdf)
<details>
<summary>Présentation de RUN rapide</summary>
<p>Semi-partitionnée</p>
<p>Optimal (pour une sous-classe : implicit-deadline-periodic independant tasks)</p>
</details>

TODO : ajouter les références téléchargées

### Note : comprendre ce qu'est le DUAL et PACK