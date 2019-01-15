# PPK-paikannin ohjeet

## Asennus
PPK-paikannin toimii Android 6.0 ja sitä uudemmissa Android-puhelimissa. 
Asennus on suoraviivainen:
1. Käynnistä asennuspaketti
2. Hyväksy asennus "tuntemattomista lähteestä". Joissain puhelinmalleissa 
tuntemattomien lähteiden asennus pitää tehdä puhelimen asetuksista käsin. 
Samsung kysyy asiaa asennuksen yhteydessä. 
Yleisohjeita löytyy täältä: https://www.androidcentral.com/unknown-sources
3. Käynnistä sovellus
4. Hyväksy paikannuksen ja tekstiviestien lähetyksen & vastaanoton käyttölopa

Sovellus on nyt täysin valmis käyttöön. Se vastaa paikkatietokyselyviestiin
automaattisesti, vaikka sitä ei olisi edes käynnistetty. Käyttäjän 
ei tarvitse tehdä yhtään mitään.

Asetuksista voit tarvittaessa estää tekstiviestipaikannuksen.

## Käyttö
Sovellus tarkkailee saapuvia tekstiviestejä ja jos viesti on paikannuskomento,
vastaa sovellus sopivalla paikkatietoviestillä. Sovellus tukee tällähetkellä 
MPTP-koirapantaprotokollaa, sekä Karttapaikka-webbilinkillä vastausta.

Voit kokeilla tekstiviestipaikannusta lähettämällä itsellesi tai kaverille tekstiviestin, 
jossa lukee vain _?LOC_ (MPTP-paikannus) tai _Sijainti?_ (Karttapaikkalinkkipaikannus).

Paikannusviestit ja vastaukset näkyvät puhelimessa normaaleina tekstiviesteinä, 
eli mitään ei tapahdu käyttäjältä piilossa. Paikannuksen ollessa käynnissä
näytetään notifikaattiviesti.
Verkkoyhteyttä sovellus ei käytetä lainkaan.

Voit asetuksissa määrittää partion nimen. Tämä näytetään Karttapaikalla sijainnin
tunnisteena.

Sovellus yrittää paikantaa aina vähintään 20m tarkkuudella. 
Jos tämä ei onnistu kahden minuutin aikana, lähetetään vastauksena paras 
saatu sijainti.

Voit tehdä manuaalisen paikannuspyynnön painamalla _Paikanna nyt_-nappia. 
Sovellus näyttää tällöin saamansa tarkimman sijainnin 2 min ajalta. Sisällä 
tarkan paikan saaminen voi olla vaikeaa, joten voit joutua hetken odottamaan
ennen kuin mitään tapahtuu. 

#### Tarkkuus
Puhelin antaa arvion sijainnin laskentavirheestä. Virhe riippuu näkyvien 
sateliittien määrästä, sekä näiden asennosta taivaalla. Hyvissä olosuhteissa, kun 
 näkyvyyttä on horisonttiin joka suuntaan (esim. metsässä) laskennallinen
virhe on usein luokkaa 3m. Mäen tai rakennuksen varjostaessa jotain suuntaa, 
voi tarkkuus tippua jopa 20-30m tasolle.
 
Tarkkuus raportoidaan välinä esim 10-30m. Ensimmäinen 
luku tarkoittaa ympyrän sädettä, jonka sisällä, ainakin laskennalliesti, 
ollaan 68% todennäköisyydellä. Toinen luku, joka on noin kolme kertaa ensimmäinen,
on sellaisen ympyrän säde, jonka sisällä ollaan 99,5% todennäköisyydellä.

Laskenta ei pysty kuitenkaan huomioimaan paikannussignaalin heijastumista esim. 
korkeiden talojen seinistä, katoista tai todella suurista maastoesteistä.
Heijastumistapauksessa laskennallinen tarkkuus voi olla
hyvä, vaikka sijainti on kymmeniä metrejä pielessä!

## Käyttö b-Barkin kanssa
PPK-paikannin on täysin itsenäinen sovellus eikä vaadi b-Barkia toimiakseen. 
B-Bark ei myöskään vaadi PPK-paikanninta toimiakseen.
Näitä kahta voi kuitenkin käyttää yhdessä seuraavalla tavalla.

B-barkin asetuksista löytyy _Kohdelista > Seurattavat kohteet_. Lisää tänne
seurattava puhelinnumero uutena MPTP-pantana painamalla b-barkin seurattaat 
kohteet sivulla plus-nappia.

Kun kohde on lisätty, painamalla pitkään kohteen kohdalla voit lähettää
paikannuspyynnön. Kun kohde vastaa, näkyy tämän sijainti kartalla ja
tietoikkunassa. Tietoikkunassa nastannäköinen nappi, jossa on plus-merkki 
lähettää uuden paikkatietopyynnön.

B-Barkin kohteen tietoikkunassa akun varaustila-kenttää käytetään ilmoittamaan
sijainnin tarkkuus. Luku tarkoittaa 68% tarkkuutta, eli tämä pitää kertoa 
kolmella, jos haluat huonoimman skenarion tarkkuuden.
 100% tarkoittaa 0m virhettä ja 95% tarkoittaa
5m virhettä tai siis tarkkuutta. Kaava on siis 100m-paikannustarkkuus.
(Huom! B-barkin akkunäytössä on virhe. Virhe korjattaneen kevään aikana.)


## Jatkokehitysajatuksia
Sovelluksen tarkoitus on mahdollistaa sijainnin kysyminen partiolta ilman että
kartturin tarvitsee tehdä mitään. Tällähetkellä tuetaan MPTP-koirapantaformaattia,
mikä toimii esim. b-barkin ja Trackerin kanssa. Multimediaviestinä 
olisi mahdollista lähettää myös vastausviesti, 
jonka saisi auki GPX-formaattia tukevilla sovelluksilla.

Turvallisuuden kannalta on esitetty myös toiveita pystyä rajaamaan paikannuspyyntöjä
eri tavoin. Yritän löytää tähän helpon ja toimivan ratkaisun. Nyt mahdollista
on estää paikannus kokonaan, kun ei sitä tarvita.

Tekstiviestit kulkevat myös puhelun aikana ja huonossa kentässä,
toisin kuin dataliikenne. Tästä huolimatta sijainnin jakaminen
esim. Whatsupin kautta voisi olla hyödyllinen ominaisuus.

