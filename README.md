ЛР 1
-
1.Выберите из таблицы orders все заказы
-
```
SELECT * FROM orders;
```
![image](https://github.com/user-attachments/assets/23460e5a-748e-4c98-af98-3b637623958c)

2.Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in
-
```
SELECT * FROM orders WHERE STATUS IN ('cancelled','in_progress','delivery');
```
![image](https://github.com/user-attachments/assets/37ed988f-4a88-4c2b-bc07-a68dc8c8b53f)

3.Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new".
-
```
SELECT * FROM orders WHERE STATUS IN ('new', 'cancelled');
```
![image](https://github.com/user-attachments/assets/9bc193b2-02e3-4e4e-aaef-d6ea182e538e)

4.Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count). Вывести нужно только номер (id) и сумму (sum) заказа.
-
```
SELECT id, SUM FROM orders WHERE products_count >3;
```
![image](https://github.com/user-attachments/assets/2f208a4d-1ca9-4cfb-8e36-058f3dc827e7)

ЛР 2
-
1.Выберите из таблицы orders 3 самых дешевых заказа за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
-
```
SELECT * FROM orders WHERE STATUS != 'отменен' ORDER BY sum ASC LIMIT 3;
``` 
![image](https://github.com/user-attachments/assets/6de610d5-391d-46e1-b894-db1ed9330e77)

2.Выберите из таблицы orders 2 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
-
```
SELECT * FROM orders WHERE STATUS != 'отменен' ORDER BY sum DESC LIMIT 2;
``` 
![image](https://github.com/user-attachments/assets/3f8fe9e3-d4f4-4b08-b5ed-0d374fe9bebf)

3.Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).
-
```
INSERT INTO orders (id, products, sum) VALUES (6, 4, 8000);
``` 
![image](https://github.com/user-attachments/assets/11d54dfc-f39b-4381-8b39-08db0a22c9a2)

![image](https://github.com/user-attachments/assets/7472531a-e42f-458c-9899-9699d2e65cea)

4.Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.
-
```
INSERT INTO products (id, name, price, count) VALUES (7, 'VR-очки', 70000, 2);
```
![image](https://github.com/user-attachments/assets/dabf7dc4-b441-4a55-8bea-48950d5cd7dc)

![image](https://github.com/user-attachments/assets/0154c806-38a1-45b6-b78f-ca24592eaeb0)

5.В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.
-
```
UPDATE products SET name = 'PS5' WHERE name = 'IMAC';
```
![image](https://github.com/user-attachments/assets/45f95fbc-ed0f-4fd9-bc35-5b8a190ecc46)

![image](https://github.com/user-attachments/assets/1288a625-6daf-4162-8be0-1e61b328eea4)

Лр 3 
-
1.Создайте таблицу users с полем id типа INT и двумя текстовыми полями, которые будут хранить имя (first_name) и фамилию (last_name). Длина имени и фамилии не превышает 50 символов. Добавьте в таблицу трех пользователей: Дмитрия Иванова, Анатолия Белого и Дениса Давыдова.
-
```
CREATE TABLE users (ID INT, first_name VARCHAR(50), last_name VARCHAR(50));
INSERT INTO users (id, first_name, last_name)
VALUE (1,'Дмитрий', 'Иванов'),
(2, 'Анатолий', 'Белый'),
(3, 'Денис', 'Давыдов');
```
![image](https://github.com/user-attachments/assets/d729b1c5-e31a-4e60-88c1-ad851c497f26)

![image](https://github.com/user-attachments/assets/4096d56a-3ebb-4e19-a839-ecc0fd60b75a)

Лр 4
-
1.Создайте таблицу users для хранения информации о пользователях сайта. В таблице должны быть следующие поля: id – идентификатор, целое положительное; email – адрес электронной почты, строка не более 100 символов; date_joined – дата регистрации 
(достаточно хранить дату, без времени) last_activity – дата и время последней активности (с точностью до секунд).
-
![image](https://github.com/user-attachments/assets/b7acc72a-7fa5-4fdd-91ff-c59c92db939c)

Неверное решение:

CREATE TABLE users( id INT UNSIGNED, email VARCHAR(100), date_joined DATE, last_activity DATETIME );
INSERT INTO users (id, email, date_joined, last_activity) VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54") INSERT INTO users (id, email, date_joined, last_activity) VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53") INSERT INTO users (id, email, date_joined, last_activity) VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07")

Верное решение: 
```
create table users ( id int(10) unsigned, email varchar (100), date_joined date, last_activity datetime );
insert into users (id, email, date_joined,last_activity) values (1,'user1@domain.com', '2014-12-12','2016-04-08 12:34:54'),
(2,'user2@domain.com', '2014-12-12','2017-02-13 11:46:53'), (3,'user3@domain.com', '2014-12-13','2017-04-04 05:12:07');
```
![image](https://github.com/user-attachments/assets/d1e72b07-f656-41cf-aa8d-06c4cd585b0c)

2.Создайте таблицу calendar для хранения календаря посетителей. В таблице должны быть следующие поля: id – идентификатор записи в календаре, целое положительное; user_id – идентификатор пользователя, целое положительное; doctor_id – идентификатор доктора, целое положительное; visit_date – дата и время визита (точность до секунд).
-
![image](https://github.com/user-attachments/assets/9fdfbd4f-2646-49d5-a954-94c48b90baf7)

Неверное решение:

Create table calendar ( id int unsigned, user_id int unsigned, doctor_id int unsigned, visit_date datetime); Insert into calendar (id, user_id, doctor_id, visit_date) Values (1, 1914 , 1, '2017-04-08 12:00:00'), (2, 12, 1, '2017-04-08 12:30:00'), (3, 4641, 2, '2017-04-09 09:00:00'), (4, 4641, 2,'2017-04-09 09:00:00'), (5, 15, 2,'2017-04-09 10:00:00')

Верное решение:
```
Create table calendar ( id int unsigned, user_id int unsigned, doctor_id int unsigned, visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date) Values (1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'), (5, 15, 2,'2017-04-09 10:00:00') 
```
![image](https://github.com/user-attachments/assets/b3af42ac-b570-424f-bb73-dadf7cf39b34)

3.Создайте таблицу users , в которой будут следующие поля: id — идентификатор, целые положительные числа. first_name— имя, строки до 50 символов. last_name — фамилия, строки до 60 символов. bio — биография, текст до 65000 символов.
-
![image](https://github.com/user-attachments/assets/0c30eb1c-25bc-42f3-8731-fb064ed04f5d)

Неверное решение:

create table users ( id int (10) unsigned, first_name varchar (50) unsigned, last_name varchar (60) unsigned, bio text ); INSERT INTO users (id, first_name, last_name, bio) VALUES (1,'Антон','Кулик','С отличием окончил 39 лицей.'), (2,'Сергей','Давыдов',''), (3,'Дмитрий','Соколов','Профессиональный программист.')

Верное решение:
```
create table users ( id int (10) unsigned, first_name varchar (50), last_name varchar (60), bio text );
INSERT INTO users (id, first_name, last_name, bio) VALUES (1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''), (3,'Дмитрий','Соколов','Профессиональный программист.')
```
![image](https://github.com/user-attachments/assets/2713ba61-ab0d-4490-8b05-c56a7af914be)

Лр 5
-
1.Выберите из таблицы orders 4 самых дорогих заказов за всё время.Данные нужно отсортировать в порядке убывания цены.Отмененные заказы не учитывайте.
-
![image](https://github.com/user-attachments/assets/db0006af-01b0-4f01-8c18-c70eb71fc894)

Решение:
-
```
SELECT * FROM orders WHERE status != 'cancelled' ORDER BY sum DESC LIMIT 4;
```
![image](https://github.com/user-attachments/assets/4fdb479a-cbe0-4390-a832-6d73cd1e419f)

2.Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе.
-
![image](https://github.com/user-attachments/assets/0d3eade9-f234-43c8-825d-966ed292ffb2)

Решение:
-
```
SELECT name, price FROM products WHERE count > 0 ORDER BY price ASC LIMIT 4;
```
![image](https://github.com/user-attachments/assets/c9547b15-56aa-4a0c-a9cb-9acb4dd5967b)

3.Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше.
Данные отсортируйте по дате в обратном порядке.
-
![image](https://github.com/user-attachments/assets/09fb9dc4-4846-42ea-b3ee-39a4c7f5914d)

Решение:
-
```
SELECT * FROM orders WHERE sum >= 3200 ORDER BY date DESC LIMIT 3;
```
![image](https://github.com/user-attachments/assets/fa96cebd-39df-4326-8fa4-945fb33445b4)

4.Создайте данную таблицу:
-
![image](https://github.com/user-attachments/assets/e638f7a4-d2e0-49ce-9243-a1a3e51426e9)

Решение:
-
```
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    count INT,
    price DECIMAL(10, 2)
);

INSERT INTO products (id, name, count, price) VALUES
(1, 'Стиральная машина', 5, 10000.00),
(2, 'Холодильник', 0, 10000.00),
(3, 'Микроволновка', 3, 4000.00),
(4, 'Пылесос', 2, 4500.00),
(5, 'Вентилятор', 0, 700.00),
(6, 'Телевизор', 7, 31740.00),
(7, 'Тостер', 2, 2500.00),
(8, 'Принтер', 4, 3000.00),
(9, 'Активные колонки', 1, 2900.00),
(10, 'Ноутбук', 4, 36990.00),
(11, 'Посудомоечная машина', 0, 17800.00),
(12, 'Видеорегистратор', 23, 4000.00),
(13, 'Смартфон', 8, 12300.00),
(14, 'Флешка', 4, 1400.00),
(15, 'Блендер', 0, 5500.00),
(16, 'Газовая плита', 5, 11900.00),
(17, 'Клавиатура', 3, 1800.00);
```
![image](https://github.com/user-attachments/assets/7e86e58c-6476-43c1-8239-8a301ebd0654)


![image](https://github.com/user-attachments/assets/a3a53f5d-5ca0-4c44-93a3-16ed39a2581e)

5.Из таблицы ниже сделать выборку на основе задания: Сайт выводит товары по 5 штук. Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).
-
![image](https://github.com/user-attachments/assets/9979c601-7080-4dfc-a9c3-d7c4257b7e93)

Решение:
-
```
SELECT name, price FROM products ORDER BY price ASC LIMIT 5 OFFSET 10;
```
![image](https://github.com/user-attachments/assets/193aed61-cd78-48cc-9708-2f1e00853770)

Лр 6
-
1.Создайте таблицу orders для хранения списка заказов:
id — идентификатор, целое положительное.
user_id — идентификатор пользователя, который оформил заказ. Целое положительное, NULL запрещен.
amount — стоимость заказа. Целое положительное число не более 1 млн. NULL запрещен, по умолчанию 0.
created — дата и время создания заказа. NULL запрещен.
state — статус заказа. Выбор из new, cancelled, in_progress, delivered, completed. Можно выбрать только один вариант. NULL запрещен. По умолчанию должен стоять new.
Добавьте 3 записи так, чтобы получалась таблица ниже:
-
![image](https://github.com/user-attachments/assets/71fe4878-4b0b-458a-a12e-be147e9bd201)

Решение:
-
```
CREATE TABLE orders (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    user_id INTEGER NOT NULL,
    amount INTEGER NOT NULL DEFAULT 0,
    created DATETIME NOT NULL,
    state ENUM('new', 'cancelled', 'in_progress', 'delivered', 'completed') NOT NULL DEFAULT 'new',
    CHECK (user_id > 0),
    CHECK (amount >= 0 AND amount <= 1000000)
);

INSERT INTO orders (user_id, amount, created) VALUES (56, 5400, '2018-02-01 17:46:59');
INSERT INTO orders (user_id, amount, created) VALUES (90, 249, '2018-02-01 19:13:04');
INSERT INTO orders (user_id, amount, created) VALUES (78, 2200, '2018-02-01 22:43:09');

SELECT * FROM orders;
```
![image](https://github.com/user-attachments/assets/2129e63a-67bc-4d85-9b5c-bd9270ac931d)

2.Создайте таблицу users для хранения списка пользователей сайта:
id — идентификатор, целое положительное.
first_name — имя, строка до 20 символов. NULL запрещен.
last_name — фамилия, строка до 20 символов. NULL запрещен.
patronymic — отчество, строка до 20 символов. NULL запрещен, по умолчанию пустая строка.
is_active — отметка об активности пользователя. Логическое поле, по умолчанию TRUE.
is_superuser — отметка администратора. Логическое поле, по умолчанию FALSE.
Добавьте 3 записи так, чтобы получалась таблица
-
![image](https://github.com/user-attachments/assets/64a74af7-1c09-40c3-a52a-34c4710709b1)

Решение:
-
```
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    patronymic VARCHAR(20) NOT NULL DEFAULT '',
    is_active BOOLEAN NOT NULL DEFAULT TRUE,
    is_superuser BOOLEAN NOT NULL DEFAULT FALSE,
    CHECK (LENGTH(first_name) <= 20),
    CHECK (LENGTH(last_name) <= 20),
    CHECK (LENGTH(patronymic) <= 20)
);

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser)
VALUES ('Дмитрий', 'Иванов', '', TRUE, FALSE);

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser)
VALUES ('Анатолий', 'Белый', 'Сергеевич', TRUE, TRUE);

INSERT INTO users (first_name, last_name, is_active, is_superuser)
VALUES ('Андрей', 'Крючков', FALSE, FALSE);

SELECT * FROM users;
```
![image](https://github.com/user-attachments/assets/733adbb7-e712-4fb8-a8ff-c5211619a2da)

3.Создайте таблицу products для хранения товаров в интернет магазине:
id — идентификатор, целое положительное.
category_id — категория, целое положительное. Может принимать NULL. По умолчанию NULL.
name — название, строка до 100 символов. NULL запрещен.
count — количество, целое положительное до 255. NULL запрещен, по умолчанию 0.
price — цена типа DECIMAL с 10 знаками, 2 из которых выделены для копеек. NULL запрещен, по умолчанию 0.00.
Добавьте 3 записи так, чтобы получалась таблица
-

Решение:
-
```
CREATE TABLE products (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    category_id INTEGER NULL DEFAULT NULL,
    name VARCHAR(100) NOT NULL,
    count TINYINT UNSIGNED NOT NULL DEFAULT 0,
    price DECIMAL(10, 2) NOT NULL DEFAULT 0.00,
    CHECK (category_id > 0 OR category_id IS NULL),
    CHECK (count >= 0 AND count <= 255),
    CHECK (price >= 0)
);

INSERT INTO products (category_id, name, count, price)
VALUES (1, 'Кружка', 5, 45.90);

INSERT INTO products (category_id, name, count, price)
VALUES (17, 'Фломастеры', 0, 78.00);

INSERT INTO products (name, count, price)
VALUES ('Сникерс', 12, 50.80);

SELECT * FROM products;
```
![image](https://github.com/user-attachments/assets/b5b73ac0-9edc-4d43-98ec-3570feabe363)
