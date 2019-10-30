---
title: Vzorky dat nativní pro cloud
description: Architekt cloudových nativních aplikací .NET pro Azure | Modely nativních dat v cloudu
ms.date: 06/30/2019
ms.openlocfilehash: 0d251f3046fcd3f3a2f5d856a123a35d3f7ecff2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087700"
---
# <a name="cloud-native-data-patterns"></a>Vzorky dat nativní pro cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

I když decentralizovaná data mohou vést k lepšímu výkonu, škálovatelnosti a úsporám nákladů, prezentují i mnoho výzev. Dotazování na data napříč mikroslužbami je složité. Transakce, která zahrnuje mikroslužby, musí být spravovaná programově, protože distribuované transakce nejsou podporované v cloudových nativních aplikacích. Přesunete se z světa *bezprostřední konzistence* na konečnou *konzistenci*.

Tyto výzvy teď probereme.

## <a name="cross-service-queries"></a>Dotazy na více služeb

Jak aplikace dotazuje data, která jsou rozložená napříč mnoha nezávislými mikroslužbami?

Obrázek 5-4 ukazuje tento scénář.

![Dotazování napříč mikroslužbami](./media/cross-service-query.png)

**Obrázek 5-4**. Dotazování napříč mikroslužbami

Všimněte si, jak vidíte na předchozím obrázku mikroslužbu nákupního košíku, která přidá položku do nákupního košíku uživatele. I když úložiště dat nákupního košíku obsahuje košík a tabulku lineItem, neobsahuje data o produktech ani cenách, protože tyto položky se nacházejí v produktech a cenách mikroslužeb. Aby bylo možné přidat položku, potřebuje mikroslužba nákupního košíku data produktu a data o cenách. Jaké jsou možnosti získání údajů o produktu a cenách?

Obrázek 5-5 ukazuje mikroslužbu nákupního košíku, která provádí přímé volání HTTP do katalogu produktů i cenové služby.

![Přímá komunikace http](./media/direct-http-communication.png)

**Obrázek 5-5**. Přímá komunikace HTTP

V kapitole 4 je sice možné implementovat, a proto jsme probrali, jak Přímá volání HTTP napříč mikroslužbami pojednávají systém a nepovažují se za dobrý postup.

Můžeme implementovat mikroslužbu Agregátoru znázorněnou na obrázku 5-6.

![Mikroslužba Agregátoru](./media/aggregator-microservice.png)

**Obrázek 5-6.** Mikroslužba Agregátoru

I když tento přístup zapouzdřuje pracovní postup obchodní operace v rámci jednotlivých mikroslužeb, zvyšuje složitost a pořád má za následek Přímá volání HTTP.

Běžným přístupem ke spouštění dotazů mezi službami se používá [model materializované zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), který je znázorněný na obrázku 5-7.

![Model materializované zobrazení](./media/materialized-view-pattern.png)

**Figure5-7**. Model materializované zobrazení

V tomto modelu přímo umístíte místní tabulku (označovanou jako *model čtení*) do služby nákupního košíku, která obsahuje denormalizovanou kopii dat, která je potřeba od produktových a cenových mikroslužeb. Umístění těchto dat uvnitř nákupního košíku mikroslužba eliminuje nutnost vyvolání nákladných volání mezi službami. S daty, která jsou místní pro službu, můžete zlepšit dobu odezvy a jejich spolehlivost.

