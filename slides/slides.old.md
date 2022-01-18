---
title: Cloud native technologie
separator: <!--s-->
verticalSeparator: <!--v-->
revealOptions:
transition: 'fade'
data-separator-notes: "^Notes:"
---

<!-- .slide: data-background="images/uvod-background.jpg" data-background-size="1920px" -->

<!--s-->
<!-- .slide: data-background="images/historie-background.jpg" data-background-size="1920px" -->
## Trocha historie nikoho nazabije

<!--s-->

<!-- .slide: data-background="images/pravek-background.jpg" data-background-size="1920px"  -->

#### Počítačový pravěk (do cca 80. let)


<div id=left2>

* první aplikace běží přímo na hardwaru
* vznik operačních systémů
* terminálové aplikace
* vyšší programovací jazyky a vznik operačních systémů

</div>

Notes:
- (zminka) o los alamos, von nuemanovi a vypoctech pro projekt vodivoe bomby<BR>
- prvni aplikace bezi primo na hardwaru - nutnost znat strojovy kod/assembler<BR>
- (zminka) jazyk c<BR>

<!--s-->

<!-- .slide: data-background="images/lan-background.jpg" data-background-size="1920px"  -->

#### 1980 - 2000 Věk sítí

<div id=left2>

* rozmach lokálních sítí a protokolů (Ethernet)
* důraz na sdílení dat

</div>

Notes:
- obrazek z dooma, netwaru, dosu
- (zminka) rozmach non-intel platforem (Sparc, Alpha, Irix)
- (zminka) firma novel
- (zminka) bbs/fidonet vytacena spojeni
- (zminka na konci) prvni klient/server aplikace
- norma posix

<!--s-->

<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### 2000 - 2010 rozmach internetu

<div id=left2>

* klient/server aplikace
* nástup nových technologií jako virtualizace apod.
* rozmach e-commerce

</div>

Notes:
- (zduraznit) slovo "internet" - mezi sitovy - mozna samostatny slide
- klient/server aplikace
    - priklad obchodu s vinem
- zduraznit ze architektura client/server umoznila vznik mnoha sitovych aplikacs
- (zminka) server side pages/cgi
- (zminka) oddeleni computingu/data - diskova pole/ san site aj
- (zminka) s rozmachem e=comerce vzrustaji pozadavky na robustnost, ha apod

<!--s-->

<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### 2010+

<div id=left2>

* velký důraz na provázání aplikací (a dat)
* spousta služeb dostupných na internetu se stává kritickými pro chod firem/společnosti
* požadavky na odolnost proti výpadku, dostupnost služeb, škálovatelnost, bezpečnost

<BR>
<BR>

## => Cloud computing!

</div>

Notes:
- (zminka) trivrstva architektura
- (zminka) pokus byl grid

<!--s-->

<!-- .slide: data-background="images/biladira-background.jpg" data-background-size="1920px" -->

## ...ale co to je ?

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Cloud je infrastruktura, která umožňuje bezpečný běh aplikací odolných vůči výpadku

<div id=left2>

* infrastruktura je dynamická
* umožňuje horizontální škálování

</div>

Notes:
Musime prepsat, vymyslet apod

<!--s-->

<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

## Architektura mikroslužeb

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Monolitické aplikace

<div id=left2>

* vetšinou 3 vrtsvá architektura (prezenční vrtva, aplikační vrstva, databáze)
* výhody
 * rychlost 
* nevýhody
 * s komplexitou řešení rostou i požadavky na zdroje (a to jak lidské tak i výpočetní)
 * složitá škálovatelnost - často pouze vertikálně
 * deployment, management komponent, udržitelnost kódu, vysoká dostupnost (HA)

</div>

Notes:
- (popis) hlavne aplikacni servery
- (popis) jedontlive komponenty komunikuji uvnitr instance os pomoci jeho primitiv jako jsou sockety, sdilena pamet etc

<!--s-->
<!-- .slide: data-background="images/microservices-background.jpg" data-background-size="1920px"  -->

#### ...a proto přišly Mikroslužby

<div id=left2>

* místo monolitické aplikační vrtstvy malé
  autonomní aplikace
* komunikace microservice mezi sebou 
  se děje po síti

</div>

