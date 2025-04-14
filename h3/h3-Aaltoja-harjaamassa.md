# h3 Aaltoja harjaamassa

## Rauta & HostOS

- Asus X570 ROG Crosshair VIII Dark Hero AM4
- AMD Ryzen 5800X3D
- G.Skill DDR4 2x16gb 3200MHz CL16
- 2x SK hynix Platinum P41 2TB PCIe NVMe Gen4
- Sapphire Radeon RX 7900 XT NITRO+ Vapor-X
- Windows 11 Home 24H2

**Tehtävän aloitusaika 13.4.2025 kello 16:00**

## x) Lue/katso/kuuntele ja tiivistä

### Hubacek 2019: Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs
- Videolla käydään läpi URH sovelluksella signaalin nauhoittamista ja sen analysointia.
- Analyysistä tärkeinpinä oli bitin pituuden vastaaminen aikaan ja error tolerancen käyttö siinä yhteydessä
- Demoluointia näytettiin bitteinä ja hexinä

(Hubmartin 2019)
### Cornelius 2022: Decode 433.92 MHz weather station data
- Artikkelissa käydään läpi rtl_433 ohjelmalla dekoodaamista. 
- Lisäksi käydään läpi Universal Radio Hacker ohjelmalla signaalin nauhoittamista ja sen analysointia
- Projektissa opetettii esimerkiksi tyypillistä demodulaatiota ja digitaalista analyysiä

(Cornelius 2022)
## a) WebSDR
Käytin tehtävän tekemiseen [University of Twente, Enschede - Netherland](http://websdr.ewi.utwente.nl:8901/) Wide-band WebSDR-ohjelmaradiota.

![K1](1.png)
![K2](2.png)

Lähetystä lähdin etsimään käyttämällä Waterfall näkymää ja valitsemalla sieltä kirkkaaksi muuttuvia kohtia. Lisäksi yritin eri vaihtoehtoja AM & FM taajuu modulaation väliltä. Lopulta päädyin kuitenkin AM-modulaation taajuudelle 15594.00kHz, mistä löytyi ilmeisesti joku Lontoosta tuleva lähetys, mutta tarkkaa mainintaa ei vartin kuuntelulla saanut mikä kanava tarkalleen kyseessä. Lähetyksessä puhuttiin sijoittamisesta ja inflaatiosta englanniksi, tämän jälkeen tuli kattava sporttiuutisia.

![K3](3.png)

(Karvinen 2025; WebSDR.org; Amateur radio club ETGD)
## b) rtl_433

## c) Automaattinen analyysi

## d) Too compex 16?

## e) Ultimate

## f) Yleiskuva

## g) Bittistä

**Tehtävän lopetusaika X.4.2025 kello XXXX. Aktiivista työskentelyä yhteensä noin X tuntia XX minuuttia.**

## Lähteet
Karvinen T 2025. h3 Aaltoja harjaamassa. Tero Karvisen verkkosivut. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/ Luettu 13.4.2025

hubmartin2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. Youtube. Katsottavissa: https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s Katsottu 13.4.2025

Cornelius 2022. Decode 433.92 MHz weather station data. Luettavissa: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html Luettu 13.4.2025

WebSDR.org. WebSDR Software Radio Listing. Luettavissa: http://websdr.org/ Luettu 13.4.2025

Amateur radio club ETGD. Wide-band WebSDR. Luettavissa: http://websdr.ewi.utwente.nl:8901/ Luettu 13.4.2025

Merbanan 2025. rtl_433 GitHub Repository. Luettavissa: https://github.com/merbanan/rtl_433 Luettu 13.4.2025

Debian 2025. Package: libsoapysdr-dev. Luettavissa: https://packages.debian.org/buster/libsoapysdr-dev Luettu 13.4.2025

Jopohl 2025. urh GitHub Repository. Luettavissa: https://github.com/jopohl/urh?tab=readme-ov-file Luettu 13.4.2025

