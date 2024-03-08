Астра
10.17.7.228
emm / install114
Подключение комплекта Astra Linux
emm@pre-astra:~$ sudo su
root@pre-astra:~# cd /home/emm/
root@pre-astra:/home/emm# ssh-keygen -f ppppp
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in ppppp.
Your public key has been saved in ppppp.pub.
The key fingerprint is:
SHA256:o/vtZXAu3MyR6L8CkrNhVrShrPxREWxomr7rn3IYuWo root@pre-astra
The key's randomart image is:
+---[RSA 2048]----+
|       o..       |
|      o *        |
|     = + +       |
|    o o +  . .   |
|   o o +S o +    |
|    * O..+ B .   |
|     O.* .+ B    |
|  E = +o ..=     |
| ..oo=+...o.o.   |
+----[SHA256]-----+
root@pre-astra:/home/emm# sudo -i mkdir -p .ssh
root@pre-astra:/home/emm# sudo -i chmod 700 .ssh
root@pre-astra:/home/emm# sudo -i chmod 600 .ssh/authorized_keys
root@pre-astra:/home/emm# cat ppppp.pub | sudo -i tee -a .ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC1tnDfUkbhvX803N0kyVoBzQuUB6R2SDpMTsrg4aMwx5iRyPXNkoGSMcVRjLlnjgMi++gvigx04hgO/ZihgGrNlT4kjNF7XOWWKFnifaD4K95duKkec80fQISQOu9vdjz9HZUZehuvOtoyglKS06go0HITFg8LCzd2QXpSV6iZVyzAA64SBG+/ibNInPnZ6a+0xqXYjo3O5O4A+5JWxJDRdHMgnQq7ERKaGXVwg5t72VoTO4pIzz3FsiQqz3IAvHHwKeR9Tiqq/lO0Pi58/VlADkPpTRH2LkGRvC55mYjXgnGwLKma5FMvVVFol+sDwL1gdlsadRV3CoMrBKzBxV9L root@pre-astra
(публичный ключ ушел в файл)
root@pre-astra:/home/emm# cat ppppp
-----BEGIN RSA PRIVATE KEY-----
-----END RSA PRIVATE KEY-----
(копируем с границами в АРМ)



Альт
10.17.7.188
emm / install114
Подключение комплекта Alt Linux
[emm@host-188 ~]$ su -
Password: install114
[root@host-188 ~]# ssh-keygen -f qwerty
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in qwerty.
Your public key has been saved in qwerty.pub.
The key fingerprint is:
SHA256:+uqPnAMXZTt86q3ysR6cUHEqOVC+GU9G3tElH/IcDs0 root@host-188
The key's randomart image is:
+---[RSA 2048]----+
|    ... o o.+++  |
|     o +o= ..OEo |
|      *+*..   =  |
|      .@+ .      |
|      +.S+       |
|    . .+..       |
|     o..=.       |
|     .o+.+.      |
|     .*BB.       |
+----[SHA256]-----+
[root@host-188 ~]# cat qwerty.pub>>~/.ssh/authorized_keys
[root@host-188 ~]# cat qwerty
-----BEGIN OPENSSH PRIVATE KEY-----
-----END OPENSSH PRIVATE KEY-----
(копируем с границами в АРМ)


Будет сделана попытка исправить нарушенные зависимости. 
Как правило, эта команда очень полезна в случае, если вы пытаетесь вручную установить пакет DEB,
не устанавливая первоначально его зависимости. Выполните команду apt-get -f install, 
а затем снова попытайтесь установить пакет.

Поиск приложений:
apt-cache show ИМЯ_приложения (apt-cache show tran) (apt-cache show airstrike)
apt-cache show ИМЯ_приложения (apt-cache show calizo) (apt-cache show QCheckers)


Удаление приложений:
apt-get remove ИМЯ_приложения (apt-get remove tran) (apt-get remove airstrike)
apt-get remove ИМЯ_приложения (apt-get remove calizo) (apt-get remove QCheckers)


посмотреть все установленные приложения: apt list --installed


установить приложение руками на vm Linux (Astra):
по мотивам 31851:
3. Открыть WinSCP
4. Добавить пакет приложения с расширением .DEB в каталог home/emm/
5. Открыть Putty
6. Авторизоваться через Putty
7. Перейти в каталог с установленным приложением
8. Установить пакет при помощи команды sudo dpkg -i  vim-athena_8.2.2434-3+deb11u1_amd64.deb
9. Проверить статус установки приложения при помощи команды apt list --installed
10. Найти установленное приложение в списке