S tímto přístupem teď máte v systému duplicitní data. V nativních systémech cloudu se duplicitní data nepovažují za [antipattern](https://en.wikipedia.org/wiki/Anti-pattern) a obvykle se implementují v nativních systémech cloudu. Jeden a jenom jeden systém může být vlastníkem libovolné datové sady a vy budete muset implementovat mechanismus synchronizace pro záznam systému, aby se aktualizovaly všechny přidružené modely čtení, když dojde ke změně podkladových dat.

## <a name="transactional-support"></a>Podpora transakcí

I když dotazy napříč mikroslužbami jsou náročné, implementace transakce napříč mikroslužbami může být složitá. Základní výzvou k udržení konzistence dat napříč zdroji dat, které se nacházejí v různých mikroslužbách, nelze podléhat podstatě. Obrázek 5-8 ukazuje problém.

![Transakce ve vzoru Saga](./media/saga-transaction-operation.png)

**Obrázek 5-8**. Implementace transakce napříč mikroslužbami

Všimněte si, jak na předchozím obrázku pět nezávislých mikroslužeb se účastní transakce distribuovaného *vytvoření objednávky* . Nicméně transakce pro každý z pěti jednotlivých mikroslužeb musí být úspěšná, nebo všechny musí operaci přerušit a vrátit zpět. I když je integrovaná transakční podpora k dispozici v rámci každé mikroslužby, není podpora distribuované transakce napříč všemi pěti službami podporovaná.

Vzhledem k tomu, že je transakční podpora pro tuto operaci zásadní pro zachování konzistence dat v jednotlivých mikroslužbách, je nutné programově sestavit distribuovanou transakci.

Oblíbeným vzorem pro programové přidávání transakcí je [Saga vzor](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/). Je implementováno seskupením místních transakcí společně a sekvenčním vyvoláním každého z nich. Pokud místní transakce dojde k chybě, Saga přeruší operaci a vyvolá sadu [kompenzačních transakcí](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) pro vrácení změn provedených předchozími místními transakcemi. Obrázek 5-9 ukazuje neúspěšnou transakci se vzorem Saga.

![Vrácení zpět ve vzoru Saga](./media/saga-rollback-operation.png)

**Obrázek 5-9**. Vrácení transakce zpět

Všimněte si, jak na předchozím obrázku se operace *GenerateContent* v mikroslužbě hudba nezdařila. Saga vyvolá kompenzační transakce (červeně) k odebrání obsahu, zrušení platby a zrušení objednávky a vrátí data pro každou mikroslužbu zpět do konzistentního stavu.

Saga vzory jsou obvykle choreographed jako série souvisejících událostí nebo Orchestrované jako sada souvisejících příkazů.

## <a name="cqrs-pattern"></a>Vzor CQRS

CQRS nebo [CQRS (Command and Query Responsibility segregation)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)je model architektury, který odděluje operace, které čtou data z těch, které zapisují data. Tento model může přispět k maximalizaci výkonu, škálovatelnosti a zabezpečení.

Při normálních scénářích přístupu k datům implementujete jeden model (objekt entity a úložiště), *který provádí operace čtení i zápisu* dat.

Pokročilejší scénář přístupu k datům ale může využívat samostatné modely a tabulky dat pro čtení a zápisy. Aby bylo možné zvýšit výkon, operace čtení známá jako *dotaz*se může dotazovat na vysoce denormalizovanou reprezentaci dat, aby nedocházelo k nákladným opakovaným spojením tabulek. Vzhledem k tomu, že operace *zápisu* , která se označuje jako *příkaz*, se může aktualizovat proti plně normalizované reprezentaci dat. Pak byste museli implementovat mechanismus, aby obě reprezentace zůstala synchronizovaná. Obvykle při každé změně tabulky pro zápis vyvolá událost, která replikuje úpravu dat do tabulky pro čtení.

Obrázek 5-10 ukazuje implementaci CQRS vzoru.

![Implementace CQRS](./media/cqrs-implementation.png)

**Obrázek 5-10**. Implementace CQRS

Všimněte si, jak na předchozím obrázku jsou implementovány samostatné příkazy a modely dotazů. Každá operace zápisu dat se navíc ukládá do úložiště pro zápis a pak se šíří do úložiště pro čtení. Věnujte velkou pozornost tomu, jak proces šíření funguje na principu konečné [konzistence](https://www.cloudcomputingpatterns.org/eventual_consistency/), zatímco model čtení se nakonec synchronizuje s modelem zápisu, ale v procesu může dojít k prodlevě.

Implementací oddělení máte možnost škálovat čtení a zápisy samostatně. Také je možné, že budete mít větší zabezpečení při operacích zápisu než v souvislosti s čtením.

CQRS vzory se obvykle aplikují na omezené části systému na základě konkrétních potřeb.

## <a name="relational-vs-nosql"></a>Relační vs NoSQL

Dopad [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) technologií nemůžete přestavovat, zejména u distribuovaných systémů nativních pro Cloud. Navýšení nových datových technologií v tomto prostoru má přerušená řešení, která se po vás exkluzivně spoléhala na relační databáze.

Na jedné straně byly relační databáze převládají na více než desetiletí. Jsou vyspělé, prověřené a široce implementované. Konkurenční databázové produkty, odborné znalosti a abounds nástrojů. Relační databáze poskytují úložiště souvisejících tabulek dat. Tyto tabulky mají pevné schéma, pomocí SQL (jazyk SQL (Structured Query Language)) můžete spravovat data a mít k dispozici [kyselinu](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (také známou jako atomická, konzistence, izolace a odolnost).

Žádné databáze SQL na druhé straně odkazují na vysoce výkonná úložiště dat, která nejsou relační. Jsou v Excelu ve vlastnostech snadného použití, škálovatelnosti, odolnosti a dostupnosti. Namísto spojování tabulek normalizovaných dat ukládá NoSQL data, která jsou v dokumentu JSON (bez schématu), obvykle. Nenabízejí záruky na [kyselinu](https://www.geeksforgeeks.org/acid-properties-in-dbms/) .

Způsob, jak pochopit rozdíly mezi těmito typy databází, najdete v [věta Cap](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e), což je sada zásad, které se dají použít pro distribuované systémy, které stav ukládá. Obrázek 5-11 ukazuje tři vlastnosti ZAKONČENí věta.

![CAP věta](./media/cap-theorem.png)

**Obrázek 5-11**. Věta CAP

Věta uvádí, že jakýkoli distribuovaný datový systém bude nabízet kompromis mezi konzistencí, dostupností a tolerancí oddílů a že každá databáze může zaručit pouze dvě ze tří vlastností:

- *Konzistence*: každý uzel v clusteru bude reagovat s nejnovějšími daty, a to i v případě, že vyžaduje blokování požadavku, dokud nebudou všechny repliky správně aktualizovány.

- *Dostupnost*: každý uzel vrátí odpověď v rozumné době, i když tato odpověď není nejaktuálnější data.

- *Tolerance oddílu*: garantuje, že systém bude pokračovat v provozu, pokud uzel selže nebo ztratí spojení s jiným.

Relační databáze vykazují konzistenci a dostupnost, ale ne toleranci oddílů. Rozdělení relační databáze, jako je například horizontálního dělení, je obtížné a může mít vliv na výkon.

Na druhé straně databáze NoSQL obvykle vykazují toleranci oddílu, označovanou jako horizontální škálovatelnost a vysoká dostupnost. Když věta CAP určuje, můžete mít jenom dva ze tří principů a ztratíte vlastnost konzistence.

Databáze NoSQL jsou distribuované a běžně se škálují napříč komoditních serverů. Díky tomu může dojišťovat skvělou dostupnost v rámci i napříč geografickými oblastmi s nižšími náklady. Data je možné rozdělit do oddílů a replikovat na těchto počítačích nebo v uzlech, které zajišťují redundanci a odolnost proti chybám. Nevýhodou je konzistence. Změna dat v jednom uzlu NoSQL může trvat delší dobu, než se rozšíří do jiných uzlů. Obvykle uzel databáze NoSQL poskytne okamžitou odezvu na dotaz, i když data, která prezentují, jsou zastaralá a zatím se neaktualizovala.

Jedná se o konečnou [konzistenci](https://www.cloudcomputingpatterns.org/eventual_consistency/), která je charakteristická pro distribuované datové systémy, kde se nepodporují nepodporované transakce kyseliny. Jedná se o krátké zpoždění mezi aktualizací datové položky a časem potřebným k rozšíření této aktualizace na každý uzel repliky. Pokud aktualizujete položku produktu v NoSQL databázi v USA, ale současně se dotazuje na stejnou datovou položku z uzlu repliky v Evropě, můžete načíst předchozí informace o produktu – dokud se neaktualizuje Evropský uzel o změnu produktu. Je možné, že při zajištění [vysoké konzistence](https://en.wikipedia.org/wiki/Strong_consistency)čeká na aktualizaci všech uzlů repliky, než se vrátí výsledek dotazu, můžete podporovat obrovský objem škálování a provozu, ale s možností prezentace starších dat.

Databáze NoSQL je možné rozdělit do kategorií podle následujících čtyř modelů:

- *Úložiště dokumentů* (MongoDB, CouchDB, Couchbase): data (a odpovídající metadata) se ukládají nevztahně do denormalizovaných dokumentů založených na JSON v rámci databáze.

- *Úložiště klíč/hodnota* (Redis, Riak, memcached): data jsou uložená v jednoduchých dvojicích klíč-hodnota se systémovými operacemi provedenými u jedinečného přístupového klíče, který je namapovaný na hodnotu uživatelských dat.

- *Úložiště* se sjednocenými sloupci (HBA, Cassandra): související data jsou uložená ve sloupcovém formátu jako množina párů s vnořenými klíči a hodnotami v jednom sloupci, kde se data obvykle načítají jako jedna jednotka, aniž by bylo nutné spojit více tabulek dohromady.

- *Úložiště grafů* (NEO4J, Titan): data jsou uložená jako grafická reprezentace v rámci uzlu spolu s hranami, které určují vztah mezi uzly.

Databáze NoSQL můžou být optimalizované tak, aby se zabývat velkými objemy dat, hlavně když jsou data relativně jednoduchá. Vezměte v úvahu databázi NoSQL v těchto případech:

- Vaše úloha vyžaduje velké a vysoké souběžnosti.
- Máte velký počet uživatelů.
- Data je možné vyjádřit jednoduše bez relací.
- Budete potřebovat geograficky distribuovat data.
- Nepotřebujete záruky KYSELosti.
- Bude nasazena do komoditního hardwaru.

Pak vezměte v úvahu relační databázi v těchto případech:

- Vaše úlohy vyžadují střední až velké měřítko.
- Souběžnost není Zásadním problémem.
- Jsou potřeba záruky KYSELosti.
- Data jsou nejlépe vyjádřena jako poměrná.
- Vaše aplikace bude nasazena na rozsáhlý a vysoce koncový hardware.

V dalším kroku se podíváme na úložiště dat v cloudu Azure.

>[!div class="step-by-step"]
>[Předchozí](distributed-data.md)
>[Další](azure-data-storage.md)