Notes:
(popis) potrebujem nejaky obrazek

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

####  Výhody použití mikroslužeb

<div id=left2>

* malé autonomní nezávislé celky se snáze vyvíjí a spravují
* teoreticky vyšší odolnost vůči výpadku (Netflix chaos monkey :)
* rychlejší uvedení nových verzí do produkce

</div>

Notes:
- (zminka) agile projektove metodiky



<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Výhody použití mikroslužeb II

<div id=left2>

* horizontalní škálování
* teoreticky vyšší úroveň bezpečnosti
* vhodné pro nasazení do public cloudu
* možnost využití public cloud služeb (PaaS, FaaS)
* automatizace

</div>

Notes:
(zminka) capacity on demand, hpa
(zminka) casto bezi v kontejnerech

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### ...ale jsou tu i jistá úskalí - třeba síťová infrastruktura

<div id=left2>

* kapacita není nekonečná
* latence nejsou nulové
* musí být citlivě navržena tak, aby byla odolná vůči výpadkům

</div>

Notes:
(zminka) socket vs tcp socket
(zminka) sdn a dynamicke prostredi - srovnani s legacy prostredim

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### ...nebo v oblasti správy, managementu a architektury

<div id=left2>

* komplexita infrastruktury a architektury
* nároky na monitoring, logging a tracing
* problém držení stavu - jak na statefull aplikace ?
* nároky na lidské zdroje, odbornost atp.

</div>

Notes:
(zminka) Monitoring - legacy vs dynaicke kontejnery- jine paradigma
(zminka) priklad s bankou
(zminka) problem s ladenim aplikaci

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->

## Komponenty, technologie

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Virtualizace I

<div id=left2>

- umožňuje spustit více instancí OS na jednom fyzickém počítači. 
- rozděluje prostředí serveru na fyzický a virtualní hw
- jednotlivé instance OS jsou od sebe oddělěny
- velmi stará technologie (1972 - ibm vm/370)

</left2>

Notes:
- (zminka) firma vmware a intel like virtualizace
- (popis) co virtualizace obecne je - realny hw na backendu, na fe instance os na nejakem generic hw
- (zminka) ruzne typy (partitioning, emulace)
- (zminka) ruzne platformy (powervm - pouziva se dodnes, sparc, dec, apod )
- (zminka) overhead, podpora hw (vtd, srv-iov, apod)

<!--s-->
<!-- .slide: data-background="images/virtualization-background.jpg" data-background-size="1920px"  -->

<BR>
<BR>
<BR>
<BR>

#### Virtualizace II
<BR>

<div id=left2>

Základem je tzv. Hypervisor, operační systém optimalizovaný na správu virtualních serverů

</div>
Notes:
(obrazek hypervisoru)
(zminka) hpervisor muze bezet i "vedle" os - lehce popsat jak je to mozne


<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Virtualizace III - výhody a nevýhody

<div id=left2>

* možnost automatizace
 * jedna z klíčových vlastností komponent v cloud native světě
* jednotný hw => snadnější backup/restore
* tiering, optimalizace zdrojů (sítě, storage, cpu, paměť)
* pokročilé funkce jako je přesun vm za běhu, snapshoty, replikace dat, deduplikace paměti apod
* ...nicméně jistá režie (v pruměru cca 5%)
* vyšší nároky na storage hw (většinou je nutná nějaká forma SAN)

</div>

Notes:
- (zminka) sdileni cpu, deduplikace pameti apod
- vysvetlit proc je nutne mit san - obrazek ? 

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px"  -->

#### Virtualizace na to naše domácí žvýkaní ;-)

<br>

<div id=left2>

- https://www.virtualbox.org/
- https://www.vmware.com/products/workstation-player.html
- https://www.qemu.org/

</div>

Notes:
podivat se na stranky treba vboxu, zduraznit k cemu je to dobry pro
domaci ucely. Napriklad vyzkouseni si jineho os, zminit moznost sdileni 
dat mezi hostitelskym a hostovanym systemem apod

<!--s-->
<!-- .slide: data-background="images/containers-background.jpg" data-background-size="1920px" -->

#### Kontejnery I

<div id=left2>

