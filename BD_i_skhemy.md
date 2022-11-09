##### БД и схемы
PostgreSQL управляет несколькими базами данных — кластером. При инициализации кластера специальным образом создаются три одинаковые базы данных. Все остальные БД, создаваемые пользователем, клонируются из какой-либо существующей.
##### Практика 1
В процессе выолнения лр я создала новую базу данных и подключилась к ней:
![avatar](https://sun9-70.userapi.com/impg/O87lhak1NXhuLZJGj_FKKEWxlRSsxYVesofvjw/gHLjBW99dOQ.jpg?size=532x94&quality=96&sign=a4aadf32419c3dac327b9b0bc5796b53&type=album)
Просмотрела размер этой пустой БД и присвоила это значение переменной:
![avatar](https://sun9-68.userapi.com/impg/G440QlMwxguVEamE9CJqK1fMYL0xD0FDhModAQ/1rhaJAN2liI.jpg?size=597x107&quality=96&sign=a42b0ce6d2ca56e639035da8018a1aa2&type=album)
Затем приступила к созданию схемы, БД в ней, и заполнила небольшим количеством данных, чтобы после просмотреть изменения:
![avatar](https://sun9-81.userapi.com/impg/KaZuWZYq2bH-NThr_eniWkS9taphx_Kh4c-fWg/mYjWYfYP9ME.jpg?size=632x345&quality=96&sign=3942205a7ac1dde521c4755136e811d6&type=album)
![avatar](https://sun9-9.userapi.com/impg/bH_ybFXOz-iv56zOJoYEWvYrZQrSoEw8Z9-rSw/_IohVxkSl-0.jpg?size=604x165&quality=96&sign=0460fcfd40818e2a86934ddf06b7eac3&type=album)
Размер изменился на:
![avatar](https://sun9-5.userapi.com/impg/TslqUUGs9d1PyHXoAYzQvcnq1KHJH38ZvvFsPQ/NoA5MX-G9IM.jpg?size=571x71&quality=96&sign=2589135e94d844bc31ee81ac9aa84017&type=album)
##### Практика 2
С текущими настройками пути поиска видны таблицы только схемы kat:
![avatar](https://sun9-87.userapi.com/impg/191sKS0DkU6et9e_hhCTLn6l8LKVAbNTSXolRg/M1fXVQuYJyY.jpg?size=264x85&quality=96&sign=2afe304063c40fda7224662340847ad1&type=album)
Для таблиц схемы app происходит синтаксическая ошибка:
![avatar](https://sun9-87.userapi.com/impg/oD1evwdoZsfSsjKUn2H6DJyLIx7gJLrH_l3aRw/hA1u_RLHoEQ.jpg?size=299x64&quality=96&sign=89271546583d372d556485554fbf1987&type=album)
Изменим путь поиска:
![avatar](https://sun9-61.userapi.com/impg/sHa0jAg3hKkgVvc3lVzyrZhh-uVoARbyIFqGPg/2tE9yLd13Og.jpg?size=625x182&quality=96&sign=81da95e5c9b6a2bc50944f4656919ae0&type=album)
После чего будет доступен поиск из таблиц схемы app:
![avatar](https://sun9-69.userapi.com/impg/7-RTiFLmRgKsz_xnB-7jaNrBmdB_XIqVVRMvjQ/94Skt2xGK-k.jpg?size=280x95&quality=96&sign=85e6f0117974a1875d0bfaab1b7ac589&type=album)
