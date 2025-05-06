#  h5 Laboratorio- ja simulaatioympäristöt hyökkäyksissä

## Rauta & HostOS

- Asus X570 ROG Crosshair VIII Dark Hero AM4
- AMD Ryzen 5800X3D
- G.Skill DDR4 2x16gb 3200MHz CL16
- 2x SK hynix Platinum P41 2TB PCIe NVMe Gen4
- Sapphire Radeon RX 7900 XT NITRO+ Vapor-X
- Windows 11 Home 24H2

**Tehtävän aloitusaika 5.5.2025 kello 12:00**

## a) Tutustu seuraavaan työkaluun: Evilginx2
Lähdin ratkaisemaan tehtävää ihan puhtaasti googlettamalla, miten saisi asennettua Kalille. Löytyi muutamakin eri tapa, mutta [Kalin omasta repositoriosta](https://www.kali.org/tools/evilginx2/) näytti löytyvän kyseinen paketti. Asentelin sen sieltä suoraan `sudo apt install evilginx2` komennolla.

![K1](1.png)

Ohjelma käyntiin terminaalista `evilginx2` komennolla ja heti käynnistellessä huomasin, että server domain ja server external ip ei ollut asetettuna. Googlailin hetken aikaa ja törmäsin evilginx community [ohjeisiin](https://help.evilginx.com/community), mitä alkuun lähdin noudattamaan. Asetin ohjeiden mukaan domain nimeksi päästä keksityn **hulluduunari.com** ja ipv4 osoitteeksi localhostin eli **127.0.0.1**.

![K2](2.png)

Tähän loppuikin oikeastaan tarjolla ollut ohjeet asennuksesta ja muusta järkevästä mitä löysin, joten lähdin puhtaasti tutustumaan ohjelmaan. Phishletit löytyi help komennolla ja sielä olikin yksi "Example" phislet valmiina mitä lähdin tutkimaan. Vähän neulaa heinäsuovasta lähdin syöttämään komentoja, miten niitä saisi käyttöön ja asetin esimerkiksi alkuun `phishlets enable example` komennolla kyseisen phishletin käyttöön, mutta se vaatikin hostnamen, joten seuraavaksi yritin syöttää sitä `phishlets hostname example test` komennolla.

![K3](3.png)

Vaati tietenkin hostnamen vielä, joten annoin test.hulluduunari.com sille.

![K4](4.png)

No mitä jos nyt käynnistellään phislet enable komennolla?

![K5](5.png)

Yritys hyvä kymmenen, mutta pahalta näyttää. Lähdin tutkimaan ohjelman muita vaihotehtoja ja **lures** kohdasta löytyi vaikka mitä.

![K6](6.png)

Yritin luoda `lures create` komennolla **example** luren ja näytti se ehkä onnistuneenkin?

![K7](7.png)

No joo, sanotaan, että olin TODELLA hukassa tässä vaiheessa ja lähdin perehtymään asiaan ihan muuta kuin omien neuvojen kautta. Löysinkin ihan hyvän suuntaa antavan [videon](https://www.youtube.com/watch?v=z5gLXmXIyH8) miten testata ohjelan toimintaa lokaalisti.

Tässä neuvossa oli tarpeellista ensin asettaa `/etc/hosts` localhostille muutamat osoitteet mitä käytetään.

![K8](8.png)

Tarkastelin lisäksi valmiiksi ohjelmasta löytyvää **Example** Phishletiä, mitä ajattelin tehtävän suorittamisessa käyttää.

![K9](9.png)

Mitään muutoksia en tehnyt, lähinnä halusin nähdä ja yrittää ymmärtää mitä se sisältää. Sisältä löytyi eri Proxy, auth_token, credentials ja login vaihtoehtoja. Okei, no miten niitä käytetään? Lähdin seuraavaksi tällä kertaa avaamaan evilginx2 ohjelmaa lisäsyötteellä `-developer`, mikä helpin mukaan "generates self-signed certificates for all hostnames"

![K10](10.png)

Asetin jälleen config domainin ja ipv4 osoitteen, mutta ne olikin oikeastaan samat mitä aikasemmin. Tällä kertaa kuitenkin annoin **example** phishletille hostnamen **hulluduunari.com** ja laitoin sen `phishlets enable example` komennolla.

![K11](11.png)

Seuraavaksi oli tarpeellista luoda lure, eli url osoite miten liikenteen huijaus tapahtuu. Tämä tapahtui `lures get-url 1` komennolla, mistä sain syötteenä Example phishletissäkin olleen academy osoitetta käytetyn hulluduunari.com osoitteen.

![K12](12.png)

No mitä jos avataan Firefox ja syötetään tuo kyseinen osoite sinne?

![K13](13.png)

Varoitusta puskee, mutta mennään sivustolle sisään joka tapauksessa.

![K14](14.png)

Tässä vaiheessa auki olevaan Evilginx2 ohjelmaan tuli jo ensimmäiset syötteet. Sivustoksi meille aukesi Breakdevin sivusto.

![K15](15.png)

Mitä jos painetaan Login? Olihan meillä Phishletissä credentials tietojakin, kuten aikaisemmin näkyi

![K16](16.png)

Syötin tekstiksi sähköpostin ja salasanan. Perään tietenkin login.

![K17](17.png)

Hei, saatiin sama sähköposti ja salasana syöte myös Evilginx2 puolelle! Videossa mainittiin myös, että `session` komennolla voidaan tarkastella kyseistä toimintaa.

![K18](18.png)

Nähdäänkin käytetty phishlets, käyttäjänimi, salasana, tokeni, ip-osoite ja aika. Pakko myöntää, että ihan en ole varma käytinkö ohjelmaa sillä tavalla kun oli tehtävässä tarkoitus "huijata liikennettä", mutta ihan mielenkiintoinen testailu oli ainakin ja tämähän oli kuitenkin aika tyypillinen Phishing tapahtuman emulointi.

(Kgretzky 2025; Kali.org 2025; Evilginx; Cybertech-Arena 2025)
## b) Sinulla on käytössäsi mininet ympäristö. Luo ympäristö, jossa voit tehdä TCP SYN-Flood hyökkäyksen.
Mininet ympäristön kanssa on tullut taisteltua enemmän tai vähemmän viimeisen viikon aikana. Itsellä meni ehkä tunnilla tai jaetusta ohjeistuksesta jotain ohi, mutta kaikkea maan ja taivaan väliltä on kokeiltu ympäristön käyntiin saamiseksi, mutta ei vain toimi. Opettajalle (Larille) laitoin tästä myös sähköpostia, enkä saanut hommaa skulaamaan riittävän ajoissa tehtävien palautukseen mennessä. 

Käytännössä en saa verkkolaitetta toimimaan / osoitetta mininetille. Kaikki VM Waren asetuksen on käyty ja kokeiltu läpi. Todennäköisesti käyttäjässä on vika ja löydän ratkaisun jostain vertaisarvioinnista, mutta palaan tämän tehtävän pariin vielä myöhemmin, kun saan Mininet ympäristön toimimaan.

![M1](mininet/1.png)
![M2](mininet/2.png)
![M3](mininet/3.png)
![M4](mininet/4.png)

**Tehtävän lopetusaika 6.5.2025 kello 21:00. Enemmän tai vähemmän aktiivista työskentelyä yhteensä noin 15 tuntia 00 minuuttia. Tästä ajasta suurin osa Mininetin kanssa taistellessa**

## Lähteet
Haaga-Helia Moodle. Verkkoon tunkeutuminen ja tiedustelu - ICI013AS3A-3001 - 2025p4 - Tero ja Lari. 5. Laboratorio- ja simulaatioympäristöt hyökkäyksissä

Kgretzky 2025. Evilginx GitHub. Luettavissa: https://github.com/kgretzky/evilginx2 Luettu 5.5.2025

Kali.org 2025. Evilginx2. Luettavissa: https://www.kali.org/tools/evilginx2/ Luettu 5.5.2025

Evilginx. Help - Community Intreduction. Luettavissa: https://help.evilginx.com/community Luettu 5.5.2025

Cybertech-Arena 2025. Master Evilginx Phishing Simulation on Localhost(No Domain, No VPS, Free Method!). Katsottavissa: https://www.youtube.com/watch?v=z5gLXmXIyH8 Katsottu 5.5.2025
