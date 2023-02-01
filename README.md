# H5 - Hello Web

## Lukuläksy
Lukuläksyä varten valitsin podcastin aiheesta TinySeed, TinyConf, joka on julkaistu 6.12.2022 Michele Hansenin & Colleen Schnettlerin toimesta. Podcast käsitteli Colleen Schnettlerin ensimmäistä TinySeed tapaamista MicroConfissa. Jouduin ennen podcastia tutustumaan TinySeediin ja sen tarjoamaan palveluun.

- TinySeedissa käsiteltiin tuotteen hinnoittelua ja liiketoimintamalleja
- TinySeed tarjoaa palveluna liiketoiminnan kiihdyttämistä siihen liittyneille yrityksille
- Kohtaaminen ja verkostoituminen olisi hyvä olla rakenteellisia
- Tuotetta pitäisi myydä tuotejohtajille (Product Manager), ei niinkään kehittäjille
- Case Study tuo lisäarvoa tuotteelle
- Asiakaskanta kannattaa olla ihan pienistä isoihin asiakkaihin. 
- Liiallinen neuvon antaminen saattaa ylikouormittaa, olisi hyvä myös pystyä luottamaan itseensä
- Intuitio tulee rakentaa, sitä ei välttämättä ole itsestään
- Liiketoiminnan kehittämistä varten olisi hyvä oppia uutta, esim. 1 asia viikossa
- Kun tuote toimitetaan, niin sitä tulee päivittää asiakkaan palautteen mukaisesti - asiakas tietysti maksaa tästä samalla
- Opi odottamattomia asioita

Podcast käsitteli mielenkiintoista aihetta ja mielestäni on tärkeää, että on TinySeedin kaltaisia organisaatioita, jotka auttavat pieniä / aloittelevia yrityksiä kasvamaan.


## Ympäristö

Hyper-V kotikoneella (Host):

- CPU: i5-9600K
- RAM: 16Gb
- HDD: 120Gb
- Win 11 Pro x64

Virtuaalikoneen speksit:

- 2 x CPU
- 4 Gb RAM
- 50 Gb HDD
- Generation 2 (Hyper-V pyytää määrittelemään)

## Aloitus 
Tehtävän tarkoituksena oli tehdä tunnilla käytyyn aiheeseen Apacheen omat kotisivut ja julkaista ne.

