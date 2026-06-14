# APACHE + DNS

stronka w `/var/www/stronka`

`chown -R www-data:www-data /var/www/stronka`
`chmod -R 755 /var/www/stronka`

`000-default.conf`
    ServerName stronka.com
    ServerAlias www.stronka.com
`systemctl restart apache2`

po linijce Listen 80 dac port w ports.conf
    na samej gorze 8080 w 000-default.conf

`ufw allow 8080`
`systemctl restart apache2`

# DNS
napisac w `/etc/bind/named.conf.local`
zone "stornka.pl" {
                 type master;
                 file "/etc/bind/db.stronka.pl";
};

example z tym `/etc/bind/named.conf.default-zones`

`cp db.local db.stronka.pl`

wszystkie localhost i 127.0.0.1 na stronka.pl
ostatnie 2 linijki na ip strony
ostatnia linijka @ na www i AAAA na A
(jesli FTP to ftp zamiast www)

`named-checkconf`
`named-checkzone stronka.pl /etc/bind/db.stronka.pl`

`systemctl restart named bind9`

# SAMBA

`ufw allow samba`

`mkdir /magazyn`

`useradd magazynier`
`smbpasswd -a magazynier | passwd magazynier`

`chmod 777 -R /magazyn`
`chown magazynier:magazynier -R /magazyn`

/etc/samba/smb.conf
przepisac na samym dole [print$] (guest zmienic na writable)

`systemctl restart smbd nmbd`

Ububtu: manager plikow>connect to server>smb://ip/magazyn
Windows: win+r \\ip\magazyn

# FTP

`ufw allow ftp`

/etc/vsftpd.conf

anonymous_enable - anon downlaod
anon_upload_enable - anon upload
write_enable - user edytuje
chroot_local_user YES - user tylko w domowym /home/user/folder
allow_writeable_chroot YES - user edytuje domowy /home/user
ssl_enable - zmusza do korzystania z SSL

`mkdir -p /srv/files/ftp - nowy folder ftp`
`usermod -d /srv/files/ftp ftp`

`useradd -m -d /magazyn magazynier`
`passwd magazynier`

`systemctl restart vsftpd`

Filezilla: IP, uzytkownik, haslo, 21

# SSH
`ufw allow ssh`
`systemctl start ssh`

/etc/ssh/sshd_config

CMD Win: ssh administrator@192.168.0.2

# DHCP

`/etc/dhcp/dhcpd.conf`
def lease, max lease juz jest
domain name, domain name servers juz jest
subnet netmask
    range
    option routers

