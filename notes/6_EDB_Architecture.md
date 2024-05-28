# EDB Architecture

EnterpriseDB (EDB) extends PostgreSQL with additional features, tools, and support tailored for enterprise-level applications. EDB Postgres Advanced Server (EPAS) builds on the core PostgreSQL architecture and includes proprietary enhancements to meet the needs of businesses requiring high performance, security, and compatibility with other database systems, such as Oracle.

## Overview

EDB Postgres Advanced Server retains the fundamental architecture of PostgreSQL while adding enhancements. The main components include:

- Process Structure
- Memory Structure
- Storage Structure
- Query Processing
- Concurrency Control
- Replication and High Availability
- Additional EDB Features

## Process Structure

### 1. Postmaster Process
- **Role**: The central controller process that handles database startup, shutdown, and connection management.
- **Responsibilities**: Manages shared memory, spawns new server processes for client connections, and oversees background processes.

### 2. Server Processes (Backends)
- **Role**: Each client connection is managed by a separate server process.
- **Responsibilities**: Executes SQL commands, manages transactions, and interacts with data storage.

### 3. Background Processes
- **Autovacuum**: Performs automatic vacuuming to reclaim storage and update statistics.
- **WAL Writer**: Writes Write-Ahead Logging (WAL) records to disk.
- **Checkpointer**: Writes data from shared memory to disk at regular intervals to ensure data durability.
- **Background Writer**: Maintains the buffer cache by writing dirty buffers to disk.
- **Archiver**: Archives WAL files for backup and recovery.
- **Statistics Collector**: Gathers and stores performance statistics for queries and activities.

## Memory Structure

### 1. Shared Memory
- **Role**: Shared among all server processes for critical data structures.
- **Components**:
  - **Shared Buffers**: Caches database pages to reduce disk I/O.
  - **WAL Buffers**: Temporary storage for WAL records.
  - **Lock Table**: Manages locks to ensure data consistency.

### 2. Local Memory
- **Role**: Used by individual server processes.
- **Components**:
  - **Work Mem**: Allocated for sorting operations and hash tables.
  - **Maintenance Work Mem**: Used for maintenance tasks like vacuuming.
  - **Temp Buffers**: Used for temporary tables and query results.

## Storage Structure

### 1. Data Files
- **Role**: Store the actual data in tables, indexes, and TOAST (The Oversized-Attribute Storage Technique) tables for large objects.

### 2. Write-Ahead Logging (WAL)
- **Role**: Ensures data durability by recording changes before they are applied.
- **Components**:
  - **WAL Segments**: Log files that store changes.
  - **Checkpoint Records**: Indicate consistent states for recovery.

### 3. System Catalogs
- **Role**: Store metadata about database objects.
- **Components**:
  - **pg_class**: Information about tables and indexes.
  - **pg_attribute**: Information about table columns.
  - **pg_proc**: Information about functions and procedures.

## Query Processing

### 1. Parsing
- **Role**: Converts SQL queries into a parse tree.
- **Component**: Parser analyzes the query syntax.

### 2. Planning/Optimization
- **Role**: Determines the most efficient execution plan.
- **Component**: Planner/Optimizer selects the best plan based on cost estimation.

### 3. Execution
- **Role**: Executes the selected plan.
- **Component**: Executor retrieves and processes data according to the plan.

## Concurrency Control

### 1. Multi-Version Concurrency Control (MVCC)
- **Role**: Allows multiple transactions without conflicts.
- **Components**:
  - **Tuple Versions**: Multiple versions of rows handle concurrent updates.
  - **Transaction IDs**: Track transaction states.

### 2. Locking
- **Role**: Ensures data integrity.
- **Components**:
  - **Row-Level Locks**: Lock individual rows.
  - **Table-Level Locks**: Lock entire tables for specific operations.

## Replication and High Availability

### 1. Streaming Replication
- **Role**: Real-time replication to standby servers.
- **Components**:
  - **Primary Server**: Sends WAL records.
  - **Standby Server**: Applies WAL records.

### 2. Logical Replication
- **Role**: Selective table replication.
- **Components**:
  - **Publisher**: Sends data changes.
  - **Subscriber**: Receives and applies changes.

### 3. Backup and Recovery
- **Role**: Data durability and recovery.
- **Components**:
  - **Base Backups**: Full database copies.
  - **WAL Archiving**: Continuous WAL file archiving.

## Additional EDB Features

### 1. Oracle Compatibility
- **Role**: Eases migration from Oracle to EDB.
- **Components**:
  - **PL/SQL Support**: Compatible with Oracle PL/SQL.
  - **Packages and Synonyms**: Oracle-like packages and synonyms.

### 2. Advanced Security
- **Role**: Enhanced security features for enterprise needs.
- **Components**:
  - **Data Redaction**: Mask sensitive data.
  - **Row-Level Security**: Restrict data access at row level.
  - **Enhanced Auditing**: Detailed auditing features.

### 3. Performance Enhancements
- **Role**: Improved performance for enterprise workloads.
- **Components**:
  - **Query Optimizer**: Advanced query optimization techniques.
  - **Partitioning**: Improved data partitioning strategies.
  - **Advanced Indexing**: Additional indexing options for performance.

### 4. Management Tools
- **EDB Postgres Enterprise Manager (PEM)**: Comprehensive tool for monitoring, managing, and tuning EDB Postgres databases.
- **Migration Tools**: Tools to facilitate migration from Oracle and other databases.
- **Backup and Recovery Tools**: Advanced tools for backup, recovery, and high availability.

## Summary

EnterpriseDB (EDB) Postgres Advanced Server extends the robust PostgreSQL architecture with additional features, tools, and support services. These enhancements make it suitable for enterprise applications that require high performance, security, compatibility with other databases, and professional support.

For more detailed information, refer to the official [EnterpriseDB documentation](https://www.enterprisedb.com/docs/).
