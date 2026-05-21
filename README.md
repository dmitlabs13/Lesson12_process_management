# Lesson12_process_management

## задание
-написать свою реализацию ps ax используя анализ /proc
-Результат ДЗ - рабочий скрипт который можно запустить

## решение
```
#собственно простейший скрипт который заглядывает во все файлы процессов в папке /proc
# и достает информацию из полей

#начало скрипта

#!/bin/bash

for proc_file in /proc/[0-9]*/; do
echo "--------------------------------"

#выводим имя процесса
awk '/Name/ {print}' $proc_file/status
#Выводим pid
awk '/\<Pid\>/ {print}' $proc_file/status
#Выводим ppid
awk '/\<PPid\>/ {print}' $proc_file/status
#Выводим состояние процесса 
awk '/State/ {print}' $proc_file/status
#Выводим команду, запустившую процесс
awk '/Cmdline/ {print}' $proc_file/status

done
#конец скрипта

```

Вывод выглядит вот так:
```
--------------------------------
Name:   kworker/R-kstrp
Pid:    89
PPid:   2
State:  I (idle)
--------------------------------
Name:   z_vdev_file
Pid:    890
PPid:   2
State:  S (sleeping)
--------------------------------
Name:   z_vdev_file
Pid:    891
PPid:   2
State:  S (sleeping)
--------------------------------
Name:   z_vdev_file
Pid:    899
PPid:   2
State:  S (sleeping)
--------------------------------
Name:   kworker/u3:0
Pid:    91
PPid:   2
State:  I (idle)
--------------------------------

```





