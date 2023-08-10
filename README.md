# Задание к практикуму по работе с Zabbix

### Цели задания

1. Научиться планировать мониторинг инфраструктуры.
2. Настроить базовые проверки с помощью системы мониторинга Zabbix.
3. Закрепить знания по архитектуре системы мониторинга Zabbix.
4. Попрактиковаться в подключении хостов по SNMP.

### Чеклист готовности к выполнению заданий практикума 

1. Ранее по программе изучены материалы занятий: "L2-сеть", "L3-сеть", "L4-сеть", "Firewall".
2. В программе VirtualBox созданы три виртуальные машины с Debian (или Ubuntu), названы следующим образом: Zabbix, client1, client2 (подобное задание вы выполняли в [занятии "Firewall"](https://github.com/netology-code/snet-homeworks/blob/snet-22/4-09.md)).
3. На ВМ Zabbix установите Zabbix-сервер.
4. В VirtualBox настройте сетевые интерфейсы виртуальных машин так, чтобы у всех ВМ была связь друг с другом и с Интернетом.

### Инструменты и дополнительные материалы, которые понадобятся для выполнения задания

1. Одна виртуальная машина с Zabbix с доступом к Интернету.
2. Две виртуальные машины (client1, client2) с ОС Linux, соединенные по сети с ВМ Zabbix.
3. Утилита snmpwalk, установленная на ВМ Zabbix (опционально).
4. Утилита tcpdump, установленная на ВМ Zabbix (опционально).
   
---

## Задание 1. Настройка мониторинга Интернет-хоста

### Описание задания

Настройте мониторинг Интернет-хоста 8.8.8.8 при помощи встроенного шаблона Template ICMP Ping. Убедитесь, что триггеры работают при потере связи с 8.8.8.8.

### Этапы выполнения задания

1. Создайте host 8.8.8.8 для группы Internet-services.
2. Подключите шаблон Template ICMP Ping к хосту 8.8.8.8.
3. Дождитесь получения данных.
4. Заблокируйте маршрут до 8.8.8.8 (ip route add blackhole 8.8.8.8).
5. Убедитесь, что триггер потери связи с 8.8.8.8 сработал.

### Требование к результату

1. Убедитесь, что триггер потери связи с 8.8.8.8 сработал.
2. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.

 
## Задание 2. Настройка мониторинга ВМ client1 и client2

### Описание задания

Настройте мониторинг ВМ client1 и client2 при помощи встроенного шаблона Template OS Linux by Zabbix agent. Убедитесь, что агенты присылают данные.


### Этапы выполнения задания

1. Установите Zabbix-agent на ВМ client1 и client2
2. Отредактируйте конфигурационный файл zabbix_agentd.conf на каждом клиенте, добавив параметр Server=IP, где IP - IP-адрес ВМ Zabbix
3. Перезагрузите службу zabbix-agent: systemctl restart zabbix-agent.
4. Создайте host client1 и client2 для группы Linux-servers.
5. Подключите шаблон Template OS Linux by Zabbix agent к хостам client1 и client2.
6. Убедитесь, что данные от client1 и client2 появились в системе мониторинга.

### Требование к результату

1. Убедитесь, что данные от client1 и client2 доступны в разделе Latest data.
2. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.

---

## Задание 3. Настройка мониторинга облачного роутера

### Описание задания

Настройте мониторинг облачного роутера netology_csr при помощи встроенного шаблона Cisco IOS versions 12.0._3_T-12.2_3.5 by SNMP. Убедитесь, что агенты присылают данные.

### Этапы выполнения задания

1. Создайте host netology_csr для группы Cloud-routers (IP - 45.134.127.23, метод опроса - SNMP, community - netology_snmp).
2. Подключите шаблон Cisco IOS versions 12.0._3_T-12.2_3.5 by SNMP.
3. Убедитесь, что даннные от netology_csr появились в системе мониторинга.

### Требование к результату

1. Убедитесь, что данные от netology_csr доступны в разделе Latest data.
3. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.
