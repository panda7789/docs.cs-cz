---
title: Distribuovaná data
description: Kontrastování datových úložišť v monolitické a cloudových nativních aplikacích.
author: robvet
ms.date: 04/24/2020
ms.openlocfilehash: 8a9f1478f1a46b2367df9372d4adaa3b4c711782
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204694"
---
# <a name="distributed-data"></a>Distribuovaná data

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak jsme viděli v této příručce, cloudový nativní přístup mění způsob, jakým navrhujete, nasazujete a spravujete aplikace. Také mění způsob, jakým spravujete a ukládáte data.

Obrázek 5-1 kontrastuje rozdíly.

![Úložiště dat v nativních aplikacích cloudu](./media/distributed-data.png)

**Obrázek 5-1**. Správa dat v cloudových nativních aplikacích

Zkušení vývojáři budou snadno rozpoznávat architekturu na levé straně obrázku 5-1. V této *aplikaci monolitické*se komponenty Business Service společné umístění společně na úrovni sdílených služeb a sdílejí data z jedné relační databáze.

V mnoha různých způsobech udržuje jedna databáze jednoduché správy dat. Dotazování dat napříč více tabulkami je jednoduché. Změny dat se aktualizují nebo se vrátí zpět. [Kyselé transakce](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) zaručují silnou a okamžitou konzistenci.

Návrh pro cloudový nativní režim nabízí jiný přístup. Na pravé straně obrázku 5-1 si všimněte, jak se firemní funkce odvíjí do malých nezávislých mikroslužeb. Každá mikroslužba zapouzdřuje konkrétní obchodní schopnost a její vlastní data. Databáze monolitické je rozdělená do distribuovaného datového modelu s mnoha menšími databázemi, a to z každého v souladu s mikroslužbou. Když se kouř nevymaže, ukážeme vám návrh, který zveřejňuje *databázi na mikroslužbu*.

## <a name="database-per-microservice-why"></a>Z databáze na mikroslužbu, proč?

Tato databáze na mikroslužbu poskytuje mnoho výhod, zejména pro systémy, které se musí rychle vyvíjet a podporují rozsáhlé škálování. S tímto modelem...

- Data domény jsou zapouzdřena v rámci služby.
- Schéma dat se může vyvíjet bez přímého dopadu na jiné služby.
- Každé úložiště dat může nezávisle škálovat
- Selhání úložiště dat v jedné službě nebude mít přímý vliv na jiné služby.

Oddělení dat také umožňuje, aby každá mikroslužba implementovala typ úložiště dat, který je nejlépe optimalizovaný pro své úlohy, potřeby úložiště a vzory čtení a zápisu. Mezi možnosti patří relační úložiště dat, dokument, klíč-hodnota a dokonce i datové obchody založené na grafu.

Obrázek 5-2 prezentuje princip Polyglot Persistence v systému nativním pro Cloud.

![Trvalost dat Polyglot](./media/polyglot-data-persistence.png)

**Obrázek 5-2**. Trvalost dat Polyglot

Všimněte si na předchozím obrázku, jak každá mikroslužba podporuje jiný typ úložiště dat.

- Mikroslužba katalogu produktů využívá relační databázi pro přizpůsobení komplexní relační struktury svých podkladových dat.
- Mikroslužba nákupního košíku spotřebovává distribuovanou mezipaměť, která podporuje své jednoduché úložiště dat klíč-hodnota.
- Pro objednávání mikroslužeb se využívá databáze NoSql dokumentů pro operace zápisu společně s vysoce denormalizovaným úložištěm klíč/hodnota, aby se vešly velké objemy operací čtení.
  
I když budou relační databáze relevantní pro mikroslužby se složitými daty, databáze NoSQL získaly značnou oblíbenou. Poskytují ohromnou škálu a vysokou dostupnost. Bez jejich schématu umožňuje vývojářům přesunout se od architektury typových datových tříd a ORMs, které vedou ke změně nákladného a časově náročného. V této kapitole se zabýváme databázemi NoSQL dále.

 I když zapouzdření dat do samostatných mikroslužeb může zvýšit flexibilitu, výkon a škálovatelnost, prezentuje i mnoho výzev. V další části se podíváme na tyto výzvy spolu se vzory a postupy, které vám pomůžou je překonat.  

