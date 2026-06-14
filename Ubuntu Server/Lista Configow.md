# Lokalizacja configow

Apache
- `/var/www` - Przechowywane strony
- `/etc/apache2/`
   - `/sites-available/000-default.conf` - Główny config
   - `/ports.conf` - Config do portów

CUPS
- `/norbert/nie/nauczyl` - I jest na hawajach

DHCP
- `/etc/dhcp`
   - `/dhcpd.conf` - Główny config
   - `/isc-dhcp-server` - Dodawanie inferface dla dhcp

DNS
- `/etc/bind/`
   - `named.conf.local` - Główny config
   - `db.local` - Plik strefy

FTP
- `/etc/vsftpd.conf` - Główny config
   - `/srv/ftp` - Katalog dla plików FTP

Netplan
- `/etc/netplan/00-installer-config.yaml` - Główny config
- `/usr/share/doc/netplan/examples` - Przykładowe configi

SSG
- `/etc/ssh/sshd_config`

SAMBA
- `/etc/samba/smb.conf`

Wszystkie configi sa w `/etc/` i wzrokowo mozna znalezc, jedynie co to trzeba zapamietać `/usr/share/doc/netplan/examples` bo jest z dupy
