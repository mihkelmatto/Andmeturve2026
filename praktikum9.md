Praktikumi eesmärk oli tutvuda ID-kaardi ja muude isikutuvastuse tehnoloogiatega. Käsitleti nii füüsilist ID-kaarti, ID-kaardi lugejaid, Mobiili-ID'd kui Smarti-ID'd. Samuti käsitleti Digidoc ID-kaardi tarkvara: kuidas sellega faile krüpteerida, digiallkirjastada ning kuidas on talletatud sertifikaadid. Samuti oli palju lugemismaterjale e-hääletamise korralduse ja tööpõhimõtete kohta.

## failide krüpteerimine Digidoc tarkvaraga
<img width="1918" height="1197" alt="praks9-2" src="https://github.com/user-attachments/assets/75b0c25d-b782-48b4-8f84-1fc300674345" />

## sertifikaadi päring
<img width="1918" height="1198" alt="praks9-1" src="https://github.com/user-attachments/assets/edc44844-8814-4d26-9469-c128bf636cb5" />

## allkirjastatud konteineri räsi uurimine
<img width="1918" height="1198" alt="praks9-3" src="https://github.com/user-attachments/assets/0168b216-0ac7-4428-b3c0-48def4903a27" />

## vastused küsimustele e-valimiste osas

### Kirjeldage võimalikult detailselt ja tehniliselt kuidas on tagatud hääle salajasus (kelle poolt sa hääletasid).

Hääletamise süsteemis kasutatakse "kahe ümbriku skeemi". Ümbrik koosneb kahest kihist: hääl ise on "sisemises" kihis ja isikuinfo "välimises" kihis. Hääl krüpteeritakse kõigepealt valimiste korraldajalt saadud avaliku võtmega, seejärel seotakse isikuinfo koos sisemise ümbrikuga omakorda ümbrikusse, mis krüpteeritakse isikliku võtmega.
Välimist kihti kasutatakse duplikaatide kaitseks (näiteks juhul, kui üks isik hääletab mitu korda), häälte lugemise rakendusele saadetakse isikuandmeteta sisemine kiht.
Samuti lisab turvalisust asjaolu, et häälte lugemise server pole internetiga ühendatud ning sinna viiakse info välisel andmekandjal.


### Oma antud häält on võimalik kontrollida nutiseadmes. Kuidas on tagatud, et nutiseadmega oma hääle kontrollimine ei avalikusta sinu häält?

Valimisrakendus kasutab krüpteerimiseks ka juhuarvu. See juhuarv skäneeritakse QR-koodi abil nutiseadmesse. Valimisserver saadab nutiseadmele siseise ümbriku ja valimisnimekirja. Nüüd proovib nutiseade iga valimisnimekirjas olevat isikut antud juhuarvuga krüpteerida ning peale iga krüpteerimist kontrollib, kas tulemus on identne antud ümbrikuga. Kui tulemus on identne, siis tegemist ongi antud häälega.


### 2025 aasta KOV valimised on esimesed, kus hääletamiseks saab kasutada lisaks ID-kaartile ja Mobiili ID-le ka Smart-ID tarkvara isiku tuvastamiseks ja hääle valiku kinnitamiseks. Millised muudatused seadusandluses ja Smart-ID turvalisuses võimaldavad nüüd ka Smart-ID abil e-hääletada? Vastakse võimalikult konkreetselt ja tehniliselt.
Vastavaid seadusi muudeti üldsõnalisemaks nii, et sobib ID-kaardiga "samaväärne" e-identimise süsteemi vahend. See ei maini täpselt, mis tehnoloogiaga on tegemist, vaid on nimetatud, mis standarditele vahend vastama peab. Smart-ID on nüüd lubatud, sest see vastab standarditele ning seda loetakse ID-kaardiga samaväärseks.

Smart-ID tagab turvalisuse järgmiselt:
Klient saadab allkirjastatava räsi Smart-ID serverile. Seejärel saadab server kliendile päringu, mille kasutaja oma PIN2-koodiga kinnitab. Nüüd Smart-ID server krüpteerib räsi privaatvõtmega (mis asub serveris) ning saadab tulemuse kliendile tagasi. Kuna privaatvõti ei lahku serverist, siis seda ei saa nii klient kui ka teenusepakkuja lugeda.


### Pärast e-valimiste tehnilise seletusega tutvumist milline on teie arvamus Kas e-hääletamine on ebaturvalisem, sama turvaline või turvalisem võrreldes valimiskasti juures paberhääletamisega? Palun põhjendage enda vastust ning tooge välja võimalikud ründekohad (probleemid turvalisusega), miks teie arvates üks või teine valimise vorm on turvalisem/ebaturvalisem.

Ütleks, et e-hääletamine on turvalisem, sest ükski osapool ei saa infole lihtsalt ligi pääseda. Paberhääletamisega on teoreetiliselt näiteks võimalik, et hääl ei jõua kohale, tehakse lugemisel viga või keegi jälgib salaja, mis hääl antud on. Samuti pole võimalik kontrollida, kas hääl sai registreeritud. Osa ohtudest ei pea realiseeruma isegi tahtlikult. E-hääletamisel on suurimaks ohuks erinevad tehnilised rikked (peamiselt voolukatkestuste või riistvara rikete tõttu), kuid hääle võltsimiseks või häälte seostamiseks reaalse isikuga on vaja mitmeastmelist ja tahtlikku rünnakut mitme erineva süsteemi vastu. Siin on suurimad turvariskid just allkirjastamise ja info transportimise faasis (enne, kui info jõuab valimisserverisse, mis pole enam internetiga ühendatud). Näiteks Smart-ID allkirja võltsimiseks oleks vaja samaaegselt ligipääsu nii kasutaja seadmele kui ka serverile. Hääle võltsimiseks ilmselt kõige "lihtsam" variant oleks võltsida häält täpselt enne krüpteerimist (vahetades kandidaadi nime), kuid selleks oleks vaja kasutaja seadmele ligipääsu täpselt hääletamise hetkel, või rikkuda hääletamistarkvara enne, kui see kasutajale saadetakse (eeldab ligipääsu vastavale serverile).
