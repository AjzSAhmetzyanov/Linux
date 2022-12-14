## Part 1. Установка системы
* Образ системы был скачан с сайта https://releases.ubuntu.com/20.04/
* Вывод названия системы с помощью команды `cat /etc/issue`<br>
***![1](images/Screen%20Shot%202022-06-15%20at%202.56.52%20PM.png)<b>
## Part 2. Создание пользователя
* Создан новый пользователь user2<br>
![2](images/Screen%20Shot%202022-07-03%20at%207.32.52%20PM.png)<br>
* Новый пользователь добавлен в группу adm<br>
![3](images/Screen%20Shot%202022-07-03%20at%207.33.56%20PM.png)
![4](images/Screen%20Shot%202022-07-03%20at%207.35.33%20PM.png)
* Отображение команды `cat /etc/passwd`<br>
![5](images/Screen%20Shot%202022-07-03%20at%207.36.21%20PM.png)
***
## Part 3. Настройка сети ОС
* Команды для смены `hostname` на `user1`<br>
![6](images/Screen%20Shot%202022-07-05%20at%206.09.47%20PM.png)<br>
![7](images/Screen%20Shot%202022-07-05%20at%206.11.42%20PM.png)<br>
![8](images/Screen%20Shot%202022-07-06%20at%204.05.21%20PM.png)<br>
* Установка временной зоны, соответсвующей местоположению<br>
![](images/Screen%20Shot%202022-07-03%20at%207.45.28%20PM.png)<br>
* Вывод названий сетевых интерфейсов командой `id link`<br>
![9](images/Screen%20Shot%202022-07-03%20at%207.46.10%20PM.png)<br>
![10](images/Screen%20Shot%202022-07-03%20at%208.20.02%20PM.png))<br>
```
Интерфейс lo по-другому называется loopback или обратная
петля. Он используется для отладки сетевых программ и запуска
серверных приложений на локальной машине. С этим интерфейсом 
всегда связан адрес 127.0.0.1. У него есть dns-имя – 
localhost.
```
* Получение ip адреса устройства с помощью команды `ip r`<br>
![10](images/Screen%20Shot%202022-07-03%20at%208.19.26%20PM.png)<br>
![](images/Screen%20Shot%202022-07-06%20at%205.30.33%20PM.png)
<br>
```
Для работы по сети любому устройству требуется IP-адрес. В
протоколе IPv4 это числовой идентификатор, состоящий из 4
разрядов, каждый из которых отделяется точкой, без него
устройство не может быть определено в сетевой инфраструктуре.
Прикладной протокол DHCP выполняет всю работу по подбору
сетевых настроек автоматически, без необходимости присваивать
вручную каждому устройству свой IP-адрес. Это очень упрощает
работу системного администратора в случае расширения сети.
```
* Вывод внешнего ip-адреса шлюза (ip) и внутреннего IP-адреса шлюза, он же ip-адрес по умолчанию (gw).<br>
![11](images/Screen%20Shot%202022-07-03%20at%208.20.30%20PM.png)<br>
* Задание статичных ip адрессов с помощью сервиса netplan<br>
>Здесь можно почитать по netplan https://habr.com/ru/post/448400/

