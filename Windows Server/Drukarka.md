GGGemini mi to cudo zrobilo

Lecimy konkretnie i na szybko. Żeby to zrobić profesjonalnie, stabilnie i z pełną kontrolą, musisz wykorzystać rolę **Print Server (Serwer wydruku)** na Windows Server.

Oto instrukcja krok po kroku – co zainstalować, jak dodać i jak tym zarządzać.

## 1. Co musisz zainstalować? (Na serwerze)

Nie instaluj sterowników przez zwykłe „Dodaj drukarkę” w Panelu sterowania. Zainstaluj dedykowaną rolę.

1. Otwórz **Server Manager**.
    
2. Kliknij **Add roles and features**.
    
3. Przeklikaj do zakładki _Server Roles_ i zaznacz **Print and Document Services**.
    
4. Potwierdź instalację wymaganych funkcji i zainstaluj.
    

Po instalacji w narzędziach administracyjnych (Tools) pojawi się konsola **Print Management** – to tutaj będziesz robić wszystko.

## 2. Jak dodać drukarkę po IP?

1. Otwórz **Print Management**.
    
2. Rozwiń _Print Servers_ -> _Twój Serwer_ -> kliknij prawym na **Printers** -> wybierz **Add Printer...**
    
3. Wybierz opcję: **Add a TCP/IP or Web Services printer by IP address or hostname**.
    
4. Wpisz IP drukarki. Zaznacz opcję _Auto-detect the printer driver..._ (jeśli serwer sam nie znajdzie sterownika, wskażesz mu plik `.inf` pobrany ze strony producenta).
    
5. Nazwij drukarkę (np. `Drukarka_Ksiegowosc`) i **zaznacz opcję "Share this printer"** (Udostępnij tę drukarkę).
    

## 3. Jak udostępnić ją w Active Directory (AD)?

Żeby klient widział drukarkę w AD (np. gdy kliknie "Wyszukaj w katalogu"):

1. W **Print Management** kliknij prawym przyciskiem myszy na dodaną drukarkę.
    
2. Wejdź w **Properties** (Właściwości) -> zakładka **Sharing** (Udostępnianie).
    
3. Zaznacz ptaszek przy **List in the directory** (Wyświetl w katalogu).
    

> 💡 **Pro Tip na auto-wdrożenie (GPO):** Zamiast kazać użytkownikom szukać drukarki ręcznie, w konsoli _Print Management_ kliknij na nią prawym przyciskiem i wybierz **Deploy with Group Policy...**. Podpinasz to pod odpowiednie GPO (np. dla danego działu) i drukarka sama instaluje się ludziom na komputerach.

## 4. Jak ustawić godziny korzystania z drukarki?

Możesz ograniczyć czas, w którym drukarka przyjmuje zadania (np. zakaz drukowania po godzinach pracy).

1. W **Print Management** wejdź we właściwości (**Properties**) drukarki.
    
2. Przejdź do zakładki **Advanced** (Zaawansowane).
    
3. Zmień opcję z _Always available_ na **Available from** i ustaw ramy czasowe (np. od 08:00 do 16:00).
    
4. Jeśli ktoś wyśle dokument o 17:00, zadanie trafi do kolejki i wydrukuje się dopiero rano o 08:00.
    

## 5. "Cokolwiek innego" czyli co jeszcze warto ustawić?

- **Prawa dostępu (Zakładka Security):** Domyślnie "Everyone" może drukować. Możesz tam usunąć "Everyone" i dodać np. tylko grupę AD `GG_Ksiegowosc`, żeby nikt inny z firmy im nie podbierał papieru.
    
- **Sterowniki x86 / x64 (Zakładka Sharing -> Additional Drivers):** Jeśli serwer jest 64-bitowy, a masz w sieci jeszcze jakieś stare trupy 32-bitowe, możesz tam dorzucić sterowniki x86, żeby klienci pobierali je automatycznie.
    
- **Domyślne ustawienia (Zakładka Advanced -> Printing Defaults):** Ustaw tu od razu druk czarno-biały i dwustronny (Duplex) jako domyślny. Zaoszczędzisz firmie mnóstwo kasy na tonerze i papierze, bo pracownicy rzadko to zmieniają sami z siebie.