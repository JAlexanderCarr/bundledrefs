===============
Graph Databases
===============

What is a Graph Database?
=========================

A graph database is a specialized database platform designed specifically for storing and manipulating graphs.
Graphs are made up of vertices, edges, and properties, which together can represent many different forms
of data.  Due to the various shapes and sizes of graphs, most graph databases are implemented using NoSQL,
which means they are not using a traditional relational database model.  In fact, a major benefit of not
being forced into a structured relational model is that there have become two leading methods for storing
and representing graph databases, the property graph model and resource description framework (RDF).  These
two methods are both very popular among industry leading graph database technologies, proving they both can
be viable when used to represent graph data structures.

Property Graph Model
--------------------

Property graphs model graphs as a set of nodes and relationships, where either nodes or relationships can have
additional attributes, called properties.  This way of representing a set of vertices and edges is straightforward,
as it adheres closely to the visual representation of a traditional graph.  In memory, a property graph is
usually stored using some adaptation of a linked data structure, such that nodes and relationships contain
pointers to each other.

.. image:: /images/property_graph.png

Resource Description Framework Model
------------------------------------

The RDF model is a bit more difficult to grasp than the property graph model.  RDF is a method of
representing highly interconnected data.  Therefore, it can easily be applied to graph databases.  In the
RDF model, data is stored in triples: subject, predicate, and object.  This is very similar to a node
and a relationship in the property graph model.  As triples are created, a network of subjects,
predicates, and objects is formed.  This network looks exactly like a graph, with vertices made up of
subjects and objects and predicates as edges.  The biggest difference between the property graph model
and the RDF model is that the unique identifier in an RDF model is the triple, whereas in the property
graph model, nodes and relationships can be uniquely identified individually.

Popular Graph Databases
=======================

The market for graph databases is large, and there exist many different companies and open source
projects that have developed different graph database products.  In order for my adaptation of a
graph database with Bundled References to be relevant, it must adapt an already common graph
database product.  To find the currently most used graph databases, I consulted a `market research
report conducted by Forrester Research`_.  This report indicated that `Neo4j`_ and `Amazon Web Services
(Amazon Neptune)`_ are the industry leaders, which is unique in the fact that they are polar opposites.
Neo4j is an open source project utilizing a property graph model, whereas Amazon Neptune is a
proprietary graph database implemented using the RDF model.  To learn more, I investigated both of
these technologies.

.. _Neo4j: https://neo4j.com/
.. _Amazon Web Services (Amazon Neptune): https://aws.amazon.com/neptune/
.. _market research report conducted by Forrester Research: https://neo4j.com/whitepapers/forrester-wave-graph-data-platforms/
.. image:: /images/graphdb_market.png
  :align: center

Amazon Neptune
--------------

asd

Neo4j
-----

asd