![12](images/Screen%20Shot%202022-07-05%20at%206.19.09%20PM.png)<br>
![13](images/Screen%20Shot%202022-07-05%20at%206.16.44%20PM.png)<br>
* Принятие внесенных изменений и вывод ip адреса устройства с помощью команды `ip r`<br>
![14](images/Screen%20Shot%202022-07-03%20at%208.27.35%20PM.png)<br>
* Пингование удаленных хостов 1.1.1.1 и ya.ru<br>
![15](images/Screen%20Shot%202022-07-03%20at%208.31.22%20PM.png)<br>
![16](images/Screen%20Shot%202022-07-03%20at%208.31.56%20PM.png)<br>
***
## Part 4. Обновление ОС
* Команда для получения пакет для обновления: <br>
`sudo apt update`<br>
* Команда для установки пакетов на устройство: <br>
`sudo apt upgrade`<br>
* Подтвеждение, что все пакеты обновлены<br>
![19](images/Screen%20Shot%202022-07-03%20at%208.34.39%20PM.png)<br>
***
## Part 5. Использование команды sudo
* Использование команды `passwd` для создания пароля для new_user<br>
* Использование команды `su` для переключения между пользователями<br>
* Использование команды `sudo usermod -aG sudo new_user` для наделения new_user правами суперпользователя<br>
* Использование команды `sudo hostnamectl set-hostname hserver` для демонстрации наличия у пользователя new_user прав суперпользователя<br>
![20](images/Screen%20Shot%202022-07-03%20at%208.37.17%20PM.png)<br>
```
Команда sudo дает право пользователю вносить любые изменение в
систему. По-другому дает права суперпользователя.
```
***
## Part 6. Установка и настройка службы времени
* Установка службы автоматической синхронизации времени `ntp`<br>
![20](images/Screen%20Shot%202022-07-03%20at%208.38.08%20PM.png)<br>
* Определение сервера времени с помощью команды `sudo ntpdate 1.ro.pool.ntp.org`<br>
![20](images/Screen%20Shot%202022-07-03%20at%208.40.13%20PM.png))<br>
***
## Part 7. Установка и использование текстовых редакторов
* Установка текстовых редакторов vim, nano, joe<br>
![21](images/Screen%20Shot%202022-07-03%20at%208.40.42%20PM.png)<br>
![22](images/Screen%20Shot%202022-07-03%20at%208.45.55%20PM.png)<br>
![23](images/Screen%20Shot%202022-07-03%20at%208.47.03%20PM.png)<br>
* Создание файла в nano с помощью команды `nano nano_test.txt`, печать своего ника и выход с сохранением `Ctrl+x` -> `y`<br>
![24](images/Screen%20Shot%202022-07-04%20at%203.35.19%20PM.png)<br>
* Создание файла в vim с помощью команды `vim vim_test.txt` -> `i`, печать своего ника и выход с сохранением `esc` -> `:` -> `wq`<br>
![26](images/Screen%20Shot%202022-07-04%20at%203.36.13%20PM.png)<br>
* Создание файла в joe с помощью команды `joe joe_test.txt`, печать своего ника и выход с сохранением `Ctrl+K+Q` -> `Enter`<br>
![27](images/Screen%20Shot%202022-07-04%20at%207.34.29%20PM.png)<br>
* Редактирование файла в nano с помощью команды `nano nano_test.txt`, печать `21 School 21` и выход без сохранения с помощью `Ctrl+x` -> `n`<br>
![32](images/Screen%20Shot%202022-07-05%20at%2012.31.03%20PM.png)<br>
* Редактирование файла в vim с помощью команды `vim vim_test.txt`, печать `21 School 21` и выход без сохранения с помощью `esc` -> `:` -> `q!`<br>
![28](images/Screen%20Shot%202022-07-05%20at%2012.32.01%20PM.png))<br>
* Редактирование файла в joe с помощью команды `joe joe_test.txt`, печать `21 School 21` и выход без сохранения с помощью `Ctrl+c` -> `y`<br>
![31](images/Screen%20Shot%202022-07-05%20at%2012.32.46%20PM.png)<br>
* Поиск с заменой в nano с помощью `Ctrl+\` -> `hash` -> `Enter` -> `hsah` -> `Enter`<br>
![36](images/Screen%20Shot%202022-07-05%20at%2012.34.52%20PM.png))<br>
![37](images/Screen%20Shot%202022-07-05%20at%2012.35.46%20PM.png))<br>
![38](images/Screen%20Shot%202022-07-05%20at%2012.36.01%20PM.png)<br>
* Поиск с заменой в vim с помощью `:s/hash/hsah`<br>
![34](images/Screen%20Shot%202022-07-05%20at%2012.36.55%20PM.png)<br>
![35](images/Screen%20Shot%202022-07-05%20at%2012.37.11%20PM.png))<br>
* Поиск с заменой в joe с помощью  `Ctrl+k+f` -> `r` -> `hash` -> `hsah`<br>
![42](images/Screen%20Shot%202022-07-05%20at%2012.39.07%20PM.png)<br>
![43](images/Screen%20Shot%202022-07-05%20at%2012.39.27%20PM.png)<br>
![44](images/Screen%20Shot%202022-07-05%20at%2012.39.41%20PM.png)<br>
***
## Part 8. Установка и базовая настройка сервиса SSHD
* Установка службы sshd с помощью команды `sudo apt install openssh-server`<br>
![46](images/Screen%20Shot%202022-07-05%20at%2012.46.27%20PM.png)<br>
* Добавление автостарта службы при запуске системы с помощью команды `sudo systemctl enable ssh`<br>
![47](images/Screen%20Shot%202022-07-05%20at%2012.47.35%20PM.png)<br>
* Перенастройка службы sshd на порт 2022<br>
  * Открываем файл конфигурации с помощью команды `sudo vim /etc/ssh/sshd_config`<br>
![49](images/Screen%20Shot%202022-07-05%20at%2012.48.32%20PM.png))<br>
  * Раскомменитруем сточку `Port 22` и поменяем ее значение на `Port 2022`<br>
![50](images/Screen%20Shot%202022-07-05%20at%2012.49.09%20PM.png))<br>
![51](images/Screen%20Shot%202022-07-05%20at%206.28.11%20PM.png)<br>
  * Перезапускаем службу sshd с помощью команды `sudo systemctl restart ssh` и проверяем значение порта с помощью команды `netstat -tan`<br>
![52](images/Screen%20Shot%202022-07-05%20at%208.51.54%20PM.png)<br>
* Вызов команды `ps -C sshd` для показа наличия процесса sshd<br>
![48](images/Screen%20Shot%202022-07-05%20at%202.09.35%20PM.png)<br>
```
Команда ps выводит список текущих процессов.
Опции для данной команды:
-A, -e, (a) - выбрать все процессы;
-a - выбрать все процессы, кроме фоновых;
-d, (g) - выбрать все процессы, даже фоновые, кроме процессов сессий;
-N - выбрать все процессы кроме указанных;
-С - выбирать процессы по имени команды;
-G - выбрать процессы по ID группы;
-p, (p) - выбрать процессы PID;
--ppid - выбрать процессы по PID родительского процесса;
-s - выбрать процессы по ID сессии;
-t, (t) - выбрать процессы по tty;
-u, (U) - выбрать процессы пользователя.

