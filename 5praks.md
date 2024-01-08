# 5. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse viienda praktikumi esitus. Aega kulus umb .... . Vahest tuli veidi nuputada ning viimase ülesande ma sooritasin enda arust loogiliselt ja õigesti, aga võibolla oodati mingit muud lahendust.
Selle praktikumi raames õppisin, kuidas luua virtuaalmasinat pilvetehnoloogiaga kasutades Azuret ning sain meelde tuletada Windowsi kui Linuxi cmd käske.  <br />

Ülesanne 5-1:

a) kataloogis /tmp/kaust oleva faili minufail.txt lugemiseks? Selleks on vaja ülemkausta otsimise õigust ehk excecute ja faili lugemise õigust e. read.

b) kataloogis /tmp/kaust oleva faili minufail.txt kustutamiseks? Selleks on vaja ülemkaustas kirjutamise õigust e. write ja kui kaust pole kasutaja aktiivses kataloogis siis on vaja mitte otsestes ülemkaustades ka otsimisõigust e. jälle excecute.


Ülesanne 5-2:

Miks chmod a=x skriptifail ei ole piisav õigus shelli skriptifaili käivitamiseks? Millist õigust lisaks käivitamisele veel vaja läheb skriptifaili käivitamiseks? Põhjendage lühidalt.

chmod a=x pole piisav, kuna süsteem nö otsib skriptist juhendit e. Shebag line, selleks et teada saada kuidas skripti interpreteerida. Käsuga chmod a+x, kui süsteem ei leia skriptist juhendit, millega skripti interpreteerida siis ta teeb seda vaikeinterpretaatoriga. Lisaks oleks vaja käivitatavale failile lugemise õigust e. read.

Ülesanne 5-3:
Miks on igal kasutajal omanimeline grupp?
