# 6. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse kuuenda praktikumi esitus. Aega kulus umb 4h . Ülesanded olid seekord üsna mõnusad.
Selle praktikumi raames õppisin, erinevaid Linuxi käske kasutama, mis on seotud protsessidega.  <br />

Ülesanne 1: 

<img width="543" alt="Kuvatõmmis 2024-01-15 192047" src="https://github.com/liinahoogand/OPS/assets/116062583/cc07eb73-76a5-4e73-a960-0390ac5d71bd">

Ülesanne 2:

<img width="547" alt="Kuvatõmmis 2024-01-15 192752" src="https://github.com/liinahoogand/OPS/assets/116062583/b22cd039-99f1-4c74-b72e-193a44c8171c">

Ülesanne 3:

Käsk: ps -axu | grep daemon | grep -v grep | tr -s ' ' | cut -d ' ' -f11- | grep daemon
<img width="545" alt="Kuvatõmmis 2024-01-15 193226" src="https://github.com/liinahoogand/OPS/assets/116062583/44c8f003-c48a-40ed-958a-48ae25a4d1cf">

Ülesanne 4:

Käsud:

ps -axu | grep snap | awk '{print $11 " " $12 " " $13}'

ip a | grep -Po 'inet (?!127\.0\.0\.1)([0-9]+\.){3}[0-9]+' | cut -d ' ' -f2

ip a | grep -Eo 'inet ([0-9]*\.){3}[0-9]*' | cut -d ' ' -f2 > ipaddress.txt

xargs -n1 ping -c 2 < ipaddress.txt

<img width="551" alt="Kuvatõmmis 2024-01-15 195646" src="https://github.com/liinahoogand/OPS/assets/116062583/ddaad31e-8dbd-482b-815f-19544038edbb">
