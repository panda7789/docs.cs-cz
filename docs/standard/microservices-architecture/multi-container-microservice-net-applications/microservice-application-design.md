---
title: Návrh aplikace mikroslužbu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Návrh aplikace mikroslužbu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: a5107e979dc2101380cf848dc574033caf750fd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="designing-a-microservice-oriented-application"></a>Návrh aplikace mikroslužbu

Tato část se zaměřuje na vývoj hypotetický enterprise serverové aplikace.

## <a name="application-specifications"></a>Specifikace aplikace

Hypotetický aplikace zpracovává požadavky na provádění obchodní logiky, přístup k databázím a pak vrácení odpovědi HTML, XML nebo JSON. Říkáme bude, že aplikace musí podporovat různých klientů, včetně plochy prohlížečů spuštěných jednostránkové aplikace (SPA), tradiční webové aplikace, mobilní webové aplikace a nativní mobilní aplikace. Aplikace může také zveřejňují rozhraní API pro třetí strany využívat. Je také nutné spojit jeho mikroslužeb nebo externí aplikace asynchronně, tak, aby přístup pomůže odolnost mikroslužeb v případě selhání částečné.

Aplikace se skládá z těchto typů součástí:

-   Prezentace komponenty. Tyto jsou zodpovědní za zpracování uživatelského rozhraní a využívání služby Vzdálená.

-   Domény nebo obchodní logiku. Toto je logiku domény aplikace.

-   Logika přístup k databázi. Tento postup se skládá součástí data access components zodpovědná za přístup k databázím (SQL nebo NoSQL).

-   Integrace logiku aplikace. To zahrnuje zasílání zpráv kanál, především podle zprostředkovatelé zprávy.

Aplikace bude vyžadovat vysokou škálovatelnost, zatímco jeho svislé subsystémy pro rozšíření Škálováním samostatně, protože určité subsystémy bude vyžadovat další škálovatelnost než jiné.

Aplikace musí být schopný nasadit v prostředí s více infrastruktury (více veřejné cloudy a místní) a v ideálním případě by měla být napříč platformami, moci snadno přesunout z Linux do systému Windows (nebo naopak).

## <a name="development-team-context"></a>Vývoj team kontextu

Předpokládáme také následující o procesu vývoje pro aplikaci:

-   Máte několik týmů vývojářů zaměřovat na odvětví různé obchodní aplikace.

-   Nové členy týmu musí být produktivní rychle a aplikace musí být snadno pochopit a upravit.

-   Aplikace bude mít dlouhodobé vývoj a proměnlivých obchodní pravidla.

-   Je nutné dobrý dlouhodobé udržovatelnosti, což znamená mít flexibility při implementaci v budoucnu nové změny při bude možné aktualizovat více subsystémy s minimální dopad na jiné podsystémy.

-   Chcete postupem průběžnou integraci a průběžné nasazování aplikace.

-   Při použití vznikajícími chcete využít výhod technologií vznikajícími (rozhraní, programovací jazyky atd.). Nechcete, aby úplné migrace aplikace při přesunu na nové technologie, protože, bude mít za následek vysoké náklady a ovlivnit předvídatelnost a stabilitu aplikace.

## <a name="choosing-an-architecture"></a>Výběr architekturu

Co by měl být architektura nasazení aplikace? Specifikace pro aplikaci, společně s vývoj kontextu, důrazně doporučujeme, aby měli architektury aplikace podle decomposing do autonomního subsystémy ve formě spolupráce mikroslužeb a kontejnerů, kde mikroslužbu je kontejner.

V tomto přístupu každou službu (kontejner) implementuje sadu získá na ucelenosti a úzce související funkce. Aplikace může například obsahovat služeb, jako je služba katalogu řazení služby, služby košík, služba profilů uživatelů atd.

Mikroslužeb komunikaci pomocí protokolů takové jako HTTP (REST), ale také asynchronně (například pomocí protokolu AMQP) kdykoli je to možné, zejména při šíření aktualizací s událostmi integrace.

Mikroslužeb se vyvíjí a nasadit jako kontejnery nezávisle na sobě. To znamená, že může být vývojový tým vývoj a nasazení určité mikroslužbu bez dopadu na ostatní subsystémy.

Každý mikroslužbu má svou vlastní databázi, díky kterému jej být plně odpojené od jiných mikroslužeb. Pokud je to nezbytné, konzistenci mezi databází z různých mikroslužeb se opírá události integrace na úrovni aplikací (prostřednictvím sběrnice logické událostí), protože zpracování v příkazu a dotaz odpovědnost oddělení (CQRS). Z tohoto důvodu, musí omezení obchodní zapojení konzistence typu případné mezi více mikroslužeb a související databází.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: referenční aplikace pro .NET Core a mikroslužeb nasadit pomocí kontejnery

