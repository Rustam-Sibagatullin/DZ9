# DZ9
## Создаем пользователей

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ useradd -m -s /bin/bash user1
				useradd: Permission denied.
				useradd: не удалось заблокировать /etc/passwd; попробуйте ещё раз позже.
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo useradd -m -s /bin/bash user1
				[sudo] пароль для rustam4:       
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo useradd -m -s /bin/bash user2
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id
				uid=1000(rustam4) gid=1000(rustam4) группы=1000(rustam4),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),112(lpadmin),121(scanner),129(sambashare)
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user1
				uid=1002(user1) gid=1002(user1) группы=1002(user1)
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user2
				uid=1003(user2) gid=1003(user2) группы=1003(user2)
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ cat /etc/passwd
				root:x:0:0:root:/root:/bin/bash
				daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
				bin:x:2:2:bin:/bin:/usr/sbin/nologin
				sys:x:3:3:sys:/dev:/usr/sbin/nologin
				sync:x:4:65534:sync:/bin:/bin/sync
				games:x:5:60:games:/usr/games:/usr/sbin/nologin
				man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
				lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
				mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
				news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
				uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
				proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
				www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
				backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
				list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
				irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
				gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
				nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
				systemd-network:x:100:102:systemd Network Management,,,:/run/systemd/netif:/usr/sbin/nologin
				systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd/resolve:/usr/sbin/nologin
				syslog:x:102:106::/home/syslog:/usr/sbin/nologin
				messagebus:x:103:107::/nonexistent:/usr/sbin/nologin
				_apt:x:104:65534::/nonexistent:/usr/sbin/nologin
				uuidd:x:105:111::/run/uuidd:/usr/sbin/nologin
				cups-pk-helper:x:106:112:user for cups-pk-helper service,,,:/home/cups-pk-helper:/usr/sbin/nologin
				kernoops:x:107:65534:Kernel Oops Tracking Daemon,,,:/:/usr/sbin/nologin
				rtkit:x:108:113:RealtimeKit,,,:/proc:/usr/sbin/nologin
				avahi-autoipd:x:109:114:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/usr/sbin/nologin
				usbmux:x:110:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
				systemd-coredump:x:111:117:systemd core dump processing,,,:/run/systemd:/usr/sbin/nologin
				ntp:x:112:118::/nonexistent:/usr/sbin/nologin
				lightdm:x:113:119:Light Display Manager:/var/lib/lightdm:/bin/false
				dnsmasq:x:114:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
				saned:x:115:122::/var/lib/saned:/usr/sbin/nologin
				nm-openvpn:x:116:123:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
				avahi:x:117:124:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/usr/sbin/nologin
				colord:x:118:125:colord colour management daemon,,,:/var/lib/colord:/usr/sbin/nologin
				speech-dispatcher:x:119:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
				pulse:x:120:126:PulseAudio daemon,,,:/var/run/pulse:/usr/sbin/nologin
				hplip:x:121:7:HPLIP system user,,,:/var/run/hplip:/bin/false
				geoclue:x:122:128::/var/lib/geoclue:/usr/sbin/nologin
				rustam4:x:1000:1000:rustam4,,,:/home/rustam4:/bin/bash
				vboxadd:x:999:1::/var/run/vboxadd:/bin/false
				postfix:x:123:131::/var/spool/postfix:/usr/sbin/nologin
				rustam5:x:1001:1001:rustam5,,,,:/home/rustam5:/bin/bash
				user1:x:1002:1002::/home/user1:/bin/bash
				user2:x:1003:1003::/home/user2:/bin/bash
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 

* Что означают опции -m и -s

			
				
       -m, --create-home
           Создать домашний каталог пользователя, если он не существует. Файлы и каталоги, содержащиеся в каталоге шаблонов (который можно
           указать с помощью параметра the -k option), будут скопированы в домашний каталог.

           По умолчанию, если этот параметр не указан и не задана переменная CREATE_HOME, домашний каталог не создаётся.
		   
       -s, --shell ОБОЛОЧКА
           Имя регистрационной оболочки пользователя. По умолчанию это поле пусто, что вызывает выбор регистрационной оболочки по умолчанию
           согласно значению переменной SHELL из файла /etc/default/useradd, или по умолчанию используется пустая строка.

rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /home/
итого 16
drwxr-xr-x 25 rustam4 rustam4 4096 мар 14 21:20 rustam4
drwxr-xr-x 15 rustam5 rustam5 4096 мар  3 19:33 rustam5
drwxr-xr-x  4 user1   user1   4096 мар 14 21:22 user1
drwxr-xr-x  4 user2   user2   4096 мар 14 21:23 user2


## Создаем группу и добавляем туда пользователей
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo groupadd admins
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo gpasswd -a user1 admins
				Добавление пользователя user1 в группу admins
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo gpasswd -a user2 admins
				Добавление пользователя user2 в группу admins

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user1
				uid=1002(user1) gid=1002(user1) группы=1002(user1),1004(admins)
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user2
				uid=1003(user2) gid=1003(user2) группы=1003(user2),1004(admins)
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 

до добавления было вот так:				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user1
				uid=1002(user1) gid=1002(user1) группы=1002(user1)
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ id user2
				uid=1003(user2) gid=1003(user2) группы=1003(user2)


## Создать каталог от рута и дать права группе admins туда писать

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo chmod 770 /opt/upload
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx--- 2 root root 4096 мар 14 21:49 upload
				drwxr-xr-x 4 root root 4096 фев  1 23:58 vagrant
				drwxr-xr-x 8 root root 4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo chgrp admins /opt/upload
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx--- 2 root admins 4096 мар 14 21:49 upload
				drwxr-xr-x 4 root root   4096 фев  1 23:58 vagrant
				drwxr-xr-x 8 root root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 

		


* что означают права 770 ?
7 для владельца вход и листинг директории
7 для группы вход и листинг директории
0 у остальных нет права на входи в директорию (поэтому нет и просмотра)


* создать по файлу от пользователей user1 и user2 в каталоге /opt/uploads

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo passwd user1
				[sudo] пароль для rustam4:       
				Введите новый пароль UNIX: 
				Повторите ввод нового пароля UNIX: 
				passwd: пароль успешно обновлён
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo passwd user2
				Введите новый пароль UNIX: 
				Повторите ввод нового пароля UNIX: 
				passwd: пароль успешно обновлён
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ su - user1
				Пароль: 
				user1@rustam4-VirtualBox:~$ cd /opt/upload/
				user1@rustam4-VirtualBox:/opt/upload$ touch user1file
				user1@rustam4-VirtualBox:/opt/upload$ exit
				выход
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ su - user2
				Пароль: 
				user2@rustam4-VirtualBox:~$ cd /opt/upload/
				user2@rustam4-VirtualBox:/opt/upload$ touch user2file
				user2@rustam4-VirtualBox:/opt/upload$ ls -l
				итого 0
				-rw-rw-r-- 1 user1 user1 0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user2 user2 0 мар 14 22:25 user2file
				user2@rustam4-VirtualBox:/opt/upload$ 


* проверьте с какой группой создались файлы от каждого пользователя. Как думаете - почему?

файлы создались от группы user1 и user2 соотвественно:

				user2@rustam4-VirtualBox:/opt/upload$ ls -l
				итого 0
				-rw-rw-r-- 1 user1 user1 0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user2 user2 0 мар 14 22:25 user2file

т.к. у них gid=1002(user1) и gid=1003(user2)

				user2@rustam4-VirtualBox:/opt/upload$ id user1
				uid=1002(user1) gid=1002(user1) группы=1002(user1),1004(admins)
				user2@rustam4-VirtualBox:/opt/upload$ id user2
				uid=1003(user2) gid=1003(user2) группы=1003(user2),1004(admins)

				

