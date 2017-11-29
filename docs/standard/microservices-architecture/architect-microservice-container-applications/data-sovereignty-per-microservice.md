---
title: "Data suverenity za mikroslužbu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Data suverenity za mikroslužbu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c51daae04215cfa6f5b5b8d2158a8ed1a8949652
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="data-sovereignty-per-microservice"></a>Data suverenity za mikroslužbu

Pravidlo důležité pro architekturu mikroslužeb je každý mikroslužbu musí být vlastníkem jeho data domény a logiku. Stejně jako úplné aplikace vlastní jeho logiku a data, takže musí každý mikroslužbu vlastní jeho logiku a data v rámci autonomního životního cyklu, nezávislé nasazení za mikroslužby.

To znamená, že mezi subsystémy nebo mikroslužeb se budou lišit konceptuálního modelu domény. Vezměte v úvahu podnikové aplikace, kde zákazník relace (CRM) aplikací pro správu, transakční nákupu subsystémy a zákaznické podpory subsystémy každé volání a atributům entity jedinečných zákaznických dat a tam, kde každý využívá jiné Kontext ohraničené (BC).

Tento princip je podobný v [řízené domény návrhu (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), kde každý [ohraničenou kontextu](https://martinfowler.com/bliki/BoundedContext.html) nebo autonomní subsystému nebo služby musí být vlastníkem svůj model domény (dat a logiku a chování). Každý DDD ohraničenou kontext koreluje s jeden obchodní mikroslužbu (jednoho nebo několika služby). (Jsme rozbalte v tomto bodě o vzoru ohraničenou kontextu v další části.)

Na druhé straně se metoda tradiční (monolitický data) používaná v mnoha aplikacích se jedné centralizované databáze nebo několika databází. To je často normalizovaný SQL database, která se používá pro celou aplikaci a všechny jeho vnitřní subsystémy, jak je znázorněno na obrázku 4-7.

![](./media/image7.png)

**Obrázek 4-7**. Porovnání suverenity dat.: monolitický databáze a mikroslužeb

Centralizované databáze přístup počátečním vypadá jednodušší a zdá se, že povolení opakovaného použití entity v různé subsystémy, aby vše konzistentní. Ale když ve skutečnosti je, že skončili s velmi velké tabulky slouží k mnoha různé subsystémy, které obsahují atributy a sloupce, které nejsou potřebné ve většině případů. je třeba pokouší použít stejné fyzické mapy pro turistika krátké záznamu, trvá dlouho den car cestě a učení geography.

Monolitický aplikace se obvykle jedné relační databáze má dvě důležité výhody: [transakce ACID](https://en.wikipedia.org/wiki/ACID) a jazyka SQL, i práci ve všech tabulkách a data související s vaší aplikace. Tento přístup poskytuje způsob, jak snadno vytvořit dotaz, který kombinuje data z více tabulek.

Přístup k datům stane však mnohem složitější, když přesouváte architektura mikroslužeb. Ale i v případě, že transakce ACID můžete nebo by měl použít v rámci mikroslužbu nebo ohraničenou kontextu, data vlastníkem jednotlivých mikroslužbu soukromý této mikroslužbu a můžete přistupovat pouze prostřednictvím jejího rozhraní API mikroslužby. Zapouzdření data zajišťuje, že mikroslužeb jsou volně vázány a můžete rozvíjet nezávisle na sobě. Pokud více služeb byly přístup ke stejným datům, aktualizace schématu vyžadovat koordinované aktualizace ke všem službám. Tím by došlo k přerušení nezávislé životního cyklu mikroslužby. Ale distribuované datové struktury znamená, že nemůžete provádět jednu transakci ACID napříč mikroslužeb. To zase znamená, že je nutné použít konzistence typu případné při obchodní proces zahrnuje více mikroslužeb. Toto je mnohem obtížnější než jednoduché spojení SQL; implementace Podobně řadu dalších funkcí relační databáze nejsou k dispozici napříč více mikroslužeb.

Budete i pokračovat, jiný mikroslužeb často používají různé *typy* databází. Moderní aplikace úložiště a proces různé druhy dat a relační databáze není vždy nejlepší volbou. Pro některé případy použití, mohou mít pohodlnější datový model a nabízí lepší výkon a škálovatelnost než databázi SQL, jako je SQL Server nebo Azure SQL Database databáze NoSQL, jako je Azure DocumentDB nebo MongoDB. V ostatních případech relační databáze je stále nejlepší metodou. Proto na základě mikroslužeb aplikace často používají směs databáze SQL a NoSQL, která se někdy nazývá [polyglot trvalost](http://martinfowler.com/bliki/PolyglotPersistence.html) přístup.

Oddílů, trvalé polyglot architektura pro úložiště dat má mnoho výhod. Patří sem volně párované služby a lepší výkon, škálovatelnost, náklady a možnosti správy. Ho může způsobovat některé běžné problémy správy distribuovaných datech jako vysvětlíme v "[identifikaci hranice modelu domény](#identifying-domain-model-boundaries-for-each-microservice)" dál v této kapitole.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Vztah mezi mikroslužeb a vzor ohraničenou kontextu

Koncept mikroslužbu je odvozena z [ohraničenou kontextu (BC) vzor](http://martinfowler.com/bliki/BoundedContext.html) v [řízené domény návrhu (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD se zabývá velké modely rozdělením je na víc BCs a probíhá explicitní o jejich hranice. Každý BC musí mít svůj vlastní modelu a databázi. Podobně každý mikroslužbu vlastní související data. Kromě toho každý BC obvykle má svou vlastní [všudypřítomný jazyk](http://martinfowler.com/bliki/UbiquitousLanguage.html) ke komunikaci mezi vývojáři softwaru a odborníky domény.

Tyto podmínky (hlavně domény entity) v jazyce všudypřítomný může mít odlišné názvy v různých kontextech ohraničenou, i když jiné domény entity sdílejí stejnou identitu (to znamená, jedinečné ID sloužící k načtení entity úložiště). Například v kontextu, ohraničenou profilu uživatele, může entita domény uživatele sdílet identity s entita domény kupujících v řazení ohraničenou kontextu.

Mikroslužbu je proto třeba kontextu ohraničenou, ale také určuje, že je distribuovaná služba. Je vytvořen jako samostatný proces pro každý ohraničenou kontext a musí používat distribuované protokoly HTTP a HTTPS, Websocket, jako je již bylo uvedeno dříve, nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Vzor ohraničenou kontextu však neurčuje zda kontext ohraničenou je distribuovaná služba, nebo pokud je jednoduše logická hranici (např. obecný subsystému) v rámci monolitický nasazení aplikace.

Je důležité, abyste měli na očích, definování služby pro každý ohraničenou kontext je dobrým místem, kde spustit. Ale nemáte, můžete zadat omezení návrhu na ni. Někdy je třeba navrhnout kontextu ohraničenou nebo obchodní mikroslužbu skládá z několika fyzických služeb. Ale nakonec, jak vzory – ohraničenou kontextu a mikroslužbu – úzce souvisejí.

Výhody DDD z mikroslužeb získáním skutečné hranice ve formě distribuované mikroslužeb. Ale nápady třeba není sdílení modelu mezi mikroslužeb co chcete taky v kontextu vázaný.

### <a name="additional-resources"></a>Další zdroje

-   **Jan Ryšánková. Vzor: Databáze pro službu**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler. BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler. PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini. Strategické domény řízené návrhu pomocí kontextu mapování**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Předchozí] (mikroslužeb architecture.md) [Další] (logické a fyzického architecture.md)
