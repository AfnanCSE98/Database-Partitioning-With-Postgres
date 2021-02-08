# Database-Partitioning-With-Postgres
Partitioning or databased partitioning is a technique where you split up a huge table into multiple tables and let the database decide which table or which partition to hit based on the where clause.
So let's say we have a beautiful customer stable here.

![](cst.PNG)

So you going to select name from customer tables where ID equals seven hundred thousand and one.So what the database will do is?If you have an index on the on that table, we're going to use the index and then we're going to land on that particular id on that disk.Or if we don't have index, we're going to do a sequential scan, which is the worst thing. But we have to scan all this rows until we find the rows we were looking for, regardless whether using an index or sequential scan and scanning hundred million row is a lot.

Partitioning is the idea to break the table down to smaller pieces so we only need to work with a smaller piece of the main table.So,let's break things up.One million rows into five partitions i.e. five tables

![](partitioned.PNG)

We can achieve both **Horizontal Partitioning** and **Vertical partitioning**.Horizontal Partitioning splits rows into partitions while Vertical partitioning splits columns into partitions.Vertical partitioning is useful while dealing with large column (blob) that you can store in a slow access drive in its own tablespace.

### Partitioning Types
* By Range
Dates, ids (e.g. by logdate or customerid from to)
* By List
Discrete values (e.g. states CA, AL, etc.) or zip codes
* By Hash
Hash functions (consistent hashing).Cassandre uses that where where we use the hash function to spread the value.In the proxies we use IP hash.

### Demo - Example with Postgres 
We are going to
* Spin up a postgres instance with docker
* create a table and Insert 10 million rows
* Create partitions






