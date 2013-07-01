oberkirch.org
=============

My server configuration.

Mailserver
----------

I use dovecot for imap/pop3 and postfix for smtp. Each with TLS/SSL- and STARTTLS-support.
I guess some/many of the files in postfix are unneeded since I use a MariaDB-database to maintain virtual Mail.
They are just there because my package-manager recreates them on every update.

Postfix and dovecot are configured as generic as possible, using a database (configured with postfixAdmin) to
store all personal/specific configuration. The only thing you need to change are the domain-names (and the
relay-server of cause).


HTTP(S)-Server
--------------

A quiet standart apache-configuration serving instances of
 - owncloud
 - postfixAdmin
 - phpmyadmin (no, postfix is not permitted)
 - roundcubemail
 - some persanal services like remote-controling my music-station over php-scripts

Security Notice
---------------

The password you find in `dovecot/dovecot-sql.conf` and `postfix/mysql_virtual_*_maps.cf` is of no use outside of
localhost. Hiding `/etc/httpd/conf/httpd.conf` is common but obscurity. It can easily be guessed by observing the
servers behaviour on the client-side.
