---
title: Návrh aplikace orientované na mikroslužby
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pochopit výhody a nevýhody aplikace orientované na mikroslužby, lze provést informované rozhodnutí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 777262ddeecf1e171344b34e586032e56f398463
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674390"
---
# <a name="designing-a-microservice-oriented-application"></a>Návrh aplikace orientované na mikroslužby

Tato část se zaměřuje na vývoj aplikace s hypotetické enterprise na straně serveru.

## <a name="application-specifications"></a>Specifikace aplikace

Hypotetický aplikace se stará o žádosti o provádění obchodní logiky, přístup k databázím a vrácení odpovědi HTML, JSON nebo XML. Říkáme bude, že aplikace musí podporovat širokou škálu klientů, včetně stolních počítačů s jednostránkové aplikace (SPA), tradičními webovými aplikacemi, mobilní webové aplikace a nativních mobilních aplikací. Aplikace může také zveřejnit rozhraní API pro třetí strany k využívání. Je také třeba schopná integrovat své mikroslužby nebo externím aplikacím asynchronně, tak, aby přístup vám pomůže odolnost proti chybám mikroslužeb v případě částečné selhání.

Aplikace se skládá z těchto typů komponent:

- Součásti prezentace. Toto jsou zodpovědná za zpracování uživatelského rozhraní a spotřebovává vzdálené služby.

- Domény nebo obchodní logiku. Toto je aplikace logiky domény.

- Logika přístupu k databázi. To se skládá z komponenty přístupu dat zodpovědná za přístup k databáze (SQL a NoSQL).

- Integrace logiku aplikace. To zahrnuje zasílání zpráv kanálu, především podle zprostředkovatele zpráv.

Aplikace bude vyžadovat, aby vysokou škálovatelnost, zároveň umožní její svislé subsystémy pro horizontální navýšení kapacity samostatně, protože určité subsystémy bude vyžadovat další škálovatelnost než jiné.

Aplikace musí být schopni nasadit ve více prostředích infrastruktury (více veřejných cloudech a v místním) a v ideálním případě by měl být napříč platformami, možnost pro snadný přechod od Linuxu na Windows (nebo naopak).

## <a name="development-team-context"></a>Kontext týmu vývoje

Také předpokládáme následující skutečnosti související proces vývoje pro aplikaci:

- Máte více vývojářské týmy, zaměřuje se na různé obchodní oblasti aplikace.

- Novým členům týmu musí být tak produktivní rychle a aplikace musí být srozumitelné a upravit.

- Aplikace bude mít dlouhodobé vývoj a neustále se měnící obchodní pravidla.

- Potřebujete dobrou dlouhodobou udržovatelnost, což znamená, že máte flexibilitu při implementaci nových změn v budoucnu při zachování aktualizovat více subsystémů s minimálním dopadem na ostatních subsystémů.

- Chcete postupů průběžné integrace a průběžného nasazování aplikace.

- Při vyvíjí aplikace chcete využít výhod nově vznikající technologie (architektury, programovacích jazyků, atd.). Nechcete, aby aplikace úplné migrace při přesunu do nových technologií, protože, která by za následek vysoké náklady a ovlivnit předvídatelnost a stabilita aplikace.

## <a name="choosing-an-architecture"></a>Výběr architekturu

Co by měla být architektura nasazení aplikace? Specifikace pro aplikaci společně s vývoj kontextu, důrazně doporučujeme, že by měla navrhovat aplikace podle rozložení do samostatného subsystémů ve formě spolupracujících mikroslužeb a kontejnerů, kde mikroslužby je kontejner.

V takovém případě každou službu (kontejner) implementuje sadu získá na ucelenosti a úzce související funkce. Aplikace může například sestávat z služeb, jako je služba katalogu řazení služby, služby nákupní košík, služba profilu uživatele atd.

Mikroslužby komunikaci pomocí protokolů takové jako HTTP (REST), ale také asynchronně (například pomocí protokolu AMQP) pokaždé, když je to možné, zejména při šíření aktualizací pomocí integrace událostí.

Mikroslužby jsou vyvíjeny a nasazené jako kontejnery nezávisle na mezi sebou. To znamená, že vývojový tým může být vývoj a nasazení určité mikroslužeb bez dopadu na ostatních subsystémů.

