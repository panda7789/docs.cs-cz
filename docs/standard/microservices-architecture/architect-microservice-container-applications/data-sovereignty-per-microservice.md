---
title: Svrchovanost dat v jednotlivých mikroslužbách
description: Svrchovanost dat v jednotlivých mikroslužeb je jedním z nastavení bodu mikroslužeb. Každá mikroslužba musí být jediným vlastníkem jeho databáze, sdílet je s žádné jiné. Všechny instance mikroslužby samozřejmě připojení k databázi stejnou vysokou dostupnost.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 1b0b1fbb72f759eb337c0c1a9c465cc4088d8eff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909702"
---
# <a name="data-sovereignty-per-microservice"></a>Svrchovanost dat v jednotlivých mikroslužbách

Pravidlo důležité pro architekturu mikroslužeb je, že každá mikroslužba musíte vlastnit jeho data domény a logiku. Stejně jako úplné aplikace vlastní jeho logiku a data, takže musíte jednotlivých mikroslužeb vlastníkem jeho logiku a data v rámci samostatného životní cyklus, s nezávislé nasazení jednotlivých mikroslužbách.

To znamená, že konceptuálního modelu domény se budou lišit mezi subsystémy nebo mikroslužeb. Vezměte v úvahu podnikové aplikace, kde aplikace vztahů se zákazníky (CRM) pro řízení, transakční nákupní subsystémy a Zákaznická podpora subsystémů každé volání na data a atributům entity jedinečné zákaznické a každá používá jiné Ohraničený kontext (BC).

