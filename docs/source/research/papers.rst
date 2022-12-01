======
Papers
======

Bundling Linked Data Structures for Linearizable Range Queries
==============================================================

The Bundled References implementation described in this paper
serve as the inspiration for applying Bundled References to a
graph database.  The goal of my project is to take this
implementation of Bundled References and add additional update
functionality.  Then, using a an augmented Bundled References
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

