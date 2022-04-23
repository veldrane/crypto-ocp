---
title: Velmi jemný úvod do kryptografie
separator: <!--s-->
verticalSeparator: <!--v-->
revealOptions:
transition: 'fade'
data-separator-notes: "^Notes:"
---

<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->
## Velmi jemný úvod do kryptografie

<!--s-->

<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Co řešíme

<div id=left2>

* přenos dat zabezpečeným kanálem (šifrování)
* identitu komunikujících stran (podpis,certifikáty)
* integritu přenášených zpráv (hash algoritmy)
* bezpečný přenos klíčů apod (key-exchange algoritmy) 

</div>

Notes:
- Vysvětlit že celá věc není jen o šifrování<BR>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Šifrovací algoritmy

Notes:
- Možná předělat nebo dát až nakonec<BR>
* symetrické
* asymetrické


<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Symetrické šifry

<div id=left2>

* symetrické proto, že k šifrování a dešifrování zpravidla používáme stejný klíč
* výhody:
  * rychlost
  * možnost hw akcelereace (aes-ni apod.)
  * délka klíče
* nevýhody:
  * nutný zabezpečený kanál pro přenos klíče, možná kompromitace
  * nachylné k útokům typu kpa, cpa apod
https://github.com/robertdavidgraham/ecb-penguin
* příklady: DES, AES, Chacha (wireguard)

</div>

Notes:
- revize, zjistit ruzne mody apod, obrazek symetrickeho siforvání<BR>

<!--s-->
<!-- .slide: data-background="images/background-keyexchangeproblem.jpg" data-background-size="1920px"  -->

#### Problém - Jak bezpečně přenést klíče ??

Notes:
  * kombinací symetrických a asymetrických algoritmů (srovnej tls_rsa_with_aes_256_gcm_sha384)
  * key exchange algoritmy


<!--s-->
<!-- .slide: data-background="images/background-diffie-hellman.jpg" data-background-size="1920px"  -->


#### Diffie-Hellman Algoritmus

<div id=left2>

  * Algoritmus umožňuje vytvořit klíč bez jeho fyzické výměny 
    * základ je modulo aritmetika nad prvočísly a problém tzv. diskrétního logaritmu
    * long story short: 
      * obě strany sezení si vygenerují pár prvočísel
      * jedno z nich zveřejní tomu druhému
      * na základě dalších výpočtů dojdou ke stejné hodnotě klíče
      * v praxi se používají velmi velká prvočísla a tím se zvyšuje bezpečnost (entropie) klíče
  * Vygenerovaný klíč, je poté použit v nějaké symetrické šifře pro vytvoření zabezpečeného kanálu 
  https://www.youtube.com/watch?v=d1KXDGgwIpA

</div>

Notes:
- obrázek rsa tvůrců<BR>

<!--s-->
<!-- .slide: data-background="images/background-diffie-hellman.jpg" data-background-size="1920px"  -->


#### Diffie-Hellman Algoritmus - praktické informace

<div id=left2>

  * DH key exchange je nedílnou součástí TLS specifikace pro iniciální výměnu klíčů
  * V praxi se přechází na novější schéma ECDH, které
    * je rychlejší
    * ma menší klíče
  * TLS 1.2 nabízí jediné schéma bez DH, v TLS 1.3 jsou všechny schémata s DH
  * Pokud TLS používá DH schéma není možné provoz dešifrovat pomocí privátního klíče: https://www.root.cz/clanky/desifrujeme-https-pomoci-nastroje-wireshark/ 

</div>

Notes:
- obrázek rsa tvůrců<BR>

<!--s-->
<!-- .slide: data-background="images/background-riviestandco.jpg" data-background-size="1920px"  -->

#### Asymetrické šifry

<div id=left2>

* Dva na sobě závislé klíče:
  * Veřejný - protistrana využije k šifrování
  * Privátní - dešifrování zpráv zašifrovaným veřejným klíčem
* Můžeme ale klíče použít i pro podepisování zpráv
  * Privátním klíčem zprávu zašifrujeme
  * Veřejným klíčem zprávu rozšifrujeme => jsme autory zprávy
  * V praxi se kombinuje s hashovací funkcí
* výhody:
  * relativní bezpečnost
* nevýhody:
  * nutný zabezpečený kanál pro přenos klíčů, možná kompromitace
  * vyšší výpočetní náročnost
  * délka klíče (RSA)
* příklady: RSA, ElGamal, ECC algoritmy (ECDSA).

</div>

