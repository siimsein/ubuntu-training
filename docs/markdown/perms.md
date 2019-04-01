# Failiõigused

Esmalt vaatame failiõiguseid teoreetilisemast poolest. Linuxi failiõigused jagunevad kolme gruppi - kasutaja, grupp, muu.
Failiõigusi saame näha `ls` käsuga, lisades lipu `-l` (long)

```bash

[ubuntu@ubuntu ~]# ls -l
total 0
-rw-r--r-- 1 ubuntu ubuntu 0 Apr  1 12:05 testfile1
-rwxr--r-- 1 ubuntu ubuntu 0 Apr  1 12:05 testfile2
-rw------- 1 ubuntu ubuntu 0 Apr  1 12:05 testfile3
     |     |    |      |   |  ---------      | 
     |     |    |      |   |      |          └  Failinimi 
     |     |    |      |   |      |
     |     |    |      |   |      └ Viimase muutmise aeg
     |     |    |      |   |    
     |     |    |      |   └ Suurus
     |     |    |      └ Grupp
     |     |    └ Omanik
     |     └ Kui tegu on kataloogiga, siis mitu faili kataloogis on
     └  Õigused
```

Näeme, et failiõigused on kirjas 10 tähemärgiga. 

Esimese märgina on õigustes kirjas tüüp. Tüübil on kolm võimalikku väärtust 
* `-` Tavaline fail   
* `d` Kaust (directory)
* `l` Link

Tüübile järgneb 3 3-bitilist õiguste sektsiooni, esimene kasutajale/omanikule, teine grupile, kolmas ülejäänutele.
Kolmikus endas jagunevad õigused järgmiselt
- lugemisõigus `r` (read)
- kirjutamisõigus `w` (write)
- käivitamisõigus `x` (eXecute)

Kuna tegu on binaarsete väärtustega, saame omistada õigustele ka numbrid - `x = 1`, `w = 2`, `r = 4`. Väärtused kokku liites 
saame numbrilised õigused 0 - 7. Numbrilise näitega on `testfile1` õigusteks 644, `testfile2` 744, ja `testfile3` 600
 
Failide lugemis- ja kirjutamisõigused on enesest mõistetavad, kuid kävitamisõiguse biti on vaja faili käivitamiseks. Nt.
käskude `rm`, `cp` jm. puhul on tegu binaarsete programmidega, mida bash välja kutsub. Selleks, et neid binaare saaks ka
kasutada on neile antud õigusteks `-rwxr-xr-x` (755), lubades faili muuta ainult omanikul, ning ülejäänutel seda lugeda ja kasutada.
Scripti/binaari/programmi käivitamiseks on vajalik ka lugemisõigus

Kaustade puhul rakenduvad õigusbitid natukene teistmoodi. Lugemisbitt lubab kausta sisu lugeda (aga mitte kausta siseneda).
Sisenemiseks on vajalik sättida kaustale ka kävitamisbitt, mis annab ka õigused kaustas muudatusi teha (kui on olemas kirjutamisõigus).
Kirjutamisbitt lubab kausta nime või sisu muuta, aga ainult siis kui käivitamisbitt on lisatud.

Faili- ja kaustaõiguste vaikeväärtusteks on tavaliselt 644 failidele ja 755 kaustadele. Küll aga on kohti (näiteks kodukataloogid),
kus õigusi hoitakse rangemalt. Failiõigusi saab muuta ainult omanik (või `root` kasutaja), faili omanikku saab muuta ainult `root`.

## Failiõiguste muutmine

Õiguste, omaniku ja grupi muutmiseks kasutame peamiselt järgnevaid tööriistu.
```bash
chown <kasutaja> <fail> #(change-owner)
chgrp <grupp> <fail> #(change-group)
chmod <mode> <fail> #(change-mode)
```

Omaniku ja grupi vahetamine on küllaltki lihtne, kui on soov mõlemad korraga vahetada siis `chown` käsus saab peale <kasutaja> 
määrata korraga ka grupi, kasutades süntaksi `<kasutaja>:<grupp>`. Õiguste enda muutmiseks on kaks võimalust.

chmod käsule saab täpsustada õigusi kas siis numbriliselt (octal mode) või tähemärkidega. Numbriliset vormaati vaatasime enne, ning m
anuaalist lugedes näeme, et 
sümbolitega õiguste süntaks on tähistatud kui `[ugoa...][[-+=][perms...]...]`. Nüüd saab selgeks ka miks kasutatakse failiõiguste
puhul terminit "kasutaja/user" mitte "omanik/owner". Tähetedega välja kirjutatud õiguste puhul tähistab `o` hoopis ülejäänusi kasutajaid.

- u - user
- g - group
- o - other
- a - all

Järgmine osa süntaksist on liitmine, lahutamine või sättimine. Tähetega õiguste muutmine lubab seda teha ka suhteliste tehetena,
lisades kaustadele ainult lugemisõiguseid või neid eemaldades olenemata eelseisust. Viimasena tähistame õigused ise `rwx` vormingus.

Failiõiguste sättimisel on hea teada mõlemat viisi kuidas õigusi märkida. Järgnevalt mõned näited.

```bash
chmod u=rwx,g=rx,o=rx <fail>
chmod 755 <fail> #Identsed õigused võrreldes eelmisega

chmod o-rwx <fail> #Lubada ainult kasutaja ja grupp, ehk eemaldada "muu" õigused
chmod ug+x <fail> #Kasutajale ja grupile korraga käivitamisõiguse andmine.
```

## Failiõiguste harjutus

Kõigepealt läbi kasutajate lisamise osa. 

Alustuseks loome ühise kausta, kuhu mõlemad meie kasutajad ligi pääsevad. 
Kõige lihtsam on selleks luua failisüsteemi "juurikasse" uus kaust.

```bash
sudo mkdir /permissions_testing/
chmod 777 /permissions_testing/ #Anname kaustale kõige laiemad õigused
```

TODO lõpeta harjutus.


