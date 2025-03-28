# Домашнее задание к занятию «Работа с данными (DDL/DML)»

### Грибанов Антон. FOPS-31


### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

```bash
sudo apt update
sudo apt install mysql-server
sudo systemctl status mysql
```
 ![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_001.png)

1.2. Создайте учётную запись sys_temp. 

 ![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_002.png)

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_003.png)

1.4. Дайте все права для пользователя sys_temp. 

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_004.png)


1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_005.png)

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_006.png)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_007.png)

1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

```bash
wget -c https://downloads.mysql.com/docs/sakila-db.zip
unzip sakila-db.zip
cd sakila-db
```

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_008.png)

1.7. Восстановите дамп в базу данных.

```bash
mysql -u sys_temp -p
show databases;
create database SakilaDB;
show databases;
use SakilaDB;
show tables;
source sakila-schema.sql;
source sakila-data.sql;
show tables;
exit
```

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_009.png)

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_010.png)

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

```bash
mysql -u sys_temp -p
show databases;
use SakilaDB;
show tables;
exit
```

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_010.png)
![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_011.png)

### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_012.png)

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

```bash
mysql -u root -p 
show grants for 'sys_temp'@'%';
grant ALL PRIVILEGES on SakilaDB.* to 'sys_temp'@'%';
revoke INSERT, UPDATE, DELETE on SakilaDB.* from 'sys_temp'@'%';
show grants for 'sys_temp'@'%';
flush privileges;
```

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_013.png)

![bd_002](https://github.com/Qshar1408/bd_homework_02/blob/main/img/bd_homework_02_014.png)

