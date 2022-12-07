#### Групповые роли и атрибуты
Атрибуты определяют свойства роли. Роль может иметь разные атрибуты, например, 
** CREATEDB ** (дает право на создание БД) и ** NOCREATEDB ** (не дает такого права).
Я создал новую БД и подключился к ней:
![avatar](https://sun9-30.userapi.com/impg/g2zIQJAcqnhDflRYEM50sABrMj56RNBejws3MQ/GUmKnhplnu0.jpg?size=539x96&quality=96&sign=ac28cf039c66a96dbff32248075876bc&type=album)
Создал пользователя kat с возможностью подключения(атрибут LOGIN) и создания других ролей(CREATEROLE):
![avatar](https://sun9-11.userapi.com/impg/SGSrUD7L4Jkmi0l0HptNk46ln97AXOOLCd_Hrg/-ZqKyddTcaI.jpg?size=657x330&quality=96&sign=1d07bcc408ceca62e3c01c82e793ee7e&type=album)
На снимке видно, что у роли kat действительно есть присвоенные при создании свойства.
Затем я изменил роль, предоставив ей возможность создания БД(команда ALTER ROLE имя CREATEDB):
![avatar](https://sun9-62.userapi.com/impg/657RfWgyDRD4BRKs3RoK9ed29e_uAWyoWSSVJw/MaCAq-NB1Rw.jpg?size=642x134&quality=96&sign=94bba324711bf6cfc77f5a8c63359c8e&type=album)
Видим,что роль обладает выше перечисленными правами.
##### Групповые роли 
Роль может быть включена в другую роль подобно тому, как пользователь Unix может быть включен в группу. Смысл такого включения состоит в том, что для роли становятся доступны атрибуты (и привилегии, о которых пойдет речь дальше), которыми обладает групповая роль.
Я создала групповую роль:
![avatar](https://sun9-22.userapi.com/impg/UfDmc_0wk7f85HqKwtb-zb6yjLBO6QkTh9fsgQ/gT08SwMH8zM.jpg?size=615x115&quality=96&sign=78ba2b474aeefe52dd88d281a8f1ab2e&type=album)
Затем изменила её, предоставив право на создания БД:
![avatar](https://sun9-82.userapi.com/impg/84p7pzDeYJm7zYYhmJjYwPQJhfraGq3vmIhU6A/7fjul-mL7uo.jpg?size=615x94&quality=96&sign=f764110c0082ace9df4590965ed55a06&type=album)
Теперь у меня есть групповая роль с неким правом. Теперь я создаю роль bob и предоствавляю ему членство в групповой роли(Включение выполняется командой GRANT):
![avatar](https://sun9-70.userapi.com/impg/mApOQQd6m1JfKxgJql0J-odgEObhfbR2pgpNSg/vLqAlyYw_EE.jpg?size=635x195&quality=96&sign=b34e21ab2863d39676a83fbfd012022b&type=album)
Видно, что bob стал пользователем - членом групповой роли. 
Отобрать права у пользователя группы можно командой REVOKE. Проверила это:
![avatar](https://sun9-21.userapi.com/impg/YK-qJy0SQaqSWIaOF_VKgaRMSUCEsIcZV4Up6w/tQmYZD4hDMs.jpg?size=629x212&quality=96&sign=afb3f505615e29b1ce54b823ff8be010&type=album)
bob покинул членство в групповой роли.
