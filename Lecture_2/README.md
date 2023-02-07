# Домашнее задание к занятию 12.2. «Работа с данными (DDL/DML)» - `Пахомов Владимир`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.
1.2. Создайте учётную запись sys_temp.
1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)
1.4. Дайте все права для пользователя sys_temp.
1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
1.6. Переподключитесь к базе данных от имени sys_temp.
1.7. Восстановите дамп в базу данных.
1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

```
Поле для вставки кода...

1.1. sudo apt install mysql-server mysql-client

1.2. mysql -u root -p
     create user 'sys_temp'@'localhost' IDENTIFIED BY 'P@ssword12345';
1.3. select user,authentication_string,plugin,host FROM mysql.user;  
или  select user,host from mysql.user where user like "%%";   
1.4. grant all privileges on localhost . * TO 'sys_temp'@'localhost';
1.5. show grants for 'sys_temp'@'localhost';
1.6. mysql -u sys_temp -p
1.7. mysql -u root -p ${DBNAME} < /home/pakhomov/Загрузки/sakila-db/sakila-schema.sql
     mysql -u root -p ${DBNAME} < /home/pakhomov/Загрузки/sakila-db/sakila-data.sql
1.8. use sakila;
     show tables;      
....
....
```


![Задание 1.2](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_1_2.png)`

![Задание 1.3](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_1_3.png)`

![Задание 1.5](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_1_5.png)`

![Задание 1.7](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_1_7.png)`

![Задание 1.8](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_1_8.png)`

---

### Задание 2

Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)


	Название таблиц			Первичный ключ
| actor                      /n | actor_id /n
| actor_info                 | нет первичного ключа
| address                    | address_id
| category                   | category_id
| city                       | city_id
| country                    | country_id
| customer                   | customer_id
| customer_list              | нет первичного ключа
| film                       | film_id
| film_actor                 | составной первичный ключ actor_id и film_id
| film_category              | составной первичный ключ film_id и category_id
| film_list                  | нет первичного ключа
| film_text                  | нет первичного ключа
| inventory                  | inventory_id
| language                   | language_id
| nicer_but_slower_film_list | нет первичного ключа
| payment                    | payment_id
| rental                     | rental_id
| sales_by_film_category     | нет первичного ключа
| sales_by_store             | нет первичного ключа
| staff                      | staff_id
| staff_list                 | нет первичного ключа
| store                      | store_id 




### Задание 3

3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)


```
Поле для вставки кода...

3.1. revoke insert,update,delete,drop,alter on sakila. *from 'sys_temp'@'localhost';
3.2. show grants for 'sys_temp'@'localhost';

```

![Задание 3](https://github.com/PakhomovV/RelationalDB/blob/main/Lecture_2/Задание_3.png)`


