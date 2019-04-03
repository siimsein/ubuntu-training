Ubuntu paigaldamine virtualboxi
=========================================

Alati ei ole kõige mõtekam paigaldada operatsioonisüsteeme otse arvutite peale -
operatsioonisüsteem võtab kettal ruumi, tihtipeale tahab oma partitsioone mille kirjutamine
kettale võib kaasa tuua andmekadu. Testimise eestmärgil Linuxit proovida saab mitut moodi
kartmata enda andmete ülekirjutamist. Kuna "live" moodis Ubuntu ei ole püsiv (muutused kaovad
pärast restarti) siis ehitame endale virtuaalmasina.

Virtualiseerimine on võimas tööriist - teha koopiad tervetest operatsioonisüsteemidest koos
teenustega on väga hea varundusviis. Testimiseks endale linuxi virtuaalmasinaid ehitada võib
olla heaks harjutamiseks, või juhtub et on vaja paigaldada tööriist mis jookseb ainult kindlal
operatsioonisüsteemil. Näeme küllaltki kiirelt miks pilveteenused on populaarseks muutunud - 
sama riistvara peal saab hoida kümneid kui mitte sadu virtuaalmasinaid.

Oma kursuses kasutame aga VirtualBoxi, käepärane tööriist üksikute virtuaalmasinate ehitamiseks.
Virtualbox peaks juba olemas olema kõikides arvutiklassi masinates.

## Ubuntu allalaadimine

Kuskilt peame saama ka oma koopia ubuntust, mille peal hakkame katsetusi tegema. Võime sisestada
oma valitud otsingumootorisse märksõna "ubuntu download", või vajutada [sellele lingile](http://releases.ubuntu.com/18.04.2/ubuntu-18.04.2-desktop-amd64.iso)

Kui allalaadimine lõpetab, jääb meile 1.8GB suurune fail `ubuntu-18.04.2-desktop-amd64.iso`, aga
samal ajal kui see laeb võime ettervalmistada virtuaalmasina.

## Virtualbox

Avame virtualboxi ja loome uue virtuaalmasina nupuga `new`. Nime võime ise valida ja virtuaalmasinate kausta
hoida seal kus ta on, kuid ära peaks muutma virtuaalmasina tüübi. Tüübiks määrame `Linux` ja versiooniks
`Ubuntu (64-bit)`

Edasi küsitakse meilt mälu kohta, mille vaikeväärtuse muudame ümber `2048` MB peale. Virtuaalse ketta
loome kohe, tüübiga `VDI`, kettaruumi hõivamise jätame dünaamiliseks ja suuruse jätame vaikimisi `10GB` peale.

Nüüd näeme uut virtuaalmasinat menüüs - kuid seadistamine ei ole veel lõppenud. Paremklikkame virtuaalmasina peal,
lähme Settings -> System -> Processors ja anname virtuaalmasinale ühe tuuma juurde, et ta erksam oleks.

Nüüd läheb meil siis vaja ubuntu.iso faili mille alguses allalaadima panime. Lähme samast sätete alt
alaüksusesse Storage ning lisame uue `IDE kontrolleri`. Meilt küsitakse, kas me soovime jätta 
kontrolleri tühjaks või anda talle kohe fail - anname talle kohe kätte ubuntu iso faili.

Virtuaalmasina kest on valmis, nüüd tuleb ta käivitada ja alustada Ubuntu paigaldamist.

## Ubuntu paigaldamine

Pärast virtuaalmasina käivitamist valime ubuntu paigaldamise. Klaviatuurisätted seadistame vastavalt endale, kuid
jätame vahele uuenduste allalaadimise paigaldamise ajal ja paigaldame ka minimaalse versiooni. Jätkame, 
kettavalikutes võime rahulikult lasta ubuntul kõik tühjaks kustutada ning vajutame `Install Now`.   

 