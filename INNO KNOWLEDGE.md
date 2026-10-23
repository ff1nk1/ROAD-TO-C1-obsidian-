MYSQL не поддерживает шардирование
ACID:
4 principles which say how transactions should be done
A - atomicity. (All or nothing) It says that transaction should be done without mistakes in other way it will roll back
C - consistency. Transaction should set another valid state in db. So all data that we added must be validated ny rules which were set in columns
I - Isolation. It says that transactions which db does at one moment should be independent from each other and doesnt see changes which each one of them are making
D - Durability. It says that after transaction data in db should be safe and if something will happen with db it will store there anyway

CAP:
There can be only 2 of them at one time in the system
C - Consistency(all nodes see the same data)
A - Availability(every query gets an answer)
P - Partition tolerance (a system work even if connection is lost between nodes)

DML - Data Manipulation Language(SELECT,INSERT,DELETE,UPDATE) (Управление самими данными в бд)
DDL - Data definition Language(ALTER,CREATE,DROP)(Управление самой бд(таблицами))
View - its table but its data doesnt locate in memory. Database is calculating it when we ask for it(through command)
Mat View - material data which is stores on disk. And we can use it everytime if we need it

Trigger - a script in databases which actives after or before INSERT UPDATE DELETE and do something, write logs for example

Stores Procedures - its scripts which saved in memory and a developer can use it in database. It takes hard database work logic on itself(it almost like function but its unneccesary to return smth)
Function - also a script in memory but it must return something and it can be put in SELECT,WHERE,etc
SO PROCEDURE DOES SOMETHING AND FUNCTION JUST CALCULATES

Constraints - rules which validate data before it put in table(for example UNIQUE, NOT NULL,FOREIGN KEY,etc)

Normal Forms - forms which helps to avoid problems with database, for example saves from repetable value in every row by relocatating it to new distinct table. So basiclly it just a set of rules which tells a programmer how database should look

Primary key - a unique column which truthly identifies a row, often it a ID column

Foreign key - its a key in a table which provides link to another column in database(primary key)
The primary purpose of a Foreign Key is to enforce **referential integrity**. This means the database acts as a gatekeeper, actively preventing any actions that would break the logical links between your tables or create invalid data.

Replication - method which use to impove read from database. It basiclly to make a several copies of your database and spread the load between them. ALL INPUT OPERATIONS GOES THROUGH MAIN DB AND AFTER THAT IT SPREADS IT BETWEEN OTHERS

Sharding - method which use to improve input in database or you don't have enough space on your disk. It basiclly splits database on 2 or more independent ones, each database stores only it's part

When to use:
Replication - problems with read(AND THERE ARE NOT MANY INPUTS), and also you need backup and fast availability
Sharding - problems with INPUT and space on disk where database is located.


Selectivity:
Its a measure which tells database how many unique rows it has in column. Its need to put index in the right place.

Index Relevancy:
This thing can say is your index are good for current query. You may have great index but if you try to do where on other column your index will become useless

Composite index:
Its an index which consists of 2 or more variables and check it at the same time. it work from left to right, so it's better to put index with high selectivity first because it will remove a lot of rows

SOLID
its 5 principles which tell how to do clean code and avoid architecture mistakes
S - single responsobility - one class should do one task. For example class orders should not do payments
O - open/closed principles - class must be closed for modifications but open for EXTENSIONS
That mean that u cant change or modify your old methond in class
L - Liskov - every parent's class method may be replaced with their children methods without problems
I - interfaces - its better to have many little interfaces then one large
DI -Dependecy Inversion - class with businness logic should not be addicted to services class.
So we should have an interface. For example its bad to have class Postgres but its right to have class Database

MyISAM vs InnoDB
MyISAM its a old engine for dbs which was freezing whole table while smthing was inserting
InnoDB its a new engine which freezes only one row while inserting

Isolation levels:
Its settings which says how much independency transactions have between them
Read uncommited:
The lowest isolation level in general it says that transaction can read changes that other transaction made and even didnt commited it
Read commited:
The second level, transaction can read only commited data from other transaction
nonRepetable Read:
It says that if data changes while transaction is still in proccess(by other transaction) it will have same data that it had before, because before transaction it did something like a snapshot of db(mysql)
Serializible:
db changes the order of transactions which are running at one time. It makes it run one after another

Transaction anomalies:
Dirty read - transaction can read uncommited but changed data from other transaction
repetable read - transaction reads the same row twice but between other transaction change something in it. And to same queries get different results
Phanthom read - situation when transaction get phantom row in tables after second query, because other transaction insert one row into table