```
***
## Part 9. Установка и использование утилит top, htop
* Установка утилиты htop, утилита top уже была установлена на устройстве<br>
![53](images/Screen%20Shot%202022-07-05%20at%202.10.02%20PM.png)<br>
* Вывод команды `top`<br>
![54](images/Screen%20Shot%202022-07-05%20at%202.10.25%20PM.png)<br>
  - uptime: `2.05`
  - количество авторизованных пользователей: `1 user`
  - общую загрузку системы: _Load average — средняя нагрузка на сервер: отображаются значения за одну, пять и 15 минут назад_ `0.15, 0.04, 0.01`
  - общее количество процессов: `124 total`
  - загрузку cpu: `0.02%`
  - загрузку памяти: `188.5 MiB`
  - pid процесса занимающего больше всего памяти: `1`
  - pid процесса, занимающего больше всего процессорного времени: `2891`
* Вывод команды `htop`<br>
![55](images/Screen%20Shot%202022-07-05%20at%202.10.50%20PM.png)<br>
  * Отсортированный по PID после команды `f6`<br>
  ![56](images/Screen%20Shot%202022-07-05%20at%202.11.50%20PM.png))<br>
  * Отсортированный по PERCENT_CPU после команды `f6`<br>
  ![57](images/Screen%20Shot%202022-07-05%20at%202.12.12%20PM.png)<br>
  * Отсортированный по PERCENT_MEM после команды `f6`<br>
  ![58](images/Screen%20Shot%202022-07-05%20at%202.12.41%20PM.png))<br>
  * Отсортированный по TIME после команды `f6`<br>
  ![59](images/Screen%20Shot%202022-07-05%20at%202.13.00%20PM.png))<br>
  * Отфильтрованный для процесса sshd с помощью команды `f4`<br>
  ![60](images/Screen%20Shot%202022-07-05%20at%202.58.24%20PM.png)<br>
  * C процессом syslog, найденным, используя поиск c помощью команды `f3`<br>
  ![61](images/Screen%20Shot%202022-07-05%20at%203.50.38%20PM.png)<br>
  * C добавленным выводом hostname, clock и uptime c помощью изменения настроек через команду `f2`<br>
  ![62](images/Screen%20Shot%202022-07-05%20at%203.55.06%20PM.png)<br>
***
## Part 10. Использование утилиты fdisk
* Запуск команды `df`<br>
![63](images/Screen%20Shot%202022-07-05%20at%203.59.46%20PM.png)<br>
  * Название жесткого диска `VBOX`<br>
  * Размер жесткого диска `20 GiB`<br>
  * Количество секторов `3`<br>
  * Размер swap `1.9 GiB`<br>
![64](images/Screen%20Shot%202022-07-05%20at%204.00.41%20PM.png)<br>
***
## Part 11. Использование утилиты df
* Выполнение команды `df`
    - размер раздела `10271528`
    - размер занятого пространства `5056180`
    - размер свободного пространства `8292144`
    - процент использования `48%`
    - единица измерения - блоки по 1 килобайту
![65](images/Screen%20Shot%202022-07-05%20at%204.01.00%20PM.png)<br>
* Выполнение команды `df -Th`
  - размер раздела `9.8G`
  - размер занятого пространства `4.5G`
  - размер свободного пространства `4.3G`
  - процент использования `48%`
  - тип файлофой системы раздела `ext4`
![66](images/Screen%20Shot%202022-07-05%20at%204.01.14%20PM.png))<br>
***
## Part 12. Использование утилиты du
* Вывод размера папки /home с помощью команды `sudo du -lhs /home`<br>
![67](images/Screen%20Shot%202022-07-05%20at%204.01.44%20PM.png)<br>
* Вывод размера папки /var с помощью команды `sudo du -lhs /var`<br>
![68](images/Screen%20Shot%202022-07-05%20at%204.02.00%20PM.png)<br>
* Вывод размера папки /var/log с помощью команды `sudo du -lhs /var/log`<br>
![69](images/Screen%20Shot%202022-07-05%20at%204.02.12%20PM.png)<br>
* Вывод размеров содержимого /var/log с помощью команды `sudo du -lh /var/log/*`<br>
![69.1](images/Screen%20Shot%202022-07-05%20at%204.02.29%20PM.png)<br>
***
## Part 13. Установка и использование утилиты ncdu
* Установка утилиты ncdu<br>
![78](images/Screen%20Shot%202022-07-05%20at%204.03.10%20PM.png)<br>
* Команда `ncdu /home`<br>
![79](images/Screen%20Shot%202022-07-05%20at%204.03.31%20PM.png))<br>
* Команда `ncdu /var`<br>
![80](images/Screen%20Shot%202022-07-05%20at%204.05.11%20PM.png)<br>
* Команда `ncdu /var/log`<br>
![81](images/Screen%20Shot%202022-07-05%20at%204.05.30%20PM.png))<br>
***
## Part 14. Работа с системными журналами
* Просмотр журналов командой `cat *путь_к_журналу*`
* Вывод журнала авторизации пользователей командой `cat /var/log/auth.log`<br>
`Время последнего входа пользователем luigiket c помощью команды lastlog`<br>
![70](images/Screen%20Shot%202022-07-05%20at%204.24.10%20PM.png)<br>
* Перезапуск службы sshd с помощью команды `sudo sysremctl restart sshd`<br>
![71](images/Screen%20Shot%202022-07-05%20at%208.51.54%20PM.png)<br>
* Отображение сообщений о рестарте службы в логах с помощью команды `cat /var/log/syslog`
![72](images/Screen%20Shot%202022-07-05%20at%206.38.52%20PM.png)<br>
***
## Part 15. Использование планировщика заданий CRON
* Вывод на экран текущих задач планировщика CRON с помощью команды `crontab -l` <br>
![73](images/Screen%20Shot%202022-07-05%20at%209.13.22%20PM.png)<br>
* Открытие файла с задачами CRON с помощью команды `crontab -e` (в первый раз будет предложен выбор из установленных тектовых редакторов для работы с файлом в нем)<br>
![74](images/Screen%20Shot%202022-07-05%20at%204.12.23%20PM.png)<br>
* Поиск выполнения задач CRON в логах системы с помощью команды `grep CRON /var/log/syslog`<br>
![75](images/Screen%20Shot%202022-07-05%20at%204.12.59%20PM.png)<br>
* Вывод списка текущих задач для CRON с помощью команды `cat /etc/crontab /etc/cron.d/*`<br>
![76](images/Screen%20Shot%202022-07-05%20at%204.13.46%20PM.png)<br>
* Удаление всех задач из CRON с помощью команды `crontab -r` и проверка текущих задач с помощью `crontab -l`<br>
![77](images/Screen%20Shot%202022-07-05%20at%204.14.11%20PM.png)<br>
