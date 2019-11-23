---
title: Svrchovanost dat v jednotlivých mikroslužbách
description: Suverenita dat na mikroslužby je jedním z klíčových bodů mikroslužeb. Každá mikroslužba musí být jediným vlastníkem své databáze a bude ji sdílet bez dalších. Všechny instance mikroslužeb se samozřejmě připojí ke stejné databázi s vysokou dostupností.
ms.date: 09/20/2018
ms.openlocfilehash: f606d6314f38bf3e2c163871af432806dddc7446
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191920"
---
# <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

Důležité pravidlo pro architekturu mikroslužeb je, že každá mikroslužba musí vlastnit svoje doménová data a logiku. Stejně jako plná aplikace vlastní svou logiku a data, takže musí každá mikroslužba vlastnit svou logiku a data v rámci autonomního životního cyklu s nezávislou nasazováním na mikroslužbu.

To znamená, že koncepční model domény se bude lišit mezi subsystémy nebo mikroslužbami. Vezměte v úvahu podnikové aplikace, kde se aplikace pro řízení vztahů se zákazníky (CRM), transakční subsystémy a subsystémy zákaznické podpory každé volání týkají jedinečných atributů a dat entit zákazníka a kde každá z nich používá jiný Ohraničený kontext (BC).

Tento princip je podobný jako u [návrhu řízeného doménou (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), kde každý [ohraničený kontext](https://martinfowler.com/bliki/BoundedContext.html) nebo autonomní podsystém nebo služba musí vlastnit svůj doménový model (data plus logiku a chování). Každý DDD ohraničený kontext je koreluje s jednou obchodní mikroslužbou (jedna nebo několik služeb). Tento bod o vzoru ohraničeného kontextu je rozbalen v následující části.

Na druhé straně používá tradiční (monolitické data) přístup v mnoha aplikacích jenom jednu centralizovanou databázi nebo jenom pár databází. To je často normalizovaná databáze SQL, která se používá pro celou aplikaci a všechny její interní subsystémy, jak je znázorněno na obrázku 4-7.

![Diagram znázorňující přístupy ke dvěma databázím](./media/data-sovereignty-per-microservice/data-sovereignty-comparison.png)

**Obrázek 4-7**. Porovnání suverenity dat: databáze monolitické versus mikroslužby

V tradičním přístupu existuje jedna databáze sdílená napříč všemi službami, obvykle v vrstvené architektuře. V přístupu k mikroslužbám vlastní mikroslužba svůj model/data. Centralizovaný přístup k databázi zpočátku vypadá zjednodušeně a zdá se, že umožňuje opakované použití entit v různých subsystémech, aby se zajistila konzistence všeho. Realita ale znamená, že máte spoustu tabulek, které obsluhují mnoho různých subsystémů, včetně atributů a sloupců, které nejsou ve většině případů nutné. Vypadá to, že se snažíte použít stejnou fyzickou mapu pro nachodíme krátkým záznamem, a to s využitím každodenního výletního provozu a učením geografie.

Aplikace monolitické, která obvykle používá jedinou relační databázi, má dvě důležité výhody: [transakční transakce](https://en.wikipedia.org/wiki/ACID) a jazyk SQL, jak pracují napříč všemi tabulkami a daty, které se vztahují k vaší aplikaci. Tento přístup poskytuje způsob, jak snadno napsat dotaz, který kombinuje data z více tabulek.

Přístup k datům se ale při přesunu do architektury mikroslužeb bude mnohem složitější. I při použití transakcí kyseliny v rámci mikroslužby nebo vázaného kontextu je důležité vzít v úvahu, že data vlastněná jednotlivými mikroslužbami jsou pro tuto mikroslužbu soukromá a měla by k ní být přistupovaná synchronně prostřednictvím koncových bodů rozhraní API (REST, gRPC, Protokol SOAP atd.) nebo asynchronně prostřednictvím zasílání zpráv (AMQP nebo podobný).

Zapouzdření dat zajišťuje, že mikroslužby budou volně propojeny a mohou se vyvíjet nezávisle na sobě. Pokud má více služeb přístup ke stejným datům, aktualizace schématu by vyžadovala koordinované aktualizace pro všechny služby. Tím by došlo k přerušení autonomie životního cyklu mikroslužeb. Ale distribuované datové struktury znamenají, že nemůžete vytvořit jedinou transakční transakci napříč mikroslužbami. To znamená, že je nutné použít konečnou konzistenci v případě, že obchodní proces zahrnuje více mikroslužeb. To je mnohem těžší implementovat než jednoduchá spojení SQL, protože nemůžete vytvářet omezení integrity ani používat distribuované transakce mezi samostatnými databázemi, jak vysvětlujeme později. Podobně mnoho dalších funkcí relační databáze není k dispozici napříč více mikroslužbami.

Ještě víc, různé mikroslužby často používají různé *druhy* databází. Moderní aplikace ukládají a zpracovávají nejrůznější druhy dat a relační databáze nejsou vždycky nejlepší volbou. V některých případech použití může databáze NoSQL, jako je Azure CosmosDB nebo MongoDB, mít užitečnější datový model a nabízet lepší výkon a škálovatelnost než databáze SQL, jako je SQL Server nebo Azure SQL Database. V ostatních případech je relační databáze stále nejlepším řešením. Proto aplikace založené na mikroslužbách často používají kombinaci databází SQL a NoSQL, která se někdy nazývá přístup [trvalosti Polyglot](https://martinfowler.com/bliki/PolyglotPersistence.html) .

Dělená Polyglot architektura pro úložiště dat má mnoho výhod. Patří mezi ně volně spárované služby a lepší výkon, škálovatelnost, náklady a možnosti správy. Může ale zavádět některé problémy se správou distribuovaných dat, jak je vysvětleno v části[Identifikace hranice doménového modelu](identify-microservice-domain-model-boundaries.md)dále v této kapitole.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Vztah mezi mikroslužbami a vzorem ohraničeného kontextu

Koncept mikroslužeb je odvozený ze [vzoru vázaného kontextu (Bc)](https://martinfowler.com/bliki/BoundedContext.html) v návrhu založeném na [doméně (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD se zabývá velkými modely jejich dělením na více BCs a jsou explicitní o jejich hranicích. Každé BC musí mít svůj vlastní model a databázi; Podobně každá mikroslužba vlastní související data. Kromě toho má každý BC obvykle svůj vlastní [všudypřítomný jazyk](https://martinfowler.com/bliki/UbiquitousLanguage.html) , který usnadňuje komunikaci mezi vývojáři softwaru a odborníky na domény.

Tyto výrazy (hlavně doménové entity) v jazyce všudypřítomný mohou mít různé názvy v různých ohraničených kontextech, a to i v případě, že různé doménové entity sdílejí stejnou identitu (tj. jedinečné ID, které se používá k načtení entity z úložiště). Například v kontextu vázaného na uživatelský profil může entita doména uživatele sdílet identitu s entitou domény Buyers v kontextu řazení.

Mikroslužba je proto podobně jako ohraničený kontext, ale také určuje, že se jedná o distribuovanou službu. Je sestaven jako samostatný proces pro každý ohraničený kontext a musí používat distribuované protokoly uvedené dříve, například HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Vzor ohraničeného kontextu však neurčuje, zda je ohraničený kontext distribuovanou službou nebo zda je v rámci aplikace monolitické-Deployment jednoduše logická hranice (například obecný podsystém).

Je důležité zdůraznit, že definování služby pro každý ohraničený kontext je dobrým místem, kde začít. Nemusíte ale omezit návrh na. Někdy je nutné navrhnout ohraničený kontext nebo obchodní mikroslužby složené z několika fyzických služeb. Ale v konečném kontextu se s nimi úzce souvisejí.

DDD výhody mikroslužeb tím, že získají reálné hranice ve formě distribuovaných mikroslužeb. Ale nápady, jako není sdílení modelu mezi mikroslužbami, je to, co v ohraničeném kontextu také potřebujete.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Chris Richardson. Vzor: \ databáze na službu**
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martin Fowlera. BoundedContext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martin Fowlera. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Strategický návrh založený na doméně s mapováním kontextu** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Předchozí](microservices-architecture.md)
>[Další](logical-versus-physical-architecture.md)
