# h1 Sniff

## Rauta & HostOS

- Asus X570 ROG Crosshair VIII Dark Hero AM4
- AMD Ryzen 5800X3D
- G.Skill DDR4 2x16gb 3200MHz CL16
- 2x SK hynix Platinum P41 2TB PCIe NVMe Gen4
- Sapphire Radeon RX 7900 XT NITRO+ Vapor-X
- Windows 11 Home 24H2

**Tehtävän aloitusaika 29.3.2025 kello 19:00.**

## x) Lue ja tiivistä

### Wireshark - Getting Started

### Network Interface Names on Linux

## a) Linux
Debian 12 asennettu virtuaalikoneeseen. Lisäksi päivitetty kaikki ohjelmat, otettu käyttöön palomuuri ja asennettu Virtualbox Guest Additions. Ei ongelmia asennuksessa.

![K1](1.png)

## b) Ei voi kalastaa
Selvittelin tätä varten ensin käytössä olevan ethernet kortin nimi, jotta saadaan se suljettua. Tämä tapahtuu ottamalla esiin listaus käytössä olevista korteista komennolla **ip a**

![K2](2.png)

Testasin vielä esimerkiksi, että pingaus toimivaan osoitteeseen **8.8.8.8** toimii, ennen yhteyden sulkemista.

![K3](3.png)

Seuraavaksi suljin koko valitun käytössä olevan interfacen ja siitä saatiin heti ilmoitus yhteyden katkeamisesta.

![K4](4.png)
![K5](5.png)

Seuraavaksi testasin, toimiiko pingaus toimivaan osoitteeseen **8.8.8.8**

![K6](6.png)

Kuten näkyy, niin ei toiminut. Nostaessa yhteys takaisin ylös saadaan jälleen homma pelittämään.

![K7](7.png)

## c) Wireshark
Wireshark asentaminen käytiin hakemalla paketti.

![K8](8.png)

Asentaessa kysytään, saako muutkin kuin superkäyttäjät siepata paketteja ja valitsin tähän Karvisen Teron ohjeistuksen mukaan kyllä.

![K9](9.png)

Lisäilin oman käyttäjäni ryhmään nimeltä wireshark käyttöä varten

![K10](10.png)

Käynnistelin Wiresharkin toimimaan moitteitta.

![K11](11.png)

Valitsin oman interfaceni, mikä selvitettiin aikasemmassa kohdassa nimeksi **enp0s3** ja aloitin paketien kaappaamisen. Pingasin jälleen kohdetta **8.8.8.8** niin saatiin jotain kaapattuakin.

![K12](12.png)

## d) Oikeesti TCP/IP
TCP/IP mallihan rakentuu neljästä kerrokseta. **Application layer**, **Transport layer**, **Internet layer** sekä **Link layer**. Tehtävää varten kaappasin uudelleen omaa liikennettäni **enp0s3** ja kävin terminaaliin syöttämmässä **curl www.google.com**. 

### Application layer
Hypertext Transfer Protocol, eli HTTP näyttää host osoitteen olevan avattu www.google.com ja näyttää esimerkiksi source sekä destination valitut portit.

![K16](16.png)

### Transport layer
Transmission Control Protocol. Näyttää esimerkiksi source ja destination portit.

![K15](15.png)

### Internet layer
Internet Protocol Version 4. IPV4. Näyttää käytössä olevan IPV4 osoitteet molempiin suuntiin.

![K14](14.png)

### Link layer
Ethernet II. Näyttää MAC-osoitteet. Kuvasta voidaan esimerkiksi päätellä käytössäni oleva Realtekin valmistama verkkokortti.

![K13](13.png)

## e) Mitäs tuli surffattua?

## f) Mitä selainta käyttäjä käyttää?

## g) Minkä merkkinen verkkokortti käyttäjällä on?

## h) Millä weppipalvelimella käyttäjä on surffaillut?

## i) Analyysi

**Tehtävän lopetusaika 29.3.2025 kello XXXX. Aktiivista työskentelyä yhteensä noin X tuntia.**

## Lähteet

