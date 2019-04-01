#Kasutajate ja gruppide haldamine

Linuxi puhul on failiõigused jagatud kolme kategooriasse - kasutaja, grupp ja muu. Hetkel vaatame lähemalt kasutajaid ja gruppe.

Igas linuxi süsteemis on olemas juba mingi arv süsteemseid kasutajaid ja gruppe. Neid saab kõige lihtsamini näha, kui vaatame failidesse
`/etc/passwd` ja `/etc/group`

```
ubuntu@ubuntutesting:~$ cat /etc/passwd

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
.....
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
  |    |  |     |    |          |          | 
  |    |  |     |    |          |          └ Shell
  |    |  |     |    |          └ Kodukausta asukoht
  |    |  |     |    └ Kirjeldus
  |    |  |     └ Grupi ID (GID)
  |    |  └ Kasutaja ID (UID)
  |    └ Parool - x tähistab, et räsitud parool asub failis /etc/shadow
  └ Kasutajatunnus
```


Süsteemsed grupid ja on vajaliku erinevate teenuste õiguste eraldamiseks. Kui meil on serveris andmebaasi ja veebimootor,
siis me ei taha, et veebimootor saaks otse lugeda andmebaasifaile, vaid siseneks andmebaasi läbi vastavate ligipääsupunktide. 
Sama põhimõte kehtib ka erinevate päriskasutajatega - üks ei tohiks saada teise faile lugeda, kui see pole just taotuslik.

## Root kasutaja

Nagu Windowsis, on ka linuxil administraatori kasutaja. Selle kasutaja nimeks on `root` ning `/etc/passwd` failist näeme,
et root kasutaja UID ja GID on mõlemad nullid. Root kasutaja on linuxis ka kordades võimekam kui tavaline Windowsi administraatori
kasutaja, nt. root kasutajal on õigus süsteemseid faile kustutada/muuta, kuid Windowsis on selle õigus ainult süsteemil endal
(SYSTEM nimega kasutaja windowsis). Root kasutaja kodukaust asub ka eraldi asukohas `/root`, mitte `/home/root`, juhul kui
on vaja linuxit hädaabi reźiimis parandada, on `root` kasutaja failid olemas.

Kuigi tavakasutaja ei tohiks kunagi saada ligi süsteemsete failidele, on süsteemiadministraatoritel seda ikkagi teha vaja. 
Pea iga linuxi distroga tuleb kaasa programm nimega `sudo`, mis lubab käske käivitada root õigustes. Sudo kasutamine ei ole 
otsesel vajalik - võimalus on ka root kasutaja alt sisse logida, kuid rootõigustes käsuga eksimine võib tähendada väga suurte
vigade parandamist hiljem.



##Kasutajate ja gruppide lisamine

Lisame uue kasutaja oma ubuntule - peale parooli küsitakse meilt lisateavet kasutaja kohta - hetkel pole see vajalik ja 
sammust saame läbi `ENTER` klahvi vajutamisega.

```bash
ubuntu@ubuntu:~$ sudo adduser juku
Adding user `juku' ...
Adding new group `juku' (1001) ...
Adding new user `juku' (1001) with group `juku' ...
Creating home directory `/home/juku' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:       #Linuxil parooli sissetrükkimise ajal ei näidata ühtegi märget.
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for juku
Enter the new value, or press ENTER for the default
	Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] 
```

Lisame nüüd ka kasutajale  `juku` sudo õigused. Sudo õigused asuvad failis `/etc/sudoers`, kuid kindluse mõttes ei redigeeri
me seda faili otse läbi tekstiredaktori. Sudoõiguste muutmiseks kasutame käsku `visudo` ning kuna /etc/sudoers fail on 
`root` õigustes, peame selle avama `sudo` käsuga. Seega `sudo visudo`

Leiame üles rea, mis ütleb `root    ALL=(ALL:ALL) ALL` ning duplitseerime selle, asendades kopeeritud real kasutaja root
kasutajaga juku. Kui muudatus tehtud, salvesta fail - juhul kui faili tekib viga püüab visudo selle kinni ja ei kirjuta faili üle.

Sudoõiguste jagamisega tuleb hoolikalt läbi mõelda, kas on vaja ja kas tohiks. Sudo õigustega kasutaja omab täielikku kontrolli
terve operatsioonisüsteemi üle.