TERRAFORM/DEPLOYER:
	TERRAFORM - its a thing which helps developer to configure how much hardware project needs in cloud like AWS
	DEPLOYER - service which is solving zero-downtime problem. It copies project into new directory and after that switch connections

Что делать, если зависла миграция:
	A developer just need to find the proccess which is working for a long time and kill it
	If it happend when a developer was altering the table. Its may be not enough storage. So for this situations you need to use ==🟠percona== so its an engine for MYSQL which optimize operations like adding a new column

How to fix high-latency queries:
	A developer need to cache some data or all of it(if it possible);
	He also needs to put indexes in db
	And use EXPLAIN on current query

DELETE vs TRUNCATE:
	DELETE is an operation which delete each row and write a log about it, so there is an option to rollback it, also it doesnt remove auto-increment
	TRUNCATE is fast operation which deletes whole table and create a new one without rollback option

КАК РЕБАЛАНСИТЬ ДЕРЕВО:
	You need to write OPTIMIZE <!TABLE!> command it will rebuild the btree

NO-SQL types:
	There are 2 types. First one is no sql dbs which work with jsons, key-value dbs like redis.

REDIS:
- **`MGET key1 [key2 ...]`**: Retrieves values for all specified string keys in a single request, minimizing network latency.
    
- **`MSET key1 val1 [key2 val2 ...]`**: Atomically sets multiple string keys to their respective values.
    
- **`MSETNX key1 val1 [key2 val2 ...]`**: Sets multiple string keys only if none of the specified keys already exist; aborts completely if even one key is present.
    
- **`HMGET key field1 [field2 ...]`**: Retrieves the values associated with multiple specified fields from a single hash.
    
- **`HSET key field1 val1 [field2 val2 ...]`**: Sets multiple field-value pairs inside a specified hash in one call.
    
- **`HGETALL key`**: Returns all field names and values stored within a hash.
    
- **`DEL key1 [key2 ...]`**: Synchronously removes multiple keys and immediately reclaims their memory in the main thread.
    
- **`UNLINK key1 [key2 ...]`**: Asynchronously deletes specified keys by detaching them immediately and freeing memory in a background thread.
    
- **`LRANGE key start stop`**: Retrieves a specified slice of elements from a list based on index offsets.
    
- **`SMEMBERS key`**: Returns all unique members contained in an unordered set.
    
- **`SRANDMEMBER key [count]`**: Returns one or multiple random members from a set without removing them.
    
- **`ZRANGE key min max`**: Returns a range of elements from a sorted set ordered by rank, score, or value.
    
- **`SCAN cursor [MATCH pattern] [COUNT count]`**: Iterates over keys in the database incrementally via a cursor without blocking the server.
    
- **`HSCAN key cursor [MATCH pattern] [COUNT count]`**: Iterates incrementally through fields and values within a specific hash.
    
- **`SSCAN key cursor [MATCH pattern] [COUNT count]`**: Iterates incrementally through members of a specific set.
    
- **`ZSCAN key cursor [MATCH pattern] [COUNT count]`**: Iterates incrementally through members and scores within a specific sorted set.


****
****
****

# PHP-LARAVEL