Tak, aby se mohli zaměřit na architektuře a technologie namísto přemýšlení o doméně hypothetic firmy, která možná nevíte, jsme vybrali domény dobře známé obchodní – konkrétně, aplikace zjednodušené elektronického obchodování (e obchod), která uvede katalog produkty, trvá objednávek zákazníků, ověřuje inventáře a provede další podnikovým funkcím. Tato aplikace založené na kontejneru zdrojový kód je k dispozici v [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) úložiště GitHub.

Aplikace se skládá z několika subsystémy, včetně několika úložiště uživatelského rozhraní front-end (webová aplikace a nativní mobilní aplikace), spolu s back-end mikroslužeb a kontejnery pro všechny požadované operace na straně serveru. Obrázek 8-1 ukazuje architekturu odkaz aplikace.

![](./media/image1.png)

**Obrázek 8-1**. EShopOnContainers odkazovat na aplikaci, zobrazující přímou komunikaci klienta mikroslužbu a sběrnice událostí

**Hostitelské prostředí**. Obrázek 8-1 zobrazí několik kontejnerů nasazuje v rámci jednoho Docker hostitele. Který by tomu bylo při nasazování na jednoho hostitele pomocí docker Docker-tvoří až příkaz. Pokud jste však pomocí orchestrator nebo kontejneru clusteru, každý kontejner může být spuštěna v jiného hostitele (uzel), a libovolný uzel může používat libovolný počet kontejnerů, jak jsme dříve popsané v části architektura.

**Architektura komunikace**. Aplikace eShopOnContainers používá dva typy komunikace, v závislosti na druhu funkční akce (dotazy a aktualizace a transakce):

-   Přímé komunikaci klienta mikroslužby. Používá se pro dotazy a při přijetí aktualizací nebo transakční příkazy z klientské aplikace.

-   Asynchronní komunikaci na základě událostí. K tomu dochází přes sběrnici událostí k šíření aktualizací přes mikroslužeb nebo k integraci s externími aplikacemi. Každá infrastruktury zasílání zpráv zprostředkovatele technologie jako RabbitMQ nebo pomocí vyšší úrovně služby sběrnicích jako Azure Service Bus, NServiceBus, MassTransit nebo Brighter se dá implementovat sběrnici událostí.

Aplikace je nasazená jako sada mikroslužeb ve formě kontejnerů. Klientské aplikace může komunikovat s těchto kontejnerech, stejně jako komunikaci mezi mikroslužeb. Jak je uvedeno, tato počáteční architektura používá přímou komunikaci klienta mikroslužbu architekturu, která znamená, že klientská aplikace můžete provádět požadavky na každé mikroslužeb přímo. Každý mikroslužbu má veřejný koncový bod jako https://servicename.applicationname.companyname. V případě potřeby jednotlivých mikroslužbu můžete použít jiný port TCP. V produkčním prostředí, která umožní mapování adresy URL mikroslužeb se službou Vyrovnávání zatížení, který rozděluje požadavky na k dispozici mikroslužbu instance.

**Důležité upozornění na vs Brána rozhraní API. Přímé komunikaci v eShopOnContainers.** Jak je popsáno v části architektura tohoto průvodce, architektura přímou komunikaci klienta mikroslužbu může mít nevýhody, pokud vytváříte velké a složité aplikace založené na mikroslužby. Ale může být dostatečně vhodný pro malý aplikaci, například v eShopOnContainers aplikace, kde je cílem a zaměřit se na jednodušší úvodní spuštění aplikace založené na kontejner Docker a nebyla chceme vytvořit jednou monolitický bránou rozhraní API, která může mít vliv mikroslužeb vývoj nezávislé.

Ale pokud chcete navrhnout rozsáhlé aplikace na základě mikroslužbu s desítek mikroslužeb, důrazně doporučujeme zvážit vzoru Brána rozhraní API jsme popsané v části architektura.
Toto rozhodnutí architektury může rozdělili, jakmile přemýšlíte o produkční prostředí aplikace a speciálně provedené průčelí pro vzdálené klienty. S více bran vlastní rozhraní API v závislosti na klientské aplikace formuláře factor můžou poskytovat výhody ohledně různých datových agregace na klientskou aplikaci plus můžete skrýt interní mikroslužeb nebo rozhraní API pro klientské aplikace a autorizaci v této jedné vrstvě. 

