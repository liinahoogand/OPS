# 9. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse üheksanda praktikumi esitus. Aega kulus umb 6h . See praktikum nõudis mõnda pusimist alguses.
Selle praktikumi raames õppisin, ressursihalduse kohta Windowsis ja Linuxis.  <br />

| Küsimus                    | Linux        | Windows      | Linuxis kasutatud käsklus | Windowsis kasutatud tööriist |
|-----------------------------|--------------|--------------|---------------------------|-----------------------------|
| [1]                         | 209 | 154  | ps -A \| wc -l | tegumihaldur (task manager) -> jõudlus -> protsessid |
| [2]                         | /sbin/init splash    | frontdrvhost.exe | ps -aux --sort -pid \|tail -1      | process explorer -> time |
| [3]                         | avahi, colord, kernoops, liina, message+, root, rtkit, syslog, systemd+ja UID | esineb vaid kasutaja millega sisse logisin | ps -ef \|cut -d'' -f1\|sort \| uniq       | tegumihaldur -> users |
| [4]                         | up 56 minutes | 0:00:57:25  | uprime -p       | tegumihaldur -> jõudlus -> CPU -> tööaeg |
| [5]                         | kworker/0:0-events   | - | ps -ef --sort -start \| head -4       | windowsil puudub selline "tegevus" |
| [6]                         | /usr/bin/gnome-shell  | windows feature experience pack | htop -> f6 sort by -> percent_cpu       | [tegumihaldur -> rakenduste ajalugu -> protsessoriaeg |
| [7]                         | /usr/bin/gnome-shell  |  MsMpEng.exe  | htop -> f6 sort by -> VIRT    | resource monitor -> commit(CPU1 suurim)|
| [8]                         | /usr/bin/gnome-shell    | firefox.exe  | HTOP -> F6 SORT BY -> PERCENT_MEM | resource monitor -> working set |
| [9]                         | 290Mi  | 1220MB  | free -h | resource monitor -> physical memory(available) |
| [10]                        | 7,7GB e. 62% | 35,4GB e. 55,8% | df -h/ | WinDirStat -> c: -> atribuudid |
| [11]                        | kaust: /usr ja fail: ./.config/Qlipper/qlipper.ini | kaust: windows ja fail: pagefile.sys| fail:find -type f exec du -Sh {} + \| sort -rh  \| head -n 1,kaust:sudo du -ah /* \| sort -rh\| head -n1 | WinDirStat -> c: -> suurus, kaust on ka seal samas |
| [12]                        |Esimese käsu puhul(zero) kulub enamik cpu ajast tegevusele us( 96,1%) ja ka sy ( 2,6%) ning teise käasu puhul (urandom) puhul jaotub cpu aeg võrdemaslt ära kui ennem, nüüd us 57,9% ja sy 42,1%                    |  -  | juhendis kirjas | - |
| [13]                        | - | 1. system, 2.C:\\$LogFile(NTFS Volume Log), 3. System, 4:C:\pagefile.sys | - | resource monitor -> disk -> disk activity -> read(mõlemad)/write(mõlemad) |
| [14]                        | - | protsess: svc.exe(NetworkServise-p), kohalikud: ip 10.0.2.15 ja port 51704, teise poole ip  20.199.120.182 ja port 443, latents 0m/s ja võrguliikluse kogumsht on 28B/sec| - | resource monitor -> network |

Ülesanne 15(Windows)
Kui sõbra arvuti oleks oluliselt aeglasemaks jäänud siis ma uuriks:<br />
1. Tegumihalduris protsessori vahelehte, kus ma näeks, millised protsessid kasutavad kõige rohkem ressursse. Jõudluse alt saan ülevaate CPU ja mälu kasutusest. Automaatsete käivituste alt näen, millised programmid käivituvad koos Windowsiga.
2. Resource Monitor-i, kuna seal saan täpse ülevaate süsteemi ressursside kasutamisest, nagu nt protsesside, mälukasutuse, kettamahu ja võrguliikluse kohta.

Ül 12 ekraanipildid

Käask zeroga
<img width="445" alt="Kuvatõmmis 2024-01-20 051113" src="https://github.com/liinahoogand/OPS/assets/116062583/46e3a306-8428-465c-8b92-9b655d08f1be">

Käsk urandomiga
<img width="542" alt="Kuvatõmmis 2024-01-20 051211" src="https://github.com/liinahoogand/OPS/assets/116062583/1431d400-7dfe-4037-b343-f005994e1f95">


Ül 14 ekraanipilt

<img width="563" alt="Kuvatõmmis 2024-01-20 030238" src="https://github.com/liinahoogand/OPS/assets/116062583/b6b6051c-0636-482f-bfed-0c48f4719172">



