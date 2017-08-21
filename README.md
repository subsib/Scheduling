![schedule](https://www.cloudbooksapp.com/blog/wp-content/uploads/2015/06/Social-Scheduling.jpg)
# Implementing a Dynamic and Global Scheduling Algorithm in a Real-Time OS
## MEMO-F-403 Master Thesis

* État de l'art : [Document](./memoire/memoire.pdf), [sources LaTeX](./memoire/memoire.tex)

* Présentation : [pdf](https://www.overleaf.com/read/xhdfrfzbdcsd)

* __HIPPEROS__ : Actuellement en stage chez [__HIPPEROS__](http://www.hipperos.com/) 
Je prévois d'implémenter __QPS__.

* Divers IDE, outils : 
        * [LaTeX](http://www.latex-project.org/)
        * Zotero pour la bibliographie : [![zotero logo](https://www.zotero.org/static/images/theme/zotero-logo.svg)](https://www.zotero.org/)

        Zotero is the only research tool that automatically senses content in your web browser, 
        allowing you to add it to your personal library with a single click. 
        Whether you're searching for a preprint on arXiv.org, a journal article from JSTOR, 
        a news story from the New York Times, or a book from your university library catalog, 
        Zotero has you covered with support for thousands of sites.

### Description of the subject

>_The problem of scheduling multiple tasks on multiple processors and multi-core platforms has been widely studied by the real-time scheduling community in recent years. The traditional (and industry standard) approach to this problem is to split the set of tasks into partitions and schedule each partition on each processor independently. However, this approach leads to wasted processor time due to the impossibility of balancing load perfectly between all partitions. Wasted cpu cycles leads to platform over-provisioning and therefore additional costs for all kinds of devices in which multi-processor scheduling is necessary._

>_By contrast, global scheduling techniques allow processes to be preempted on one processor and re-scheduled on another processor. This range of techniques offers potentially greater efficiency than the widely used partitioned techniques. A number of interesting algorithms for the global scheduling problem have been proposed, such as DP-Wrap [1], RUN [2] and U-EDF [3]. However, such algorithms are more complex than traditional ones.
References_

> [1] Greg Levin, Shelby Funk, Caitlin Sadowski, Ian Pye, and Scott Brandt. DP-FAIR: A simple model for understanding optimal multiprocessor scheduling. 22nd Euromicro Conference on Real-Time Systems (ECRTS), pp. 3-13, IEEE, 2010.

> [2] Paul Regnier, George Lima, Ernesto Massa, Greg Levin, and Scott Brandt. RUN: Optimal multiprocessor real-time scheduling via reduction to uniprocessor. 32nd Real-Time Systems Symposium (RTSS), pp. 104-115, IEEE, 2011.

> [3] Geoffrey Nelissen, Vandy Berten, Vincent Nélis, Joël Goossens, and Dragomir Milojevic. U-EDF: An unfair but optimal multiprocessor scheduling algorithm for sporadic tasks. 24th Euromicro Conference on Real-Time Systems (ECRTS), pp. 13-23, IEEE, 2012.

> [4] Antonio Paolillo, Olivier Desenfans, Vladimir Svoboda, Joël Goossens, and Ben Rodriguez. A new configurable and parallel embedded real-time micro-kernel for multi-core platforms. OSPERT, 2015.

> [5] The HIPPEROS Real-Time Operating System: https://www.mpi-sws.org/~bbb/events/ospert15/pdf/ospert15-p25.pdf

### Abstract 

>Le problème de l'ordonnancement des tâches dans un système d'exploitation est 
>central : il a un impact majeur dans la gestion des ressources. 
>En effet, même si les applications sont sobres individuellement, dans le cas où 
>l'ordonnanceur n'offre pas une utilisation optimisée des ressources, alors 
>il en résultera un gaspillage tant d'énergie que d'infrastructure.    
>Malgré l'existence d'ordonnanceurs multi-processeurs globaux optimaux décrits 
>dans la littérature scientifique, l'industrie continue à ce jour à préférer des 
>solutions mono-processeurs voire multi-processeurs partitionnées plus simples, 
>éprouvées mais moins efficaces. 
>Ainsi, les conditions, les contraintes, et les 
>effets de la mise en œuvre pratique de tels ordonnanceurs restent mal connus.
>
>Le présent document expose cette problématique, puis propose un état de l'art 
>embrassant l'éventail des ordonnanceurs mono-processeurs, multiprocesseurs 
>partitionnés jusqu'aux multi-processeurs globaux connus.

>Le projet final étant d'implémenter un ordonnanceur au sein du système 
>d'exploitation temps réel __HIPPEROS__, pour analyser ses performances 
>en situation réelle, cet état de l'art permet de motiver le choix de 
>l'ordonnanceur étudié : il s'agira de __QPS__.

### Todo-list

- [x] Rédiger état de l'art (échéance 21/08/2017)
- [x] Corriger état de l'art (il reste des tas de petites erreurs stupides)
- [x] Prépaprer présentation (wip)
- [ ] Présenter état de l'art (25/08/2017)
- [ ] Ajouter un CMake pour compiler mes documents LaTeX
- [ ] Implémenter __QPS__