Ale a jak je uvedeno mějte na paměti, proti velké a monolitický brány rozhraní API, která může ukončit vaše mikroslužeb vývoj nezávislé.

### <a name="data-sovereignty-per-microservice"></a>Data suverenity za mikroslužbu

V ukázkové aplikaci každý mikroslužbu vlastní svou vlastní databázi nebo zdroj dat a každou databázi, nebo zdroj dat je nasazená jako jiný kontejner. Tomuto rozhodnutí o návrhu došlo jenom kvůli usnadňují Vývojář získáte kód z Githubu, naklonujte a otevřete jej v sadě Visual Studio nebo Visual Studio Code. Nebo můžete taky usnadňuje pro kompilaci vlastních imagí Dockeru pomocí rozhraní .NET Core rozhraní příkazového řádku a rozhraní příkazového řádku Dockeru a pak nasadit a spustit v prostředí pro vývoj Docker. V obou případech pomocí kontejnery pro datové zdroje umožňuje vývojářům vytvářet a nasazovat v řádu minut bez nutnosti ke zřízení externí databáze nebo jiného zdroje dat pomocí pevných závislosti na infrastruktuře (cloudové nebo místní).

V skutečné produkční prostředí pro vysokou dostupnost a škálovatelnost databáze by měla být založena na serverech databáze v cloudu nebo místně, ale ne v kontejnerech.

Proto jednotky nasazení pro mikroslužeb (a to i pro databáze v této aplikaci) jsou kontejnery Docker a referenční aplikace je více kontejneru aplikace, která zahrnuje zásady mikroslužeb.

### <a name="additional-resources"></a>Další zdroje

-   **eShopOnContainers úložiště GitHub. Zdrojový kód je referenční aplikací**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Výhody řešení na základě mikroslužbu

Mikroslužbu na základě řešení takto má mnoho výhod:

**Každý mikroslužbu je poměrně malý – snadnou správu a momentální**. Konkrétně:

-   Je snadné pro vývojáře k pochopení a rychle začít s funkčním produktivitu.

-   Kontejnery spustit rychlé, takže vývojáři produktivnější.

-   Rozhraní IDE, jako Visual Studio můžete načíst menší projekty rychlé, což vývojářům produktivitu.

-   Každý mikroslužbu můžete určený, vyvinuté a nasadit nezávisle na jiných mikroslužeb, která poskytuje flexibility, protože je snazší nasazování nových verzí mikroslužeb často.

**Je možné škálování jednotlivých oblastí aplikace**. Například služba katalogu nebo službu košík potřebovat k možné škálovat na více systémů, ale není proces řazení. Mikroslužeb infrastruktury budou mnohem efektivnější s ohledem na prostředky využívané při zmenšování měřítka, než by bylo monolitický architektura.

**Rozdělte vývoji mezi více týmů**. Každá služba může být vlastněn jeden vývojový tým. Každý tým může spravovat, vývoj, zavádět a škálovat své služby nezávisle na zbytek týmy.

**Problémy s více izolují**. Pokud nastane problém v jedné službě, nejdřív ovlivní pouze služby (s výjimkou při chybě návrhu je použití přímé závislosti mezi mikroslužeb) a další služby můžete i nadále zpracovávat požadavky. Naproti tomu jedna součást chybně fungující v architektuře monolitický nasazení může způsobit zastavení celého systému, zejména v případě, že se týká prostředky, například nevrácenou pamětí. Kromě toho po vyřešení problému v mikroslužbu můžete nasadit jenom ovlivněných mikroslužbu bez vlivu na zbytek aplikace.

**Můžete použít nejnovější technologie**. Protože můžete začít vyvíjet služby nezávisle a jejich spuštění vedle sebe (díky kontejnerů a .NET Core), můžete začít používat nejnovější technologie a architektury expediently místo se zablokuje na starší zásobníku nebo framework pro celé aplikace.

## <a name="downsides-of-a-microservice-based-solution"></a>Downsides na základě mikroslužbu řešení

Mikroslužbu na základě řešení takto má také některé nevýhody:

**Distribuované aplikace**. Distribuce aplikace přidá složitost pro vývojáře, při navrhování a vytváření služby. Například vývojáři musí implementovat přesahující jednotlivé služby komunikaci pomocí protokolů HTTP nebo AMPQ, který přidá složitost pro testování a výjimek. Přidá také latence do systému.