Aloitin tehtävät 1.2.2023 klo 16:20 käynnistämällä Debian virtuaalikoneen ja poistamalla vanhan Apache asennuksen käyttämällä komentoa
```sudo apt-get purge apache2 apache2-bin; sudo systemctl stop apache2 ``` ja samantien uudelleenasentamalla sen ```sudo apt-get -y install apache2``` </br>
![Kuva 1](https://user-images.githubusercontent.com/122887740/216070555-900ce178-b982-42c9-871f-93dc0517c728.png) </br>

## Apachen esimerkkisivun vaihdos localhostissa
Tehtävän aluksi varmistin, että apache2:n palvelu on ylhäällä käyttämällä komentoa: ```sudo systemctl start apache2``` sekä ```sudo systemctl status apache2```</br>
![Kuva 2](https://user-images.githubusercontent.com/122887740/216071847-57e8385d-ff19-4705-ae28-8c45bcaf0848.png) </br>
Ylhäällä näyttää olevan. </br>

Seuraavaksi siirryin lisäämään tekstiä localhostin esimerkki sivulle käyttämällä komentoa ```echo "Toimiikohan tämä"|sudo tee /var/www/html/index.html```
![Kuva 3](https://user-images.githubusercontent.com/122887740/216072506-29dbd4cd-3037-4026-8995-86ff11dd460c.png)
Lisäys näytti onnistuvan hyvin. Seuraavaksi vielä tarkistin tilanteen selaimella:
![Kuva 4](https://user-images.githubusercontent.com/122887740/216072709-7d1dab3c-b8c1-4901-867e-68935f8b187d.png)
Vastauksena selaimen kysymykseen: Kyllä toimii!

## Käyttäjänsivut
Klo 16:39
Siirtyessäni seuraavaan tehtävään, tuli minun alustaa ennen muokkausta Apachea käyttämällä komentoa ```sudo a2enmod userdir```. Tämä komento mahdollistaa käyttäjäkohtaisten sivujen luonnin ja muokkauksen. Komennon lisäksi tuli vielä käynnistää Apache palvelu uudelleen komennolla ```sudo systemctl restart apache2```</br>
![Kuva 5](https://user-images.githubusercontent.com/122887740/216073860-776e4c08-7b83-41e5-a8d7-be1ee0d9038c.png)</br>
Vasta alustuksen jälkeen pääsin luomaan ja konfiguroimaan käyttäjän sivut. Sivuja luotaessa on hyvin tärkeää, että navigoi käyttäjän kotikansioon ja luo sinne uuden kansion nimeltä ```public_html``` käyttämällä ```mkdir``` komentoa. Kansiossa public_html tuli micro komennolla luoda uusi tiedosto index.html käyttäen komentoa ```micro index.html```. Muokattu tiedosto näyttää tältä: </br>
![Kuva 6](https://user-images.githubusercontent.com/122887740/216074992-97298bc5-c2b6-4f77-b33e-8e0a0d120bcf.png)</br>
Julkaisun jälkeen sivusto näyttää tältä (localhost/~mattis/): </br>
![Kuva 7](https://user-images.githubusercontent.com/122887740/216075296-507d2fe1-04d0-433b-9e6d-a9057941eb6e.png)</br>

## Uuden käyttäjän käyttäjäsivut
Klo 16:49
Tehtävänanto oli käytännössä sama kuin edellisessä, mutta tehtävää varten tuli ensin luoda toinen käyttäjä koneelle ja kirjautua siihen. Aloitin luomalla uuden käyttäjän nimeltä masa käyttäen komentoa ```sudo adduser masa```:
![Kuva 8](https://user-images.githubusercontent.com/122887740/216076439-d35c0baa-bf31-4d75-9328-d7fb5c9afd00.png)
Tein samat temput kuin toisella käyttäjällä:</br>
![Kuva 9](https://user-images.githubusercontent.com/122887740/216078241-5c2cb714-d020-47c2-b2f9-546ddb5757cf.png)</br>
Kummastelin tulosta Firefoxissa: </br>
![Kuva 10](https://user-images.githubusercontent.com/122887740/216078433-767830e7-ab81-4b12-9193-376a3ce5e05d.png)</br>
Tajusin mokani hyvin pian ja loin index.html tiedoston oikeaan kansioon: </br>
![Kuva 11](https://user-images.githubusercontent.com/122887740/216078733-e35fef38-0894-4da4-93b8-9948f9b14144.png)</br>
Nyt näyttää toimivan oikein. On siis käyttäjän masa pakata kimpsut ja kampsut, sekä kirjautua ulos.

## Validi html-sivusto
Klo 17:01
Viimeistä tehtävää varten tuli katsoa ensin ohjeet sen tekemiseen, opettajani Tero Karvinen on tehnyt hyvän kuvauksen lyhyestä HTML-sivustosta omassa artikkelissaan Short HTML5 page (https://terokarvinen.com/2012/short-html5-page/). Päätin käyttää kyseistä ohjetta oman HTML5 sivun luomiseksi aloittamalla muokkaamalla muokkaamalla käyttäjänkansiossa olevalla index.html ```micro``` komennolla: </br>
![Kuva 12](https://user-images.githubusercontent.com/122887740/216082441-24741a18-af38-494d-a184-571ed02651d8.png)</br>
Valmis tuotos näytti tältä: </br>
![Kuva 13](https://user-images.githubusercontent.com/122887740/216082899-21130619-313a-4565-9197-531c159727ad.png)</br>

Lopulta vielä validoin saman sivuston syöttämällä koofdin W3C:n Markup Validation Serviceen:
![Kuva 14](https://user-images.githubusercontent.com/122887740/216084015-94459468-52c5-481b-b5a5-659d239bbe81.png)
![Kuva 15](https://user-images.githubusercontent.com/122887740/216084026-ad3a2074-f839-4e7a-8895-1b5dd0236efe.png)
![Kuva 16](https://user-images.githubusercontent.com/122887740/216084035-c62daf9e-8b56-43b3-8d14-6e137706f7c4.png)




## Lopetus
Kyseinen tehtävä avasi hyvin Apachen käyttäytymistä ja sen konfigurointia. Minun eduksi oli se, että olen aiemmilla kursseilla + elämässä käsitellyt jonkin verran HTML:ää, joten ei jäänyt tehtävät siitä ainakaan kiinni. Hommiin meni tällä erää n. 1h.

## Lähteet:
TinySeed, TinyConf - EPISODE 129 / by Michele Hansen & Colleen Schnettler (https://share.transistor.fm/s/f68bf479)

MRR tai ARR on SaaS-yrityksen liikevaihto (https://saasfinland.fi/sanasto/mrr-tai-arr-on-saas-yrityksen-liikevaihto/)

About Us, TinySeed (https://tinyseed.com/about)

Vivek, Gite, 18.1.2023 - How to view status of a service on Linux using systemctl 
(https://www.cyberciti.biz/faq/systemd-systemctl-view-status-of-a-service-on-linux/)

Tero Karvinen, 12.2.2012, Short HTML5 page (https://terokarvinen.com/2012/short-html5-page/)
