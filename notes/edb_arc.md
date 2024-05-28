EDB Postgres, from EnterpriseDB, is a high-performance relational database management system (RDBMS) that's built on the open-source PostgreSQL platform.  It offers a variety of deployment architectures to suit different needs, from single-server deployments to complex distributed systems.

Here are some of the common EDB Postgres architectures:

* **Single Server:** This is the simplest architecture, with just one database server instance. It's suitable for small deployments or development environments.
[Image of Single Server EDB Postgres architecture]
* **Multi-Node with Synchronous Replication:** This architecture uses two or more database server instances with synchronous replication between them. This provides high availability, as the primary node can be quickly replaced with a standby in the event of a failure.
[Image of Multi-Node with Synchronous Replication EDB Postgres architecture]
* **Multi-Node with Asynchronous Replication:** This architecture is similar to the multi-node with synchronous replication architecture, but uses asynchronous replication. This means that changes are not immediately replicated to all nodes, but are instead replicated at a later time. This can provide better performance, but can also lead to data loss if a failure occurs before the changes are replicated.
[Image of Multi-Node with Asynchronous Replication EDB Postgres architecture]
* **EDB Postgres Distributed (PGD):**  This is a comprehensive suite of software that allows you to build and manage distributed PostgreSQL clusters. It provides features for high availability, scalability, and disaster recovery.
[Image of EDB Postgres Distributed (PGD) architecture]

The best architecture for your needs will depend on your specific requirements, such as your uptime requirements, performance needs, and budget. EDB offers a variety of reference architectures that you can use as a starting point for designing your own deployment. You can find more information about EDB Postgres architectures on the EDB website [https://www.enterprisedb.com/blog/edb-reference-architectures](https://www.enterprisedb.com/blog/edb-reference-architectures).

