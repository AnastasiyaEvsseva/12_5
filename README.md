# 12_5

### Задание 1
Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

![image](https://github.com/AnastasiyaEvsseva/12_5/assets/151757353/73b572a0-250a-4a59-be81-83c1714e463b)

### Задание 2
Выполните explain analyze следующего запроса:

select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id

* перечислите узкие места;
* оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.

Узкие места наблюдаются в момент использования оконных функций OVER и PARTITION BY, а так же в момент фильтрации вывода, в сравнении колонок из разных таблиц.

![image](https://github.com/AnastasiyaEvsseva/12_5/assets/151757353/b3b1f935-fb02-4318-9e4e-24901b155acc)

![image](https://github.com/AnastasiyaEvsseva/12_5/assets/151757353/2272e3a8-ceb3-4ece-9ffe-777b50615daa)

