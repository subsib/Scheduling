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

 j2 | j2 | j2 | .. | .. | .. | .. | .. | .. | .. | ________
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

	> The budget bdg_i,j(t1 ,t2) denotes the total amount of time reserved for the task τi on
	processor πj in the interval extending from t 1 to t 2 (with t  ≥ di(t1)). It includes the
	allotment allot i, j (t 1 ) for the currently active job of τ i at time t 1 and the reservation
	res i, j (d i (t 1 ),t 2 ) for the execution of the future jobs of τ i that might potentially arrive
	within [d i (t 1 ),t 2 ), i.e.,

En français dans le texte, ça signifie que le budget représente la somme totale 
de temps réservé pour le job i sur le processeur j durant l'intervalle 
qui va de t1 à t2, (où t2 est après ou égal à la deadline de i)
Ça inclut donc l'allotment du job i + les réservations.
J'imagine qu'on s'attent à ce que le budget soit >= à exec_time de la tâche i.

	> bdg_i,j_(t1,t2) = allot_i,j(t1) + res_i,j(di(t1),t2)

Donc c'est qoi res_i,J(di(t1), t2) maintenant ?
-----------------------------------------------

futur job reservation (p. 194)

	> The future jobs reservation res_i,j(t1,t2) computed at time t for a task τi, 
	denotes the amount of time reserved on processor π j for the execution of the 
	future jobs of τ i that might be released within [t1 ,t) where d_i(t) ≤ t1 < t2. 
	This reservation is defined as follows:

	> resi,j(t1,t2) = u_i,j(t)×(t2 − t1)

càd le facteur d'utilisation * le temps compris entre t1 et t2.

u, c'est le facteur d'utilisation.
Il se calcule comme suit : 

	> The u_i,j(t) value denotes the proportion of the utilization factor of τi 
	that will be reserved on processor πj for the scheduling of future jobs of 
	τi. This value is obtained by aligning blocs of size U_i in an increasing 
	current deadline di(t) order, and then, by cutting this alignment in boxes 
	of size 1

En gros, faut appliquer bêtement la formule :
	
	> [Sigma Ux for x € tâches dans le higherPrioritySetTask + tâche courante] - [Sigma Ux for x € tâches dans le higherPrioritySetTask]
	Sachant que [] est un opérateur qui n'a pas de nom et qui se calcule comme suit :
	[x]a_b = max{a, min{b, x}}
	et faut remarquer que x est borné. Si x < a, x = a, si x > b, x = b.

