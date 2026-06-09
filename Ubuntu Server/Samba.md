pakiet: samba

[Rekomendowana muzyka](https://www.youtube.com/watch?v=pRpeEdMmmQ0)
# Instalacja (nie ważne na egzaminie)
Bierzemy internet z puszki, i instalujemy powyższy pakiet

# Firewall
Robimy `sudo ufw allow samba` 

# Konfiguracja

## Katalog

Tworzymy katalog gdzie chciemy mieć udział, np:

`sudo mkdir /magazyn`

## Użytkownik i uprawnienia

Teraz stwórzmy jakiegoś użytkownika:

`sudo useradd magazynier`

Tworzymy hasło do użytkownika. Jako że samba jest specjalna to trzeba jej odzielne hasło stworzyć:

`sudo smbpasswd -a magazynier` oraz dla pewnosci normalnie tez mozna zrobic `sudo passwd magazynier`

Konfigurujemy uprawnienia i wlasciciela (ja dla latwosci daje uprawnienia kazdemu i tylko dla pewnosci robie chowna):

`sudo chmod 777 -R /magazyn` (flaga R daje uprawnienia rekursywnie)   
`sudo chwon magazynier:magazynier -R /magazyn` 
## Plik konfiguracyjny

Edytujemy config:

`sudo nano /etc/samba/smb.conf`

Zjeżdżamy na sam dół pliku i tam piszemy nasz konfig(można sie wspomoc wyzej wpisanymi configami):   
![tekst](../../Obrazki/samba1.png)   

     
Skupiamy sie tylko na sekcji na samym dole, tzn:
```
[Magazyn]
	comment = Zajebane paletami
	path = /magazyn
	read only = no
	browsable = yes
	writable = yes
```     
Oczywiście ścieżke, nazwe(to w nawiasie) i opis/komentarz adekwatnie ustawiamy. Opcje sie same tłumaczą, ale wszystkie z nich musza byc zeby dalo sie zapisywac

Teraz tylko zapisujemy plik i restartujemy serwis oraz sprawdzamy jego status

`sudo systemctl restart smbd nmbd` i `sudo systemctl status smbd`

# Wejscie na serwer

## Ubuntu
Odpalamy managzer plikow, klikamy `Connect to Server` i w polu wpisujemy: `smb://adres.ip/nazawaudzialu` (czyli w tym przypadku to `smb://192.168.10.50/magazyn`)

## Windows

Najprosciej to kliknąć `Win + R` i wpisać `\\adres.ip\nazwaudzialu`

Inny sposób to wejscie w eksplorator plikow, klikniecie prawym na zakladke `Network`, klikniecie `Map network drive` i wpisanie tego samego co na gorze. Trzeba tez zaznaxczyc `Connect using different credentials`