Každá mikroslužba má svou vlastní databázi, což umožňuje být zcela oddělená od jiných mikroslužeb. Pokud je to nezbytné, konzistenci mezi databází z různých mikroslužeb se opírá události integrace na úrovni aplikace (prostřednictvím sběrnice logické událostí), jako zpracované v příkazu a model dělení zodpovědnosti dotazů (CQRS). Proto musí obchodní omezení zapojte konečnou konzistenci mezi různými mikroslužbami a související databází.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: Referenční aplikace pro .NET Core a mikroslužby se nasazují pomocí kontejnerů

Abyste se mohli zaměřit na architektury a technologie místo přemýšlení o hypotetický obchodní domény, který možná nevíte, jsme vybrali dobře známé obchodní domény – konkrétně, zjednodušené aplikaci elektronického obchodování (kde e), která předkládá katalog produktů, trvá objednávek zákazníků, ověřuje inventáře a provede další podnikové funkce. Tento zdrojový kód aplikace založené na kontejnerech je k dispozici v [aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture) úložiště GitHub.

Aplikace se skládá z více subsystémů, včetně několika úložiště uživatelského rozhraní front-endů (webová aplikace a nativní mobilní aplikace), spolu s back-end mikroslužeb a kontejnerů pro všechny požadované operace na straně serveru s několika brány rozhraní API jako konsolidované vstupní body do interního mikroslužeb. Obrázek 6-1 ukazuje architekturu referenční aplikace.

![Mobilní zařízení a SPA klienti komunikují do jedné brány koncových bodů rozhraní API, které pak sdělí mikroslužeb. Tradičními webovými klienty sdělit MVC mikroslužeb, která komunikuje s mikroslužeb](./media/image1.png)

**Obrázek 6-1**. Aplikaci eShopOnContainers referenční architektuře aplikace pro vývojové prostředí

**Hostitelské prostředí**. Obrázek 6-1, se zobrazí několik kontejnerů, které jsou nasazené v rámci jednoho hostitele Dockeru. Který by tomu bylo při nasazování pomocí dockeru na jednoho hostitele Docker-compose up příkazu. Ale pokud jste pomocí orchestrátoru nebo clusteru služby container, každý kontejner může být spuštěn v jiného hostitele (uzel) a libovolný uzel může používat libovolný počet kontejnerů, jak jsme je vysvětleno výše v části architektura.

**Architektura Communication**. Aplikaci eShopOnContainers aplikace používá dva typy komunikace, v závislosti na druhu funkční akce (dotazů a aktualizace a transakce):

- Klient mikroslužeb komunikaci pomocí protokolu HTTP prostřednictvím brány rozhraní API. Používá se pro dotazy a při přijetí aktualizací nebo transakční příkazy z klientských aplikací. Přístup pomocí brány rozhraní API je podrobně popsána v předchozích částech.

- Asynchronní komunikace na základě událostí. Tato akce proběhne prostřednictvím událostí Service bus k šíření aktualizací přes mikroslužby nebo integrovat s externími aplikacemi. Události Service bus je možné implementovat pomocí jakékoli infrastruktury zasílání zpráv zprostředkovatele technologie jako RabbitMQ nebo pomocí vyšší úrovně služby (na úrovni abstrakce) autobusové, jako je Azure Service Bus, NServiceBus, MassTransit nebo Brighter.

Aplikace je nasazená jako sada mikroslužeb v podobě kontejnerů. Klientské aplikace můžou komunikovat s těchto mikroslužeb spouštěných jako kontejnery pomocí veřejné adresy URL publikována serverem brány rozhraní API.

### <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

V ukázkové aplikaci vlastní jednotlivých mikroslužeb svou vlastní databázi nebo zdroj dat, i když jsou všechny databáze SQL serveru nasadit jako jednoho kontejneru. Toto rozhodnutí o návrhu byla vytvořena pouze k tomu, aby vývojáři získat kód z Githubu, naklonovat ho a otevřete ho v sadě Visual Studio nebo Visual Studio Code. Nebo alternativně to usnadňuje kompilovat vlastní Image Dockeru pomocí rozhraní příkazového řádku .NET Core a rozhraní příkazového řádku Dockeru a pak nasaďte a spusťte je v vývojové prostředí pro Docker. V obou případech použití kontejnerů pro data zdrojů umožňuje vývojářům vytvářet a nasazovat během několika minut bez nutnosti zřizovat externí databáze nebo kterýkoli jiný zdroj dat se pevný závislostmi na infrastrukturu (cloudu nebo místně).

Ve skutečné produkční prostředí, pro zajištění vysoké dostupnosti a škálovatelnosti databáze by měla vycházet z databázových serverů v cloudu nebo místně, ale ne v kontejnerech.