* slouží k relativně bezpečnému provozovaní (nejen) microservices
* klíčová myšlenka je izolace aplikace/processu od okolního světa OS a to zejména
 * od ostatních procesů/aplikací
 * síťového a i/o stacku
* správa výpočetních zdrojů - workload management
* pozor nejedná se o druh virtualizace!

</div>

Notes:
(popis) co to znamena
    - popsat jak vypada prostredi linuxoveho/windows serveru, balicky
    - vysvetlit jaky je problem je napriklad upgrade
    - vysvetlit co je image
    - zduraznit ze se nejedna o virtualizaci
    - polozit otazku jak vidi svuj svet aplikace
        - predstavte si ze jste apliace, jaky svet vlastne vidite ?
            - nejake soubory na fs
            - sitova rozhranni
            - processy kolem sebe
            - ...zkratka nejak humpolacky vysvetlit linux namespaces
- (zminka) technologie je opet velmi stara (aix wpars, freebsd jails, solaris zones apod)

<!--s-->
<!-- .slide: data-background="images/containers-background.jpg" data-background-size="1920px" -->

#### Kontejnery II - Obrazy

<div id=left2>

* Každý kontejner se startuje ze svého obrazu (image)
* Tvorba image je popsána jednoduchým souborem (docker file)
* Image jako jsou uloženy v repositářích a mohou být sdíleny i přes internet
  * dockerhub - public repository
  * hub.docker.com 

</div>

Notes:
- (zminka) duvod proc docker prorazil a stal se popularni
(ukazka startu nejake aplikace)

<!--s-->
<!-- .slide: data-background="images/containers-background.jpg" data-background-size="1920px" -->

#### Kontejnery III - Stateless prostředí


<div id=left2>


* běžící kontejner i obraz jsou read-only
* pokud proces v kontejneru nebo kontejner samotný "umře", veškerá data se obvykle zahodí
* neladí se chyby "uvnitř" kontejneru, řeší se pouze funkčnost jako celku
* aplikace v kontejneru by díky obrazu měla běžet na jakémkoliv systému stejně

Notes:
(zminka o dockeru)
(zminka - chalenge) o tom ze kontejnery na linuxu nejsou zavisle na dockeru, ten pouze prinasi lepsi management
(zminka) aplikace v kontejneru by díky obrazu měla běžet na jakémkoliv systému stejně - záleží na infrastruktuře
         a architekture - obraz je platforme zavisly. Neni mozne aby intel aplikace bezela na armu 

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->

#### Další technologie

<div id=left2>

* Infrastructure as code
* rozkládání požadavků (dns, loadbalancery, reverse proxy)
* softwarově definované sitě
* objektové storage
* document oriented databáze (nosql)
* monitoring, logging, tracing
* CI/CD

</div>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->

#### Další technologie - linky

<div id=left2>

- https://www.cncf.io/
- https://kubernetes.io/
- https://www.nginx.com/
- http://www.haproxy.org/
- https://antrea.io/
- https://ceph.io/
- https://www.elastic.co/
- https://prometheus.io/

</div>

<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->

#### Otázky ?


<!--s-->
<!-- .slide: data-background="images/general-background.jpg" data-background-size="1920px" -->

#### Pojmy

<div id=left2-small>

* Public cloud:
 Prostředí poskytované 3rd firmou. Nejznamějším provideři: Amazon (AWS), Google (GCP), Microsoft (Azure)
* Cloud on-premise:
 Řešení cloud technologii na vlastní infrastruktuře
* IaaC: Infrastruktura jako kód - prvky infrastruktury (servery, switche, site, storage apod) se vytváří pomoci
  skriptovacího (ansible) nebo deklarativního jazyka (teraform) 
* IaaS:
 Inftrastruktura jako služba. Pronajímané virtuální prostředí na míru v rámci nějakého public cloudu
* PaaS:
 Platforma jako služba. Komponenty(např. elasticsearch, mongodb, kuberenetes apod) dle požadavků v rámci public cloudu. 
* FaaS:
 Funkce jako služba: Možnost spuštění jednoduchých úloh (třeba python skripty) v rámci veřejného cloudu 
* Horizontální škálování: Výkon aplikace se zvyšuje přidáním instancí místo zvyšováním výkonu hw (vertikální škálování)

</div>