Tato zásada je podobná [návrhu řízeného doménou (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), kde každý [ohraničená kontextu](https://martinfowler.com/bliki/BoundedContext.html) nebo autonomní subsystému nebo služby musíte vlastnit jeho doménový model (data a logiku a chování). Každý kontext ohraničená DDD souvisí s jednu obchodní mikroslužeb (jednu nebo několik služeb). Tento bod o ohraničená kontextu vzoru rozbalen v další části.

Na druhé straně přístup tradiční (monolitické data) používaný v mnoha aplikacích je do centralizované databáze jedné nebo několika databází. To je často normalizované databáze SQL, který se používá pro celou aplikaci a všechny jeho vnitřní subsystémy, jak ukazuje obrázek 4 – 7.

![V tradiční přístup je izolované databáze, sdílené napříč všemi službami, obvykle v vrstvené architektury. V metodě mikroslužeb jednotlivých mikroslužeb vlastní jeho modelu/dat](./media/image7.png)

**Obrázek 4 – 7**. Porovnání suverenita dat: monolitické databáze a mikroslužeb

Centralizované databázi přístup zpočátku vypadá jednodušší a zdá se, že umožňují opakované použití entit v různé subsystémy, aby všechno, co konzistentní vzhledem k aplikacím. Ale ve skutečnosti je, že skončíte s velkou tabulkami, které slouží řada různé subsystémy a ve většině případů, které zahrnují atributy a sloupce, které nejsou potřebné. Je to jako pokusu použijte stejný fyzický mapu věnovat turistice krátký záznam pro pořízení automobilu jednodenní cesty a učení zeměpisné oblasti.

Monolitické aplikace se obvykle jediné relační databáze má dvě důležité výhody: [Transakce ACID](https://en.wikipedia.org/wiki/ACID) a jazyka SQL, obě práce ve všech tabulkách a data související s vaší aplikace. Tento přístup poskytuje způsob, jak snadno vytvořit dotaz, který kombinuje data z více tabulek.

Přístup k datům nebude však mnohem složitější, když přesunete na architekturu mikroslužeb. Ale i v případě, že transakce ACID jde nebo by měl použít v rámci mikroslužeb nebo ohraničená kontextu, dat vlastněných touto jednotlivých mikroslužeb je privátní pro tento mikroslužeb a je přístupný pouze prostřednictvím jejího rozhraní API mikroslužby. Zapouzdření dat zajišťuje, že mikroslužby jsou volně propojené a můžete rozvíjet nezávisle na mezi sebou. Pokud několik služeb, které získávali přístup stejná data, by aktualizace schématu vyžadují koordinované aktualizace ke všem službám. To by narušil autonomie životního cyklu mikroslužeb. Ale distribuovaných datových struktur znamená, že nemůžete provádět jednu transakci ACID napříč mikroslužeb. To zase znamená, že při obchodní proces zahrnuje více mikroslužeb je nutné použít konečné konzistence. To je mnohem obtížnější než jednoduché spojení SQL, implementace, protože nelze vytvořit omezení integrity nebo použijte distribuované transakce mezi samostatné databáze, jak vám objasníme později. Podobně mnoho dalších funkcí relační databáze nejsou k dispozici, napříč několika mikroslužeb.

Když se ještě dál, různé mikroslužeb často používají různé *typy* databází. Úložiště pro moderní aplikace a různé druhy dat procesu a relační databáze není vždy nejlepší volbou. Pro některé případy použití, může být databáze NoSQL, jako jsou služby Azure cosmos DB nebo MongoDB pohodlnější datový model a nabízí lepší výkon a škálovatelnost než databáze SQL jako SQL Server nebo databázi SQL Azure. V ostatních případech je relační databáze stále nejlepším řešením. Proto založených na mikroslužbách aplikace často používají kombinaci databáze SQL a NoSQL, která se někdy označuje jako [polyglotické trvalosti](https://martinfowler.com/bliki/PolyglotPersistence.html) přístup.

Dělené polyglot trvalé architektury pro ukládání dat má mnoho výhod. Patří mezi ně volně propojených služeb a lepší výkon, škálovatelnost, náklady a možností správy. To může způsobovat některé běžné problémy správy distribuovaných dat, jak je vysvětleno v "[identifikace hranic mezi modelem a doménou](identify-microservice-domain-model-boundaries.md)" dále v této kapitole.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Vztah mezi mikroslužbami a vzor ohraničená kontextu

Koncept mikroslužeb je odvozen od [ohraničená kontextu (BC) vzor](https://martinfowler.com/bliki/BoundedContext.html) v [návrhu řízeného doménou (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD se zabývá velké modely jejich rozdělení do několika BCs a použití explicitní o jejich hranice. Každý BC musí mít svůj vlastní model a databázi. Každá mikroslužba podobně, vlastní související data. Kromě toho každá BC obvykle má svou vlastní [všudypřítomná jazyk](https://martinfowler.com/bliki/UbiquitousLanguage.html) ke komunikaci mezi vývojáři a odborníky na domény.

Tyto podmínky (hlavně domény entity) v jazyce všudypřítomná může mít různé názvy v různých kontextech ohraničená, i když jiné domény entity sdílejí stejnou identitu (to znamená, jedinečný Identifikátor, který se má použít ke čtení entit ze služby storage). Například v rámci ohraničená profil uživatele entita domény uživatele může nasdílet identity kupujících entita domény v rámci pořadí omezená.

Mikroslužba je proto třeba ohraničená kontext, ale také určuje, že je distribuovaná služba. Je vytvořen jako samostatný proces pro jednotlivých ohraničených kontextech, a musí používat distribuované protokoly, které jste si poznamenali dříve, jako jsou HTTP/HTTPS, protokoly Websocket, nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Vzor ohraničená kontextu, ale neurčuje, zda je kontext ohraničená distribuované služby nebo pokud je jednoduše logické hraniční (například obecný subsystému) v rámci monolitické nasazení aplikace.

Je důležité, abyste měli na očích, definování služby pro jednotlivých ohraničených kontextech je dobrým začátkem. Ale nemáte k omezení návrhu na ni. Někdy je třeba navrhnout kontext ohraničená nebo obchodní mikroslužeb se skládá z několika fyzických služeb. Ale nakonec oba vzorky – omezená kontextu a mikroslužby jsou úzce souvisí.

DDD těží z mikroslužeb tím, že získáme skutečné hranice ve formě distribuovaných mikroslužeb. Ale nápady jako nesdílí modelu mezi mikroslužbami co chcete také v kontextu omezená.

### <a name="additional-resources"></a>Další zdroje

- **Chris Richardson. Vzor: Databáze na službu** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martina Fowlera. BoundedContext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martina Fowlera. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Návrh s použitím kontextu mapování na základě strategické domény** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Předchozí](microservices-architecture.md)
>[další](logical-versus-physical-architecture.md)
