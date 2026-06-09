## Практическая работа на тему "Организация сети"

1. Создал с помощью [манифестов terraform](tf/main.tf):

- Новую VPC cloud-net
- Публичную подсеть с именем public
- NAT инстанцию с указанным в задании IP и image_id
- Виртуальную машину pub-01

2. Проверил подключение к ВМ и ее соединение с интернет

```
alex@uxtu-note:~/Study/cloud-net/cloud-net/tf$ ssh ubuntu@81.26.191.37
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-179-generic x86_64)
...
Last login: Tue Jun  9 12:35:39 2026 from 46.39.228.157
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@pub-01:~$ curl ipinfo.io/ip
81.26.191.37ubuntu@pub-01:~$
```

3. Создал теми же манифестами:

- Подсеть private
- Таблицу маршрутизации
- Виртуальную машину pvt-01

4. Проверил подключение к pvt-01 через SSH jump и убедился, что доступ к интернет есть

```


```
