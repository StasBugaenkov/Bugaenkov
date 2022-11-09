#### Аутентификация
При подключении клиента сервер должен выполнить несколько задач.Во-первых, идентифицировать пользователя, то есть определить его имя. Для этого пользователь представляется, но указанное имя может отличаться от имени пользователя БД (например, если пользователь представляется своим именем в ОС).
В целях выполнения данной лр я создала суперпользователя kat:
![avatar](https://sun9-24.userapi.com/impg/Mg1ABDx3zMZcfAwwRmeLgX1F-2b8A_Q9i8sueg/M9j6mWiC1YI.jpg?size=619x135&quality=96&sign=9201715919e35b2ad8917220d9b14232&type=album)
Затем я сохранила файл pg_hba.conf, чтобы иметь возможность восстановить:
![avatar](https://sun9-70.userapi.com/impg/QDZ4JrK2Yy9Jv3zqR07a8VvVnlZSRfNb02YQgA/8SCQa5IHB7A.jpg?size=677x32&quality=96&sign=491975ea503997ea7d78f7797cd5281f&type=album)
Проверила содержимое pg_hba.conf(используя представление pg_hba_file_rules):
![avatar](https://sun9-10.userapi.com/impg/vupbUl0RSJudUqEKEnHUAbVnVX5Nud7OdA_ZVQ/RGb0KFI4Zrw.jpg?size=594x189&quality=96&sign=562641d0ade742f8cc0ca4a408636e7f&type=album)
Затем перезаписала pg_hba.conf с нуля:
![avatar](https://sun9-69.userapi.com/impg/1d8mJLped8coy7P4E00KbZhmh795wnxxnll5Dg/CgumskvITs0.jpg?size=560x134&quality=96&sign=304a4a4c7a5fd91f52b27bc17d1d4199&type=album)
Перезагрузила файл для сохранения настроек с помощью команды sudo pg_ctlcluster 12 main reload и просмотрела содержимое файла:
![avatar](https://sun9-78.userapi.com/impg/Q7wdOA58twFuGa5bzXD_JmtQxk99wcT-DsZvNQ/rbLuEMrH1Hk.jpg?size=590x225&quality=96&sign=23f92d85356d52109696198f6633c027&type=album)
Проверила подключение. Подключилась как пользователь kat к тестовой БД bd1:
![avatar](https://sun9-87.userapi.com/impg/qawpIlDhDBnnmI54_-NW6SS7gIBiPwn0AcDSvg/hxeZkMYj5Kg.jpg?size=805x69&quality=96&sign=d37360eefe412a35b9ae69c3a497e24a&type=album)
На снимке видно, что подключение прошло успешно.

