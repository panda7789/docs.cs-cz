---
title: Samostatná databáze pro každou mikroslužbu
description: Kontrastní ukládání dat v monolitických a cloudově nativních aplikacích.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c0c5611fa866d70f155e4bdad2eee1181b13c065
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141442"
---
# <a name="database-per-microservice"></a>Samostatná databáze pro každou mikroslužbu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak jsme viděli v této knize, přístup nativní pro cloud mění způsob, jakým navrhujete, nasadíte a spravujete aplikace. Změní také způsob správy a ukládání dat.

Obrázek 5-1 kontrastuje rozdíly.

![Úložiště dat v cloudových aplikacích](./media/distributed-data.png)

**Obrázek 5-1**. Správa dat v cloudových nativních aplikacích

Zkušení vývojáři snadno rozpoznají architekturu na levé straně obrázku 5-1. V této *monolitické aplikaci*se komponenty obchodní ch odpovědny společně nacházejí ve vrstvě sdílených služeb a sdílejí data z jedné relační databáze.

V mnoha ohledech, jedna databáze udržuje správu dat jednoduché. Dotazování dat ve více tabulkách je jednoduché. Změny dat aktualizovat společně nebo všechny vrácení zpět. [Transakce ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) zaručují silnou a okamžitou konzistenci.

Navrhování pro cloud nativní, bereme jiný přístup. Na pravé straně obrázku 5-1 si všimněte, jak se obchodní funkce odděluje do malých, nezávislých mikroslužeb. Každá mikroslužba zapouzdřuje konkrétní obchodní schopnosti a vlastní data. Monolitické databáze se rozkládá do distribuovaného datového modelu s mnoha menších databází, z nichž každý zarovnání s mikroslužeb. Když se kouř vyčistí, objevíme se s návrhem, který zveřejňuje *databázi na mikroslužbu*.

## <a name="why"></a>Proč?

Tato databáze na mikroslužbu poskytuje mnoho výhod, zejména pro systémy, které se musí rychle vyvíjet a podporovat masivní škálování. S tímto modelem...

- Data domény jsou zapouzdřena v rámci služby.
- Schéma dat se může vyvíjet bez přímého dopadu na další služby
- Každé úložiště dat může nezávisle škálovat
- Selhání úložiště dat v jedné službě nebude mít přímý dopad na jiné služby

Oddělení dat také umožňuje každé mikroslužeb implementovat typ úložiště dat, který je nejlépe optimalizován pro jeho zatížení, potřeby úložiště a čtení a zápis u vzorců. Volby zahrnují relační, dokument, klíč-hodnota, a dokonce i graf-založené úložiště dat.

Obrázek 5-2 představuje princip perzistence polyglotu v cloudově nativním systému.

![Trvalosti dat polyglotu](./media/polyglot-data-persistence.png)

**Obrázek 5-2**. Trvalosti dat polyglotu

Všimněte si na předchozím obrázku, jak každá mikroslužba podporuje jiný typ úložiště dat.

- Mikroslužba katalogu produktů spotřebovává relační databázi tak, aby vyhovovala bohaté relační struktuře podkladových dat.
- Mikroslužba nákupního košíku spotřebovává distribuovanou mezipaměť, která podporuje jeho jednoduché úložiště dat klíč-hodnota.
- Řazení mikroslužby spotřebovává jak databáze dokumentů NoSql pro operace zápisu spolu s vysoce nenormalizované úložiště klíč/hodnota pro umístění velké objemy operací čtení.
  
Zatímco relační databáze zůstávají relevantní pro mikroslužby se složitými daty, NoSQL databáze získaly značnou popularitu. Poskytují masivní rozsah a vysokou dostupnost. Jejich bezschématová povaha umožňuje vývojářům přejít od architektury zadaných datových tříd a ORMů, které usnadňují změny a jsou časově náročné. NoSQL databáze pokrýváme dále v této kapitole.

 Zatímco zapouzdření dat do samostatných mikroslužeb může zvýšit agilitu, výkon a škálovatelnost, představuje také mnoho výzev. V další části diskutujeme o těchto výzvách spolu se vzory a postupy, které jim pomohou je překonat.  

