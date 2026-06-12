
# HELP
```
help for
help set
help logic
set
```
# Zapisywanie

Zapisujemy jako `.cmd` lub `.bat` i podczas pisania w notatniku wybieramy wszystkie pliki a nie jako plik tekstowy

# Ważne rzeczy
`@echo off` - ukrywa wykonanie przed uzytkownikiem, pojazuje sie tylko wynik   
`>` - pozwala przekierowac wynik polecnia do pliku tekstowego   
`pause` - konczy skrypt tak ze cmd dalej jest po jego zakonczeniu    
`start` pozwala na uruchomienie innej aplikacji (np `calc.exe`)     

# Pętle
```
@echo off
FOR /L %%i IN (1,1,5) DO(
net user student%%i student /ADD
)
pause
```

Co tu się dzieje: 
`FOR` - oznacza petle    
`/L` - argument oznaczajacy licznik   
`%%i` - zmienna ktora pod ktora mozna podstawic dane (musi sie zaczynac na `%%` i musi miec jedna litere)
`IN (1,1,5)` - ozacza ze petle bedzie leciec od wartosci jeden, co krok zwiekszac sie o jeden i zatrzyma sie na 5

# Zmienne
Aby ustawic zmienna, piszemy:    
`set nazwa_zmiennej=wartosc`    

Aby wypisac zmienna: `echo %nazwa_zmiennej%`

## Dodawanie zmiennych:

musimy dac argument /a jak definijumy zmienna na podstawie dodawania/odejmowania etc innych zmiennych:   

```
set a=5
set b=7
set /a wynik=a+b
echo %wynik%
```

## Zmienne systemowe

Aby je podejrzec, wpisujemy polecenie `set`. Nie widac tam dwoch zmiennych: `%DATE%` oraz `%TIME%`. 

## Parametry

Aby utworzyc zmienna ktora definiujemy o danym parametrze, uzywamy argument `p`:   
`set /p imie="Podaj swoje imie"`     

Jesli chcemy zeby zmienna zdefiniowac podczas odpalania skryptu w cmd, to w danej komendzie uzywamy `%1`, `%2` ktore odpowiadaja za kolejne podane argumenty

# Skrypty warunkowe

aby znalezc operatory wpisujemy w cmd `help if`

```
@echo off
set sklep=biedronka
if %sklep%==biedronka (
echo zajebane paletami
) else (
czysciutko
)
pause
```

Jako ze windows jest uposledzony to nie moze miec sensownych operatorow

```
@echo off
set wiek=19
if %wiek% GEQ 18 (
echo no to jedziemy
) else (
echo halo halo nie tak szybko
)
pause
```