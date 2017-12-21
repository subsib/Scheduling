p. 191, thèse Nelissen :

description U-EDF en deux temps.

2/6
3/6
9/10

On décide de la priorité sur EDF généralisé horizontalement.

version verticale :
deadlines : j1 : 6, j2 : 3-6, j3: 10. égalité j1, j2, arbitrairement, on décide j1

  1    2    3    4    5    6    7    8   9    10
------------------------------------------------------------
 j1 | j1 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | X Argh...
 j2 | j2 | j2 | .. | .. | .. | .. | .. | .. | .. | _______
 -----------------------------------------------------------

 La version verticale ne marche pas avec cet exemple.

 Maintenant, prenons la version horizontale :

  1    2    3    4    5    6    7    8   9    10
------------------------------------------------------------
 j1 | j1 | j2 | j2 | j2 | .. | .. | .. | .. | .. |
 j3 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | j3 |
 -----------------------------------------------------------
 En résumé, on essaie de mettre séquentiellement les tâches prioritaires sur le premier CPU 
 jusqu'à ce qu'il n'y ait plus de place, et on descend. Comme ça, 
 on s'assure que les jobs les plus prioritaires seront traités.

En résumé, U-EDF fait ça :
1. Pré.schedule avec EDF horizontal
> histoire de réservation ?! Un peu comme DP-Wrap ou EKG, zone un peu obscure (see p.197)
En fait, il s'agit de réserver une portion de capacité de calcul sur le système, 
afin de s'assurer qu'il y ait une chance d'avoir la place pour le job.
2. Allot, EDF-D, D comme Delay : see p.198

L'appel à l'ago se fait sur event, pas à chaque instant.
Donc quand un job est terminé, ou arrive 


Définitions : 

budget : 

Le calcul du budget dépend de hp, qui n'est pas HyperPeriod, mais 
Higher Priority task set : 

see p.184
	> hp_i = {tau_j : d_j(t) > 0 and d_j(t) < d_i(t) ou d_j(t) = d_ i(t) AND j < i}

En français, ça veut dire :
higherPrioritySetTask de la tâche i = l'ensemble de tâches tau_j telles que y a une deadline, 
que la deadline est avant celle de i, 
ou alors que la deadline de j soit égale à di et que j < i.

En gros, c'est juste l'ensemble des tâches avec priorité plus élevée... 

Sur HIPPEROS, ça correspond aux tâches avant la tâche i dans le HEAP.

Mais c'est QUOI le budget ?
---------------------------

	> bdg_i,j_(t1,t2) = allot_i,j(t1) + res_i,j(di(t1),t2)

Donc c'est qoi res_i,J(di(t1), t2) maintenant ?
-----------------------------------------------