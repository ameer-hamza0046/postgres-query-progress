# postgres-query-progress
PostgreSQL does not currently provide a way to track the progress of running queries, which can be frustrating for users and database administrators (DBAs). Long-running queries make users uncertain about whether to wait or abort them, leading to inefficiency and poor user experience. A query progress indicator would provide real-time updates on query execution. It will help users to make informed decisions and improving overall database management. Implementing this feature requires understanding PostgreSQL’s internal query processing and finding accurate methods to estimate query progress.

We modified the following files:
1. /postgresql/src/include/executor/executor.h
2. /postgresql/src/include/nodes/execnodes.h
3. /postgresql/src/backend/executor/nodeSeqscan.c

We used the number of getNext() calls to estimate the total running time for each query to indicate the query progress.
