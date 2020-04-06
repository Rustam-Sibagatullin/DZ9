# Даннная инструкция запрещает всем пользователям, кроме группы admin логин в выходные (суббота и воскресенье).

  Для решения задачи требуется редакитрование 3-х файлов:
1. /etc/pam.d/sshd
2. /etc/security/time.conf
3. /etc/security/access.conf


В файл /etc/security/access.conf добавляем строки:  
+:admin:ALL  
-:ALL:ALL


В файл /etc/security/access.conf добавляем строки  
*;*;*;!Wd0000-2400  
таким образом задается запрет входа в выходные.

объединяем эти 2 правила в файле /etc/pam.d/sshd:  
account  [success=1 default=ignore]     pam_access.so  
account  required     pam_time.so  
success=1 обозначает, что следующие 1 правило игнорируется.


Проверка логов /etc/log/auth.log:  
Apr  5 22:52:18 rustam3-HP-ProBook-6460b sshd[1057]: fatal: Access denied for user rustam3 by PAM account configuration [preauth]  
Apr  5 22:52:37 rustam3-HP-ProBook-6460b sshd[1059]: Accepted password for testpam1 from 192.168.0.104 port 57353 ssh2  
Apr  5 22:52:37 rustam3-HP-ProBook-6460b sshd[1059]: pam_unix(sshd:session): session opened for user testpam1 by (uid=0)  






rustam3@rustam3-HP-ProBook-6460b:~$ cat /etc/pam.d/sshd
# PAM configuration for the Secure Shell service

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
account  [success=1 default=ignore]     pam_access.so
account  required     pam_time.so
# Standard Un*x authorization.
@include common-account

# SELinux needs to be the first session rule.  This ensures that any
# lingering context has been cleared.  Without this it is possible that a
# module could execute code in the wrong domain.
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so close

# Set the loginuid process attribute.
session    required     pam_loginuid.so

# Create a new session keyring.
session    optional     pam_keyinit.so force revoke

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
# This includes a dynamically generated part from /run/motd.dynamic
# and a static (admin-editable) part from /etc/motd.
session    optional     pam_motd.so  motd=/run/motd.dynamic
session    optional     pam_motd.so noupdate

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
session    required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
session    required     pam_env.so user_readenv=1 envfile=/etc/default/locale

# SELinux needs to intervene at login time to ensure that the process starts
# in the proper default security context.  Only sessions which are intended
# to run in the user's context should be run after this.
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so open

# Standard Un*x password updating.
@include common-password
account    required     pam_nologin.so