## <a name="cross-service-queries"></a>Dotazy na více služeb

I když jsou mikroslužby nezávislé a zaměřují se na konkrétní funkční možnosti, jako je inventarizace, přeprava nebo objednávání, často vyžadují integraci s dalšími mikroslužbami. Integrace často zahrnuje jednu mikroslužbu, která pro data obsahuje *dotazování* druhé. Obrázek 5-3 ukazuje scénář.

![Dotazování napříč mikroslužbami](./media/cross-service-query.png)

**Obrázek 5-3**. Dotazování napříč mikroslužbami

Na předchozím obrázku se uvidí mikroslužba nákupního košíku, která přidá položku do nákupního košíku uživatele. I když úložiště dat pro tuto mikroslužbu obsahuje data koše a položky řádku, neudržuje data o produktech ani cenách. Místo toho tyto datové položky vlastní katalog a cenové služby. To představuje problém. Jak může mikroslužba nákupního košíku přidat produkt do nákupního košíku uživatele, pokud nemá v databázi ani data o produktech ani ceny?

Jedna z možností popsaná v části kapitola 4 je [přímé volání http](service-to-service-communication.md#queries) od nákupního košíku ke službě Catalog and Price. V kapitole 4 se však říká *synchronní volání http* , které spojuje mikroslužby, což snižuje autonomii a zmenšuje jejich výhody architektury.

Pro každou službu můžeme také implementovat vzor požadavek-odpověď s oddělenými příchozími a odchozími frontami. Tento model je však složitý a vyžaduje k tomu, aby bylo možné korelovat zprávy žádosti a odpovědi.
I když oddělí volání mikroslužby back-end, volající služba musí stále synchronně čekat na dokončení volání. Zahlcení sítě, přechodné chyby nebo přetížená mikroslužba a výsledkem může být dlouhotrvající a dokonce neúspěšné operace.

Místo toho je široce přijatý vzor pro odebrání závislostí mezi službami, což je [vzor materializované zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)znázorněný na obrázku 5-4.

![Model materializované zobrazení](./media/materialized-view-pattern.png)

**Obrázek 5-4**. Model materializovaného zobrazení

V tomto vzoru umístíte do služby nákupního košíku místní datovou tabulku (označovanou jako *model pro čtení*). Tato tabulka obsahuje denormalizovanou kopii dat potřebných z produktových a cenových mikroslužeb. Kopírování dat přímo do nákupního košíku mikroslužba eliminuje nutnost nákladných hovorů mezi službami. S daty, která jsou místní pro službu, můžete zlepšit dobu a spolehlivost odezvy služby. Navíc s vlastní kopií dat je služba nákupního košíku pružnější. Pokud by služba katalogu neměla být k dispozici, měla by přímo ovlivnit službu nákupního košíku. Nákupní košík může pokračovat v práci s daty z vlastního úložiště.

Tento přístup znamená, že v systému teď máte duplicitní data. *Strategická* duplikace dat v systémech nativních pro Cloud je ale stanovený postup a nepovažuje se za antipattern nebo špatný postup. Mějte na paměti, že *jedna a jenom jedna služba* může vlastnit sadu dat a mít nad ní oprávnění. Pokud aktualizujete systém záznamu, bude nutné synchronizovat modely čtení. Synchronizace je obvykle implementována prostřednictvím asynchronního zasílání zpráv pomocí [vzoru pro publikování a odběr](service-to-service-communication.md#events), jak je znázorněno na obrázku 5,4.

## <a name="distributed-transactions"></a>Distribuované transakce

Dotazování na data napříč mikroslužbami je obtížné a implementace transakce napříč několika mikroslužbami je ještě složitější. Podstata zachování konzistence dat napříč nezávislými zdroji dat v různých mikroslužbách nemůže být podstavová. Chybějící distribuované transakce v cloudových nativních aplikacích znamená, že je nutné spravovat distribuované transakce programově. Přesunete se od světa *bezprostřední konzistence* s konečnou *konzistencí*.

Obrázek 5-5 ukazuje problém.

![Transakce ve vzoru Saga](./media/saga-transaction-operation.png)

**Obrázek 5-5**. Implementace transakce napříč mikroslužbami

Na předchozím obrázku se pět nezávislých mikroslužeb účastní v distribuované transakci, která vytváří objednávku. Každá mikroslužba udržuje své vlastní úložiště dat a implementuje místní transakci pro své úložiště. Chcete-li vytvořit objednávku, místní transakce pro *každou* jednotlivou mikroslužbu musí být úspěšná, nebo *všechny* musí přerušit a vrátit zpět operaci. I když je integrovaná transakční podpora k dispozici v rámci každé mikroslužby, neexistuje žádná podpora distribuované transakce, která by byla rozložená do všech pěti služeb za účelem zachování konzistence dat.

Místo toho je nutné tuto distribuovanou transakci sestavit *programově*.

Oblíbeným vzorem pro přidání podpory distribuovaných transakcí je SAGA vzor. Je implementováno seskupením místních transakcí společně a následným vyvoláním každého z nich. Pokud některá z místních transakcí selže, Saga přeruší operaci a vyvolá sadu [kompenzačních transakcí](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Kompenzační transakce vrátí zpět změny provedené předchozími místními transakcemi a obnoví konzistenci dat. Obrázek 5-6 ukazuje neúspěšnou transakci se vzorem Saga.

![Vracení zpět ve vzoru Saga](./media/saga-rollback-operation.png)

**Obrázek 5-6**. Vrácení transakce zpět

V předchozím obrázku se v mikroslužbě inventáře nezdařila operace *inventarizace aktualizací* . Saga vyvolá sadu kompenzačních transakcí (červeně) pro úpravu inventury, zrušení platby a objednávky a vrátí data pro každou mikroslužbu zpět do konzistentního stavu.

Vzorce Saga jsou obvykle choreographed jako série souvisejících událostí nebo Orchestrované jako sada souvisejících příkazů. V kapitole 4 jsme probrali model Agregátoru služby, který by byl základem pro orchestraci Saga implementace. Provedli jsme také vytváření událostí společně s Azure Service Bus a Azure Event Grid témata, která by byla základem pro implementaci choreographed Saga.

## <a name="high-volume-data"></a>Velké objemy dat

Rozsáhlé aplikace pro nativní Cloud často podporují požadavky na velké objemy dat. V těchto scénářích můžou tradiční techniky úložiště dat způsobovat problémová místa. U složitých systémů, které se nasazují ve velkém měřítku, může výkon aplikace zvýšit jak CQRS (Command and Query Responsibility Segregation) (CQRS), tak i zdroje událostí.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs)je model architektury, který může přispět k maximalizaci výkonu, škálovatelnosti a zabezpečení. Vzor odděluje operace, které čtou data z operací, které zapisují data.

V případě normálních scénářů se stejný model entity a objekt úložiště dat používají pro *operace čtení i* zápisu.

Scénář s vysokými objemy dat ale může využívat samostatné modely a tabulky dat pro čtení a zápis. Aby bylo možné zvýšit výkon, operace čtení se může dotazovat na vysoce denormalizovanou reprezentaci dat, aby nedocházelo k nákladným opakovaným spojením tabulek a zámkům tabulek. Operace *zápisu* , která se označuje jako *příkaz*, by se aktualizovala na plně normalizovanou reprezentaci dat, která by zajistila konzistenci. Pak je nutné implementovat mechanismus, aby obě reprezentace zůstala synchronizovaná. Obvykle při každé změně tabulky zápisu publikuje událost, která replikuje úpravu do tabulky pro čtení.

Obrázek 5-7 ukazuje implementaci CQRS vzoru.

![CQRS (Command and Query Responsibility Segregation)](./media/cqrs-implementation.png)

**Obrázek 5-7**. Implementace CQRS

Na předchozím obrázku jsou implementované samostatné modely příkazů a dotazů. Každá operace zápisu dat je uložena do úložiště pro zápis a následně šířena do úložiště pro čtení. Věnujte velkou pozornost tomu, jak proces šíření dat funguje na principu konečné [konzistence](http://www.cloudcomputingpatterns.org/eventual_consistency/). Model čtení se nakonec synchronizuje s modelem zápisu, ale v procesu může dojít k prodlevě. V další části se podíváme na konečnou konzistenci.

Toto oddělení umožňuje čtení a zápisy nezávisle na velikosti. Operace čtení používají schéma optimalizované pro dotazy, zatímco zápisy používají schéma optimalizované pro aktualizace. Čtení dotazů přechází na Denormalizovaná data, zatímco složitá obchodní logika může být použita na model zápisu. Také můžete způsobit zvýšení zabezpečení při operacích zápisu než čtení, které zveřejňuje.

Implementace CQRS může zlepšit výkon aplikace pro cloudové nativní služby. Výsledkem ale je složitější návrh. Aplikujte tento princip pečlivě a strategicky na tyto části vaší cloudové aplikace, která z nich bude výhodná. Další informace o CQRS naleznete v části [mikroslužby Microsoft Book .NET: architektura pro kontejnerové aplikace .NET](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Původ události

Dalším přístupem k optimalizaci scénářů s velkými objemy dat je využití [zdrojů událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

Systém obvykle ukládá aktuální stav datové entity. Pokud uživatel změní své telefonní číslo, například záznam zákazníka se aktualizuje o nové číslo. Vždycky ví, že aktuální stav entity dat je, ale každá aktualizace Přepisuje předchozí stav.

Ve většině případů tento model funguje dobře. V systémech s vysokým objemem ale režie z transakčního uzamykání a častých operací aktualizace může ovlivnit výkon databáze, rychlost odezvy a omezení škálovatelnosti.

Pro zachytávání dat má navýšení zdroje událostí jiný přístup. Všechny operace, které mají vliv na data, jsou uchovávány v úložišti událostí. Místo aktualizace stavu datového záznamu připojíme každou změnu do sekvenčního seznamu minulých událostí – podobně jako v hlavní knize účetní knihy. Úložiště událostí se v systému zaznamená pro data. Slouží k rozšíření různých vyhodnocených zobrazení v rámci ohraničeného kontextu mikroslužby. Obrázek 5,8 ukazuje vzor.

![Event Sourcing](./media/event-sourcing.png)

**Obrázek 5-8**. Event Sourcing

Na předchozím obrázku si všimněte, že každá položka (modře) pro nákupní košík uživatele je připojená k základnímu úložišti událostí. V sousedícím materializovém zobrazení systém projektuje aktuální stav přehráním všech událostí spojených s každým nákupním košíkem. Toto zobrazení nebo model čtení je pak zpřístupněno zpět do uživatelského rozhraní. Události je také možné integrovat s externími systémy a aplikacemi nebo s dotazem, abyste zjistili aktuální stav entity. S tímto přístupem zachováte historii. Znáte nejen aktuální stav entity, ale také to, jak jste dosáhli tohoto stavu.

Naproti mechanickému nahlasování se u zdroje událostí zjednoduší model zápisu. Neexistují žádné aktualizace ani odstranění. Připojení každé datové položky jako neproměnlivá událost minimalizuje konflikty kolizí, uzamykání a souběžnosti spojené s relačními databázemi. Sestavování modelů čtení pomocí vzoru materializované zobrazení umožňuje oddělit zobrazení od modelu zápisu a zvolit nejvhodnější úložiště dat pro optimalizaci potřeb uživatelského rozhraní aplikace.

Pro tento model Vezměte v úvahu úložiště dat, které přímo podporuje zdrojové události. Azure Cosmos DB, MongoDB, Cassandra, CouchDB a RavenDB jsou vhodné kandidáty.

Stejně jako u všech vzorů a technologií implementujte strategické a v případě potřeby. I když může poskytovat zvýšení výkonu a škálovatelnosti, přináší se vám náklady na složitost a výuková křivka.

>[!div class="step-by-step"]
>[Předchozí](service-mesh-communication-infrastructure.md)
>[Další](relational-vs-nosql-data.md)
