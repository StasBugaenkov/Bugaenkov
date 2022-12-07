##### Мониторинг
##### Статистика обращений к таблице
PostgreSQL работает под управлением операционной системы ив известной степени зависит от ее настроек.Unix предоставляет множество инструментов для анализа состояния и производительности.
Создал базу данных и таблицу, наполнил её и удалил данные:
![avatar](https://sun9-1.userapi.com/impg/PyUe28E5bDbNwxgNFQawhKhMYNbT7xzJq9GQFA/awYgzUOXLks.jpg?size=528x184&quality=96&sign=de778fb097964442540d834d817458b5&type=album)
Проверил статистику обращений.
![avatar](https://sun9-45.userapi.com/impg/E6rQc-Fd-Zo8FX1TLfMPG35jMZs_cV4FadwJ0g/xHNggvOWgIc.jpg?size=617x379&quality=96&sign=ddcc4d1aac3572805c46be57d2480017&type=album)
Было вставлено 1000 строк (n_tup_ins = 1000), удалили 1000 строк (n_tup_del = 1000).
После этого не осталось активных версий строк (n_live_tup = 0), все 1000 строк не актуальны на текущий момент (n_dead_tup = 1000).
Выполнил очистку:
![avatar](https://sun9-47.userapi.com/impg/VQp-a83PgTeHB5fYDuazpnUnyNVjmGyNcdwsZA/Z7-P1fbw1Tc.jpg?size=614x395&quality=96&sign=80c4ce743109c7340817a706b8a372cf&type=album)
Неактуальные версии строк убраны при очистке (n_dead_tup = 0), очистка обрабатывала таблицу один раз (vacuum_count = 1).
##### Взаимоблокировка
Одна транзакция блокирует первую строку таблицы.Затем другая транзакция блокирует вторую строку.Теперь первая транзакция пытается изменить вторую строку и ждет ее освобождения.А вторая транзакция пытается изменить первую строку.Происходит взаимоблокировка:
![avatar](https://sun9-76.userapi.com/impg/1M-wpXJURv1ZXtslhSHQWYyKJgIQEi6GttUujQ/xtCRfBVax5Q.jpg?size=550x187&quality=96&sign=69969fdefeb8b340c96760ddbc1800c1&type=album)
Необходимо просмотреть журнал сообщений:
![avatar](https://sun9-west.userapi.com/sun9-52/s/v1/ig2/KSFbv1-yK0NJVodwoU-vHC15hKUNrXN7aiTagKhuXRBmGNXxPU0FWI4ihltUrI5dUJlmLh8eIao7A0e7gyUn36mz.jpg?size=604x153&quality=96&type=album)
Расширение pg_stat_statements - собирает статистику планирования и выполнения всех запросов. Для работы расширения требуется загрузить одноименный модуль. Для этого имя модуля нужно прописать в параметре shared_preload_libraries и перезагрузить сервер. Изменять этот параметр лучше в файле postgresql.conf, но для целей демонстрации установим параметр с помощью команды ALTER SYSTEM.
![avatar](https://sun9-north.userapi.com/sun9-87/s/v1/ig2/QgMbPNRS0B5T-5shcrygaZJTulJcfV61Y6DGbShSvjiUZ2AziI-1AeKXtGG77EpkvpbvRrRvqgvt4F4hnAEQn4wL.jpg?size=604x200&quality=96&type=album)
Создала EXTENSION и выполнила несколько запросов:
![avatar](https://sun9-65.userapi.com/impg/d8HdIX94upiRa5c6LUW_YBt2TrRuAS_gyem4cA/N6NngGOI5Cs.jpg?size=409x225&quality=96&sign=d888ae2a1518c1b8edb21808a7059cdc&type=album)
Затем посмотрел на статистику запроса, который выполнялся чаще всего:
![avatar](https://sun9-30.userapi.com/impg/pcYaTubbQziiSnEc77hvk72KOlwYtfoUoY_mWA/0LaAlDY4VI8.jpg?size=537x382&quality=96&sign=94e90e5f9dd32f15c4e3514037e09269&type=album)



