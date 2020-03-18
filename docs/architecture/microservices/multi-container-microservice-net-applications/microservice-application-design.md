---
title: Návrh aplikace orientované na mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s výhodami a nevýhodami aplikace orientované na mikroslužby, takže můžete přijmout informované rozhodnutí.
ms.date: 10/02/2018
ms.openlocfilehash: 619440c02c1a82e05adb2cec9ddba933cd3e0a65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76965760"
---
# <a name="design-a-microservice-oriented-application"></a>Návrh aplikace orientované na mikroslužby

Tato část se zaměřuje na vývoj hypotetické podnikové aplikace na straně serveru.

## <a name="application-specifications"></a>Specifikace aplikace

Hypotetická aplikace zpracovává požadavky spuštěním obchodní logiky, přístupem k databázím a vrácením odpovědí HTML, JSON nebo XML. Řekneme, že aplikace musí podporovat celou řadu klientů, včetně desktopových prohlížečů se systémem Jednostránkové aplikace (SPA), tradičních webových aplikací, mobilních webových aplikací a nativních mobilních aplikací. Aplikace může také vystavit rozhraní API pro třetí strany využívat. Měl by být také schopen integrovat své mikroslužby nebo externí aplikace asynchronně, takže tento přístup pomůže odolnost mikroslužeb v případě částečné chyby.

Aplikace se bude skládat z těchto typů komponent:

- Komponenty prezentace. Ty jsou zodpovědné za zpracování uživatelského uživatelského zařízení a využívání vzdálených služeb.

- Doména nebo obchodní logika. Toto je logika domény aplikace.

- Logika přístupu k databázi. To se skládá z komponent přístupu k datům odpovědných za přístup k databázím (SQL nebo NoSQL).

- Logika integrace aplikací. To zahrnuje kanál pro zasílání zpráv, hlavně na základě zprostředkovatelů zpráv.

Aplikace bude vyžadovat vysokou škálovatelnost a zároveň umožní, aby její vertikální subsystémy škálovat autonomně, protože některé subsystémy budou vyžadovat větší škálovatelnost než jiné.

Aplikace musí být možné nasadit ve více prostředích infrastruktury (více veřejných cloudů a místních) a v ideálním případě by měla být cross-platformní, možnost přechodu z Linuxu na Windows (nebo naopak) snadno.

## <a name="development-team-context"></a>Kontext vývojového týmu

Předpokládáme také následující informace o procesu vývoje aplikace:

- Máte několik vývojářských týmů zaměřených na různé obchodní oblasti aplikace.

- Noví členové týmu musí být produktivní rychle a aplikace musí být snadno pochopitelný a upravit.

- Aplikace bude mít dlouhodobý vývoj a neustále se měnící obchodní pravidla.

- Potřebujete dobrou dlouhodobou udržovatelnost, což znamená, že budete mít flexibilitu při implementaci nových změn v budoucnu a zároveň budete moci aktualizovat více subsystémů s minimálním dopadem na ostatní subsystémy.

- Chcete procvičit průběžnou integraci a průběžné nasazování aplikace.

- Chcete využít nově vznikající technologie (architektury, programovací jazyky atd.) při vývoji aplikace. Nechcete provést úplnou migraci aplikace při přechodu na nové technologie, protože to by mělo za následek vysoké náklady a ovlivnit předvídatelnost a stabilitu aplikace.

## <a name="choosing-an-architecture"></a>Výběr architektury

Jaká by měla být architektura nasazení aplikace? Specifikace pro aplikaci, spolu s kontextem vývoje, důrazně naznačují, že byste měli architekt aplikace rozkladem do autonomních subsystémů ve formě spolupracujících mikroslužeb a kontejnerů, kde mikroslužby je kontejner.

V tomto přístupu každá služba (kontejner) implementuje sadu soudržné a úzce související funkce. Aplikace se může například skládat ze služeb, jako je služba katalogu, objednávková služba, služba košíku, služba profilu uživatele atd.

Mikroslužby komunikují pomocí protokolů, jako je HTTP (REST), ale také asynchronně (například pomocí AMQP) kdykoli je to možné, zejména při šíření aktualizací s událostmi integrace.

Mikroslužby jsou vyvíjeny a nasazovány jako kontejnery nezávisle na sobě. To znamená, že vývojový tým může vyvíjet a nasazovat určitou mikroslužbu bez dopadu na jiné subsystémy.