php it's a language WITHOUT multi inheritance
Interfaces - ...
(u can define constant inside of it)
(u can't define protected or private variable inside)
traits - classes which helps to solve multi inheritance problem in php

composer - php packet manager
autoloader - using rules which were written in composer.json "App\\": "src/"  to find files using App\smth\ instead of src\smth\

Shared nothing - one http request - one isolated task
multi thread - php basiclly does not has it, but there are modern solutions such as
	fibers - not multi threading but help to do tasks async
	Swoole/RoadRunner - cli servers which help php become async it is loading php app ones and after uses it async
	ext-parallel - with it php supports multi threadind

php fpm - fast cgi process manager

WEBSOCKETS(CENTRIFUGO):
	There is a problem with sync languages(php,python,etc) that for each web socket connection u need to make a worker. So CENTRIFUGO solves it, it just a pub/sub broker which made for fast operations, it communicate with backend via HTTP and just replace the idea with workers
### Типизация

PHP становится строго типизированным. Обязательно спросят про:

- `declare(strict_types=1);` — включает строгую типизацию в файле. Без нее PHP попытается привести строку `"5"` к числу `5`. С ней — выкинет `TypeError`.
    
- **Union types (PHP 8.0):** `public function foo(int|string $var)`
    
- **Intersection types (PHP 8.1):** `public function foo(Runnable&Flyable $var)`


register() - This is used **only for binding things into the Service Container**
boot() - This is where the actual initialization happens (e.g., registering event listeners, loading routes, publishing config files).

closures - anonymous function which can take variables from outer scope with word "use"

LARAVEL LIFECYCLE - PHP-FPM open index.php which includes composer it gets all dependencies and after that it goes to bootstrap which register all functions and classes and after that is goes to kernel - service providers

Reflection API - its API which helps laravel application to explore itself it can see classes declarations methods etc and it used in DI

php ob - buffer which takes all input to console and not website(php does it basiclly)

PDO - it builds a connection between php and every database

BIND - PDO feature which helps to avoid SQL-injections

XSS - A hacker attack which puts his code on site
CSRF - A hacker attack which can send cookies from hacker site to the website where you are authorized
			**they trick **your browser** into making a request to the website where you are authorized (like your bank). Because your browser automatically attaches your saved cookies to that request, the bank thinks _you_ made the request on purpose. That's why Laravel's `@csrf` token is required—it proves the request actually came from a form on _your_ site, not a hidden iframe on a hacker's site.


****
****
****

# REST

Status codes:
	2** - success 
	3** - redirect
	4** - a mistake on client side
	5** - server mistake/problem

Methods:
	GET,POST,PATCH,PUT,DELETE
	PATCH - change part of object(only 1 row for example)
	PUT - change the whole object(user sends all rows of object)

==🔴REST RULES==:
	There are 6 rules:
		1. Client-Server - Its strict separtion between client and server, client is responsible only for user interface and app state on device. And server should do bussiness logic, work with database and etc.
		2. Stateless - each HTTP is completly autonomous. It doesn't store data from user's past actions
		3.  Cacheable - server must put infomation about caching in headers. For example can this data be cached and how long.
		4. Uniform Interface:
			1. clear URLs very often with nouns
			2. standart HTTP methods
			3. Self-descriptive messages (using formats like JSON).
			4. HATEOAS (Hypermedia as the Engine of Application State) — the server should return not just data, but also links to related resources or available actions.
		5.Layered System - the client should communicate only with API, and he shouldn't has ability to communicate with database,loadbalancer and etc.
		6.**Code on Demand** _(Optional)_: The server can temporarily extend the client's functionality by sending executable code (such as JavaScript to run in a browser). This is the only constraint out of the six that is not strictly required for an API to be considered RESTful.

RESTful AND RESTlike:
	RESTful its an application which is following all REST rules;
	RESTlike its an application which is using only convinient rules for work(like http methods,json answers)
	Basiclly RESTful app implements HATEOAS(server return connected links) and RESTlike doesn't

IDEMPOTENCY:
	A rule which tell that every request after the first one should return the same state, for example if someone tries to delete the same object 2 times it will be deleted once and on the second time it will return(NO CONTENT).
	 It helps to avoid retries of operations. For example if client has bug and click to times ot button sumbit or send money it will send it only one time.(POST OPERATION ARE NOT IDEMPOTENCY BUT FOR THIS CASE WE NEED TO USE IDEMPOTENCY KEY)
	So basiclly IDEMPOTENCY MAKES RETRIES SAFE


****
****
****


# auth concepts

JWT - auth method where server doesn't store the state. It just generates access token and refresh token and when user tries to get locked resource it get his token from cookies using header and payload makes signature(third part of jwt token) and if it equals with the origin return the resource. If access token is expired it uses refresh to make a new one(REFRESH TOKEN IS STORED IN THE DATABASE)

Session - auth method where server stores the state. It just put session id into database and gives it to user. If user tries to get to abonded resource it compare these session_ids.

**CORS (Cross-Origin Resource Sharing)** is a browser-based security mechanism that allows a server to specify who can access its resources. If the backend does not properly configure CORS headers, an independent frontend (hosted on a different domain or port) will be blocked by the browser from reading the API responses.



# MESSAGE BROKERS

SYNC VS ASYNC:
sync: One services request another and do nothing before second one will answer.
async: Message publishes to kafka and server answers to user instanly

PULL VS PUSH:
PULL models get messages to comsumer by itself. So it automaticlly sends it there.
The main problem that if Message Broker will face a lot of messages it can kill slow conusmer with this amount of data
PUSH models it's when consumer ask topic for new messages by itself it helps to control load

Partitions - Kafka can split topic on partitions each partition has its own part of date(like sharding in db) consumers automaticlly connect with partitions, message broker does it