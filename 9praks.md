# 9. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse üheksanda praktikumi esitus. Aega kulus umb ........h . Vahest tuli veidi nuputada ning viimase ülesande ma sooritasin enda arust loogiliselt ja õigesti, aga võibolla oodati mingit muud lahendust.
Selle praktikumi raames õppisin, kuidas luua virtuaalmasinat pilvetehnoloogiaga kasutades Azuret ning sain meelde tuletada Windowsi kui Linuxi cmd käske.  <br />

| Küsimus                    | Linux        | Windows      | Linuxis kasutatud käsklus | Windowsis kasutatud tööriist |
|-----------------------------|--------------|--------------|---------------------------|-----------------------------|
| [1]                         | [Linux 1]    | 154  | ps -A \| wc -l | tegumihaldur (task manager) -> jõudlus -> protsessid |
| [2]                         | [Linux 2]    | frontdrvhost.exe | ps -aux --sort -pid \|tail -1      | process explorer -> time |
| [3]                         | [Linux 3]    | esineb vaid kasutaja millega sisse logisin | ps -ef \|cut -d'' -f1\|sort \| uniq       | teumihaldur -> users |
| [4]                         | [Linux 4]    | 0:00:57:25  | uprime -p       | tegumihaldur -> jõudlus -> CPU -> tööaeg |
| [5]                         | [Linux 5]    | - | ps -ef --sort -start \| head -4       | windowsil puudub selline "tegevus" |
| [6]                         | [Linux 6]    | windows feature experience pack | htop -> f6 sort by -> percent_cpu       | [tegumihaldur -> rakenduste ajalugu -> protsessoriaeg |
| [7]                         | [Linux 7]    MsMpEng.exe  | htop -> f6 sort by -> VIRT    | resource monitor -> commit(CPU1 suurim)|
| [8]                         | [Linux 8]    | [Windows 8]  | [Linux käsklus 8]        | resource monitor -> working set |
| [9]                         | [Linux 9]    | 1220MB  | [Linux käsklus 9]        | resource monitor -> physical memory(available) |
| [10]                        | [Linux 10]   | 35,4GB e. 55,8% | [Linux käsklus 10]       | WinDirStat -> c: -> atribuudid |
| [11]                        | [Linux 11]   | kaust: windows ja fail: pagefile.sys| [Linux käsklus 11]       | WinDirStat -> c: -> suurus, kaust on ka seal samas |
| [12]                        | [Linux 12]   | -| [Linux käsklus 12]       | - |
| [13]                        | [Linux 13]   | 1. system, 2.C:\\$LogFile(NTFS Volume Log), 3. System, 4:C:\pagefile.sys | [Linux käsklus 13]       | resource monitor -> disk -> disk activity -> read(mõlemad)/write(mõlemad) |
| [14]                        | [Linux 14]   | protsess: svc.exe(NetworkServise-p), kohalikud: ip 10.0.2.15 ja port 51704, teise poole ip  20.199.120.182 ja port 443, latents 0m/s ja võrguliikluse kogumsht on 28B/sec| [Linux käsklus 14]       | resource monitor -> network |