* (*) попробуйте сменить текущую группу пользователя  ```newgrp admins``` у пользователя user2 и создайте еще файл
* приложить ```ls -l /opt/upload```  в  README.md

				user2@rustam4-VirtualBox:/opt/upload$ touch user2file2
				user2@rustam4-VirtualBox:/opt/upload$ ls -l
				итого 0
				-rw-rw-r-- 1 user1 user1  0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user2 user2  0 мар 14 22:25 user2file
				-rw-rw-r-- 1 user2 admins 0 мар 14 23:52 user2file2

				

				
				
## Создать пользователя user3 и дать ему права писать в /opt/uploads

* Создайте пользователя user3
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo useradd -m -s /bin/bash user3
				[sudo] пароль для rustam4:       
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo passwd user3
				Введите новый пароль UNIX: 
				Повторите ввод нового пароля UNIX: 
				passwd: пароль успешно обновлён


* Попробуйте записать из под него файл в /opt/uploads. Должны получить ошибку

				user3@rustam4-VirtualBox:~$ touch /opt/uploads/user3file
				touch: невозможно выполнить touch для '/opt/uploads/user3file': Нет такого файла или каталога
				user3@rustam4-VirtualBox:~$ ls -l /opt/
				итого 12
				drwxrwx--- 2 root admins 4096 мар 14 23:52 upload
				drwxr-xr-x 4 root root   4096 фев  1 23:58 vagrant
				drwxr-xr-x 8 root root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				user3@rustam4-VirtualBox:~$ 




* Считайте acl с каталога. Добавьте черерз  setfacl права на запись в каталог.
```bash
man getfacl
man setfacl
getfacl /opt/upload
setfacl -m u:user3:rwx /opt/upload
su - user3
touch /opt/upload/user3_file
ls -l /opt/upload/user3_file
```
* приложить ```ls -l /opt/upload```  в  README.md
* приложить финишный acl  директории в README.md


				rustam4@rustam4-VirtualBox:~/Рабочий стол$ getfacl /opt/upload
				getfacl: Удаление начальных '/' из абсолютных путей
				# file: opt/upload
				# owner: root
				# group: admins
				user::rwx
				group::rwx
				other::---

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ setfacl -m u:user3:rwx /opt/upload
				setfacl: /opt/upload: Операция не позволена
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo setfacl -m u:user3:rwx /opt/upload
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ setfacl -m u:user3:rwx /opt/upload
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ getfacl /opt/upload
				getfacl: Удаление начальных '/' из абсолютных путей
				# file: opt/upload
				# owner: root
				# group: admins
				user::rwx
				user:user3:rwx
				group::rwx
				mask::rwx
				other::---
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx---+ 2 root admins 4096 мар 14 23:52 upload
				drwxr-xr-x  4 root root   4096 фев  1 23:58 vagrant
				drwxr-xr-x  8 root root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				user3@rustam4-VirtualBox:~$ ls -l /opt/upload/user3_file
				-rw-rw-r-- 1 user3 user3 0 мар 15 00:02 /opt/upload/user3_file


## Установить  SUID  флаг на выполняемый файл

_текущие версии Linux игнорируют выставление SUID на shell скрипт (проеврка на shebang)_

* Установим suid бит на просмотрщик cat 
* В начале  попробуйте прочитать cat /etc/shadow  из под пользователя user3

				user3@rustam4-VirtualBox:~$ cat /etc/shadow
				cat: /etc/shadow: Отказано в доступе
				user3@rustam4-VirtualBox:~$ 


* Установить suid /bin/cat и прочитайте снова из под user3

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /bin/cat 
				-rwxr-xr-x 1 root root 35064 янв 18  2018 /bin/cat
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo chmod +s /bin/cat
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /bin/cat 
				-rwsr-sr-x 1 root root 35064 янв 18  2018 /bin/cat

				
				user3@rustam4-VirtualBox:~$ cat /etc/shadow
				root:$6$9xCsp2NF$3lp1.frf2sKmZdVnrx0fJPicG3Cs.pfuhLftoZU7Et/ZhLx3Z0AKdwzmJnI7ZgXCbX73tw9Bp8cudJaFRenBI.:18323:0:99999:7:::
				daemon:*:18246:0:99999:7:::
				bin:*:18246:0:99999:7:::
				sys:*:18246:0:99999:7:::
				sync:*:18246:0:99999:7:::



