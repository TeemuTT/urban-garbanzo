# Tokkeli

* 17.4.2016
* Teemu Tuomela
* WWW-palvelinohjelmointi.

Tokkeli on www-pohjainen ajankäytön seurantajärjestelmä, jonka avulla käyttäjä voi helposti tallentaa eri projekteihin käyttämänsä ajan. Käyttäjä voi luoda palveluun useita projekteja ja kommentoida sekä kategorioida eri työvaiheet. Käyttäjä voi myös kutsua ystävänsä samaan projektiin, jolloin on helppo seurata koko ryhmän etenemistä. Toiminnallisuus on pitkälti samankaltainen kuin [toggl.com](https://toggl.com/) sivustolla.

Sovellus on tarkoitettu pääasiassa omaan käyttööni opiskeluprojektien seurantaan, mutta vapaan rekisteröitymisen ansiosta sovellus on vapaasti kaikkien käytettävissä.

Sovelluksen on toteuttanut kokonaisuudessaan Teemu Tuomela osana Jyväskylän ammattikorkeakoulun IT-instituutin www-palvelinohjelmointikurssia.

# Käytetyt teknologiat

Sovellus on toteutettu käyttäen Laravel-sovelluskehystä. Halusin oppia PHP:n lisäksi mvc-mallin käyttämstä sekä sovelluskehyksen hyödyntämistä. Larvel on PHP:n kehyksistä käytetyin ja siihen päädyttiinkin sen suosion takia.

Tietovarastona käytetään SQLite-tietokantaa. SQLite valittiin sen helppokäyttöisyyden takia. Koska sovellus ei sijaitse oppilaitoksen palvelimella, ei oppilaitoksen tarjoamaa MySQL-tietokantaa ei valittu, sillä sen käyttö olisi vaatinut aina VPN-yhteyden.

Palvelimena toimi aluksi Raspberry Pi 2 Model B varustettuna Linux + Apache + SQLite + PHP-kokoonpanolla. Nykyisellään tokkeli on tarjolla myös herokussa osoitteessa [http://tokkeli.herokuapp.com](http://tokkeli.herokuapp.com).

# Järjestelmän yleiskuvaus
![deploymentdiagram](http://student.labranet.jamk.fi/~H8705/IIM50300/deployment1.png)
![deploymentdiagram](http://student.labranet.jamk.fi/~H8705/IIM50300/deployment2.png)

Sovelluksessa toteutetaan mvc-mallia. Reititin ohjaa käyttäjän pyynnön oikealle ohjaimelle. Ohjain hakee näkymälle tarvittavat tiedot ja palauttaa näkymän käyttäjän katseltavaksi.
![](http://student.labranet.jamk.fi/~H8705/IIM50300/sequencediagram.png)

Laravelin Eloquent-ORM tarjoaa hyvät välineet tietokannan hallitsemiseen. Jokaiselle tietokannan taululle on malli (Eloquent Model), jota käytetään taulun hallitsemiseen. Näitä malleja käyttäen tietokantaa voi käsitellä ymmärtämättä kyselykielistä juuri mitään.

Taulujen väliset suhteet ovat myös helposti hallittavissa. Kaikilla malleilla on funktiot, jotka palauttavat objektin relaation hallitsemiseen.
![](http://student.labranet.jamk.fi/~H8705/IIM50300/luokkakaavio.png)

Vastaavasti Tietokannan käsitemalli:

![EntityRelation](http://student.labranet.jamk.fi/~H8705/IIM50300/entityrelation.png)

SQLite-tietokannassa ei käytetä viiteavaimia. Alla oleva vanhentunut MySQL-käsitemalli auttaa hahmottamaan taulujen välisiä relaatioita:

![EntityRelation](http://student.labranet.jamk.fi/~H8705/IIM50300/entityrelation-old.png)

# Työmäärä
Projektin työvaiheet ja ajat on kirjattu itse palveluun osoitteessa [http://tokkeli.herokuapp.com/api/project/1](http://tokkeli.herokuapp.com/api/project/1).

Karkeasti työmäärät ovat seuraavat:

|Tehtävä                |Aika|
|:----------------------|:---|
|Tietokanta             |3h|
|Laravelin opettelu     |2h|
|Dokumentointi          |4h|
|Suunnittelu            |3h|
|Proto puhtaalla PHP:llä|6h|
|Vaihto Laraveliin      |10h|
|Muu logiikka           |5h 30m|
|Ulkoasu                |7h 30m|

Projektia suunniteltiin toisella kurssilla arviolta ~10h. Kokonaistyömäärä liikkunee 50 tunnin lähimain.

# Loppukaneetit
Harjoitustyö onnistui erittäin hyvin. Suunnittelussa määritellyt käyttötapaukset saatiin tomimaan ja palvelusta tuli jokseenkin helppokäyttöinen. Työssä onnistuttiin käyttämään Laravel-kehystä ja MVC-mallia niiden edellyttämällä tavalla. Harjoitustyö opetti paljon php-sovelluskehysten toimintaperiaatteista.

Muutamat virheenkäsittelyt jäivät vielä puuttumaan ja ne hoidetaan toistaiseksi ystävällisellä, mutta mitäänsanomattomalla virheilmoituksella ("Sorry, not available"). Sovelluksesta olisi mukava saada ulos myös monipuolista dataa ajan käytöstä ja esittää sitä graafisesti esimerkiksi google charts integraatiolla.

Sovellus on kuitenkin riittävän toimiva ainakin omaan käyttööni ja se pääsi jo tositoimiin windows-ohjelmointikurssin harjoitustyöni seurannassa. Tulen luultavasti käyttämään sovellusta jatkossakin ja parannuksia voi olla luvassa sitä mukaa, kun niitä itse kaipaan.

Arvioisin harjoitustyön arvosanaksi 4, edellä mainituin lisäyksin ehkä jopa 5.
