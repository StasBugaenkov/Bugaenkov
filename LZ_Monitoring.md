##### Мониторинг
##### Статистика обращений к таблице
PostgreSQL работает под управлением операционной системы ив известной степени зависит от ее настроек.Unix предоставляет множество инструментов для анализа состояния и производительности.
Создала базу данных и таблицу, наполнила её и удалила данные:
![avatar](https://sun9-1.userapi.com/impg/PyUe28E5bDbNwxgNFQawhKhMYNbT7xzJq9GQFA/awYgzUOXLks.jpg?size=528x184&quality=96&sign=de778fb097964442540d834d817458b5&type=album)
Проверила статистику обращений.
![avatar](https://sun9-45.userapi.com/impg/E6rQc-Fd-Zo8FX1TLfMPG35jMZs_cV4FadwJ0g/xHNggvOWgIc.jpg?size=617x379&quality=96&sign=ddcc4d1aac3572805c46be57d2480017&type=album)
Было вставлено 1000 строк (n_tup_ins = 1000), удалили 1000 строк (n_tup_del = 1000).
После этого не осталось активных версий строк (n_live_tup = 0), все 1000 строк не актуальны на текущий момент (n_dead_tup = 1000).
Выполнила очистку:
![avatar](https://sun9-47.userapi.com/impg/VQp-a83PgTeHB5fYDuazpnUnyNVjmGyNcdwsZA/Z7-P1fbw1Tc.jpg?size=614x395&quality=96&sign=80c4ce743109c7340817a706b8a372cf&type=album)
Неактуальные версии строк убраны при очистке (n_dead_tup = 0), очистка обрабатывала таблицу один раз (vacuum_count = 1).
##### Взаимоблокировка
Одна транзакция блокирует первую строку таблицы.Затем другая транзакция блокирует вторую строку.Теперь первая транзакция пытается изменить вторую строку и ждет ее освобождения.А вторая транзакция пытается изменить первую строку.Происходит взаимоблокировка:
![avatar](https://sun9-76.userapi.com/impg/1M-wpXJURv1ZXtslhSHQWYyKJgIQEi6GttUujQ/xtCRfBVax5Q.jpg?size=550x187&quality=96&sign=69969fdefeb8b340c96760ddbc1800c1&type=album)
Необходимо просмотреть журнал сообщений:
![avatar](https://sun9-79.userapi.com/impg/mVsbX8sxe3ivVkL32uKBmhABYDT1C68NrETMFw/ZggU8Zj-KUg.jpg?size=786x199&quality=96&sign=4a923d401add82e88aa37734c5026ca5&type=album)
Расширение pg_stat_statements - собирает статистику планирования и выполнения всех запросов. Для работы расширения требуется загрузить одноименный модуль. Для этого имя модуля нужно прописать в параметре shared_preload_libraries и перезагрузить сервер. Изменять этот параметр лучше в файле postgresql.conf, но для целей демонстрации установим параметр с помощью команды ALTER SYSTEM.
![avatar](https://sun2-11.userapi.com/impg/p-rIkJY-m5bC9EQNZpwWYmBP-eSEMKxTtV79Xw/QJvuUm4ll_U.jpg?size=621x206&quality=96&sign=e1705d17539bea7001045fb17e9bd220&type=album)
Создала EXTENSION и выполнила несколько запросов:
![avatar](https://sun9-65.userapi.com/impg/d8HdIX94upiRa5c6LUW_YBt2TrRuAS_gyem4cA/N6NngGOI5Cs.jpg?size=409x225&quality=96&sign=d888ae2a1518c1b8edb21808a7059cdc&type=album)
Затем посмотрела на статистику запроса, который выполнялся чаще всего:
![avatar](https://sun9-30.userapi.com/impg/pcYaTubbQziiSnEc77hvk72KOlwYtfoUoY_mWA/0LaAlDY4VI8.jpg?size=537x382&quality=96&sign=94e90e5f9dd32f15c4e3514037e09269&type=album)



