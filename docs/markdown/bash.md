#Sissejuhatus käsureale

Bash (Bourne-again shell), kõige tavalisem käsurea keel, mis enamike tänapäevaste linuxi versioonidega  kaasa tuleb. Bash on
edasiarendatud versioon Bourne-shellist, käsurea keelest mis on aastast 1979 saati olnud linuxi standard kest (shell)
Unixi shellid on kõik käsurea interpeteerijad, seega peale keelepõhiste lisanduste saavad käsureakeeled kutsuda välja
süsteemseid programme. 


## Käsurea süntaks

Pea kõik käsud käsureal järgivad sarnast vormeeringut. Hea ingliskeelse juhendi bashis navigeerimise kohta leiab aadressilt 
http://www.linuxcommand.org/lc3_learning_the_shell.php

```bash
käsk/programm [argumendid] parameeter1 parameeter2
```

Käsu argumendid ei ole alati kohustuslikud, kuid muudavad käsu töötamise põhimõtteid. Erinevate käskude ja programmide
dokumentatsiooni saab vaadata ka käsurealt endalt. Kaks kõige levinumat võimalust on kas käsurea manuaal `man` või 
jooksutada käsku lipuga `--help` / `-h`. Kuigi programmi argumentide süntaks ei ole rangelt määratud, jälgitakse mõnd kindlat 
tava.

Käsurea puhul on tarvis ka teada oma töökausta - käsurida avades on töökaustaks alati kasutaja kodukaust. Alljärgnevalt on
kirjeldatud mõned tavalisemad käsud. Käskude näidiste puhul nurksulgudega `<>` märgitud argumendid tuleks kohandada vastavalt
Lisaks bash eirab kõike mis on pärast trellide märki `#`  - see lubab meil lisada kommentaare oma käskudele või scriptidele

```bash
# Praegune töökaust
pwd #(print-working-directory)

# Töökausta asukoha vahetamine
cd #(change-directory)

# Näitab töökausta sisu
ls #(list)

# Kausta loomine
mkdir <kausta-nimi> #(make-directory)

# Kustutamine
rm <kausta või faili nimi> #(remove)

# Kopeerimine
cp <allikas> <sihtkoht> #(copy)

# Liigutamine - toimib ka ümbernimetamiseks
mv <allikas> <sihtkoht> #(move)

# Ümbernimetamine
rename

```

## Failide redigeerimine

Serverite haldamisega tuleb paratamatult kaasa ka failide lugemine ja kirjutamine. Faili kirjutamiseks on võimalusi mitmeid, kuid hetkel 
keskendume käsurea tekstiredaktoritele. Kaks kõige populaarsemat on `nano` ja `vi`/`vim`. Vim'i puhul on tegu vi täiendatud versiooniga (vi-improved)

Faili avamiseks sisestame käsuks `nano <failinimi>` või `vi <failinimi>`. Kui soovime kasutada vi täiustatud versiooni peame selle 
kõigepealt paigaldama. Seda saame teha käsuga `apt install vim -y` (aptist ja tarkvara paigaldamisest räägime hiljem)

Raskem osa käsureapõhiste tekstiredaktoritega on salvestamine.

_Nano_

---

CTRL-X (terminali alumises osas on näha nano käsud, `^C EXIT` väljumiseks).
Edasi küsitakse kas (muudetud) fail salvestada? `Y`
Ning kinnitame failinime `ENTER / RETURN` klahviga

**Lühidalt - CTRL-X, Y, ENTER**


---

_vi/vim (Käsud on identsed, edasipidi kasutan viitamiseks `vim`)_


Esmalt peame teadma, vim'il on kaks erinevat režiimi, milleks on redigeerimine ja käsurežiim. Vimi käivitamisel avatakse vim
alati käsureziimil. Seega, et üldse faili kirjutada saaks läheme kirjutamisreziimi tähega `i` (insert). Nüüd Näeme alumises osas kirja `-- INSERT --` 
ning oleme valmis muutma faili sisu. 

Faili salvestamiseks väljume kirjutamisrežiimist klahviga `ESC`. Edasi faili salvestamiseks kirjutame `:` - all näeme nüüd vimi enda
shelli `:` ning sinna sisestame `wq` (write, quit). `Enter` klahviga edastame käsu

**Lühidalt - ESC :wq**

## Harjutus

Soenduseks mängime läbi järgmised käsud.

```
    1. Mis on praegune töökaust?
    2. Liigume kodukausta
    3. Teeme endale sobiva nimega kausta kodukausta
    4. Vaatame kodukausta sisu
    5. Liigume uude kauasta
    6. Kontrollime praegust töökausta
    7. Loome uue faili "test"
    8. Kirjutame faili sisse endale sobiva teksti.
    9. Kopeerime faili
    10. Kontrolli kausta sisu, kas koopia on ikka olemas 
    11. Puhasta terminali väljund
    12. Liiguta koopia oma kodukausta
    13. Vaheta töökaustaks kodukaust
    14. Tee ennist loodud kausta uus tühi fail
    15. Kopeeri terve kaust
    16. Kui oled kontrollinud, et tervest kaustast on koopia, kustuta terve originaalne kaust
    17. Kui suured on failid kopeeritud kaustas?
    18. Kustuta ka kopeeritud kaust.
```

