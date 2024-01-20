# 12. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse kaheteistkümnenda praktikumi esitus. Aega kulus umb 4h. See praktikum nõudis tsut pusimist aga lõpuks sain hakkama vast.
Selle praktikumi raames õppisin Linuxis skriptimist.  <br />

Ülesanne 3:

Sisu:

#!/bin/bash

echo "Nimi:"

read nimi

echo "Eriala:"

read eriala

echo "Matriklinumber:"

read matriklinumber

echo "Tere, $nimi! Sinu eriala on $eriala ja matriklinumber on $matriklinumber."

Ekraanikuva:

<img width="553" alt="Kuvatõmmis 2024-01-20 115822" src="https://github.com/liinahoogand/OPS/assets/116062583/cdad1fa8-229b-4640-aac6-c694308fd908">




Ülesanne 4:

Sisu:

    #!/bin/bash
    
    if [ "$#" -ne 2 ]; then
        echo "Kasutus: $0 <laiend_A> <laiend_B>"
        exit 1
    fi
    
    laiend_A="$1"
    laiend_B="$2"
    
    for fail in *"$laiend_A"; do
        if [ -f "$fail" ]; then
            if [ "${fail##*.}" = "$laiend_A" ]; then
                uus_fail="${fail/$laiend_A/$laiend_B}"
                mv "$fail" "$uus_fail"
                echo "Fail \"$fail\" ümbernimetatud kujule \"$uus_fail\""
            fi
        fi
    done

Ekraanikuva: lõin paar faili kontrollimiseks ja töötab ilusti


<img width="548" alt="Kuvatõmmis 2024-01-20 124030" src="https://github.com/liinahoogand/OPS/assets/116062583/2f6a2530-7aeb-4cc4-8312-633990858df2">





Ülesanne5:


Sisu:



    #!/bin/bash
    
    if [ "$#" -ne 1 ]; then
        echo "Lisa peale käsku $0 ka argument: <protsessi_nimi>"
        exit 1
    fi
    
    protsessi_nimi="$1"
    
    pgrep -l -x "$protsessi_nimi" | while read -r pid nimi; do
        echo "> Protsessi nimi: $nimi, PID: $pid"
    done



Ekraanikuva:


<img width="547" alt="Kuvatõmmis 2024-01-20 125414" src="https://github.com/liinahoogand/OPS/assets/116062583/f97721ab-4d26-41b7-8dbd-1f3bc3ba1150">



Ülesanne 6:

Sisu:

    #!/bin/bash
    
    astenda() {
        if [ "$2" -lt 0 ]; then
            echo "Astendaja peab olema pos."
            exit 1
        fi
    
        tulemus=1
    
        for ((i=1; i<=$2; i++)); do
            tulemus=$((tulemus * $1))
        done
    
        echo "$1 astmel $2 on $tulemus"
    }
    
    astendus=$(astenda 9 5)
    echo $astendus



Ekraanikuva: 

<img width="544" alt="Kuvatõmmis 2024-01-20 132305" src="https://github.com/liinahoogand/OPS/assets/116062583/fe932b8c-2fa9-4ad8-9792-3b8a09f33df0">


Ülesanne 7:

<img width="960" alt="Kuvatõmmis 2024-01-20 132735" src="https://github.com/liinahoogand/OPS/assets/116062583/a834aefe-bf2e-42a6-b525-7ce06c7d2e0e">



