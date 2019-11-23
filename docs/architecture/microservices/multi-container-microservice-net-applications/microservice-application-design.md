---
title: Návrh aplikace orientované na mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s výhodami a downsides aplikací orientovaných na mikroslužby, abyste mohli vzít v úvahu své rozhodnutí.
ms.date: 10/02/2018
ms.openlocfilehash: a783d582f39d25be0123f410553a54af970a4f67
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739536"
---
# <a name="designing-a-microservice-oriented-application"></a>Návrh aplikace orientované na mikroslužby

Tato část se zaměřuje na vývoj hypotetické podnikové aplikace na straně serveru.

## <a name="application-specifications"></a>Specifikace aplikace

Hypotetická aplikace zpracovává požadavky pomocí obchodní logiky, přístupu k databázím a vrácení odpovědí HTML, JSON nebo XML. Řekněme, že aplikace musí podporovat celou řadu klientů, včetně stolních prohlížečů spouštějících jednostránkové aplikace (jednostránkové), tradičních webových aplikací, mobilních webových aplikací a nativních mobilních aplikací. Aplikace může také vystavit rozhraní API, které bude využívat třetí strany. Mělo by být taky možné asynchronně integrovat mikroslužby nebo externí aplikace, aby tento přístup v případě částečných selhání pomohly odolnost mikroslužeb.

Aplikace bude obsahovat tyto typy komponent:

- Prezentační komponenty. Zodpovídá za zpracování uživatelského rozhraní a využívání vzdálených služeb.

- Doména nebo obchodní logika. Toto je logika domény aplikace.

- Logika přístupu k databázi. To se skládá z komponent pro přístup k datům zodpovědných za přístup k databázím (SQL nebo NoSQL).

- Logic Integration Application. To zahrnuje kanál pro zasílání zpráv, hlavně založený na zprostředkovatelích zpráv.

Aplikace bude vyžadovat vysokou škálovatelnost a zároveň umožní jejím vertikálním systémům horizontální horizontální navýšení kapacity, protože některé subsystémy budou vyžadovat větší škálovatelnost než jiné.

Aplikace musí být schopna být nasazena v několika prostředích infrastruktury (více veřejných cloudů a místních) a v ideálním případě by měla být schopná přejít ze systému Linux do systému Windows (nebo naopak) snadno.

## <a name="development-team-context"></a>Kontext vývojového týmu

V rámci procesu vývoje aplikace také předpokládáme:

- Máte několik vývojových týmů, které se zaměřují na různé obchodní oblasti aplikace.

- Noví členové týmu musí rychle zvýšit produktivitu a aplikaci je třeba snadno pochopit a upravit.

- Tato aplikace bude mít dlouhodobý vývoj a neustále se měnící obchodní pravidla.

- Je potřeba mít dobrou dlouhodobou udržovatelnost, což znamená flexibilitu při implementaci nových změn v budoucnu a zároveň umožnit aktualizaci více subsystémů s minimálním dopadem na jiné subsystémy.

- Chcete se zachováním průběžné integrace a průběžného nasazování aplikace.

- Chcete využívat nově vznikající technologie (architektury, programovací jazyky atd.) při vývoji aplikace. Při přechodu na nové technologie nechcete provádět úplné migrace aplikace, protože by to vedlo k vysokým nákladům a dopadům na předvídatelnost a stabilitu aplikace.

## <a name="choosing-an-architecture"></a>Výběr architektury

Co má architektura nasazení aplikace být? Specifikace pro aplikaci, společně s vývojovým kontextem, důrazně navrhují, že byste měli architektovat aplikaci tím, že ji vyřadíte do autonomních subsystémů ve formě spolupráce mikroslužeb a kontejnerů, kde mikroslužba je kontejner.

V tomto přístupu každá služba (kontejner) implementuje sadu soudržných a úzkých souvisejících funkcí. Například aplikace může obsahovat služby, jako je služba katalogu, služba řazení, služba koše, Služba profilů uživatelů atd.

Mikroslužby komunikují pomocí protokolů, jako je HTTP (REST), ale také asynchronně (například pomocí AMQP), pokud je to možné, zejména při rozšiřování aktualizací s integračními událostmi.

Mikroslužby se vyvíjí a nasazují jako kontejnery nezávisle na sobě. To znamená, že vývojový tým může vyvíjet a nasazovat určitou mikroslužbu, aniž by to ovlivnilo jiné subsystémy.