**Nasazení složitost**. Aplikace, která má desítek mikroslužeb typy a potřebuje vysokou škálovatelnost (musí se jednat o schopná vytvořit mnoho instancí na služby a vyrovnávat tyto služby ve mnoho hostitelů) znamená vysoký stupeň složitost nasazení pro IT oddělení a správu. Pokud nepoužíváte orientované mikroslužbu infrastruktura (třeba orchestrator a scheduler), může vyžadovat tuto další složitosti podstatně více úsilí vývoj než vlastní obchodní aplikace.

**Jednotlivé transakce**. Jednotlivé transakce mezi více mikroslužeb obvykle nejsou možné. Obchodní požadavky mít zapojení konzistence typu případné mezi více mikroslužeb.

**Vyšší globální prostředek potřebám** (celková paměť, jednotky a síťové prostředky pro všechny servery nebo hostitelů). V mnoha případech při nahrazení monolitický aplikace s přístupem mikroslužeb množství globální prostředky potřebné pro novou aplikaci na základě mikroslužbu bude větší než infrastruktury potřebám původní monolitický aplikace. Je to proto, že na vyšší úrovni členitosti a distribuované služby vyžaduje více globální prostředky. Však zadána nízké náklady na prostředky v obecné vlastnosti a výhodou schopnost škálovat pouze určité oblasti aplikace ve srovnání s dlouhodobých nákladů při vyvíjející se monolitický aplikace vyšší využití prostředků je obvykle dobrou kompromis pro velké dlouhodobé aplikace.

**Problémy s komunikací přímé client‑to‑microservice**. Když je aplikace velký, s desítek mikroslužeb, existují problémy a omezení Pokud aplikace vyžaduje přímé komunikaci klienta mikroslužby. Jedním z problémů je potenciální neshodu mezi potřebám klienta a rozhraní API vystavená každou mikroslužeb. V některých případech klientská aplikace možná muset udělat mnoho samostatné žádostí o tvoří uživatelské rozhraní, která může být neefektivní přes Internet a by bylo nepraktické přes mobilní síť. Proto by měl být minimální žádosti z klienta aplikace k back-end systému.

Jiný problém s přímé komunikaci klienta mikroslužbu je, že některé mikroslužeb může používat protokoly, které nejsou webové popisný. Jedna služba může použít binární protokol, zatímco použít jiné služby zasílání zpráv protokolu AMQP. Tyto protokoly nejsou firewall‑friendly a nejlépe interní použití. Aplikace by měl obvykle použít protokoly, například HTTP a WebSockets pro komunikaci mimo bránu firewall.

Ještě Další nevýhodou s tímto přístupem přímé client‑to‑service je, že ho ztěžuje Refaktorovat kontrakty pro tyto mikroslužeb. V čase vývojáři chtít změnit, jak systém rozdělena do služby. Může například sloučení dvě služby nebo služby rozdělit na dvě nebo více služeb. Ale pokud klienti komunikují přímo s služby, provádění tento druh refaktoring může dojít k narušení kompatibilitu s klientské aplikace.

Jak je uvedeno v části architektura, při navrhování a vytváření složitých aplikací podle mikroslužeb, zvažte použití více bran podrobných API místo jednodušší způsob komunikace přímé client‑to‑microservice.

**Dělení mikroslužeb**. Nakonec bez ohledu na to, jaký přístup je provést v architektuře mikroslužbu, je dalším problémem rozhodování o oddílu aplikace začátku do konce do více mikroslužeb. Jak je uvedeno v části Architektura průvodce, je několik technik a přístupy, které můžete provést. V podstatě musíte určit oblasti aplikace, které jsou odpojené od ostatních oblastech a které mají nízký počet pevných závislosti. V mnoha případech to je zarovnán k vytváření oddílů služby případem použití. Například v naší aplikaci e obchod máme řazení služby, která je odpovědná za všechny obchodní logiku související s procesem pořadí. Máme také služba katalogu a košík službou, která implementovat další možnosti. Každé služby v ideálním případě by měli pouze malou sadu odpovědnosti. Toto je podobná jeden odpovědnost princip (SRP) u třídy, které stavy třídu musí mít pouze jeden důvod změnit. Ale v takovém případě jde o mikroslužeb, takže bude větší než jedna třída oboru. Nejvíce všech musí být zcela autonomního, koncová, včetně odpovědnost za vlastní zdroje dat mikroslužby.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externí versus interní architektury a návrhu vzory

Externí architektura je architektury mikroslužby sestává z několika služeb, následující zásady popsané v části architektura tohoto průvodce. Ale v závislosti na povaze každý mikroslužbu a nezávisle na Architektura vysoké úrovně mikroslužbu zvolíte, je běžné a někdy doporučuje mít různé interní architektury, každý podle různé vzorce pro různé mikroslužeb. Mikroslužeb můžete použít i různé technologie a programovací jazyky. Obrázek 8-2 je znázorněný tyto rozdíly.

