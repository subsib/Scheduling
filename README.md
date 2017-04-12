# Scheduling
Avancées de mes travaux/recherches en la matière

1. Le dépôt se trouve là : [GitHub](https://github.com/subsib/Scheduling.git)
2. Avancées en matière d'état de l'art ici : [state of art](./refs/statof_arts.md)

Le sujet est :

## Description

_The problem of scheduling multiple tasks on multiple processors and multi-core platforms has been widely studied by the real-time scheduling community in recent years. The traditional (and industry standard) approach to this problem is to split the set of tasks into partitions and schedule each partition on each processor independently. However, this approach leads to wasted processor time due to the impossibility of balancing load perfectly between all partitions. Wasted cpu cycles leads to platform over-provisioning and therefore additional costs for all kinds of devices in which multi-processor scheduling is necessary._

_By contrast, global scheduling techniques allow processes to be preempted on one processor and re-scheduled on another processor. This range of techniques offers potentially greater efficiency than the widely used partitioned techniques. A number of interesting algorithms for the global scheduling problem have been proposed, such as DP-Wrap [1], RUN [2] and U-EDF [3]. However, such algorithms are more complex than traditional ones.
References_

    Greg Levin, Shelby Funk, Caitlin Sadowski, Ian Pye, and Scott Brandt. DP-FAIR: A simple model for understanding optimal multiprocessor scheduling. 22nd Euromicro Conference on Real-Time Systems (ECRTS), pp. 3-13, IEEE, 2010.

    Paul Regnier, George Lima, Ernesto Massa, Greg Levin, and Scott Brandt. RUN: Optimal multiprocessor real-time scheduling via reduction to uniprocessor. 32nd Real-Time Systems Symposium (RTSS), pp. 104-115, IEEE, 2011.

    Geoffrey Nelissen, Vandy Berten, Vincent Nélis, Joël Goossens, and Dragomir Milojevic. U-EDF: An unfair but optimal multiprocessor scheduling algorithm for sporadic tasks. 24th Euromicro Conference on Real-Time Systems (ECRTS), pp. 13-23, IEEE, 2012.

    Antonio Paolillo, Olivier Desenfans, Vladimir Svoboda, Joël Goossens, and Ben Rodriguez. A new configurable and parallel embedded real-time micro-kernel for multi-core platforms. OSPERT, 2015.

    The HIPPEROS Real-Time Operating System: https://www.mpi-sws.org/~bbb/events/ospert15/pdf/ospert15-p25.pdf