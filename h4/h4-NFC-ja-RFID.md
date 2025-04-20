#  h4 NFC ja RFID

## Rauta & HostOS

- Asus X570 ROG Crosshair VIII Dark Hero AM4
- AMD Ryzen 5800X3D
- G.Skill DDR4 2x16gb 3200MHz CL16
- 2x SK hynix Platinum P41 2TB PCIe NVMe Gen4
- Sapphire Radeon RX 7900 XT NITRO+ Vapor-X
- Windows 11 Home 24H2

**Tehtävän aloitusaika 20.4.2025 kello 18:30**

## a) Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?
Itselle tuli ensipuraisulta mieleen seuraavan tyyppisiä RFID tuotteita mitä omistan:
- Työpaikan kulkutunniste
- Pankki- ja luottokortit
- Passi ja henkilökortti
- Muut kortit, kuten HSL / asiakasetukortit
- Puhelin
- Älykello
- Koirien mikrosirut

Yleisellä tasolla olen varmaan melko hyvin suojautunut urkinnalta. Tunneilla opitusta materiaalista käsitin, että pankki- ja luottokortit sekä nykyiset passit/henkilökortit on niin suojattuja, että niistä on lähes mahdoton saada mitään irti. Puhelimesta ja älykellosta voisi käytännössä laittaa NFC pois päältä kokonaan, mutta riski taitaa olla aika pieni sillä tunnistautumista käyttöön tarvitaan joka tapauksessa. Eläinten mikrosiruilla vaikea usko kenenkään tekevän mitään relevanttia ja tsemppiä skannaamiseen huomaamatta. 

Itselle ehkä päälimmäisenä nousi mieleen, että teoriassa isoin riski olisi mikäli joku voisi kloonata työpaikan kulkutunnisteen. Kulkutunniste kun taitaa olla vielä LF (Low Frequency) tyypiltään niin ilmeisesti se voisi olla mahdollistakin kloonata. Tosin, normaalisti pidän työavaimia niin lähellä itseä että pitäisi nähdä todella extra efforttia päästä kloonaamaan.

(Amster 2021)
## b) Tutustu APDU komentojen rakenteeseen
Itse lähdin kysymään tarkemmin ChatGPT-4 versiolta tarkemmin aiheesta. Tarkalleen kysyin seuraavaa: `Kerro APDU:sta ja APDU komentojen rakenteesta.`

APDU-komennon rakenne koostuu pääasiassa seuraavista asioista.

- **Header:** Headerin alta löytyy CLA, INS, P1, P2
- **Body:** Bodyn alta löytyy Lc, Data Field, Le

Tarkemmin kun tarkastellaan vielä rakennetta niin:

- **CLA - Instruction class:** Protokollaluokka, voi määrittää esim salauksen
- **INS - Instruction code:** Mitä toimintoa pyydetään (esim. SELECT, READ)
- **P1 - Instruction parameter 1:** Lisätietoa toiminnosta
- **P2 - Instruction parameter 2:** Toinen lisäparametri
- **Lc - Data lenght:** Kuinka monta tavua dataa seuraa, jos sitä on
- **Command data:** Lähetettävä data
- **Le - Expected Lenght:** Kuinka monta tavua odotetaan vastaukseksi

ChatGPT antaa esimerkiksi SELECT-komennon, missä on otettu AID eli Application ID:

00 A4 04 00 07 A0 00 00 00 03 10 10 00

- 00 = CLA (ISO 7816 standardi)
- A4 = INS (SELECT-komento)
- 04 = P1 (valitaan sovellus ID:llä)
- 00 = P2 (ei mitään erityistä)
- 07 = Lc (7 tavua dataa)
- A0 00 00 00 03 10 10 = AID (Visa-kortin tyypillinen tunniste)
- 00 = Le (paljonko dataa odotetaan takaisin)

Tutkin vielä tarkemmin asiaa artikkeleista ja tarkensin tietoja, mitä ChatGPT kertoi.

(ChatGPT-4; CardLogix)
## c) Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit
Löysin uutisen [Wired sivustolta](https://www.wired.com/story/saflok-hotel-lock-unsaflok-hack-technique/), missä hakkerit löysivät vuonna 2022 vakavan haavoittuvuuden Dormakaban valmistamissa Saflok-merkkisissä RFID-lukoissa mitä käytettiin ainakin 3 miljoonassa hotellissa maailmanlaajuisesti.

Haavoittuvuudessa käytetty "Unsaflok" tapa mahdollisti minkä tahansa huoneen oven avaamisen kahdella tekniikkaa hyödyntävällä avainkortilla. Hyökkäys perustui MIFARE Classic -korttien tunnettuun haavoittuvuuteen ja Dormakaban salausjärjestelmän heikkouteen. Hyökkäyken toteuttamiseen tarvittiin vain käytetty tai vanhentunut avainkortti hotellista, RFID-lukulaite (kuten Proxmark3 tai Flipper Zero) ja Saflok-järjestelmän tuntemusta. Ensimmäinen kortti muokkaa lukon tietoja ja toinen kortti avaa lopulta oven.

Dormakaba aloitti päivityksen jakelun marraskuussa 2023 ja maaliskuuhun 2024 mennessä oli päivitetty vasta 36% lukoista. Lukot eivät ole yhteydessä internettiin, joten päivitysprosessi vaatii manuaalisen päivityksen huonekohtaisesti.

Tapauksen tutkijat eivät ole tietoisia tapauksista, joissa haavoittuvuutta olisi hyödynnetty, mutta artikkelissa korostetaan, että haavoittuvuus on saattanut olla olemassa jo vuosikymmeniä ja heidän tavoite on lisätä tietoisuutta ja kannustaa hotelleita päivittämään järjestelmänsä.

(Andy Greenberg 2024)

**Tehtävän lopetusaika 20.4.2025 kello 19:30. Aktiivista työskentelyä yhteensä noin 1 tuntia 00 minuuttia.**

## Lähteet
Sarah Amster 2021. RFID (radio frequency identification). Luettavissa: https://www.techtarget.com/iotagenda/definition/RFID-radio-frequency-identification Luettu 20.4.2025

CardLogix. Application Protocol Data Unit (APDU). Luettavissa: https://www.cardlogix.com/glossary/apdu-application-protocol-data-unit-smart-card/ Luettu 20.4.2025

Andy Greenberg 2024. Hackers Found a Way to Open Any of 3 Million Hotel Keycard Locks in Seconds. Luettavissa: https://www.wired.com/story/saflok-hotel-lock-unsaflok-hack-technique/ Luettu 20.4.2025
