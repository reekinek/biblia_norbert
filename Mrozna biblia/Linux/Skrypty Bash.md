# Rozpoczęcie
kazdy skrypt zaczynamy z ta linijka:   
`#!/bin/bash`

# Uruchamianie skryptu

piszemy albo `bash skrypt.sh` albo `./skrypt.sh`

# Petle

Składnia:

```
for licznik in {1..10}; do
	kod
done
```



```
for licznik in {1..5}; do
	useradd "student$licznik"
done
```

# Zmienne

Odwolujemy sie do nich uzywajac `$`

```
a=10
b=5
echo $a
wynik=$((a+b))
echo $wynik
```

# Parametry

## Po zapytaniu w terminalu

```
echo "podaj mi wartosc tej zmiennej"
read imie
echo $imie
```

## w czasie uruchamiania skryptu

tzn `bash skrypt.sh parametr1 parametr2`
`$1`to pierwszy parametr, `$2` to druga itd.  

```
cp *.$1* /home/pliki
```


Co to robi: kopiuje pliki o wskazanym rozszerzeniu w parametrze

# jezeli

```
sklep="biedronka"
if [[ "$typ" == "biedronka"]]; then
echo "zajebane paletami"
else
echo "ladnie i schludnie"
fi
```

linux tex jest zjebany i nie ma sensownych operatorow, oto ich lista
```
-ge - wiekszy lub rowny
-gt - wiekszy niz
-le - mniejszy lu rowny
-lt - mniejszy niz
-eq - rowny
-ne - nie rowny
```