Každá mikroslužba má svou vlastní databázi, což umožňuje, aby byla plně oddělena od jiných mikroslužeb. V případě potřeby je dosaženo konzistence mezi databázemi z různých mikroslužeb pomocí událostí integrace na úrovni aplikace (prostřednictvím sběrnice logických událostí), jak je zpracováno v oddělení odpovědnosti příkazu a dotazu (CQRS). Z tohoto důvodu obchodní omezení musí zahrnovat konečné konzistence mezi více mikroslužeb a souvisejícídatabáze.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: Referenční aplikace pro .NET Core a mikroslužby nasazené pomocí kontejnerů

Abyste se mohli soustředit na architekturu a technologie namísto přemýšlení o hypotetické obchodní doméně, kterou možná neznáte, vybrali jsme známou obchodní doménu – konkrétně zjednodušenou aplikaci elektronického obchodu (e-shop), která představuje katalog produktů, přijímá objednávky od zákazníků, ověřuje zásoby a plní další obchodní funkce. Tento zdrojový kód aplikace založený na kontejneru je k dispozici v úložišti [githubu eShopOnContainers.](https://aka.ms/MicroservicesArchitecture)

Aplikace se skládá z více subsystémů, včetně několika front-endů uživatelského rozhraní úložiště (webová aplikace a nativní mobilní aplikace), spolu s back-endovými mikroslužbami a kontejnery pro všechny požadované operace na straně serveru s několika bránami rozhraní API konsolidovaných vstupních bodů do interních mikroslužeb. Obrázek 6-1 znázorňuje architekturu referenční aplikace.

![Diagram klientských aplikací používajících eShopOnContainers v jednom hostiteli Dockeru.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Obrázek 6-1**. Referenční architektura aplikace eShopOnContainers pro vývojové prostředí

Výše uvedený diagram ukazuje, že mobilní a SPA klienti komunikovat do jednoho koncového bodu brány rozhraní API, které pak komunikovat mikroslužeb. Tradiční weboví klienti komunikují s mikroslužbou MVC, která komunikuje s mikroslužbami prostřednictvím brány rozhraní API.

**Hostingové prostředí**. Na obrázku 6-1 uvidíte několik kontejnerů nasazených v rámci jednoho hostitele Dockeru. To by byl případ při nasazování do jednoho hostitele Dockeru s příkazem docker-compose up. Pokud však používáte orchestrator nebo cluster kontejnerů, každý kontejner může být spuštěn v jiném hostiteli (uzlu) a libovolný uzel může být spuštěn libovolný počet kontejnerů, jak jsme vysvětlili dříve v části architektura.

**Komunikační architektura**. Aplikace eShopOnContainers používá dva typy komunikace, v závislosti na druhu funkční akce (dotazy versus aktualizace a transakce):

- Http komunikace klient-mikroslužby prostřednictvím brány rozhraní API. Používá se pro dotazy a při přijímání příkazů aktualizace nebo transakce z klientských aplikací. Přístup pomocí brány rozhraní API je podrobně vysvětlen v dalších částech.

- Asynchronní komunikace založená na událostech. K tomu dochází prostřednictvím sběrnice událostí k šíření aktualizací napříč mikroslužbami nebo k integraci s externími aplikacemi. Sběrnice událostí může být implementována s jakoukoli technologií infrastruktury zprostředkovatele zasílání zpráv, jako je RabbitMQ, nebo pomocí služeb na vyšší úrovni (úroveň abstrakce), jako je Azure Service Bus, NServiceBus, MassTransit nebo Brighter.

Aplikace se nasadí jako sada mikroslužeb ve formě kontejnerů. Klientské aplikace mohou komunikovat s těmito mikroslužbami spuštěnými jako kontejnery prostřednictvím veřejných adres URL publikovaných branami rozhraní API.

### <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

V ukázkové aplikaci každá mikroslužba vlastní vlastní databázi nebo zdroj dat, i když všechny databáze SQL Serveru jsou nasazeny jako jeden kontejner. Toto rozhodnutí o návrhu bylo provedeno pouze proto, aby vývojář mohl vývojáři snadno získat kód z GitHubu, naklonovat jej a otevřít jej v sadě Visual Studio nebo Visual Studio Code. Nebo alternativně usnadňuje kompilaci vlastních ih dockeru pomocí rozhraní CLI jádra .NET a rozhraní cli Dockeru a pak je nasadit a spustit ve vývojovém prostředí Dockeru. V obou tak či onak umožňuje vývojářům vytvářet a nasazovat během několika minut bez nutnosti zřizování externí databáze nebo jiného zdroje dat s pevnými závislostmi na infrastruktuře (cloud nebo místní).

V reálném produkčním prostředí pro vysokou dostupnost a škálovatelnost by databáze měly být založeny na databázových serverech v cloudu nebo v místním prostředí, ale ne v kontejnerech.

Proto jednotky nasazení pro mikroslužeb (a dokonce i pro databáze v této aplikaci) jsou kontejnery Dockeru a referenční aplikace je aplikace s více kontejnery, která zahrnuje zásady mikroslužeb.

### <a name="additional-resources"></a>Další zdroje

- **eShopOnContainers GitHub úložiště. Zdrojový kód referenční aplikace** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Výhody řešení založeného na mikroslužbách

Řešení založené na mikroslužbách, jako je tento, má mnoho výhod:

**Každá mikroslužba je relativně malá – snadno se spravuje a vyvíjí**. Konkrétně:

- Pro vývojáře je snadné pochopit a začít rychle s dobrou produktivitou.

- Kontejnery se spouštějí rychle, což dělá vývojáře produktivnějšími.

- Ide jako Visual Studio můžete načíst menší projekty rychle, takže vývojáři produktivní.

- Každá mikroslužba může být navržena, vyvinuta a nasazena nezávisle na jiných mikroslužeb, které poskytuje flexibilitu, protože je snazší nasadit nové verze mikroslužeb často.

**Je možné škálovat jednotlivé oblasti aplikace**. Například služby katalogu nebo služby košíku může být nutné škálovat, ale ne proces objednávání. Infrastruktura mikroslužeb bude mnohem efektivnější s ohledem na prostředky používané při horizontálním navýšení kapacity, než by byla monolitická architektura.

**Vývojovou práci můžete rozdělit mezi více týmů**. Každá služba může být vlastněna jedním vývojovým týmem. Každý tým může spravovat, vyvíjet, nasazovat a škálovat své služby nezávisle na ostatních týmech.

**Problémy jsou izolovanější**. Pokud je problém v jedné službě, pouze tato služba je zpočátku ovlivněna (s výjimkou případů, kdy je použit nesprávný návrh, s přímými závislostmi mezi mikroslužbami) a další služby mohou nadále zpracovávat požadavky. Naproti tomu jedna nefunkční součást v monolitické architektuře nasazení může snížit celý systém, zejména pokud zahrnuje prostředky, jako je například nevracení paměti. Navíc při vyřešení problému v mikroslužbě, můžete nasadit pouze ovlivněné mikroslužby bez dopadu na zbytek aplikace.

**Můžete použít nejnovější technologie**. Vzhledem k tomu, že můžete začít vyvíjet služby nezávisle a spouštět je vedle sebe (díky kontejnerům a .NET Core), můžete začít používat nejnovější technologie a architektury účelně namísto toho, abyste se zasekli na starším zásobníku nebo rámci pro celek Aplikace.

## <a name="downsides-of-a-microservice-based-solution"></a>Nevýhody řešení založeného na mikroslužbách

Řešení založené na mikroslužbách, jako je tento, má také některé nevýhody:

**Distribuovaná aplikace**. Distribuce aplikace zvyšuje složitost pro vývojáře při navrhování a vytváření služeb. Vývojáři musí například implementovat mezistránkovou komunikaci pomocí protokolů, jako je HTTP nebo AMPQ, což zvyšuje složitost pro testování a zpracování výjimek. Také přidává latenci do systému.

**Složitost nasazení**. Aplikace, která má desítky typů mikroslužeb a potřebuje vysokou škálovatelnost (musí být schopna vytvořit mnoho instancí na službu a vyvážit tyto služby mezi mnoha hostiteli) znamená vysoký stupeň složitosti nasazení pro operace it a správu. Pokud nepoužíváte infrastrukturu orientovanou na mikroslužby (například orchestrátor a plánovač), může tato další složitost vyžadovat mnohem více úsilí o vývoj než samotná obchodní aplikace.

**Atomické transakce**. Atomické transakce mezi více mikroslužeb obvykle nejsou možné. Obchodní požadavky musí přijmout konečnou konzistenci mezi více mikroslužeb.

**Zvýšené potřeby globálních prostředků** (celková paměť, jednotky a síťové prostředky pro všechny servery nebo hostitele). V mnoha případech při nahrazení monolitické aplikace s přístupem mikroslužeb, množství počáteční globální prostředky potřebné pro nové aplikace založené na mikroslužbách bude větší než potřeby infrastruktury původní monolitické aplikace. Důvodem je, že vyšší stupeň rozlišovací schopnost a distribuované služby vyžaduje více globálních prostředků. Avšak vzhledem k nízkým nákladům na zdroje obecně a výhodám plynoucí z toho, že je možné škálovat pouze určité oblasti aplikace ve srovnání s dlouhodobými náklady při vývoji monolitických aplikací, je zvýšené využívání zdrojů obvykle dobrým kompromisem pro velké, dlouhodobé aplikace.

**Problémy s přímou komunikaci mezi klientem a mikroslužbou**. Když je aplikace velká, s desítkami mikroslužeb, existují problémy a omezení, pokud aplikace vyžaduje přímou komunikaci mezi klientem a mikroslužbami. Jedním z problémů je potenciální nesoulad mezi potřebami klienta a api vystavené každou z mikroslužeb. V některých případech může být nutné, aby klientská aplikace provést mnoho samostatných požadavků na vytvoření uj. Proto by měly být minimalizovány požadavky z klientské aplikace do systému back-end.

Dalším problémem s přímou komunikaci klienta mikroslužeb je, že některé mikroslužby může používat protokoly, které nejsou vhodné pro web. Jedna služba může používat binární protokol, zatímco jiná služba může používat zasílání zpráv AMQP. Tyto protokoly nejsou vhodné pro bránu firewall a jsou nejlépe používány interně. Aplikace by obvykle měla používat protokoly, jako je http a websockets pro komunikaci mimo bránu firewall.

Další nevýhodou tohoto přímého přístupu klienta ke službě je, že ztěžuje refaktorování smluv pro tyto mikroslužby. V průběhu času vývojáři chtít změnit způsob, jakým je systém rozdělen do služeb. Mohou například sloučit dvě služby nebo rozdělit službu na dvě nebo více služeb. Pokud však klienti komunikují přímo se službami, provádění tohoto druhu refaktoringu může přerušit kompatibilitu s klientskými aplikacemi.

Jak je uvedeno v části architektura při navrhování a vytváření komplexní aplikace založené na mikroslužeb, můžete zvážit použití více jemně odstupňované brány rozhraní API namísto jednodušší přístup přímé komunikace klienta mikroslužeb.

**Rozdělení mikroslužeb**. Nakonec bez ohledu na to, jaký přístup budete mít pro architekturu mikroslužeb, další výzvou je rozhodování o rozdělení aplikace end-to-end do více mikroslužeb. Jak je uvedeno v architektuře části průvodce, existuje několik technik a přístupů, které můžete vzít. V podstatě je třeba identifikovat oblasti aplikace, které jsou odděleny od ostatních oblastí a které mají nízký počet pevných závislostí. V mnoha případech je to zarovnáno se službami dělení podle případu použití. Například v naší aplikaci e-shopu máme objednávkovou službu, která je zodpovědná za veškerou obchodní logiku související s procesem objednávky. Máme také katalogslužby a košíku služby, které implementují další funkce. V ideálním případě by každá služba měla mít pouze malou sadu povinností. To je podobné principu jediné odpovědnosti (SRP) použít pro třídy, který uvádí, že třída by měla mít pouze jeden důvod ke změně. Ale v tomto případě se jedná o mikroslužeb, takže obor bude větší než jedna třída. Nejvíce ze všeho musí být mikroslužba zcela autonomní, od konce do konce, včetně odpovědnosti za vlastní zdroje dat.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externí versus interní architektura a návrhové vzory

Externí architektura je architektura mikroslužeb složená z více služeb podle zásad popsaných v části architektura této příručky. V závislosti na povaze každé mikroslužby a nezávisle na architektuře mikroslužeb na vysoké úrovni, kterou zvolíte, je však běžné a někdy vhodné mít různé vnitřní architektury, z nichž každá je založena na různých vzorech, pro různé mikroslužeb. Mikroslužby mohou dokonce používat různé technologie a programovací jazyky. Obrázek 6-2 tuto rozmanitost ilustruje.

![Diagram porovnání externí a vnitřní vzory architektury.](./media/microservice-application-design/external-versus-internal-architecture.png)

**Obrázek 6-2**. Externí versus interní architektura a design

Například v naší ukázce *eShopOnContainers* jsou mikroslužby katalogu, košíku a uživatelského profilu jednoduché (v podstatě subsystémy CRUD). Proto je jejich vnitřní architektura a design přímočará. Můžete však mít jiné mikroslužby, jako je například řazení mikroslužeb, což je složitější a představuje neustále se měnící obchodní pravidla s vysokým stupněm složitosti domény. V případech, jako jsou tyto, můžete chtít implementovat pokročilejší vzory v rámci konkrétní mikroslužby, jako jsou ty definované s přístupem návrhu řízeného doménou (DDD), jak to děláme v *eShopOnContainers* objednávání mikroslužeb. (Tyto vzory DDD prověříme v části, která vysvětluje implementaci *eShopOnContainers* objednávajícího mikroslužbu.)

Dalším důvodem pro jinou technologii na mikroslužbu může být povaha každé mikroslužby. Například může být lepší použít funkční programovací\#jazyk, jako je F , nebo dokonce jazyk, jako je R, pokud cílíte na ai a oblasti strojového učení, namísto více objektově orientovaného programovacího jazyka, jako je C\#.

Pointa je, že každá mikroslužba může mít jinou vnitřní architekturu založenou na různých návrhových vzorcích. Ne všechny mikroslužby by měly být implementovány pomocí rozšířené vzory DDD, protože to by bylo over-engineering je. Podobně složité mikroslužby s neustále se měnící obchodní logikou by neměly být implementovány jako komponenty CRUD nebo můžete skončit s kódem nízké kvality.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Nový svět: více architektonických vzorů a polyglot mikroslužeb

Existuje mnoho architektonických vzorů používaných softwarovými architekty a vývojáři. Následuje několik (míchání stylů architektury a vzorů architektury):

- Jednoduché CRUD, jednovrstvé, jednovrstvé.

- [Tradiční N-vrstvené](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Návrh řízený doménou N vrstvami](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Čistá architektura](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (jak se používá s [eShopOnWeb)](https://aka.ms/WebAppArchitecture)

- [Oddělení odpovědnosti příkazů a dotazů](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Architektura řízená událostmi](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Můžete také vytvářet mikroslužby s mnoha technologiemi a jazyky, jako jsou ASP.NET core web OVÁ\#ROZHRANÍ API, NancyFx, ASP.NET Core SignalR (k dispozici s .NET Core 2), F , Node.js, Python, Java, C++, GoLang a další.

Důležité je, že žádný konkrétní architektura vzor nebo styl, ani žádné konkrétní technologie, je správné pro všechny situace. Obrázek 6-3 ukazuje některé přístupy a technologie (i když ne v určitém pořadí), které by mohly být použity v různých mikroslužeb.

![Diagram znázorňující 12 komplexnímikroslužeb v polyglot světové architektury.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Obrázek 6-3**. Více-architektonické vzory a polyglot mikroslužeb světě

Vícearchitektonický vzor a polyglot mikroslužeb znamená, že můžete kombinovat jazyky a technologie s potřebami každé mikroslužby a stále je mluvit mezi sebou. Jak je znázorněno na obrázku 6-3, v aplikacích složených z mnoha mikroslužeb (ohraničené kontexty v terminologii návrhu řízené doménou nebo jednoduše "subsystémy" jako autonomní mikroslužby), můžete implementovat každou mikroslužbu jiným způsobem. Každý může mít jiný vzor architektury a používat různé jazyky a databáze v závislosti na povaze aplikace, obchodní požadavky a priority. V některých případech mikroslužeb může být podobné. Ale to není obvykle případ, protože každý subsystém je kontext hranice a požadavky jsou obvykle odlišné.

Například pro jednoduchou aplikaci údržby CRUD nemusí mít smysl navrhovat a implementovat vzory DDD. Ale pro vaši hlavní doménu nebo hlavní podnikání možná budete muset použít pokročilejší vzory, abyste se vypořádali se složitostí podnikání s neustále se měnícími obchodními pravidly.

Zejména při řešení velkých aplikací složených z více subsystémů, neměli byste použít jednu architekturu nejvyšší úrovně založenou na vzoru jedné architektury. Například CQRS by neměla být použita jako architektura nejvyšší úrovně pro celou aplikaci, ale může být užitečné pro konkrétní sadu služeb.

Neexistuje žádná stříbrná kulka nebo správný vzor architektury pro každý daný případ. Nemůžete mít "jeden vzor architektury vládnout jim všem." V závislosti na prioritách každé mikroslužby je nutné zvolit jiný přístup pro každou z nich, jak je vysvětleno v následujících částech.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](data-driven-crud-microservice.md)