* В README.md добавьте оба результат
* Объясните почему
				
suid бит позволил выполнить просмотр, т.к. дает право запуска файла с правами владельца (в данном слуаче это root), потом просмотр файл идет от root-а.


##  Сменить владельца  /opt/uploads  на user3 и добавить sticky bit
```bash
chown user3 /opt/upload
chmod +t /opt/upload
su - user1
touch /opt/upload/user1_file_test
ls -l /opt/upload/user1_file_test
su - user3
rm -f  /opt/upload/user1_file_test
```
				ustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx---+ 2 root admins 4096 мар 15 00:02 upload
				drwxr-xr-x  4 root root   4096 фев  1 23:58 vagrant
				drwxr-xr-x  8 root root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo chown user3 /opt/upload
		
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx---+ 2 user3 admins 4096 мар 15 00:02 upload
				drwxr-xr-x  4 root  root   4096 фев  1 23:58 vagrant
				drwxr-xr-x  8 root  root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 


				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo chmod +t /opt/upload
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /opt/
				итого 12
				drwxrwx--T+ 2 user3 admins 4096 мар 15 00:28 upload
				drwxr-xr-x  4 root  root   4096 фев  1 23:58 vagrant
				drwxr-xr-x  8 root  root   4096 фев  1 23:46 VBoxGuestAdditions-6.1.2

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ su - user1
				Пароль: 
				 
				user1@rustam4-VirtualBox:~$ touch /opt/upload/user1_file_test
				user1@rustam4-VirtualBox:~$ ls -l  /opt/upload/
				итого 0
				-rw-rw-r-- 1 user1 user1  0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user1 user1  0 мар 15 00:31 user1_file_test
				-rw-rw-r-- 1 user2 user2  0 мар 14 22:25 user2file
				-rw-rw-r-- 1 user2 admins 0 мар 14 23:52 user2file2
				-rw-rw-r-- 1 user3 user3  0 мар 15 00:02 user3_file
				user1@rustam4-VirtualBox:~$ 


* Объясните почему user3 смог удалить файл, который ему не принадлежит

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ su - user3
				Пароль: 
				user3@rustam4-VirtualBox:~$ 
				user3@rustam4-VirtualBox:~$ rm -f  /opt/upload/user1_file_test
				user3@rustam4-VirtualBox:~$ ls -l  /opt/upload/user1_file_test
				ls: невозможно получить доступ к '/opt/upload/user1_file_test': Нет такого файла или каталога
				user3@rustam4-VirtualBox:~$ ls -l  /opt/upload/
				итого 0
				-rw-rw-r-- 1 user1 user1  0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user2 user2  0 мар 14 22:25 user2file
				-rw-rw-r-- 1 user2 admins 0 мар 14 23:52 user2file2
				-rw-rw-r-- 1 user3 user3  0 мар 15 00:02 user3_file
				user3@rustam4-VirtualBox:~$ 


user3 смог удалить это файл, т.к. диркетория /opt/upload/ принадлежит ему и на нее выстален Sticky bit

* Создайте теперь файл от user1 и удалите его пользователем user1
				user1@rustam4-VirtualBox:~$ touch /opt/upload/user1_file_test1
				user1@rustam4-VirtualBox:~$ ls -l  /opt/upload/
				итого 0
				-rw-rw-r-- 1 user1 user1  0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user1 user1  0 мар 15 00:34 user1_file_test1
				-rw-rw-r-- 1 user2 user2  0 мар 14 22:25 user2file
				-rw-rw-r-- 1 user2 admins 0 мар 14 23:52 user2file2
				-rw-rw-r-- 1 user3 user3  0 мар 15 00:02 user3_file
				user1@rustam4-VirtualBox:~$ rm -f /opt/upload/user1_file_test1
				user1@rustam4-VirtualBox:~$ ls -l  /opt/upload/
				итого 0
				-rw-rw-r-- 1 user1 user1  0 мар 14 22:24 user1file
				-rw-rw-r-- 1 user2 user2  0 мар 14 22:25 user2file
				-rw-rw-r-- 1 user2 admins 0 мар 14 23:52 user2file2
				-rw-rw-r-- 1 user3 user3  0 мар 15 00:02 user3_file



