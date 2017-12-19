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
 j1 | j1 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | j3 | Argh...
 j2 | j2 | j2 | ..........................................
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


