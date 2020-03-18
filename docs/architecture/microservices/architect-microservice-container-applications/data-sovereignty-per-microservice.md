---
title: Svrchovanost dat v jednotlivých mikroslužbách
description: Suverenita dat na mikroslužbu je jedním z klíčových bodů mikroslužeb. Každá mikroslužba musí být jediným vlastníkem své databáze a sdílet ji s žádným jiným. Samozřejmě všechny instance mikroslužeb připojit ke stejné databázi s vysokou dostupností.
ms.date: 09/20/2018
ms.openlocfilehash: f606d6314f38bf3e2c163871af432806dddc7446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73191920"
---
# <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

Důležitým pravidlem pro architekturu mikroslužeb je, že každá mikroslužba musí vlastnit data a logiku své domény. Stejně jako úplná aplikace vlastní svou logiku a data, tak musí každá mikroslužba vlastnit svou logiku a data v rámci autonomního životního cyklu, s nezávislým nasazením na mikroslužbu.

To znamená, že koncepční model domény se bude lišit mezi subsystémy nebo mikroslužeb. Zvažte podnikové aplikace, kde aplikace pro řízení vztahů se zákazníky (CRM), subsystémy transakčních nákupů a subsystémy zákaznické podpory vyžadují atributy a data jedinečných entit zákazníka a kde každý z nich používá jiný Ohraničený kontext (BC).

