## Практическая работа на тему "Организация сети"

1. Создал с помощью [манифестов terraform](tf/main.tf):

- Новую VPC cloud-net
- Публичную подсеть с именем public
- NAT инстанцию с указанным в задании IP и image_id
- Виртуальную машину pub-01

2. Проверил подключение к ВМ и ее соединение с интернет

```
alex@uxtu-note:~/Study/cloud-net/cloud-net/tf$ ssh ubuntu@51.250.42.116
The authenticity of host '51.250.42.116 (51.250.42.116)' can't be established.
ED25519 key fingerprint is SHA256:tKvsohds9hFQuRQsy8WjlKRVitQZ+N6hv/C+Pu5ijXc.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '51.250.42.116' (ED25519) to the list of known hosts.
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-179-generic x86_64)
...
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@pub-01:~$ curl ipinfo.io/ip
51.250.42.116ubuntu@pub-01:~$
```

3. Создал теми же манифестами:

- Подсеть private
- Таблицу маршрутизации
- Виртуальную машину pvt-01

4. Проверил подключение к pvt-01 через SSH jump и убедился, что доступ к интернет есть

```
alex@uxtu-note:~/Study/cloud-net/cloud-net/tf$ ssh -J ubuntu@51.250.42.116 ubuntu@192.168.20.17
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-179-generic x86_64)
...
Last login: Tue Jun  9 18:38:29 2026 from 192.168.10.31
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@pvt-01:~$ ping ya.ru
PING ya.ru (77.88.55.242) 56(84) bytes of data.
64 bytes from ya.ru (77.88.55.242): icmp_seq=1 ttl=54 time=6.70 ms
64 bytes from ya.ru (77.88.55.242): icmp_seq=2 ttl=54 time=6.54 ms
64 bytes from ya.ru (77.88.55.242): icmp_seq=3 ttl=54 time=6.66 ms
^C
--- ya.ru ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 6.539/6.634/6.701/0.069 ms
```