Notes:
- obrázek rsa tvůrců<BR>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Hashovací funkce - kontrola integrity přenášených zpráv

<div id=left2>

* Hashovací fce ja taková která převede vstupní data do množiny s menší mohutností (prostě udělá otisk/checksum etc)
* tato funkce by měla být nejlépe tzv. bezkolizní 
* příklady: SHA family, MD5 (nepoužívá se, nalezeny kolize => prolemena) 

</div>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Hashovací funkce - pokračování

<div id=left2>

* možné využití:
  * zjištění zda se zprávou nikdo nemanipuloval
  * ...nebo zda nebyla poškozena
  * umíme ověřit zda byly poslány nebo zadány správné údaje aniž bychom je znali (viz. /etc/shadow)
    * nachylné k útokům pomocí rainbow tables -> řešení salt nebo iv https://project-rainbowcrack.com/table.htm
  * v kombinaci s asymetrickou (většinou) šifrou umíme vytvořit tzv. ELEKTRONICKÝ PODPIS.
  * Hashovací funkce se také hojně využívají jako tzv. hash indexy (memory mgmt, db engines apod). 
    * zadáte vstupní data -> udělá se hash -> ten ukazuje na data která hledáte (index)

</div>


<!--s-->
<!-- .slide: data-background="images/background-identity.jpg" data-background-size="1920px"  -->

#### ...ale co když komunikuju s někým jiným než si myslím


<div id=left2>

  * musíme nějak ověřit totožnost protistrany....

</div>

Notes:
- obrázek rsa tvůrců<BR>

<!--s-->
<!-- .slide: data-background="images/background-cert.jpg" data-background-size="1920px"  -->

#### Co je certifikát

<div id=left2>

  * Certifikát je struktura popisující jeho vlastníka
  * Obsahuje:
    * Atributy
    * Většinou veřejný klíč držitele (ale není podmínkou)
    * Je podepsán privátním klíčem Certifikační Autority (selfsigned neřešíme)
  * Různé formáty (PEM, DER, P12...)
  * X509 ITU Standard

</div>


<!--s-->
<!-- .slide: data-background="images/background-cert.jpg" data-background-size="1920px"  -->

#### Důležité atributy


<div id=left2>

* Platnost
* Subject
* Seriové číslo
* Kdo ho vydal
* Informace o klíčích 
* Podpis CA
* OCSP/CRL

</div>

Notes:
- Možná předělat nebo dát až nakonec<BR>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Certifikční autorita


<div id=left2>

* Prezentuje se vlastním certifikátem, který obsahuje její veřejný klíč
* Pečlivě chrání vlastní privátní klíč
* Každý vydaný certifikát musí mít unikátní SN
* Je zodpovědná za distrubuci CRL (případně OCSP)
* Je zodpovědná za pravost jeho vlastníka
  * někdy zavádíme termín Registrační Autorita (hlavně u veřejných CA)
* Může být "podepsána" jinou CA => tzv. chain. (používáme ve FEG) => Anchor of Trust

</div>

Notes:
- Možná předělat nebo dát až nakonec<BR>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Postup při vytváření certifikátů


<div id=left2>

* uživatel vytvoří dvojici klíčů
* vytvoří tzv. CSR který obsahuje:
  * atributy popisující uživatele (případně server, email)
  * veřejný klíč
  * Poznámka: openssl umí vytvořit klíče a příslušný CSR v jediném kroku.
* Paranoici si vytvoří klíče + CSR sami, v praxi je většinou vytvořen na nějakém trusted zařízení CA/RA  
* CA ověří uživatele a to že informace v CSR jsou v pořádku
* CA vydá certifikát s unikátním SN a přidá atributy, které ji popisují, případně další atributy vlastníka

</div>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Srovnání pki a jwt/openid connect

<div id=left3>

* Certifikační autorita
* Longterm validita (typicky rok)
* Šifrováni, Autentizace, Podpis
* Osoby, Servery
* Atributy, kliče, podpis

</div>

<div id=right3>

-
-

</div>

<div id=middle3>

* Identity Provider (IdP)
* Shortterm (minuty max dny)
* Autentizace, Autorizace
* Osoby, Aplikace
* Atributy, podpis

</div>

Notes:
- Možná předělat nebo dát až nakonec<BR>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Malý slovníček pojmů


<div id=left2>

* plain text/šifrovaná zpráva
* šifrovací alogitmus
* hash algoritmus
* key-exchange algoritmus
* klíč
* inicializační vektor
* certifkát
* salt
* TLS

</div>

Notes:
- Možná předělat nebo dát až nakonec<BR>