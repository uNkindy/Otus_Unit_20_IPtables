### Домашнее задание №20 (iptables)
За основу взят стенд из ДЗ №18 (IP). Используются следующие виртуальные машины (ВМ): inetRouter, centalRouter, centralServer. Дополнительно создана ВМ inetRouter2.
#### 1. Реализация knocking port:
- на ВМ inetRouter устанавливаются пакеты iptables, iptables-services.
- на ВМ inetRouter пишется правило для реализации [knocking port]();
- на ВМ centralRouter установлен пакет nmap, написан [скрипт](), стучащийся на порты 8881, 7777, 9991.
- после простукивания портов на inetRouter можно зайти в течение 30 секунд.
Проверка работы скрипта:
- попытка захода по ssh без knocking порта:
```console
[root@centralRouter vagrant]# ssh 192.168.56.241

```
- выполняем скрипт knock.sh:
```console
[root@centralRouter vagrant]# ./knock.sh 192.168.56.241 8881 7777 9991

Starting Nmap 6.40 ( http://nmap.org ) at 2022-12-22 15:57 UTC
Warning: 192.168.56.241 giving up on port because retransmission cap hit (0).
Nmap scan report for 192.168.56.241
Host is up (0.00032s latency).
PORT     STATE    SERVICE
8881/tcp filtered unknown
MAC Address: 08:00:27:ED:15:E8 (Cadmus Computer Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.34 seconds

Starting Nmap 6.40 ( http://nmap.org ) at 2022-12-22 15:57 UTC
Warning: 192.168.56.241 giving up on port because retransmission cap hit (0).
Nmap scan report for 192.168.56.241
Host is up (0.00037s latency).
PORT     STATE    SERVICE
7777/tcp filtered cbt
MAC Address: 08:00:27:ED:15:E8 (Cadmus Computer Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.34 seconds

Starting Nmap 6.40 ( http://nmap.org ) at 2022-12-22 15:57 UTC
Warning: 192.168.56.241 giving up on port because retransmission cap hit (0).
Nmap scan report for 192.168.56.241
Host is up (0.00036s latency).
PORT     STATE    SERVICE
9991/tcp filtered issa
MAC Address: 08:00:27:ED:15:E8 (Cadmus Computer Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.34 seconds
```
- заходим по ssh на inetRouter:
```console
[root@centralRouter vagrant]# ssh 192.168.56.241
root@192.168.56.241's password: 
Last login: Thu Dec 22 14:35:14 2022 from 192.168.56.240
[root@inetRouter ~]# 
```
___
#### Для подготовки стенда написан [playbook]().