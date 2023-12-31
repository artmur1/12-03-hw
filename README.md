# Домашнее задание к занятию "`SQL. Часть 1`" - `Мурчин Артем`

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### Решение 1

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad1.png)

SELECT district FROM address

WHERE district LIKE 'K%a'

AND district NOT LIKE '% %';

### Доработка решения 1

В запросе добавил оператор DISTINCT для получения уникальных названий районов.

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad_dorab.png)

SELECT DISTINCT district FROM address

WHERE district LIKE 'K%a'

AND district NOT LIKE '% %';

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

### Решение 2

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad2.png)

SELECT amount, payment_date FROM payment

WHERE payment_date between '2005-06-15 00:00:00' and '2005-06-18 23:59:00'

AND amount >= 10;

### Задание 3

Получите последние пять аренд фильмов.

### Решение 3

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad3.png)

SELECT rental_id, rental_date, inventory_id, customer_id, return_date, staff_id, last_update

FROM rental ORDER BY rental_id DESC LIMIT 5;

### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

### Решение 4

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad4.png)

SELECT customer_id, REPLACE(LOWER(first_name), 'll', 'pp'), LOWER(last_name) FROM customer

WHERE first_name LIKE 'Kelly'

OR first_name LIKE 'Willie';

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 5*

Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.

### Решение 5*

![alt text](https://github.com/artmur1/12-03-hw/blob/main/12-03-zad5.png)

SELECT SUBSTRING_INDEX(email, '@', 1) as column1,

RIGHT(email, CHAR_LENGTH(email) - POSITION('@' IN email)) as column2

FROM customer c ;

### Задание 6*

Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные — строчными.
