1. Lecture d'un premier papier "de base" sur le scheduling multiproc : 
[A New Configurable and Parallel Embedded Real-time Micro-Kernel for Multi-core platforms](./refs/ospert15-p25.pdf) 
<details>
  <summary>Commentaires actuels</summary>
   <p>Explique l'implémentation de HIPPEROS. Plusieurs éléments restent flous pour moi, notamment l'usage d'un coeur maître et de coeurs esclaves. Le coeur maître envoie des systèmes à scheduler aux slaves ?! Pas sûre de voir comment ça marche.</p>
   <p>   Inter-Process Communication : IPC</p>
   <p> Il me semble important aussi de comprendre comment fonctionne cet OS pour implémenter un scheduler dessus... </p>
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
  <p>RUN : Reduction to UNiprocessor</p>
  <p></p>
  <p></p>
  <p></p>
  <p></p>
  <p></p>
</details>

5. [Recap on RUN](http://www.math.unipd.it/~tullio/RTS/2016/RUN_Impl.pdf)
<details>
<summary>Présentation de RUN rapide</summary>
<p>Semi-partitionnée</p>
<p>Optimal (pour une sous-classe : implicit-deadline-periodic independant tasks)</p>
</details>


### Note : comprendre ce qu'est le DUAL et PACK