![](./media/image2.png)

**Obrázek 8-2**. Externí versus interní architektury a návrhu

Například v našem *eShopOnContainers* mikroslužeb profil ukázkové, katalog, košík a uživatele jsou jednoduché (v podstatě, subsystémy CRUD). Proto jejich interní architektury a návrhu je jednoduchá. Však může mít jiné mikroslužeb, jako je například řazení mikroslužbu, který je složitější a představuje proměnlivých obchodní pravidla s vysokým zabezpečením složitost domény. V takových případech můžete chtít implementace pokročilejší vzorů v rámci konkrétní mikroslužbu, jako jsou definována s přístupy k návrhu řízené domény (DDD), jako jsme to děláte *eShopOnContainers* řazení mikroslužby. (Jsme zkontrolujete tyto vzory DDD v později oddíl, který vysvětluje implementace *eShopOnContainers* řazení mikroslužby.)

Dalším důvodem pro různé technologie za mikroslužbu může být povaha každý mikroslužby. Například může být vhodnější použít funkční programovací jazyk jako F\#, nebo dokonce jazyk jako R, pokud cílíte AI a machine learningu domén, místo více objektově orientované programovací jazyky jako C\#.

Dolní řádek je, že každý mikroslužbu může mít jiný interní architekturu na základě různých způsobů. Ne všechny mikroslužeb by měla být implementována pomocí pokročilé vzory DDD, vzhledem k tomu, který by být přepsání technici je. Podobně jako komponenty CRUD neměli byste je implementovat komplexní mikroslužeb se někdy změna obchodní logikou nebo můžou skončit s kódem nízké kvality.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nové world: více architektury vzory a polyglot mikroslužeb

Existuje mnoho architektury vzory používané softwarové architekty a vývojáře. Toto jsou některé (kombinování architektura styly a architektura vzory):

-   Jednoduché CRUD, oddělených, jednou vrstvou.

-   [Tradiční N vrstvami](https://msdn.microsoft.com/library/ee658109.aspx#Layers).

-   [Domény řízené návrhu vrstvený N](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Vyčištění architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jako použít s [eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [Příkaz a dotazování odpovědnost oddělení](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Událostmi řízené architektura](https://en.wikipedia.org/wiki/Event-driven_architecture) (Automatizace elektronického designu).

Můžete také vytvořit mikroslužeb s mnoha technologie a jazyky, jako je ASP.NET Core webovým rozhraním API, NancyFx, ASP.NET SignalR Core (dostupné s .NET Core 2), F\#, Node.js, Python, Java, C++, GoLang a další.

Důležité je, že je správný pro všechny případy žádné konkrétní architektura vzor nebo styl, ani žádné konkrétní technologie. Obrázek 8-3 ukazuje některé přístupy a technologie (i když není v libovolném pořadí), který může být používá v jiné mikroslužeb.

![](./media/image3.png)

**Obrázek 8-3**. Více architektury vzory a polyglot mikroslužeb world

Jak ukazuje obrázek 8-3, v aplikacích skládá z mnoha mikroslužeb (ohraničenou kontextů v terminologii funguje na základě domény nebo jednoduše "subsystémy" jako autonomní mikroslužeb), může implementovat každý mikroslužbu jiným způsobem. Každý může mít různé architektura vzor a používat různé jazyky a databáze v závislosti na povaze aplikace, obchodní požadavky a priority. V některých případech může být podobně jako mikroslužeb. Ale které obvykle tak není, protože kontext hranic a požadavky na každý subsystém se obvykle liší.

Například pro jednoduchou aplikaci údržby CRUD, nemusí mít smysl navrhovat a implementovat DDD vzory. Ale pro základní doménu nebo obchodní jádra, možná budete muset použít pokročilejší vzory pro řešení business složitý a proměnlivých obchodní pravidla.

Zejména v případě, že budete pracovat s velké aplikace skládá více dílčí systémy, nesmí použít jeden nejvyšší úrovně architektura na základě vzoru pro jeden architektura. Například CQRS neměly používat jako nejvyšší úrovně architektura pro celou aplikaci, ale mohou být užitečné pro konkrétní skupinu služeb.

Neexistuje žádné stříbrným odrážek a pravém architektura vzor pro každý daný případ. Nemůže mít "jeden architektura vzor pravidlo je všechny." V závislosti na priorit každý mikroslužbu musíte zvolit jiný přístup pro každou, jak je popsáno v následujících částech.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (data řízené crud-microservice.md)