Každá mikroslužba má svou vlastní databázi a umožňuje ji úplně oddělit od ostatních mikroslužeb. V případě potřeby se konzistence mezi databázemi z různých mikroslužeb dosahuje pomocí integračních událostí na úrovni aplikace (prostřednictvím logické sběrnice událostí), jak je zpracovávána v CQRS (Command and Query Responsibility Segregation) (CQRS). Z toho důvodu obchodní omezení musí zamezit konečnou konzistenci mezi několika mikroslužbami a souvisejícími databázemi.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: Referenční aplikace pro .NET Core a mikroslužby nasazené pomocí kontejnerů

Takže se můžete soustředit na architekturu a technologie a nemusíte se zajímat o hypotetickou obchodní doménu, kterou možná neznáte, zvolili jsme známou podnikovou doménu – konkrétně, zjednodušenou aplikaci elektronického obchodování (e-shop), která prezentuje katalog. produktů, provádí objednávky od zákazníků, ověřuje inventář a provádí další obchodní funkce. Tento zdrojový kód aplikace založený na kontejneru je k dispozici v úložišti GitHub [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) .

Aplikace se skládá z několika subsystémů, včetně několika front-endu uživatelského rozhraní úložiště (webová aplikace a nativní mobilní aplikace), spolu s back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru s několika branami rozhraní API, jako je konsolidované vstupní body do interních mikroslužeb. Obrázek 6-1 ukazuje architekturu referenční aplikace.

