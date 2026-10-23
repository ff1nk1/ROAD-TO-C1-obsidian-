нфDATABASE,PHP/FRAMEWORKS/DEPLOY/REDIS/OPENSEARCH
### DATABASE
active record(eloquent), data mapper(doctrine), background tasks php, acid - значение каждой буквы. solid - тоже самое
team setup
did you use elasticsearch
which usecases has been covered by you by docker
tell me please about phpunit did you use it?
which types of indexes do you know.
Tell me about pipeline of optimization of page loading which problems could we faced. How to increase performance?
what do you know about outbox pattern.
reducing cache uploading cache(job which monitor is cache become old and update it async)4
+lifecycle of laravel application
+selectivity,index,transactions
+MOSLTY ABOUT DB (+ релевантность индексов) композитные индексы и остальные +индексы почитать


!!!
+кластеризованные и некластеризованные
+CGI -What is it
+шардирование, репликация в бд
+percona - db (проблема, что решает)
+click house

----------------------------------------------

+terraform 
+(deploy bit backet pipline(ci/cd)):
+порядок действий
1. линтеры(Php stan,etc)
2. pipeline тестов
3. аппрув от 
+deployer
+что делать, если зависла миграция?(дропнуть в mysql)
+случаи, когда что-то может упасть:
	1. добавление столбца в новую бд 
	2. ...
+случаи, почему медленные запросы в бд, как фиксить:
	3. Кэширование
	4. explain на запрос
	5. Индексирование
	Если нет, то хуёвый индекс низкая селективность

+DELETE/TRUNCATE
+TRUNCATE УДАЛЯЕТ ЗАПИСИ И ИНДЕКСЫ
+Как ребалансировать дерево

+Работа с вебсокетами(abi,центрифуга)
+Redis mget
 
	

### PHP-LARAVEL

+closure жестко зашарить
+laravel life cycile - nginx - index - kernel - app service provider - routing - ...
+reflection api
+data types
+php ob
patterns basic!!!!!!!!!!!! (пораждающие и структурные) adapter pattern
+pdo
+bind
+csrf attack and xss attacks
cors
линейное и другое масштабирование 
аннотации
логи вся инфа в фреймворках
cache lock
chukcks laravel !!!
chunck_by_id 
расписание задач/команд (schedudle )

поменять insert clickhouse
Если какая-то хуйня с производительностью
	производительность бд - кэш - репликация - рефакторинг
 
AWS basics Выучить  