Tento princip je podobný v [návrhu řízeném doménou (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), kde každý [ohraničený kontext](https://martinfowler.com/bliki/BoundedContext.html) nebo autonomní subsystém nebo služba musí vlastnit svůj model domény (data plus logiku a chování). Každý kontext ohraničený DDD koreluje s jednou obchodní mikroslužbou (jednou nebo několika službami). Tento bod o ohraničeném kontextu vzor je rozbalen v další části.

Na druhou stranu tradiční (monolitická data) přístup používaný v mnoha aplikacích je mít jednu centralizovanou databázi nebo jen několik databází. Toto je často normalizovaná databáze SQL, která se používá pro celou aplikaci a všechny její vnitřní subsystémy, jak je znázorněno na obrázku 4-7.

![Diagram znázorňující dva přístupy databáze.](./media/data-sovereignty-per-microservice/data-sovereignty-comparison.png)

**Obrázek 4-7**. Porovnání suverenity dat: monolitická databáze versus mikroslužby

V tradičním přístupu je jedna databáze sdílená napříč všemi službami, obvykle v vrstvené architektuře. V přístupu mikroslužeb každá mikroslužba vlastní svůj model/data. Centralizovaný databázový přístup zpočátku vypadá jednodušeji a zdá se, že umožňuje opakované použití entit v různých subsystémech, aby bylo vše konzistentní. Ale realita je, že skončíte s obrovskými tabulkami, které slouží mnoha různým subsystémům a které zahrnují atributy a sloupce, které nejsou ve většině případů potřeba. Je to jako snažit se použít stejnou fyzickou mapu pro pěší turistiku na krátké stezce, celodenní výlet autem a učení geografie.

Monolitická aplikace s obvykle jedinou relační databáze má dvě důležité výhody: [ACID transakce](https://en.wikipedia.org/wiki/ACID) a jazyk SQL, jak pracovat napříč všemi tabulkami a data související s vaší aplikací. Tento přístup poskytuje způsob, jak snadno napsat dotaz, který kombinuje data z více tabulek.

Přístup k datům se však stane mnohem složitější při přechodu na architekturu mikroslužeb. I při použití acid transakcí v rámci mikroslužeb nebo ohraničené kontextu, je důležité vzít v úvahu, že data vlastněná každou mikroslužbu je privátní pro tuto mikroslužbu a by měly být přístupné pouze synchronně prostřednictvím koncových bodů rozhraní API (REST, gRPC, SOAP, atd.) nebo asynchronně prostřednictvím zasílání zpráv (AMQP nebo podobné).

Zapouzdření dat zajišťuje, že mikroslužby jsou volně spojeny a může vyvíjet nezávisle na sobě. Pokud více služeb byly přístup ke stejným datům, aktualizace schématu by vyžadovalo koordinované aktualizace všech služeb. To by přerušilo autonomii životního cyklu mikroslužeb. Ale distribuované datové struktury znamenají, že nelze provést jednu transakci ACID napříč mikroslužbami. To zase znamená, že je nutné použít konečnou konzistenci, když obchodní proces zahrnuje více mikroslužeb. To je mnohem těžší implementovat než jednoduché sql spojení, protože nelze vytvořit omezení integrity nebo použít distribuované transakce mezi samostatnými databázemi, jak vysvětlíme později. Podobně mnoho dalších funkcí relační databáze nejsou k dispozici ve více mikroslužeb.

Chystáte ještě dále, různé mikroslužby často používají různé *druhy* databází. Moderní aplikace ukládají a zpracovávají různé druhy dat a relační databáze není vždy tou nejlepší volbou. V některých případech použití může mít databáze NoSQL, jako je Azure CosmosDB nebo MongoDB, pohodlnější datový model a nabízet lepší výkon a škálovatelnost než databáze SQL, jako je SQL Server nebo Azure SQL Database. V ostatních případech relační databáze je stále nejlepší přístup. Proto aplikace založené na mikroslužbách často používají směs sql a nosql databází, což se někdy nazývá přístup [polyglot perzistence.](https://martinfowler.com/bliki/PolyglotPersistence.html)

Rozdělená, polyglot trvalá architektura pro ukládání dat má mnoho výhod. Patří mezi ně volně vázané služby a lepší výkon, škálovatelnost, náklady a možnosti správy. Může však zavést některé problémy správy distribuovaných dat, jak je vysvětleno v "[Identifikace hranic modelu domény](identify-microservice-domain-model-boundaries.md)" dále v této kapitole.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Vztah mezi mikroslužeb a ohraničený kontext vzor

Koncept mikroslužeb je odvozen od [vzoru ohraničeného kontextu (BC)](https://martinfowler.com/bliki/BoundedContext.html) v [návrhu řízeném doménou (DDD).](https://en.wikipedia.org/wiki/Domain-driven_design) DDD se zabývá velkými modely jejich rozdělením do více př. Každý BC musí mít svůj vlastní model a databázi; stejně tak každá mikroslužba vlastní související data. Kromě toho má každý BC obvykle svůj [vlastní všudypřítomný jazyk,](https://martinfowler.com/bliki/UbiquitousLanguage.html) který pomáhá komunikaci mezi vývojáři softwaru a odborníky na domény.

Tyto termíny (hlavně entity domény) v všudypřítomném jazyce mohou mít různé názvy v různých ohraničených kontextech, i když různé entity domény sdílejí stejnou identitu (to znamená jedinečné ID, které se používá ke čtení entity z úložiště). Například v kontextu ohraničený profil uživatele může entita domény uživatele sdílet identitu s entitou domény kupujícího v objednacím ohraničeném kontextu.

Mikroslužba je tedy jako ohraničený kontext, ale také určuje, že je distribuované služby. Je vytvořen jako samostatný proces pro každý ohraničený kontext a musí používat distribuované protokoly uvedené dříve, jako je HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Ohraničený kontext vzor, ale neurčuje, zda ohraničený kontext je distribuovaná služba nebo pokud je to prostě logická hranice (například obecný subsystém) v rámci aplikace monolitického nasazení.

Je důležité zdůraznit, že definování služby pro každý ohraničený kontext je vhodné začít. Ale nemusíte omezovat svůj návrh na to. Někdy je nutné navrhnout ohraničený kontext nebo obchodní mikroslužbu složenou z několika fyzických služeb. Ale nakonec oba vzory -Ohraničený kontext a mikroslužby- úzce souvisí.

DDD těží z mikroslužeb tím, že získá skutečné hranice ve formě distribuovaných mikroslužeb. Ale nápady, jako je nesdílení modelu mezi mikroslužeb jsou to, co také chcete v ohraničené kontextu.

### <a name="additional-resources"></a>Další zdroje

- **Chrise Richardsona. Vzor: Databáze na službu** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martin Fowler. Ohraničený kontext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martin Fowler. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Strategický návrh řízený doménou s mapováním kontextu** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Předchozí](microservices-architecture.md)
>[další](logical-versus-physical-architecture.md)
