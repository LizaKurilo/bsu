# lab4

Packages

## init

- Выбирите СУБД `Oracle` для выполнения лабораторной.
- Оознакомтесь со скриптом создания и заполнения таблиц для выполнения лабораторной ([`create.sql`](https://github.com/Drapegnik/bsu/blob/master/dms/lab1/create.sql)).
- Запустите скрипт `create.sql` на выполнение.

## task

- Создайте пакет, включающий в свой состав процедуру и функцию.
- Процедура должна вычислять ежегодную добавку к зарплате сотрудников на детей
  за `2016` год и заносить её в виде дополнительной премии в последнем месяце
  (`декабре`) `2016` года в поле `bonvalue` таблицы `bonus`.
- В качестве параметров процедуре передаются проценты в зависимости от
  количества детей (см. правило начисления добавки).
- Функция должна вычислять ежегодную добавку за `2015` год на детей к зарплате
  конкретного сотрудника (номер сотрудника - параметр передаваемый функции) без
  занесения в таблицу.

### Правило начисления добавки

> Добавка к заработной плате на детей вычисляется только для работавших в
> `декабре` (хотя бы один день) `2016` году сотрудников по следующему правилу:

Добавка равна `x%` от суммы должностного месячного оклада (поле `minsalary`
таблицы `job`) по занимаемой в `декабре` `2016` года должности и всех
начисленных за `2016` год премий (поле `bonvalue` таблицы `bonus`), где: _ `x%`
равны `x1%`, если сотрудник имеет одного ребёнка; _ `x%` равны `x2%`, если
сотрудник имеет двух детей; _ `x%` равны `x3%`, если сотрудник имеет трёх и
более детей. _ `x1%<x2%<x3%` являются передаваемыми процедуре и функции
параметрами.

- Кроме этого, функции в качестве параметра передаётся номер сотрудника
  (`empno`).

### Замечание

> Для проверки правильности выполнения процедуры `proc(...)` её исполнение можно
> вызвать следующим блоком:

```sql
BEGIN
	proc(...);
END;
```

> Для проверки правильности выполнения функции с именем `fun(...)` можно
> использоватьзовать следующий блок вывода значения функции на экран:

```sql
BEGIN
	DECLARE y REAL;
	BEGIN
		y := fun(...);
		DBMS_OUTPUT.PUT_LINE(y);
	END;
END;
```

---

> results check out in
> [`lab4.sql`](https://github.com/Drapegnik/bsu/blob/master/dms/lab4/lab4.sql)