Proto jednotky nasazení pro mikroslužby (a dokonce i pro databáze v této aplikaci) jsou kontejnery Docker a referenční aplikace je aplikace, která zahrnuje využití principů mikroslužeb.

### <a name="additional-resources"></a>Další zdroje

- **aplikaci eShopOnContainers úložiště GitHub. Zdrojový kód pro odkaz na aplikaci**\
    [https://aka.ms/eShopOnContainers/](https://aka.ms/eShopOnContainers/)

## <a name="benefits-of-a-microservice-based-solution"></a>Výhody řešení založených na mikroslužbách

Řešení na základě mikroslužeb tímto způsobem má mnoho výhod:

**Každá mikroslužba je poměrně málo početnému – lze snadno řídit a rozvíjet**. Konkrétně:

- Je to jednoduché vývojář, abyste mohli pochopit a rychlé zahájení práce s dobrým produktivitu.

- Kontejnery rychle se pusťte, takže vývojáři produktivnější.

- Rozhraní IDE, jako je Visual Studio můžete načíst menších projektů rychlý, což produktivitu vývojářů.

- Jednotlivých mikroslužeb můžete navržený, vyvinutý a nasadit nezávisle na jiných mikroslužeb, která poskytuje flexibilitu, protože je snazší nasazování nových verzí mikroslužeb často.

**Je možné horizontálně škálovat jednotlivé oblasti aplikace**. Například služba katalogu nebo službu nákupní košík možná muset škálovat, ale ne proces objednávání. Mikroslužby infrastruktury budou mnohem efektivněji s ohledem na prostředky používané při horizontálním navýšení kapacity, než by bylo monolitické architektury.

**Rozdělíte vývojové práce mezi několika týmy**. Každá služba může být vlastněn jeden vývojový tým. Každý tým může spravovat, vývoj, nasazení a škálování své služby nezávisle na ostatních týmů.

**Problémy jsou izolovanějším**. Pokud se vyskytl problém v jedné službě, pouze tuto službu je zpočátku vliv (Pokud chybný návrhu se nepoužije, pomocí přímých závislostí mezi mikroslužbami) a dalších služeb můžete nadále zpracovávat žádosti. Naproti tomu jedné nefunkční součásti v architektuře monolitické nasazení můžete použít dolů celého systému, zejména v případě, že zahrnuje prostředky, jako je nevrácená paměť. Kromě toho po vyřešení problému v mikroslužbě můžete nasadit jenom ovlivněných mikroslužeb bez dopadu na zbývajících částí aplikace.

**Můžete použít nejnovější technologie**. Protože můžete začít s vývojem služby nezávisle a spouštět je vedle sebe (díky kontejnerů a .NET Core), můžete začít využívat nejnovější technologie a platformy expediently místo se zablokuje a na starší zásobníku nebo architektura určená k celku aplikace.

## <a name="downsides-of-a-microservice-based-solution"></a>Nevýhody řešení založených na mikroslužbách

Řešení na základě mikroslužeb tímto způsobem má také určité nevýhody:

**Distribuované aplikace**. Distribuce aplikace zvyšuje složitost pro vývojáře, při navrhování a vytváření služeb. Například vývojáři musí implementovat objemu komunikace mezi službami pomocí protokolů, jako jsou HTTP nebo AMPQ, což zvyšuje složitost pro účely testování a zpracování výjimek. Také zvyšuje latenci v systému.

**Složitost nasazení**. Aplikace, která má desítky typy mikroslužeb a potřebuje vysokou škálovatelnost (musí se jednat o může vytvářet velký počet instancí služby a vyrovnání těchto služeb napříč mnoha hostitelích) znamená, že vysoký stupeň složitost nasazení pro správu a provoz IT. Pokud nepoužíváte infrastrukturu orientované na mikroslužby (například nástroje orchestrator a plánovač), můžete vyžadovat další složitost mnohem více činností souvisejících s vývojem než vlastní obchodní aplikace.

**Atomické transakce**. Atomické transakce mezi různými mikroslužbami obvykle nejsou možné. Obchodní požadavky nutné zapojte konečnou konzistenci mezi několika mikroslužeb.

**Zvýšit globální prostředek potřebám** (celková paměť, disky a síťové prostředky pro všemi servery nebo hostitele). V mnoha případech Pokud nahradíte monolitické aplikace přístup založený na mikroslužbách, množství počáteční globální prostředky potřebné pro novou aplikaci založených na mikroslužbách bude větší než infrastruktury potřeb původní monolitické aplikace. Je to proto vyšší stupeň členitosti a distribuované služby vyžaduje víc globálních prostředků. Zadané nízkých nákladech prostředků v rámci obecné a výhody nebudou moct horizontálně navýšit kapacitu pouze určité oblasti aplikace ve srovnání s dlouhodobých nákladů při vyvíjejí monolitické aplikace, zvýšené využití prostředků je však obvykle dobrou kompromis pro velké dlouhodobé aplikace.

**Problémy s přímou komunikaci klienta mikroslužeb**. Když je aplikace velké desítky mikroslužeb, existují problémy a omezení Pokud aplikace vyžaduje přímé komunikace klienta mikroslužeb. Jeden problém je potenciální Neshoda mezi požadavky klienta a rozhraní API podle jednotlivých mikroslužeb. V některých případech může být nutné klientská aplikace provádět mnoho samostatné požadavků na vytvoření uživatelského rozhraní, která může být neefektivní přes Internet a by to bylo nepraktické přes mobilní síť. Proto byste měli minimalizovat žádosti z klienta aplikace k back endovému systému.

Dalším problémem s přímé komunikace klienta mikroslužeb je, že některé mikroslužeb může používat protokoly, které nejsou webové skvěle. Jedna služba může používat binární protokol, zatímco jiná služba může používat zasílání zpráv protokolu AMQP. Tyto protokoly nejsou firewallem procházející a je nejvhodnější používat interně. Obvykle by měla aplikace použít protokoly, jako jsou HTTP a Websocket pro komunikaci mimo bránu firewall.

Ještě další z nevýhod tohoto přímého přístupu klienta služby je, že to je těžké Refaktorovat kontrakty těchto mikroslužeb. V čase vývojáři chtít změnit, jak systém je rozdělený do služby. Může být třeba sloučit dvě služby nebo služby rozdělit na dvě nebo více služeb. Ale pokud klienti komunikují přímo s služeb, provedení tento druh refaktoring může dojít k narušení kompatibilitu s klientské aplikace.

Jak je uvedeno v části architektura při navrhování a vytváření komplexních aplikačních založeného na mikroslužbách, můžete zvážit použití více podrobných brány rozhraní API namísto jednodušší přístup přímá komunikace klienta mikroslužeb.

**Dělení mikroslužby**. A konečně bez ohledu na to, jaký přístup je provést pro architektury mikroslužeb, dalším problémem je rozhodování o tom, jak dělit začátku do konce aplikaci do několika mikroslužeb. Jak je uvedeno v části Architektura průvodce, existuje několik technik a postupů, které můžete provést. V podstatě je potřeba identifikovat oblasti aplikace, které jsou oddělené od ostatních oblastech, které mají nízký počet pevných závislosti. V mnoha případech to je umístěno na vytváření oddílů služby případu použití. Například v naší aplikaci e, kde máme pořadí služba, která je zodpovědná za všechny obchodní logiky související s proces zpracování objednávky. Máme také katalog služeb a nákupní košík, implementovat další možnosti. V ideálním případě by každá služba má pouze malou sadu odpovědnosti. To se podobá jednotnou zodpovědnost princip (SRP) použít na třídy, která stanovuje třídy by měl mít jenom jeden důvod, proč změnit. Ale v tomto případě jde o mikroslužeb, takže obor bude větší než jedna třída. Co je nejdůležitější mikroslužby musí být zcela autonomní, komplexní, včetně odpovědnost za datovými zdroji.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externí a interní architektur a vzorů návrhu

Externí architektura je architekturu mikroslužeb sestává z více služeb, následující zásady je popsáno v části architektura tohoto průvodce. Ale v závislosti na povaze jednotlivých mikroslužeb a nezávisle na architekturu mikroslužeb vysoké úrovně zvolíte, je běžné a v některých případech žádoucí mít různé interní architektury, každý různé vzorce, podle pro různé mikroslužby. Mikroslužby dá dokonce využít různé technologie a programovacích jazyků. Obrázek 6-2 znázorňuje tuto různorodost.

![Rozdíl mezi externí architektury: mikroslužeb vzory, brány rozhraní API, odolné komunikace, publikování a odběr, atd. a interní architekturu: data driven/CRUD vzorů DDD, vkládání závislostí, více knihoven, atd.](./media/image2.png)

**Obrázek 6 – 2**. Externí a interní architektury a návrhu

Například v našich *aplikaci eShopOnContainers* jsou jednoduché mikroslužby profilu vzorku, katalog, nákupní košík a uživatele (v podstatě subsystémy CRUD). Proto své interní architektury a návrhu je jednoduché. Však může mít jiné mikroslužeb, jako je například řazení mikroslužeb, což je složitější a představuje neustále se měnící obchodní pravidla s vysokým stupněm složitosti domény. V takových případech můžete chtít implementovat rozšířené vzorů v rámci konkrétní mikroslužeb, jako jsou definované pomocí návrhu řízeného doménou (DDD) přístupy, jak si vedeme *aplikaci eShopOnContainers* řazení mikroslužby. (Probereme těchto vzorů DDD v části později, který vysvětluje provádění *aplikaci eShopOnContainers* řazení mikroslužeb.)

Dalším důvodem pro různé technologie jednotlivých mikroslužbách může být povaze jednotlivých mikroslužeb. Například může být vhodnější použít funkcionální programovací jazyk jako F\#, nebo pokud se zaměřujete na AI a strojového učení domén namísto více objektově orientované programovací jazyky jako C i jazyka, jako je R\#.

Dolní řádek je, že každá mikroslužba může mít jinou interní architekturu podle vzorů návrhů. Ne všechny mikroslužby by měla být implementována pomocí pokročilé vzorů DDD, protože, který by být over-pass-the inženýrství je. Podobně komplexní mikroslužby s neustále se měnící obchodní logiku, neměli byste je implementovat jako komponentu CRUD, nebo můžete skončit s kódem nízké kvality.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Novém světě: více vzorech architektury a mikroslužby polyglot

Existuje mnoho vzorech architektury, které jsou používané softwarové architekty a vývojáře. Toto jsou některé (kombinace stylů architektury a vzory architektury):

- Jednoduché CRUD, oddělených, jednou vrstvou.

- [Tradiční N vrstvami](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Řízené doménou návrhu N vrstvami](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Vyčistit architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jak je použít s [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [Příkazů a dotazů Responsibility Segregation](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektury řízené událostmi](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Můžete také vytvářet mikroslužby s mnoha technologie a jazyky, jako je rozhraní Web API ASP.NET Core, NancyFx, základní funkce SignalR technologie ASP.NET (dostupné s .NET Core 2), F\#, Node.js, Python, Java, C++, go a další.

Důležité je, že žádná konkrétní architektura vzor nebo styl ani žádné konkrétní technologie, je nejvhodnější pro všechny situace. Obrázek 6 – 3 znázorňuje některé přístupy a technologie (i když není v libovolném pořadí), které se daly použít v různých mikroslužeb.

![Více z možných architektonických a polyglotické mikroslužeb prostředky lze kombinovat a odpovídají jazyků a technologií podle potřeb jednotlivých mikroslužeb a ještě je hovoří spolu.](./media/image3.png)

**Obrázek 6 – 3**. Více schématu architektury a world polyglot mikroslužeb

Jak ukazuje obrázek 6 – 3 v aplikacích skládají z mnoha mikroslužeb (ohraničených kontextech v terminologii návrhem řízeným doménou nebo jednoduše "subsystémy" jako autonomní mikroslužeb), jednotlivých mikroslužeb může implementovat jiným způsobem. Každý máte vzoru pro jinou architekturu a používáte různé jazyky a databází v závislosti na povaze aplikace, obchodní požadavky a priority. V některých případech může být podobné mikroslužby. Ale to není obvykle případ, protože každý subsystém hranic kontextu a požadavky se obvykle liší.

Například pro jednoduchou aplikaci údržby CRUD, nemusí mít smysl návrh a implementace vzorů DDD. Ale pro základní doménu nebo podstatu podnikání, možná budete muset použít rozšířené vzory řešit firemní složitosti s neustále se měnící obchodní pravidla.

Zejména v případě, že budete pracovat s velké aplikace vytváří více subsystémů, nesmí použít jeden architekturou nejvyšší úrovně na základě vzoru architektura samostatného. Například modelu CQRS neměla používat jako architekturou nejvyšší úrovně pro aplikaci jako celek, ale může být užitečná pro konkrétní sadu služeb.

Neexistuje žádné stříbrné odrážek a vzor správné architektury pro každý daný případ. Nemůže obsahovat "jeden vzor architektury vládne všem." V závislosti na priorit jednotlivých mikroslužeb musíte zvolit jiný přístup pro každou, jak je popsáno v následujících částech.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](data-driven-crud-microservice.md)