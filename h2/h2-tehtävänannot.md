# h2 Tehtävänannot

## Rauta & HostOS

- Asus X570 ROG Crosshair VIII Dark Hero AM4
- AMD Ryzen 5800X3D
- G.Skill DDR4 2x16gb 3200MHz CL16
- 2x SK hynix Platinum P41 2TB PCIe NVMe Gen4
- Sapphire Radeon RX 7900 XT NITRO+ Vapor-X
- Windows 11 Home 24H2

**Tehtävän aloitusaika 6.4.2025 kello 17:00**

## x) Lue/katso/kuuntele ja tiivistä

### Selitä tuskan pyramidin idea
- Tuskan pyramiidi kuvaa sitä, kuinka hyökkääjän tiedon tunnistamisen arvo vs aiheutuva vaiva kohtaavat, eli käytännössä kuinka paljon työtä vaaditaan hyökkääjältä hyökkäyksen muokkaamiseen.
- Tuskan pyramiidissa on seitsemän eri kohtaa. Helpoin on hash values pyramiidin alin, välistä löytyy IP addresses, domain names, network/host artifacts, tools ja ylimpänä ns. vaikein eli TTP's (Tactics, Techniques and Procedures)

(Bianco 2013)
### Selitä timanttimallin (Diamond Model) idea
- Timanttimalli on neljästä toisiinsa liittyvstä ydinteemsta muodostuva tunkeutumisen analysoinnin kehys
- Neljä ydinteemaa ovat: Adversary, Capability, Infrastructure ja Victim

(Caltagirone 2013)
## a) Apache log
Tehtävän suorittamista varten oli alkuun oleellista asentaa ja käynnistää Apache2 demoni.

![K1](1.png)
![K2](2.png)
![K3](3.png)

Aktiivisten lokitietojen tarkastelua varten suoritin komennon **sudo tail -F /var/log/apache2/access.log** ja refreshasin localhost osoitteen selaimessa.

![K4](4.png)

Tarkastellaan ylimmäistä lokitietoa tarkemmin.
- **127.0.0.1**: Tämä on IP-osoitteeni, tässä tapauksessa localhost osoitteeni sillä pyyntö on tullut samalla koneelta missä palvelin (Apache2) toimii.
- **Päivämäärä ja aika**: Kuvaa luonnollisesti tapahtuman aikaa.
- **GET / HTTP/1.1**: Kysessä on GET-pyyntö, millä pyydettiin palvelimella tietoja. HTTP 1.1 on protokolla, mitä käytettiin.
- **200**: HTTP-statuskoodi, 200 tarkoittaa OK, eli pyyntö onnistui.
- **3388**: Bytes Sent. Palvelimen lähettämän vastauksen tavujen kokonaismäärä.
- **-**: Referer kenttä, eli näyttää sivun URL, jola käyttäjä tuli pyydetylle sivulle. Tässä tapauksessa - tarkoittaa, että käyttäjä ei lähettänyt Referer otsikkoa vaan kirjoitti URL esimerkiksi suoraan selaimeen kuten tein.
- **Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0** User Agent. Tunnistaa mistä ohjelmistosta, eli selaimesta tässä tapauksessa pyyntö on tullut.

(Karvinen 2025; Dancuk 2024)
## b) Nmapped
Tehtävää varten asentelin alkuun nmapin.

![K5](5.png)

Ettei vahingossakaan skannata muita kuin omia portteja, suljin varmuudeksi verkkoyhteyteni. Testiksi pingaus 8.8.8.8, että meni varmasti kiinni.

![K6](6.png)

Tarkoitus oli porttiskannata omaa localhostia. Tein sen tässä tapauskessa komennolla **sudo nmap -T4 -A localhosts**. Analysoidaan vielä syötettyä tekstiä tarkemmin:

- **nmap**: nmap valintakomento / ohjelman nimi, että saadaan edes ohjelma käyttöön.
- **-T4**: -T0-5 valinnalla saadaan määritettyä kuinka porttiskannaus ajoitetaan. -T0 ollen hitain vaihtoehto ja -T5 nopein. Tässä skannauksessa käytetty -T4 vaihtoehto on manuaalin mukaan luokkaa "Aggressive scan".
- **-A**: on version detection valinta. Lisäämällä -A syötteeseen, porttiskannaus toimittaa esimerkiksi OS detection, version detection, script scanning ja traceroute lisäykset skannaukseen.
- **localhost**: Toimittaa kohteen virkaa. Tähän voisi vaihtaa minkä tahansa IP osoitteen mitä skannataan, mutta koska kohteena on oma tietokone voidaan käyttää luonnollisesti myös localhost vaihtoehtoa.

![K7](7.png)

Tuloksia voidaan analysoida hieman tarkemmin, mutta etenkin 80/TCP oli pyydetty analysoitavaksi tehtävän puolesta:

- **Starting Nmap 7.93**: Nmap käynnistyy ja lisäksi kerrottu versionumero sekä ajankohta
- **Nmap scan report for localhost**: Kohdeosoite
- **Host is up**: Vahvistus siitä, että kohde on tavoitettavissa
- **Not shown**: 997 suljettua tcp porttia ei näytetty
- **80/tcp open**: Portista 80 löytyy puolestaan käynnistelty Apache2 ja siihen liittyvät http-server-header/title postaukset
- **Network Distances**: 0 hops, koska tapauskessa skannataan omaa verkkoa.
- **OS and Service detection performed**: Tämä on vain muistutus siitä, että OS and Service detection suoritettiin.
- **Nmap done**: Lopuksi vielä raportti siitä, kuinka monta IP-osoitetta skannattiin ja kuinka kauan skannauksessa kesti. Tässä tapauksessa yksi osoite ja 10.06 sekunttia.

(Karvinen 2025; Nurminen 2025)
## c) Skriptit

## d) Jäljet lokissa

## e) Wire sharking

## f) Net grep

## g) Agentti

## h) Pienemmät jäljet

## i) Hieman vaikeampi

**Tehtävän lopetusaika X.4.2025 kello XXXX. Aktiivista työskentelyä yhteensä noin X tuntia XX minuuttia.**

## Lähteet
Karvinen T 2025. h2 Tehtävänannot. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/ Luettu 6.4.2025

Bianco D 2013. The Pyramid of Pain. Enterprise Detection & Response verkkosivut. Luettavissa: https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html Luettu 6.4.2025

Caltagirone, Pendergast & Betz. The Diamond Model of Intrusion Analysis. Luettavissa: https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf Luettu 6.4.2025

Dancuk M 2024. Apache Log Files: How to View, Configure & Use Them. PhoenixNAP verkkosivut. Luettavissa: https://phoenixnap.com/kb/apache-access-log Luettu 6.4.2025

Nurminen 2025. H1 Kybertappoketju. GitHub. Luettavissa: https://github.com/nurminenkasper/Tunkeutumistestaus/blob/main/h1/h1-kybertappoketju.md Luettu 6.4.2025