## <a name="cross-service-queries"></a>Dotazy mezi službami

Zatímco mikroslužby jsou nezávislé a zaměřují se na konkrétní funkční funkce, jako je inventář, expedice nebo objednávání, často vyžadují integraci s jinými mikroslužbami. Často integrace zahrnuje jednu *mikroslužbu dotazování* jiné pro data. Obrázek 5-3 ukazuje scénář.

![Dotazování napříč mikroslužbami](./media/cross-service-query.png)

**Obrázek 5-3**. Dotazování napříč mikroslužbami

Na předchozím obrázku vidíme mikroslužbu nákupního košíku, která přidá položku do nákupního košíku uživatele. Zatímco úložiště dat pro tuto mikroslužbu obsahuje data košíku a řádkové položky, neudržuje data o produktech nebo cenách. Místo toho jsou tyto datové položky vlastněny katalogu a ceny mikroslužeb. To představuje problém. Jak může mikroslužba nákupního košíku přidat produkt do nákupního košíku uživatele, když nemá produkt ani údaje o cenách ve své databázi?

Jednou z možností popsaných v kapitole 4 je [přímé volání HTTP](service-to-service-communication.md#queries) z nákupního košíku do katalogu a stanovení cen mikroslužeb. V kapitole 4 jsme však řekli, že synchronní volání HTTP *spojuje pár* mikroslužeb, čímž snižuje jejich autonomii a snižuje jejich architektonické výhody.

Můžeme také implementovat vzor požadavek odpověď se samostatnými příchozía odchozí fronty pro každou službu. Tento vzor je však složité a vyžaduje instalatérství korelovat požadavky a odpovědi zprávy.
Zatímco to odpojit volání back-endu mikroslužby, volání služby musí stále synchronně čekat na dokončení volání. Zahlcení sítě, přechodné chyby nebo přetížené mikroslužby a může mít za následek dlouhotrvající a dokonce i neúspěšné operace.

Místo toho široce přijímaný vzor pro odstranění závislostí mezi službami je [materiální vzorek zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), znázorněný na obrázku 5-4.

![Zhmotněný řez](./media/materialized-view-pattern.png)

**Obrázek 5-4**. Model materializovaného zobrazení

Pomocí tohoto vzoru umístíte do služby nákupního košíku místní tabulku dat (označovanou jako *model pro čtení).* Tato tabulka obsahuje nenormalizovanou kopii dat potřebných z mikroslužeb produktu a cen. Kopírování dat přímo do mikroslužby nákupního košíku eliminuje potřebu nákladných volání mezi službami. S místními daty pro službu můžete zlepšit dobu odezvy a spolehlivost služby. Navíc s vlastní kopii dat je služba nákupního košíku odolnější. Pokud by služba katalogu přestala být dostupná, neměla by přímý vliv na službu nákupního košíku. Nákupní košík může pokračovat v provozu s daty z vlastního obchodu.

Úlovek s tímto přístupem je, že nyní máte duplicitní data ve vašem systému. *Strategicky* duplikace dat v cloudnativních systémech je však zavedenou praxí a není považována za anti-pattern nebo špatnou praxi. Mějte na paměti, že *jedna a jediná služba* může vlastnit sadu dat a mít nad ní oprávnění. Při aktualizaci systému záznamu budete muset synchronizovat modely čtení. Synchronizace je obvykle implementována prostřednictvím asynchronního zasílání zpráv se [vzorem publikování/odběru](service-to-service-communication.md#events), jak je znázorněno na obrázku 5.4.

## <a name="distributed-transactions"></a>Distribuované transakce

Zatímco dotazování dat napříč mikroslužbami je obtížné, implementace transakce napříč několika mikroslužeb je ještě složitější. Inherentní výzvu zachování konzistence dat napříč nezávislými zdroji dat v různých mikroslužeb nelze podceňovat. Nedostatek distribuovaných transakcí v aplikacích nativních pro cloud znamená, že je nutné spravovat distribuované transakce programově. Přesunete se ze světa *okamžité konzistence* do světa *případné konzistence*.

Obrázek 5-5 ukazuje problém.

![Transakce ve vzoru ságy](./media/saga-transaction-operation.png)

**Obrázek 5-5**. Implementace transakce mezi mikroslužbami

Na předchozím obrázku pět nezávislých mikroslužeb účastnit distribuované transakce, která vytvoří objednávku. Každá mikroslužba udržuje své vlastní úložiště dat a implementuje místní transakce pro své úložiště. Chcete-li vytvořit pořadí, musí být úspěšná místní transakce pro *každou* jednotlivou mikroslužbu, nebo *musí všechny* přerušit a vrátit zpět operaci. Zatímco integrovaná transakční podpora je k dispozici v rámci každé mikroslužeb, neexistuje žádná podpora pro distribuované transakce, která by se rozprostírala napříč všemi pěti službami, aby byla data konzistentní.

Místo toho je nutné vytvořit tuto distribuovanou transakci *programově*.

Populární vzor pro přidání distribuované transakční podporu je vzor Saga. Je implementována seskupením místních transakcí dohromady programově a postupně s oprávněním ke každému z nich. Pokud některá z místních transakcí nezdaří, Saga přeruší operaci a vyvolá sadu [vyrovnávacítransakce](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Kompenzační transakce vrátit zpět změny provedené předchozí místní transakce a obnovit konzistenci dat. Obrázek 5-6 ukazuje neúspěšnou transakci se vzorem Saga.

![Vrátit se zpět do vzoru ságy](./media/saga-rollback-operation.png)

**Obrázek 5-6**. Vrácení transakce zpět

Na předchozím obrázku *operace Aktualizovat zásoby* selhala v mikroslužbě Zásoby. Saga vyvolá sadu vyrovnávacích transakcí (červeně) upravit počty zásob, zrušit platbu a objednávku a vrátit data pro každou mikroslužbu zpět do konzistentního stavu.

Vzorce ságy jsou obvykle choreografovány jako série souvisejících událostí nebo orchestrovány jako sada souvisejících příkazů. V kapitole 4 jsme diskutovali o agregátoru služeb vzor, který by byl základem pro řízené ságy provádění. Také jsme diskutovali o událostech spolu s tématy Azure Service Bus a Azure Event Grid, které by byly základem pro choreografickou implementaci ságy.

## <a name="high-volume-data"></a>Velkoobjemová data

Velké aplikace nativní pro cloud často podporují požadavky na velkoobjemová data. V těchto scénářích tradiční techniky ukládání dat může způsobit kritické body. U složitých systémů, které se nasazují ve velkém měřítku, může oddělení odpovědnosti příkazů i dotazů (CQRS) i získávání událostí zlepšit výkon aplikací.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), je architektonický vzor, který může pomoci maximalizovat výkon, škálovatelnost a zabezpečení. Vzor odděluje operace, které čtou data z těchto operací, které zapisují data.

Pro normální scénáře se stejný model entity a objekt úložiště dat používají pro operace čtení *i* zápisu.

Scénář dat s velkým objemem však může těžit ze samostatných modelů a tabulek dat pro čtení a zápisy. Chcete-li zlepšit výkon operace čtení může dotaz proti vysoce nenormalizované reprezentace dat, aby se zabránilo nákladné opakující se tabulka spojení a tabulka zámky. Operace *zápisu,* označovaná jako *příkaz*, by se aktualizovala proti plně normalizované reprezentaci dat, která by zaručila konzistenci. Potom je třeba implementovat mechanismus zachovat obě reprezentace v synchronizaci. Obvykle při každé změně tabulky zápisu publikuje událost, která replikuje změny tabulky pro čtení.

Obrázek 5-7 ukazuje implementaci cqrs vzor.

![Oddělení odpovědnosti příkazů a dotazů](./media/cqrs-implementation.png)

**Obrázek 5-7**. Implementace CQRS

Na předchozím obrázku jsou implementovány samostatné modely příkazů a dotazů. Každá operace zápisu dat je uložena do úložiště zápisu a poté rozšířena do úložiště pro čtení. Věnujte velkou pozornost tomu, jak proces šíření dat funguje na principu [případné konzistence](http://www.cloudcomputingpatterns.org/eventual_consistency/). Čtení modelu nakonec synchronizuje s modelem zápisu, ale může být určité zpoždění v procesu. V další části diskutujeme o případné konzistenci.

Toto oddělení umožňuje čtení a zápisy škálovat nezávisle. Operace čtení používají schéma optimalizované pro dotazy, zatímco zápisy používají schéma optimalizované pro aktualizace. Dotazy pro čtení jdou proti nenormalizovaným datům, zatímco komplexní obchodní logiku lze použít pro model zápisu. Stejně tak můžete uložit přísnější zabezpečení pro operace zápisu, než ty, které odhalují čtení.

Implementace CQRS může zlepšit výkon aplikací pro cloudové nativní služby. Výsledkem však je složitější návrh. Tento princip používejte pečlivě a strategicky na ty části aplikace nativní pro cloud, které z něj budou mít prospěch. Další informace o CQRS naleznete v knize Microsoft [Book .NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Získávání událostí

Další přístup k optimalizaci scénářů velkoobjemových dat zahrnuje [získávání událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

Systém obvykle ukládá aktuální stav datové entity. Pokud například uživatel změní své telefonní číslo, záznam zákazníka se aktualizuje o nové číslo. Vždy známe aktuální stav datové entity, ale každá aktualizace přepíše předchozí stav.

Ve většině případů tento model funguje dobře. V systémech s vysokou objemem však režie z transakčního uzamčení a častých operací aktualizace může ovlivnit výkon databáze, odezvu a omezit škálovatelnost.

Event Sourcing má jiný přístup k zachycení dat. Každá operace, která ovlivňuje data, je v úložišti událostí zachována. Namísto aktualizace stavu datového záznamu připojíme každou změnu do sekvenčního seznamu minulých událostí - podobně jako účetní knihy. Úložiště událostí se stane systémem záznamu pro data. Používá se k šíření různých zhmotněných zobrazení v rámci ohraničené kontextu mikroslužeb. Obrázek 5.8 ukazuje vzorek.

![Event Sourcing](./media/event-sourcing.png)

**Obrázek 5-8**. Event Sourcing

Na předchozím obrázku si všimněte, jak je každá položka (modře) pro nákupní košík uživatele připojena k podkladovému úložišti událostí. V přilehlém zhmotněným zobrazení systém promítá aktuální stav přehráním všech událostí přidružených ke každému nákupnímu košíku. Tento pohled nebo čtení modelu je pak vystavena zpět do ui. Události lze také integrovat s externími systémy a aplikacemi nebo dotazovány k určení aktuálního stavu entity. S tímto přístupem, budete udržovat historii. Znáte nejen aktuální stav entity, ale také to, jak jste k tomuto stavu dosáhli.

Mechanicky řečeno, získávání událostí zjednodušuje model zápisu. Neexistují žádné aktualizace nebo odstranění. Připojení každé položky dat jako neměnné události minimalizuje konflikty konfliktů kolizí, uzamčení a souběžnosti přidružené k relačním databázím. Vytváření modelů čtení s materiálním vzorem zobrazení umožňuje oddělit zobrazení od modelu zápisu a zvolit nejlepší úložiště dat pro optimalizaci potřeb vašeho aplikačního uj.

Pro tento vzor zvažte úložiště dat, které přímo podporuje získávání událostí. Azure Cosmos DB, MongoDB, Cassandra, CouchDB a RavenDB jsou dobří kandidáti.

Stejně jako u všech vzorů a technologií, realizovat strategicky a v případě potřeby. Zatímco získávání událostí může poskytovat vyšší výkon a škálovatelnost, přichází na úkor složitosti a křivky učení.

>[!div class="step-by-step"]
>[Předchozí](service-mesh-communication-infrastructure.md)
>[další](relational-vs-nosql-data.md)
