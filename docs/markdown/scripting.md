#Scriptimine

Iga hea süsteemiadministraatori ülesanne on oma tööülesandeid automatiseerida. Rusikareeglina võib öelda, et sama asja
üle kahe korra käsitsi on juba ebavajalik ja pigem võib ülesande automatiseerida. Peale järgmise korra lihtsustamise on 
automatiseerimisel ka üks suurepärane lisaboonus - dokumentatsioon. Suuremad scriptid millega teenuseid üles seatakse 
annavad aastaid hiljem aimu, mis samme oli vaja läbida peale ametliku dokumentatsiooni.

![](https://imgs.xkcd.com/comics/is_it_worth_the_time.png)

<sub><sup>Randall Munroe - XKCD</sup></sub>

Scriptide kirjutamisel on üheks tähtsamaks osaks keele valik - scriptid on mõeldud automatiseerima samme, mida 
inimene sisestaks ükshaaval. Seepärast on tavaliselt linuxi scriptide puhul ka tarvis, et scriptid saaks välja kutsuda 
süsteemseid programme ja binaare. Scriptimiskeelega bash olema me juba tuttavad, kuid nimekiri nendest on pikk. Peale 
kõikide shellipõhiste keelte kuuluvad scriptimiskeelte alla ka nt. Powershell, python, perl. Täna vaatame kahte linuxi
populaarsemat keelt - bash ja python.


##Bash


##Python

Kuigi python olemuslikult ei ole päris scriptimiskeelena mõeldud, on ta piisavalt lihtne, kerge ja võimas, et linuxis
täita scriptimiskeele rolli. Kuigi süsteemsete binaaride jooksutamine on pythonis keerulisem, pakub python täieliku turning-complete keele rolli 
scriptimises. Bashi puudusteks võrreldes pythoniga on raamatukogu (dictionary) andmetüübi puudus, lugemise lihtsus,
teksti manipulatsioonivõimekus, ja üleüldine loogika. 

Pythonis saame süsteemseid binaare kutsuda lisateegiga `subprocess`.

```
#!/bin/env python3

import subprocess

subprocess.call(["adduser", "-g", "1001", "-m", "juku" ])

```

Pythoni võimekus scriptimises on ka peidus pythoni lisapaketis `shutils`, mille dokumentatsiooni leiab TODO


