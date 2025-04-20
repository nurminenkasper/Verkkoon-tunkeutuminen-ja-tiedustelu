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

+------+------+------+-------+--------+-----------+---------+
| CLA  | INS  | P1   | P2    | Lc     | Data      | Le      |
+------+------+------+-------+--------+-----------+---------+
Kenttä | Tarkoittaa | Koko (tavua) | Kuvaus
CLA | Class byte | 1 | Protokollaluokka (voi määrittää esim. salauksen)
INS | Instruction byte | 1 | Mitä toimintoa pyydetään (esim. SELECT, READ)
P1 | Parametri 1 | 1 | Lisätietoa toiminnosta
P2 | Parametri 2 | 1 | Toinen lisäparametri
Lc | Data length | 0 tai 1 | Kuinka monta tavua dataa seuraa (jos dataa on)
Data | Data | 0–255 | Lähetettävä data
Le | Expected Length | 0 tai 1 | Kuinka monta tavua odotetaan vastaukseksi

## c) Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit

**Tehtävän lopetusaika 20.4.2025 kello XXXX. Aktiivista työskentelyä yhteensä noin X tuntia XX minuuttia.**

## Lähteet
Sarah Amster 2021. RFID (radio frequency identification). Luettavissa: https://www.techtarget.com/iotagenda/definition/RFID-radio-frequency-identification Luettu 20.4.2025