* Объясните результат				
на дерикторию /opt/upload/ выставлен Sticky bit. Удалять файл могут владельцы файл, владельцы директории и суперпользователи.			
				

				
				
## Записи в sudoers
* попробуйте из под user3 выполнить ```sudo ls -l /root```

				user3@rustam4-VirtualBox:~$ sudo ls -l /root
				[sudo] пароль для user3:         
				Пользователю user3 запрещено выполнять '/bin/ls -l /root' с правами root на rustam4-VirtualBox.



* для редактирования sudoers используйте  visudo
* почему у вас не получилось?
```bash
vi /etc/sudoers.d/user3
user3	ALL=NOPASSWD:/bin/ls
```


				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /etc/sudoers.d/
				итого 12
				-r--r----- 1 root root  20 фев  7  2019 0pwfeedback
				-r--r----- 1 root root 278 дек 11 19:28 mintupdate
				-r--r----- 1 root root 958 янв 18  2018 README
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ vi /etc/sudoers.d/user3
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ sudo vi /etc/sudoers.d/user3
				[sudo] пароль для rustam4:       
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ 
				 
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ cat /etc/sudoers.d/user3
				user3	ALL=NOPASSWD:/bin/ls
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ ls -l /etc/sudoers.d/
				итого 16
				-r--r----- 1 root root  20 фев  7  2019 0pwfeedback
				-r--r----- 1 root root 278 дек 11 19:28 mintupdate
				-r--r----- 1 root root 958 янв 18  2018 README
				-rw-r--r-- 1 root root  27 мар 15 00:51 user3


				
				
				rustam4@rustam4-VirtualBox:~/Рабочий стол$ su - user3
				Пароль: 
				user3@rustam4-VirtualBox:~$ 
				user3@rustam4-VirtualBox:~$ 
				user3@rustam4-VirtualBox:~$ 
				user3@rustam4-VirtualBox:~$ 
				user3@rustam4-VirtualBox:~$ sudo ls -l /root
				итого 0
				user3@rustam4-VirtualBox:~$ 
				
				

* добавьте запись в /etc/sudoers.d/admins разрешающий группе admins любые команды с вводом пароля

				rustam4@rustam4-VirtualBox:~/Рабочий стол$ whereis passwd
				passwd: /usr/bin/passwd /etc/passwd /usr/share/man/man1/passwd.1.gz /usr/share/man/man1/passwd.1ssl.gz /usr/share/man/man5/passwd.5.gz

				rustam4@rustam4-VirtualBox:~$ sudo vi /etc/sudoers.d/admins 
				rustam4@rustam4-VirtualBox:~$ 
				rustam4@rustam4-VirtualBox:~$ cat /etc/sudoers.d/admins 
				%admins ALL=(ALL)NOPASSWD:/usr/bin/passwd

замена пароля от пользователя user1:

				rustam4@rustam4-VirtualBox:~$ su - user1
				Пароль: 
				user1@rustam4-VirtualBox:~$ passwd user3
				passwd: вы не можете посмотреть или изменить пароль user3.
				user1@rustam4-VirtualBox:~$ sudo passwd user3
				Введите новый пароль UNIX: 
				Повторите ввод нового пароля UNIX: 
				passwd: пароль успешно обновлён
				user1@rustam4-VirtualBox:~$ id
				uid=1002(user1) gid=1002(user1) группы=1002(user1),1004(admins)
				user1@rustam4-VirtualBox:~$ 


				


				
				
				






		   
