======
Papers
======

Bundling Linked Data Structures for Linearizable Range Queries
==============================================================

The Bundled References implementation described in this paper
serve as the inspiration for applying Bundled References to a
graph database.  The goal of my project is to take this
implementation of Bundled References and add additional update
functionality.  Then, using an augmented Bundled References
data structure, adapt a graph database that uses linked data
structures to use Bundled References instead.  The goal is for
this adaptation to increase the performance of range queries
on graph database nodes.  `Bundling Linked Data Structures for
Linearizable Range Queries`_ was authored by Jacob Nelson-Slivon,
Ahmed Hassan, and Roberto Palmieri.

.. _Bundling Linked Data Structures for Linearizable Range Queries: https://arxiv.org/abs/2201.00874

Abstract
--------

We present bundled references, a new building block to provide
linearizable range query operations for highly concurrent
lock-based linked data structures. Bundled references
allow range queries to traverse a path through the data
structure that is consistent with the target atomic snapshot. We
demonstrate our technique with three data structures: a
linked list, skip list, and a binary search tree. Our evaluation
reveals that in mixed workloads, our design can improve
upon the state-of-the-art techniques by 1.2x-1.8x for a skip
list and 1.3x-3.7x for a binary search tree. We also integrate
our bundled data structure into the DBx1000 in-memory
database, yielding up to 40% gain over the same competitors.

Black-box Concurrent Data Structures for NUMA Architectures
===========================================================

Besides applying Bundled References to graph databases, there
are other ways of achieving higher performance.  One of those ways is
through taking advantage of NUMA architectures.  The reason for
reviewing this paper was to create a better understanding
of how data structures could be adapted to take full
advantage of NUMA machines.  `Black-box Concurrent
Data Structures for NUMA Architectures`_ was authored by Irina Calciu,
Siddhartha Sen, Mahesh Balakrishnan, and Marcos K. Aguilera.

.. _Black-box Concurrent Data Structures for NUMA Architectures: https://dl.acm.org/doi/pdf/10.1145/3093336.3037721

Abstract
--------

High-performance servers are Non-Uniform Memory Access (NUMA) machines.
To fully leverage these machines, programmers need efficient concurrent
data structures that are aware of the NUMA performance artifacts. We
propose Node Replication (NR), a black-box approach to obtaining such
data structures. NR takes an arbitrary sequential data structure and
automatically transforms it into a NUMA-aware concurrent data structure
satisfying linearizability. Using NR requires no expertise in concurrent
data structure design, and the result is free of concurrency bugs. NR
draws ideas from two disciplines: shared-memory algorithms and distributed
systems. Briefly, NR implements a NUMA-aware shared log, and then uses the
log to replicate data structures consistently across NUMA nodes. NR is best
suited for contended data structures, where it can outperform lock-free
algorithms by 3.1x, and lock-based solutions by 30x. To show the benefits
of NR to a real application, we apply NR to the data structures of Redis,
an in-memory storage system. The result outperforms other methods by up to
14x. The cost of NR is additional memory for its log and replicas.

NUMASK: High Performance Scalable Skip List for NUMA
====================================================

To dive a bit deeper on NUMA performance improvements, I reviewed a paper
that used NUMA to speed up implementation of a skip list, which is a linked
data structure that could also be adapted for Bundled References.  Therefore,
my goal was to consider the benefits of using Bundled References and NUMA aware
linked data structures in graph databases.  `NUMASK: High Performance Scalable
Skip List for NUMA <https://drops.dagstuhl.de/opus/volltexte/2018/9807/pdf/LIPIcs-DISC-2018-18.pdf>`_
was authored by Henry Daly, Ahmed Hassan, Michael F. Spear, and Roberto Palmieri.

Abstract
--------

This paper presents NUMASK, a skip list data structure specifically designed to exploit the
characteristics of Non-Uniform Memory Access (NUMA) architectures to improve performance.
NUMASK deploys an architecture around a concurrent skip list so that all metadata accesses
(e.g., traversals of the skip list index levels) read and write memory blocks allocated in the NUMA
zone where the thread is executing. To the best of our knowledge, NUMASK is the first NUMA-
aware skip list design that goes beyond merely limiting the performance penalties introduced by
NUMA, and leverages the NUMA architecture to outperform state-of-the-art concurrent high-
performance implementations. We tested NUMASK on a four-socket server. Its performance
scales for both read-intensive and write-intensive workloads (tested up to 160 threads). In write-
intensive workload, NUMASK shows speedups over competitors in the range of 2x to 16x.

Harnessing Epoch-based Reclamation for Efficient Range Queries
==============================================================

Bundled References uses an epoch based global timestamp to order
references, which greatly speeds up range queries.  A competing
linked data structure described in this paper also utilizes an
epoch based global timestamp to speed up range queries as well.
I reviewed this paper in order to get a better understanding of
how this implementation differs from Bundled References, and
consider if there are any graph database applications for this
linked data structure.  `Harnessing Epoch-based Reclamation for
Efficient Range Queries`_ was authored by Maya Arbel-Raviv and
Trevor Brown.

.. _Harnessing Epoch-based Reclamation for Efficient Range Queries: https://dl.acm.org/doi/pdf/10.1145/3200691.3178489

Abstract
--------

Concurrent sets with range query operations are highly desirable
in applications such as in-memory databases. However, few set
implementations offer range queries. Known techniques for augmenting
data structures with range queries (or operations that can be used
to build range queries) have numerous problems that limit their
usefulness. For example, they impose high overhead or rely heavily
on garbage collection. In this work, we show how to augment data
structures with highly efficient range queries, without relying
on garbage collection. We identify a property of epoch-based memory
reclamation algorithms that makes them ideal for implementing range
queries, and produce three algorithms, which use locks, transactional
memory and lock-free techniques, respectively. Our algorithms are
applicable to more data structures than previous work, and are
shown to be highly efficient on a large scale Intel system.

