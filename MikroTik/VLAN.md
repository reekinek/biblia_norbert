- No default config bo jak nie to cing ciang ciong szósteczkę wciong
- Stworzyć bridge
- Przypisać port do bridge(np port 3, byle nie ten na ktorym jestesmy polaczeni)
- Wejść w interface -> vlan, utworzyć vlan10 i vlan20, ustawic id na adekwatne i przypisac do bridgea
  ![[Pasted image 20260519184221.png]]
- Wejść znowu w bridgea, w zakładke vlan i wpisac 10 i 20(nie zaznaczac zadnego taggingu)
- Wejść w IP -> DHCP Server, kliknąć dhcp setup i zrobić dhcp na obu vlanach
  ![[Pasted image 20260519184344.png]]
- Teraz pora na switch TpLink, najlepiej zrestartować przez wyciagniecie ip, potem ustawić ip na kompie i podłączyć się do portu (byle nie ten którego będziemy konfigurować)
- Wejsc w vlan, zakładka ports, zaznaczyc port np 5 i dac tam trunk
- W zakładce vlan utworzyc vlan10(oczywiscie id tez 10) i przypisac na port np 4 i 5, analogicznie z vlan 20 tylko na np porty 5 i 6
- vlan10(oczywiscie id tez 10) i przypisac na port np 4 i 5, analogicznie z vlan 20 tylko na np porty 5 i 6