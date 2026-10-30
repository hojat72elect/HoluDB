### Holu Database

Open source database with a new take on underlying technologies, observability, performance, and practicality.

The most important modules of a SQL database are:

<ol>
    <li>SQL parser</li>
    <li>query planner</li>
    <li>storage engine</li>
    For more info about how a <strong>storage engine</strong> works with other parts of the database, have a look at the diagram below:<br/>
    <img src="./docs/storage_engine.jpeg" alt="the diagram of storage engine" width="400" />
    <br/>
    <li>indexing</li>
    <li>transaction manager</li>
    <li>execution engine</li>
</ol>

## Architecture

We're following a modular architecture that separates `SQL compilation`, `execution`, `storage`,
 and `caching` into different modules.

<img src="./docs/db_layers.jpg" alt="the diagram of database architecture" width="400" />

My plan is to support a small yet reasonable subset of SQL for the alpha version of **HoluDB**. This is the
plan I have come up with so far:

`Data types` |	INTEGER, TEXT, REAL, BOOLEAN, NULL<br/>
`Schema` |	CREATE TABLE, DROP TABLE<br/>
`Writes` |	INSERT, UPDATE, DELETE<br/>
`Reads` |	SELECT, WHERE, ORDER BY, LIMIT<br/>
`Constraints` |	PRIMARY KEY, NOT NULL, UNIQUE<br/>
`Storage` |	Custom binary database file<br/>
`Indexes` |	Initially none; later B+ tree<br/>
`Transactions` |	Initially basic atomic operations; later full transactions<br/>
`Joins` |	Later: INNER JOIN, then other join types<br/>
`Durability` |	File persistence, followed by a write-ahead log