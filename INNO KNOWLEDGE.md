ACID:
4 principles which say how transactions should be done
A - atomicity. (All or nothing) It says that transaction should be done without mistakes in other way it will roll back
C - consistency. Transaction should set another valid state in db. So all data that we added must be validated ny rules which were set in columns
I - Isolation. It says that transactions which db does at one moment should be independent from each other and doesnt see changes which each one of them are making
D - Durability. It says that after transaction data in db should be safe and if something will happen with db it will store there anyway

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
non repetable read - transaction reads the same row twice but between other transaction change something in it. And to same queries get different results
Phanthom read - situation when transaction get phantom row in tables after second query, because other transaction insert one row into table


### PHP-LARAVEL

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
### Типизация

PHP становится строго типизированным. Обязательно спросят про:

- `declare(strict_types=1);` — включает строгую типизацию в файле. Без нее PHP попытается привести строку `"5"` к числу `5`. С ней — выкинет `TypeError`.
    
- **Union types (PHP 8.0):** `public function foo(int|string $var)`
    
- **Intersection types (PHP 8.1):** `public function foo(Runnable&Flyable $var)`
		

