# ДЗ №25 Архитектура сетей
### Разворачиваем сетевую лабораторию
--------------------------------------------------------------------------------------------

# otus-linux
Vagrantfile - для стенда урока 9 - Network

# Дано
https://github.com/erlong15/otus-linux/tree/network
(ветка network)

Vagrantfile с начальным построением сети
- inetRouter
- centralRouter
- centralServer

тестировалось на virtualbox

# Планируемая архитектура
построить следующую архитектуру

Сеть office1
- 192.168.2.0/26 - dev
- 192.168.2.64/26 - test servers
- 192.168.2.128/26 - managers
- 192.168.2.192/26 - office hardware

Сеть office2
- 192.168.1.0/25 - dev
- 192.168.1.128/26 - test servers
- 192.168.1.192/26 - office hardware

Сеть central
- 192.168.0.0/28 - directors
- 192.168.0.32/28 - office hardware
- 192.168.0.64/26 - wifi

```
Office1 ---\
-----> Central --IRouter --> internet
Office2----/
```
Итого должны получится следующие сервера
- inetRouter
- centralRouter
- office1Router
- office2Router
- centralServer
- office1Server
- office2Server

# Теоретическая часть
- Найти свободные подсети
- Посчитать сколько узлов в каждой подсети, включая свободные
- Указать broadcast адрес для каждой подсети
- проверить нет ли ошибок при разбиении

# Практическая часть
- Соединить офисы в сеть согласно схеме и настроить роутинг
- Все сервера и роутеры должны ходить в инет черз inetRouter
- Все сервера должны видеть друг друга
- у всех новых серверов отключить дефолт на нат (eth0), который вагрант поднимает для связи
- при нехватке сетевых интервейсов добавить по несколько адресов на интерфейс


### Выполнение ДЗ

# Теоретическая часть
- Найти свободные подсети
- Посчитать сколько узлов в каждой подсети, включая свободные
- Указать broadcast адрес для каждой подсети
- проверить нет ли ошибок при разбиении

__Сеть office1__

- 192.168.2.0/26 - dev
```
Адрес сети - 192.168.2.0/26
Широковещательный адрес - 192.168.2.63/26
Пул доступных адресов для узлов сети - 192.168.2.1/26 - 192.168.2.62/26
```

- 192.168.2.64/26 - test servers
```
Адрес сети - 192.168.2.64
Широковещательный адрес - 192.168.2.127
Пул доступных адресов для узлов сети - 192.168.2.65 - 192.168.2.126
```

- 192.168.2.128/26 - managers
```
Адрес сети - 192.168.2.128
Широковещательный адрес - 192.168.2.191
Пул доступных адресов для узлов сети - 192.168.2.129 - 192.168.2.191
```

- 192.168.2.192/26 - office hardware
```
Адрес сети - 192.168.2.192
Широковещательный адрес - 192.168.2.255
Пул доступных адресов для узлов сети - 192.168.2.193 - 192.168.2.254
```

__Сеть office2__

- 192.168.1.0/25 - dev
```
Адрес сети - 192.168.1.0
Широковещательный адрес - 192.168.1.127
Пул доступных адресов для узлов сети - 192.168.1.1 - 192.168.1.126
```

- 192.168.1.128/26 - test servers
```
Адрес сети - 192.168.1.128
Широковещательный адрес - 192.168.1.191
Пул доступных адресов для узлов сети - 192.168.1.129 - 192.168.1.190
```

- 192.168.1.192/26 - office hardware
```
Адрес сети - 192.168.1.192
Широковещательный адрес - 192.168.1.255
Пул доступных адресов для узлов сети - 192.168.1.193 - 192.168.1.254
```