![Diagram klientských aplikací využívajících eShopOnContainers v jednom hostiteli Docker.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Obrázek 6-1**. Architektura referenčních aplikací eShopOnContainers pro vývojové prostředí

Na výše uvedeném diagramu vidíte, že mobilní a SPA klienti komunikují s koncovými body brány rozhraní API, které pak komunikují s mikroslužbami. Tradiční webové klienty komunikují s mikroslužbou MVC, která komunikuje s mikroslužbami prostřednictvím brány rozhraní API.

**Hostitelské prostředí**. Na obrázku 6-1 vidíte několik kontejnerů nasazených v rámci jednoho hostitele Docker. To by znamenalo, že při nasazování do jednoho hostitele Docker s příkazem Docker-sestavit. Pokud ale používáte cluster Orchestrator nebo kontejnerů, každý kontejner může běžet na jiném hostiteli (uzlu) a kterýkoli uzel může spustit libovolný počet kontejnerů, jak jsme už zjistili v části architektura.

**Komunikační architektura**. Aplikace eShopOnContainers používá dva typy komunikace v závislosti na druhu funkční akce (dotazy oproti aktualizacím a transakcích):

- Komunikace mezi klientem a mikroslužbou HTTP prostřednictvím bran rozhraní API. Používá se pro dotazy a při přijímání příkazů Update nebo Transaction z klientských aplikací. Přístup pomocí bran rozhraní API je podrobně vysvětlen v dalších částech.

- Asynchronní komunikace založená na událostech. K tomu dochází prostřednictvím sběrnice událostí za účelem šíření aktualizací mezi mikroslužbami nebo pro integraci s externími aplikacemi. Sběrnice událostí se dá implementovat s jakoukoli technologií infrastruktury zasílání zpráv, jako je RabbitMQ, nebo pomocí sběrnice služby vyšší úrovně (abstrakce), jako je Azure Service Bus, NServiceBus, MassTransit nebo jasnější.

Aplikace je nasazena jako sada mikroslužeb ve formě kontejnerů. Klientské aplikace můžou komunikovat s těmito mikroslužbami, které běží jako kontejnery, prostřednictvím veřejných adres URL publikovaných pomocí bran rozhraní API.

### <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

V ukázkové aplikaci každá mikroslužba vlastní svoji vlastní databázi nebo zdroj dat, i když jsou všechny SQL Server databáze nasazené jako jeden kontejner. Toto rozhodnutí o návrhu bylo provedeno pouze proto, aby mohl vývojář snadno získat kód z GitHubu, klonovat ho a otevřít v aplikaci Visual Studio nebo Visual Studio Code. Případně můžete snadno zkompilovat vlastní image Docker pomocí .NET Core CLI a Docker CLI a pak je nasadit a spustit ve vývojovém prostředí Docker. Buď pomocí kontejnerů pro zdroje dat umožníte vývojářům vytvářet a nasazovat během několika minut, aniž byste museli zřídit externí databázi nebo jiný zdroj dat s pevnými závislostmi na infrastruktuře (Cloud nebo místní).

Pro zajištění vysoké dostupnosti a škálovatelnosti v reálném produkčním prostředí by databáze měly být založené na databázových serverech v cloudu nebo místně, ale ne v kontejnerech.

Jednotky nasazení pro mikroslužby (a dokonce i pro databáze v této aplikaci) jsou proto kontejnery Docker a referenční aplikace je aplikace s více kontejnery, která zahrnuje Principy mikroslužeb.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **úložiště GitHub eShopOnContainers Zdrojový kód pro referenční aplikaci** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Výhody řešení založeného na mikroslužbách

Řešení založené na mikroslužbách má mnoho výhod:

**Každá mikroslužba je poměrně malá – Snadná správa a vývoj**. Určen

- Vývojář může snadno pochopit a rychle začít pracovat s dobrou produktivitou.

- Kontejnery se rychle spouštějí, což vývojářům přináší větší produktivitu.

- Integrované vývojové prostředí (IDE), jako je Visual Studio, může rychle načíst menší projekty a vývojářům produktivitu.

- Každá mikroslužba se dá navrhovat, vyvíjet a nasazovat nezávisle na ostatních mikroslužbách, které poskytují flexibilitu, protože je snazší nasazovat nové verze mikroslužeb často.

**Je možné škálovat jednotlivé oblasti aplikace**. Například může být potřeba škálovat službu katalogu nebo službu koše, ale ne proces objednávání. Infrastruktura mikroslužeb bude mnohem efektivnější, pokud jde o prostředky používané při škálování, než je monolitické architektura.

**Vývojovou práci můžete rozdělit mezi několik týmů**. Každou službu může vlastnit jeden vývojový tým. Každý tým může spravovat, vyvíjet, nasazovat a škálovat služby nezávisle na ostatních týmech.

**Problémy jsou lépe izolované**. V případě, že dojde k potížím v jedné službě, bude to mít na začátku dopad jenom na tuto službu (s výjimkou případů, kdy se používá nesprávný návrh s přímými závislostmi mezi mikroslužbami) a další služby můžou dál zpracovávat požadavky. Naproti tomu jedna součást selhání v architektuře nasazení monolitické může využít celý systém, zejména v případě, že zahrnuje prostředky, jako je nevrácená paměť. Kromě toho, pokud dojde k vyřešení problému mikroslužby, můžete nasadit jenom ovlivněnou mikroslužbu, aniž by to mělo vliv na zbytek aplikace.

**Můžete využít nejnovější technologie**. Vzhledem k tomu, že můžete začít vyvíjet služby nezávisle na sobě a spouštět je vedle sebe (díky kontejnerům a .NET Core), můžete začít využívat nejnovější technologie a architektury, a nemusíte je zablokovat na starší verzi zásobníku nebo architektury pro celou aplikaci. použití.

## <a name="downsides-of-a-microservice-based-solution"></a>Downsides řešení založeného na mikroslužbách

Řešení založené na mikroslužbách, podobně jako toto, má také nějaké nevýhody:

**Distribuovaná aplikace**. Distribuce aplikace při navrhování a sestavování služeb přidá složitost pro vývojáře. Vývojáři například musí implementovat komunikaci mezi službami pomocí protokolů jako HTTP nebo AMPQ, které zvyšují složitost pro testování a zpracování výjimek. Zároveň přidá latenci systému.

**Složitost nasazení**. Aplikace, která má desítky typů mikroslužeb a potřebuje vysokou škálovatelnost (musí být schopná vytvořit mnoho instancí na službu a vyrovnávat tyto služby napříč mnoha hostiteli) znamená vysoký stupeň složitosti nasazení pro IT operace a správu. Pokud nepoužíváte infrastrukturu orientovanou na mikroslužby (například Orchestrator a Scheduler), může další složitost vyžadovat mnohem více vývojových úsilí než samotná obchodní aplikace.

**Atomické transakce**. Atomické transakce mezi několika mikroslužbami většinou nejsou možné. Obchodní požadavky musí využívat konečnou konzistenci mezi několika mikroslužbami.

**Zvýšení globálních potřeb prostředků** (celková paměť, jednotky a síťové prostředky pro všechny servery nebo hostitele). V mnoha případech platí, že při nahrazení aplikace monolitické pomocí přístupu k mikroslužbám bude velikost počátečních globálních prostředků vyžadovaných novou aplikací založenou na mikroslužbách větší než v případě potřeby infrastruktury původní aplikace monolitické. Důvodem je to, že vyšší stupeň členitosti a distribuovaných služeb vyžaduje více globálních prostředků. Vzhledem k nízkým nákladům na prostředky a výhodou možností horizontálního navýšení kapacity aplikace v porovnání s dlouhodobými náklady při vývoji monolitické aplikací je ale zvýšené využívání prostředků obvykle dobré pro velké, dlouhodobé aplikace.

**Problémy s přímou komunikací mezi klientem a mikroslužbou**. Pokud je aplikace velká, s desítkami mikroslužeb, existují výzvy a omezení, pokud aplikace vyžaduje přímou komunikaci mezi klientem a mikroslužbou. Jedním z problémů je potenciální Neshoda mezi požadavky klienta a rozhraní API vystavených jednotlivými mikroslužbami. V některých případech může klientská aplikace potřebovat udělat mnoho samostatných požadavků na vytvoření uživatelského rozhraní, které může být neefektivní po internetu a bude nepraktické v mobilní síti. Proto by měly být minimalizovány požadavky z klientské aplikace do back-endového systému.

Dalším problémem s přímou komunikací mezi klientem a mikroslužbou je, že některé mikroslužby můžou používat protokoly, které nejsou srozumitelné pro web. Jedna služba může používat binární protokol, zatímco jiná služba může používat zasílání zpráv AMQP. Tyto protokoly nejsou srozumitelné pro bránu firewall a jsou nejvhodnější pro interní používání. Aplikace by obvykle měla pro komunikaci mimo bránu firewall používat protokoly, jako jsou HTTP a WebSockets.

Ještě další nevýhodou s tímto přímým přístupem mezi klientem a službou je, že je obtížné Refaktorovat smlouvy pro tyto mikroslužby. Vývojáři mohou v průběhu času chtít změnit rozdělení systému na služby. Například mohou sloučit dvě služby nebo rozdělit službu do dvou nebo více služeb. Pokud však klienti komunikují přímo se službami, může tento druh refaktoringu přerušit kompatibilitu s klientskými aplikacemi.

Jak je uvedeno v části architektura, při navrhování a sestavování komplexní aplikace založené na mikroslužbách můžete zvážit použití několika jemně odstupňovaných bran rozhraní API namísto jednoduššího přímého přímého komunikačního přístupu mezi klientem a mikroslužbám.

**Dělení mikroslužeb**. A konečně bez ohledu na to, jaký je přístup k architektuře mikroslužeb, další otázkou se rozhodují, jak rozdělit koncovou aplikaci do více mikroslužeb. Jak je uvedeno v části architektura příručky, existuje několik postupů a přístupů, které můžete provést. V podstatě je potřeba určit oblasti aplikace, které jsou oddělené od ostatních oblastí a mají nízký počet pevných závislostí. V mnoha případech je tato volba zarovnaná na dělení služeb pomocí případu použití. Například v naší aplikaci elektronického nákupu máme službu řazení, která zodpovídá za veškerou obchodní logiku související s procesem objednávky. Máme také službu katalogu a službu koše, která implementuje další funkce. V ideálním případě by měla každá služba obsahovat jenom malou sadu odpovědností. Jedná se o podobnou zásadu jednotného přinesení na třídy, která uvádí, že třída by měla mít pouze jeden důvod ke změně. V tomto případě se ale jedná o mikroslužby, takže rozsah bude větší než jedna třída. Ve většině případů musí být mikroslužba zcela autonomní a koncová, včetně zodpovědnosti za vlastní zdroje dat.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externí versus interní architektura a vzory návrhu

Externí architektura je architektura mikroslužeb, která se skládá z několika služeb, podle principů popsaných v části architektura této příručky. V závislosti na povaze jednotlivých mikroslužeb a nezávisle na architektuře mikroslužeb na vysoké úrovni se ale jedná o běžné a občas vhodné mít různé interní architektury, z nichž každá vychází z různých vzorů pro různé mikroslužeb. Mikroslužby můžou dokonce používat různé technologie a programovací jazyky. Obrázek 6-2 znázorňuje tuto různorodost.

![Diagram porovnání vzorů externích a interních architektur](./media/microservice-application-design/external-versus-internal-architecture.png)

**Obrázek 6-2**. Externí versus interní architektura a návrh

Například v naší ukázce *eShopOnContainers* jsou mikroslužby katalogu, košíku a profilů uživatelů jednoduché (v podstatě i subsystémy CRUD). Proto jsou jejich interní architektura a návrh jednoduché. Můžete ale mít jiné mikroslužby, jako je objednávání mikroslužby, což je složitější a představuje neustále se měnící obchodní pravidla s vysokou mírou složitosti domény. V takových případech můžete chtít implementovat pokročilejší vzory v rámci určité mikroslužby, jako jsou ty, které jsou definované pomocí přístupů k návrhu řízenému doménou (DDD), jak provádíme v *eShopOnContainers* řazení mikroslužeb. (Tyto DDD vzory prozkoumáme později v části, které popisují implementaci mikroslužby pro řazení *eShopOnContainers* .)

Dalším důvodem pro jinou technologii na mikroslužbu může být povaha každé mikroslužby. Může být například lepší používat funkční programovací jazyk, například F\#, nebo i jazyk, jako je R, pokud cílíte na domény AI a strojového učení, nikoli na objektově orientovaný programovací jazyk, jako je C\#.

Dolním řádkem je, že každá mikroslužba může mít jinou interní architekturu založenou na různých vzorech návrhu. Ne všechny mikroslužby by se měly implementovat pomocí pokročilých vzorů DDD, protože by byly předálené. Podobně komplexní mikroslužby s neustále se měnící obchodní logikou by neměly být implementovány jako komponenty CRUD nebo můžete ukončit kód s nízkou kvalitou.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nový svět: více architektonických vzorů a mikroslužeb Polyglot

Software architekti a vývojáři používá mnoho vzorů architektury. Níže jsou uvedené některé (kombinace stylů architektury a schémat architektury):

- Jednoduchá CRUD, jedna vrstva, jedna vrstva.

- [Tradiční N-vrstvený](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Návrh založený na doméně N-vrstvý](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Čistá architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jako při použití s [eShopOnWeb](https://aka.ms/WebAppArchitecture))

- [CQRS (Command and Query Responsibility segregation)](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektura řízená událostmi](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Můžete také vytvářet mikroslužby s mnoha technologiemi a jazyky, jako jsou ASP.NET Core Web API, NancyFx, ASP.NET Core Signal (k dispozici v .NET Core 2), F\#, Node. js, Python, Java, C++, GoLang a další.

Důležitým bodem je, že žádný konkrétní model ani styl architektury ani žádná konkrétní technologie nejsou pro všechny situace správné. Obrázek 6-3 ukazuje některé přístupy a technologie (i když nejsou v žádné konkrétní objednávce), které by mohly být použity v různých mikroslužbách.

![Diagram znázorňující 12 komplexní mikroslužby v architektuře Polyglot World.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Obrázek 6-3**. Modely s více architekturami a Polyglot mikroslužby na světě

Multi-architektonické vzory a Polyglot mikroslužby znamená, že můžete kombinovat a používat jazyky a technologie pro potřeby jednotlivých mikroslužeb a pořád je vzájemně komunikovat. Jak je znázorněno na obrázku 6-3, můžete v aplikacích složených z mnoha mikroslužeb (ohraničených kontextů v terminologii návrhu založené na doméně nebo jednoduše "subsystémy" jako autonomní mikroslužby) implementovat jednotlivé mikroslužby jiným způsobem. Každá z nich může mít jiný model architektury a používat různé jazyky a databáze v závislosti na povaze aplikace, obchodních požadavcích a prioritách. V některých případech mohou být mikroslužby podobné. Ale to není obvykle případ, protože hranice kontextu a požadavky každého subsystému jsou obvykle odlišné.

Například pro jednoduchou aplikaci údržby CRUD nemusí mít smysl navrhovat a implementovat vzory DDD. Ale pro vaši základní doménu nebo základní firmu možná budete muset použít pokročilejší vzory pro řešení složitých obchodních pravidel s neustále se měnícími obchodními pravidly.

Zejména při práci s velkými aplikacemi, které se skládají z více podsystémů, byste neměli používat jednu architekturu nejvyšší úrovně založenou na jednom vzoru architektury. Například CQRS by neměl být použit jako architektura nejvyšší úrovně pro celou aplikaci, ale může být užitečný pro konkrétní sadu služeb.

U každého daného případu není k dispozici žádný stříbrný nebo správný vzor architektury. Nemůžete mít žádný vzor architektury, který by je měl pokaždé. V závislosti na prioritách každé mikroslužby musíte pro každý z nich zvolit jiný přístup, jak je vysvětleno v následujících oddílech.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](data-driven-crud-microservice.md)
