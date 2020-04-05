# Даннная инструкция запрещает всем пользователям, кроме группы admin логин в выходные (суббота и воскресенье).

# Для решения задачи требуется редакитрование 3-х файлов:
# 1. /etc/pam.d/sshd
# 2. /etc/security/time.conf
# 3. /etc/security/access.conf


# В файл /etc/security/access.conf добавляем строки:
+:admin:ALL
-:ALL:ALL


# В файл /etc/security/access.conf добавляем строки
*;*;*;!Wd0000-2400
# таким образом задается запрет входа в выходные.

# объединяем эти 2 правил в файле /etc/pam.d/sshd:
account  [success=1 default=ignore]     pam_access.so
account  required     pam_time.so
# success=1 обозначает, что следующие правило игнорируется.


# Проверка логов /etc/log/auth.log:
Apr  5 22:52:18 rustam3-HP-ProBook-6460b sshd[1057]: fatal: Access denied for user rustam3 by PAM account configuration [preauth]
Apr  5 22:52:37 rustam3-HP-ProBook-6460b sshd[1059]: Accepted password for testpam1 from 192.168.0.104 port 57353 ssh2
Apr  5 22:52:37 rustam3-HP-ProBook-6460b sshd[1059]: pam_unix(sshd:session): session opened for user testpam1 by (uid=0)
# Список группы admin:
cat /etc/group | grep "^admin"
admin:x:1010:testpam1,testpam2
