oberkirch.org
=============

My server configuration.

Mailserver
----------

I use dovecot for imap/pop3 and postfix for smtp. Each with TLS/SSL- and STARTTLS-support.
I guess some/many of the files in postfix are unneeded since I use a MariaDB-database to maintain virtual Mail.
They are just there since my package-manager recreates them on every update.

HTTP(S)-Server
--------------

A quiet standart apache-configuration serving instances of
 - owncloud
 - postfixAdmin
 - phpmyadmin (no, postfix is not permittet)
 - roundcubemail
 - some persanal services like remote-controling my music-station over php-scripts

Security Notice
---------------

The password you find in `dovecot/dovecot-sql.conf` and `postfix/mysql_virtual_*_maps.cf` is of no use outside of
localhost. Hiding `/etc/httpd/conf/httpd.conf` is common but obscurity. It can easily be guessed by observing the servers
behaviour on the client-side.
