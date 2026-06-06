
# gpupdate

Zmusza windowsa to synchronizacja zasad grupy. Opcja /force go bardziej zmusza
# net user

`net user` - wyświetla liste wszystkich użytkowników
`net user marian` - wyświetla szczegółowe informacje o użytkowniku marian. Jest to też baza do której dodajemy argumenty podane poniżej:
Aby dodać hasło to po nazwie użytkownika w komendzie wpisujemy hasło (`net user marian haslomaslo`). Ewentualnie hasło zastępujemy `*` aby cmd sie nas zapytalo o haslo zeby nie bylo go widac w plain texcie

/add - tworzy użytkownika
/delete - usuwa użytkownika
/active:{yes|no} - włącza lub wyłącza konto
/times:{time|all} - ogranicza czas w którym można się logować na konto (opcja all usuwa ograniczenia). Np. `/times:M-F,08:00-18:00`
/expires:{Date|never} - ustawia czas wygaśniećia konta. (opcja never usuwa wygaśnięcie). Np. `/expires:31/12/2026` Format daty zależy od locale systemu. Na polskim bedzie DD/MM/YYYY a na amerykanskim bedzie MM/DD/YYYY (moze wywalic blad wtedy)
/passwordchg:{yes|no} - pozwala badź nie użytkownikowi na zmiane hasła

Przykładowa komenda:

`net user marianek haslomaslo /add /expires:31/12/2026 /passwordchg:no /times:M-F,08:00-18:00`

# net accounts

Taki troche secpol ale w cmd. Sama komenda daje nam po prostu status jej parametrów

/domain - sprawia że  operacja jesst wykonywana na kontrolerze domeny(globalnie) a nie lokalnie(moze sie przydac jak ktos zapomnial jak wyklikac na serwerze)
/minpwlen:{length} - ustawia minimalną wymaganą dlugosc hasła
/maxpwage:{days | unlimited} - po ilu dniach użytkownicy wygasa hasło
/minpwage:{days} - po ilu dniach uzytkównicy moga zmienic swoje haslo
/uniquepw:{number} - zachowuje podana ilosc poprzednich hasel, uzytkownicy nie moga ich potem ustawic na haslo
/forcelogoff:{minutes | no} - jesli podamy czas w minutach to po podanym czasie uzytkownik zostanie wylogowy
# net localgroup
Do zarządzania grupami lokalnymi

`net localgroup` - lista wszystkich grup
`net localgroup Administrators` - daje info o danej grupie

Argumenty:
/domain - sprawia że  operacja jesst wykonywana na kontrolerze domeny(globalnie) a nie lokalnie(moze sie przydac jak ktos zapomnial jak wyklikac na serwerze)
/add - dodaje użytkownika/grupe globalna do grupy lokalnej
/delete - usuwa uzyszkodnika z grupy lokalnej
/comment:"Text" - dodaje komentarz do grupy

Przykladowa komenda:
`net localgroup "Administrators" marian /add` - dodaje uzytkownika marian do grupy Administratorzy
# net share
Zarządanie udziałami sieciowymi i drukarkami.

`net share` - pokazuje info o udziałach
`net share Magazyn=C:\magazyn` - tworzy udział o nazwie/aliasie Magazyn zmapowany do folderu C:\magazyn

Argumenty:
/grant:{UserName},{Permissions} - daje danemu użytkownikowi uprawnienia ACL do danego udziału. Możliwe uprawnienia to READ, CHANGE i FULL
/users:{Number} - ustawia limit ile użytkowników może być jednoczesnie zalogowanych do udziały
/unlimited - usuwa jakiekolwiek numeryczne udziały
/remark:"Text" - daje opis do udziału
/delete - usuwa udział (ale nie folder) (wtedy robimy np `net share Magazyn /delete`)

Przykład:
`net share Magazyn=C:\magazyn /grant:marian,READ /remark:"zajebane paletami"
