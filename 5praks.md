# 5. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse viienda praktikumi esitus. Aega kulus umb 5h . Vahest tuli veidi nuputada ning viimase ülesande ma sooritasin enda arust loogiliselt ja õigesti, aga võibolla oodati mingit muud lahendust.
Selle praktikumi raames õppisin, kuidas luua virtuaalmasinat pilvetehnoloogiaga kasutades Azuret ning sain meelde tuletada Windowsi kui Linuxi cmd käske.  <br />

Ülesanne 5-1:

 a) kataloogis /tmp/kaust oleva faili minufail.txt lugemiseks? Selleks on vaja ülemkausta otsimise õigust ehk excecute ja faili lugemise õigust e. read.

 b) kataloogis /tmp/kaust oleva faili minufail.txt kustutamiseks? Selleks on vaja ülemkaustas kirjutamise õigust e. write ja kui kaust pole kasutaja aktiivses kataloogis siis on vaja mitte otsestes ülemkaustades ka otsimisõigust e. jälle excecute.


Ülesanne 5-2:

Miks chmod a=x skriptifail ei ole piisav õigus shelli skriptifaili käivitamiseks? Millist õigust lisaks käivitamisele veel vaja läheb skriptifaili käivitamiseks? Põhjendage lühidalt.

 chmod a=x pole piisav, kuna süsteem nö otsib skriptist juhendit e. Shebag line, selleks et teada saada kuidas skripti interpreteerida. Käsuga chmod a+x, kui süsteem ei leia skriptist juhendit, millega skripti interpreteerida siis ta teeb seda vaikeinterpretaatoriga. Lisaks oleks vaja käivitatavale failile lugemise õigust e. read.

Ülesanne 5-3:

Miks on igal kasutajal omanimeline grupp?

 See loodi siis kui Unix-süsteemid olid üldiselt mitme kasutaja jaoks mõeldud suurtes arvutivõrkudes, kus omanimeline grupp lihtsustas failide jagamist ja tiimi koostööd. Siis said kõik kasutajad vaikimisi ligipääsu üksteise failidele ja nõnda on palju kergem anda failiõigusi korraga ühele kasutajale.

Ülesanne 5-4:

Millised on minimaalsed õigused (rwx), mis on vajalikud teie tavakasutajal (kuulub gruppi majasisene) (mitte root- või peeter-kasutajal, kausta ja faili omanikud) faili uusfail.txt sisu kuvamiseks? 

 Minimaalsed õigused, mis on vajalikud tavakasutajal faili sisu kuvamiseks, on lugemisõigused (read)
 
<img width="865" alt="Kuvatõmmis 2024-01-09 001258" src="https://github.com/liinahoogand/OPS/assets/116062583/5d541330-964b-41d6-bd06-725964436e15">

Ülesanne 5-5:

Milleks on vaja setuid-õigust? Setuid (set user ID) võimaldab käivitada programmil selle omaniku õigustes, mitte käivitaja õigustes. Setuid-bit on seotud failiga ja mitte käivitatava protsessiga, ja see võimaldab kasutajal käivitada programm, omandades faili omaniku õigused ajutiselt, kui programm töötab.

<img width="675" alt="Kuvatõmmis 2024-01-09 014301" src="https://github.com/liinahoogand/OPS/assets/116062583/abe69179-84b8-47e9-8389-1aad6493814b">

Ülesanne 5-6:

Kas setuid-i kasutamine võib vähendada süsteemi turvalisust? Kui jah, siis kuidas?
 Jah, see võib potentsiaalselt vähendada süsteemi turvalisust. Setuid-õigusega failid käivitatakse nende omaniku õigustes, mis võivad olla oluliselt suuremad kui käivitaja õigused see võib avada tee tehnika rünnakutele või kasutaja õiguste kuritarvitamisele. 


Ülesanne 5-7:

 Kirjutage oma esitusele kõik kasutajad, kes saavad sticky bit-õigustega yhiskaust-kataloogist nüüd peeter-kasutaja loodud faile kustutada. (Õige vastus sisaldab vähemalt 3 eri kasutajat).
  Praeguses seadistuses saavad kustutada "peeter", "opetaja" ja süsteemi administraator (root).

Ülesanne 5-8:
  
<img width="502" alt="Kuvatõmmis 2024-01-09 021639" src="https://github.com/liinahoogand/OPS/assets/116062583/7f51f6f2-db3d-42cb-95ff-59c155b3bb01">

Ülesanne 5-9:

 Kes saab chattr +i-parameetriga faili sisu modifitseerida (kirjutada)? Milliste käskudega saate kustutada testfail-2-nimelise faili (ehk kuidas siiski kustutada +i-parameetriga faili)?

Mitte keegi ei saa seda muuta, isegi mitte superuser
Kustutamiseks :
sudo chattr -i testfail-2 && sudo rm testfail-2

