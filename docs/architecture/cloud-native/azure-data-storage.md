---
title: Ukládání dat v Azure
description: Architekt cloudových nativních aplikací .NET pro Azure | Ukládání dat v Azure
ms.date: 06/30/2019
ms.openlocfilehash: ef9a83745b723dce90bc3e48eecbc9690fd386ab
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183628"
---
# <a name="data-storage-in-azure"></a>Ukládání dat v Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak jsme viděli v této příručce, Cloud mění způsob, jakým se aplikace navrhují, nasazují a spravují. Při přesunu do cloudu se kritickou otázkou, jak přesouváte data? Naštěstí cloud Azure nabízí spoustu možností.

Mohli jste jenom zřídit virtuální počítač Azure a nainstalovat svou databázi podle vlastního výběru. Tato služba se nazývá [Infrastruktura jako služba (IaaS)](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas). Tento přístup zjednodušuje přesun místní databáze do cloudu, jak je, ale posune zatížení pro správu virtuálního počítače a databáze.  

Místo toho je lepší volbou plně spravovaná [databáze jako služba (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) . Získáte spoustu integrovaných funkcí, zatímco hostování, údržba a licencování spravuje společnost Microsoft. Azure nabízí různé druhy plně spravovaných možností úložiště dat, z nichž každá má konkrétní výhody. Všechny podporují kapacitu za běhu a model průběžných plateb.

Dál se podíváme na možnosti DBaaS dostupné v Azure. Zjistíte, jak bude Microsoft dál považovat za udržování "otevřené platformy", a nabízí spravovanou podporu pro spoustu Open Source relačních a NoSQL databází a poskytování klíčových příspěvků různým Open-Source základům jako aktivnímu členu.

## <a name="azure-sql-database"></a>Azure SQL Database

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/) je bohatá relační databáze jako služba (DBaaS) pro obecné účely, založená na databázovém stroji Microsoft SQL Server. Je plně spravovaná Microsoftem a je vysoce výkonná, spolehlivá a zabezpečená cloudová databáze. Služba sdílí mnoho funkcí, které najdete v místní verzi SQL Server. 

SQL Database Server a databázi můžete zřídit během několika minut. Když poptávka po vaší aplikaci roste od několik zákazníků po miliony, Azure SQL Database se průběžně škáluje s minimálními prostoji. Můžete dynamicky přidávat nebo odebírat prostředky, včetně výkonu procesoru, paměti, propustnosti v/v a úložiště, které jsou přiděleny vašim databázím.

Obrázek 5-12 ukazuje možnosti nasazení Azure SQL Database.

![Možnosti nasazení Azure SQL](./media/azure-sql-database-deployment-options.png)

**Obrázek 5-12**. Možnosti nasazení Azure SQL

Všimněte si alternativ na předchozím obrázku při nasazení SQL Database:

- [Jediná databáze](https://docs.microsoft.com/azure/sql-database/sql-database-single-database) s vlastní sadou prostředků spravovaných [serverem SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers). Jedna databáze je podobná databázi s [omezením](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases)v místním nasazení SQL Server.

- [Elastický fond](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool) , ve kterém kolekce databází SQL sdílí jeden SQL Database Server za stanovenou cenu. Izolované databáze je možné do elastického fondu přesunout a z něj, a to podle potřeby pro optimalizaci cenového výkonu pro skupinu databází.

- [Spravovaná instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) , ve které je kolekce systémových a uživatelských databází, nabízí téměř 100% kompatibilitu s místními SQL Server. Tato možnost podporuje větší databáze, až 35 TB a je umístěná v [Virtual Network Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pro lepší izolaci.

Azure SQL Database je plně spravovaný [databázový stroj PaaS (Platform as a Service)](https://docs.microsoft.com/azure/sql-database/sql-database-paas) , který zpracovává upgrade, opravy, zálohování a monitorování bez zásahu uživatele. Vždy spustí nejnovější stabilní verzi SQL Server databázový stroj a opravený operační systém a garantuje 99,99% dostupnost. Jedna funkce a [Aktivní geografická replikace](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)umožňuje vytvářet čitelné sekundární databáze ve stejném nebo jiném datovém centru Azure. Po selhání se dá iniciovat převzetí služeb při selhání sekundární databází. V tomto okamžiku se druhá sekundární skupina automaticky připojí k nové primární lokalitě. Až čtyři sekundární repliky jsou podporovány v rámci stejné nebo v různých oblastech a tyto sekundární typy lze také použít pro dotazy přístupu jen pro čtení.

Azure SQL Database obsahuje [integrované funkce monitorování a inteligentního ladění](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index) , které vám pomůžou maximalizovat výkon a snížit provozní náklady. Například funkce [automatického ladění](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning) poskytuje nepřetržité ladění výkonu na základě AI a strojového učení. Služba se učí od vašich spuštěných úloh a může použít doporučení pro vyladění. Čím delší je Azure SQL Database běží s povoleným automatickým laděním, tím lepší je výkon.

[Azure SQL Database bez serveru](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) (k dispozici pro náhled v době psaní této knihy) je výpočetní vrstva pro izolovanou databázi, která se automaticky škáluje podle požadavků na zatížení a účtuje se za množství výpočetní služby za sekundu. Výpočetní vrstva bez serveru taky automaticky pozastaví databáze během neaktivních období, takže se účtují jenom poplatky za úložiště. Automaticky pokračuje při návratu aktivity.

Nakonec je k dispozici nová Azure SQL Database cenová úroveň s [měřítkem](https://azure.microsoft.com/services/sql-database/) . Využívá vysoce škálovatelnou architekturu úložiště a umožňuje, aby se databáze v případě potřeby rostla a nemusela předem zřizovat prostředky úložiště. Výpočetní prostředky a prostředky úložiště můžete škálovat nezávisle a zajistit tak flexibilitu pro optimalizaci výkonu pro jednotlivé úlohy. Azure SQL Database škálování je optimalizované pro zpracování [OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) a úlohy s vysokou propustností s úložištěm až 100 TB.  Díky úlohám náročným na čtení poskytuje škálování na více instancí rychlé škálování tím, že je potřeba zřídit další repliky pro čtení podle potřeby pro přesměrování zatížení pro úlohy čtení. 

Kromě tradičního Microsoft SQL Serverového zásobníku nabízí Azure taky spravované verze několika oblíbených open source databází.

## <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[](https://en.wikipedia.org/wiki/MySQL)MySQL je [Open Source](https://en.wikipedia.org/wiki/Open-source_software) [relační databáze](https://en.wikipedia.org/wiki/Relational_database_management_system). Je součástí [softwarového zásobníku lamp](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) a používá mnoho velkých organizací, včetně Facebooku, Twitteru a YouTube. Edice Community je dostupná zdarma a edice Enterprise vyžaduje zakoupení licence. Produkt byl původně vytvořen v 1995, společnost Sun Microsystems v 2008, kterou získal Oracle v 2010.

[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) je plně spravovaná služba relačních databází připravená pro podnikové prostředí založená na Open Source stroji serveru MySQL. Implementace MySQL Community Edition zahrnuje tyto možnosti PaaS bez dalších poplatků:

- Integrovaná [Vysoká dostupnost](https://docs.microsoft.com/azure/mysql/concepts-high-availability).

- Předvídatelný výkon s využitím celkových cen průběžných [plateb](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers). 

- [Škálování](https://docs.microsoft.com/azure/mysql/concepts-high-availability) podle potřeby během několika sekund.

- Zabezpečené pro ochranu citlivých dat a v pohybu.

- [Automatické zálohování](https://docs.microsoft.com/azure/mysql/concepts-backup) a [obnovení k bodu v čase](https://docs.microsoft.com/azure/mysql/concepts-backup) po dobu až 35 dnů.

- Zabezpečení a dodržování předpisů na podnikové úrovni.

Tyto integrované funkce PaaS jsou důležité pro organizace, které mají v datových centrech stovky databází taktické (nestrategická), ale nemají k dispozici žádné prostředky, které by měly provádět opravy, zálohování, zabezpečení a sledování výkonu. 

Kromě toho může [Služba Azure Data Migration Service](https://azure.microsoft.com/services/database-migration/) migrovat data z více databázových zdrojů do datových platforem Azure s minimálními výpadky. Služba generuje sestavy hodnocení a poskytuje doporučení, která vás provedou změnami potřebnými k provádění migrace, malými i velkými.

Spravovaný [Server Azure MySQL](https://docs.microsoft.com/azure/mysql/concepts-servers) je ústředním bodem pro správu služby. Je to stejný stroj serveru MySQL, který se používá pro místní nasazení. Díky tomu můžete vytvořit izolovanou databázi na jeden server a využívat všechny prostředky nebo vytvořit více databází na jeden server pro sdílení prostředků. Váš tým může dál vyvíjet aplikace pomocí Open source nástrojů a platformy podle vašeho výběru, aniž by se museli učit nové dovednosti nebo spravovat virtuální počítače a infrastrukturu.

## <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Server je dalším oblíbeným Open Source databázovým serverem. V době, kdy si společnost Oracle zakoupila MySQL, vytvořila jako větev MySQL původní vývojáře MySQL. Záměrem je zajistit, aby MariaDB zůstaly open source.

Vzhledem k tomu, že MariaDB je [rozvětvení MySQL](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql), definice dat a tabulek jsou kompatibilní a klientské protokoly, struktury a rozhraní API jsou Close-spojit. Datové konektory MySQL budou fungovat MariaDB bez úprav.

MariaDB má silný následující a používá se v mnoha velkých podnicích. I když Oracle nadále udržuje, vylepšuje a podporuje MySQL, MariaDB je spravováno pomocí MariaDB Foundation, což umožňuje veřejným příspěvkům na produkt a dokumentaci.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) je plně spravovaná databáze jako služba v cloudu Azure. Vychází ze strojového serveru [MariaDB Community Edition](https://mariadb.org/download/) . Může zpracovávat klíčové úlohy s předvídatelným výkonem a dynamickou škálovatelností. Podobně jako u ostatních databázových platforem Azure zahrnuje řadu možností typu platforma jako služba bez dalších poplatků:

- Integrovaná [Vysoká dostupnost](https://docs.microsoft.com/azure/mariadb/concepts-high-availability).

- Předvídatelný výkon s využitím celkových cen průběžných [plateb](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers). 
 
- [Škálování](https://docs.microsoft.com/azure/mariadb/concepts-high-availability) podle potřeby během několika sekund.

- Zabezpečená ochrana citlivých dat v klidovém provozu a v pohybu.

- [Automatické zálohování](https://docs.microsoft.com/azure/mariadb/concepts-backup) a [obnovení k bodu v čase](https://docs.microsoft.com/azure/mariadb/concepts-backup) po dobu až 35 dnů.

- Zabezpečení a dodržování předpisů na podnikové úrovni.

## <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL 

[PostgreSQL](https://www.postgresql.org/) je jiná oblíbená a open source relační databáze s více než 30 lety aktivního vývoje. Je to univerzální systém pro správu relačních databází a objektů. Jeho licence se považují za "svobodně" a produkt je zdarma používat, upravovat a distribuovat v jakékoli podobě. Řada velkých podniků, včetně Apple, Red Hat a Fujitsu, vytvořila produkty s využitím PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) je plně spravovaná služba relačních databází založená na Open Source databázovém stroji Postgres. Může zpracovávat klíčové úlohy s předvídatelným výkonem, zabezpečením, vysokou dostupností a dynamickou škálovatelností. Podporuje několik Open Source platforem a jazyků, mezi které patří C++jazyky Java, Python, Node, C\#a php. Umožňuje [migraci](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) databází PostgreSQL prostřednictvím rozhraní příkazového řádku nebo [služby Azure Data Migration Service](https://azure.microsoft.com/services/database-migration/).

Služba obsahuje [integrované inteligentní](https://docs.microsoft.com/azure/postgresql/concepts-monitoring) funkce, které vycházejí z vašich jedinečných databázových vzorů a nabízí přizpůsobená doporučení a přehledy, které vám pomůžou maximalizovat výkon databáze PostgreSQL. [Rozšířená ochrana před internetovými útoky](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection) monitoruje vaši databázi po hodinách a detekuje potenciální škodlivé aktivity, které vás upozorňují na detekci, abyste se mohli hned zasáhnout.

Azure Database for PostgreSQL je k dispozici jako dvě možnosti nasazení: Jeden server a Citus (škálování na více serverů), dostupné pro náhled v době psaní této knihy

- Možnost nasazení [jediného serveru](https://docs.microsoft.com/azure/postgresql/concepts-servers) je centrálním bodem správy pro více databází. Je to stejný modul PostgreSQL serveru, který je k dispozici pro místní nasazení. Díky tomu můžete vytvořit izolovanou databázi na jeden server, abyste mohli využívat všechny prostředky, nebo vytvořit více databází pro sdílení prostředků. Ceny jsou strukturované podle serveru založeného na jádrech a úložišti.

- [Možnost Citus ()](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) využívá technologii [Citus (data](https://www.citusdata.com/) Technology). Díky horizontálnímu škálování jedné databáze na stovkách uzlů nabízí vysoce výkonné škálování pro zajištění podporuje jiho rychlého výkonu a škálování. Tato možnost umožňuje modulu přizpůsobovat více dat v paměti, paralelizovat dotazy napříč stovkami uzlů a rychleji indexovat data. Funkce škálování na úrovni Standard je kompatibilní s nejnovějšími inovacemi, verzemi a nástroji pro PostgreSQL, takže můžete využívat své stávající PostgreSQLé znalosti.

## <a name="cosmos-db"></a>Databáze Cosmos

Azure Cosmos DB je plně spravovaná globálně distribuovaná databázová služba NoSQL, která je navržená tak, aby poskytovala nízkou latenci, elastickou škálovatelnost, spravovanou konzistenci dat a vysokou dostupnost. V krátké době, pokud vaše aplikace potřebuje zaručit rychlou odezvu na celém světě, pokud je potřeba vždycky online a potřebujete neomezenou a elastickou škálovatelnost propustnosti a úložiště, Cosmos DB je skvělou volbou. Obrázek 5-13 obsahuje podrobný přehled Cosmos DB.

![Přehled Cosmos DB](./media/cosmos-db-overview.png)

**Obrázek 5-13**: Přehled Cosmos DB

Všimněte si, že na obrázku 5-13 je Cosmos DB robustní a vysoce všestranná databázová služba s mnoha integrovanými možnostmi nativního cloudu. V této části se podíváme na tyto.

### <a name="global-support"></a>Globální podpora

Databáze Cosmos můžete globálně distribuovat napříč všemi oblastmi Azure po celém světě, umístit data blízko uživatele, zlepšit dobu odezvy a snížit latenci. Databázi můžete přidat nebo odebrat z oblasti bez pozastavení nebo opětovného nasazení aplikace. Cosmos DB transparentně replikuje data do všech nakonfigurovaných oblastí na pozadí.

Cosmos DB podporuje clustering [aktivní/aktivní](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) na globální úrovni, což vám umožní nakonfigurovat všechny oblasti databáze, aby podporovaly zápis a čtení.

Funkce [vícenásobného hlavního](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master) protokolu v Cosmos DB umožňuje následující funkce:

- Neomezený pružný zápis a škálovatelnost pro čtení.

- 99,999% dostupnost čtení a zápisu všech po celém světě.

- Garantuje čtení a zápisy poskytované za méně než 10 milisekund v 99 percentilu.

Interně Cosmos DB zpracovává replikaci dat mezi oblastmi a zárukami na úrovni konzistence a finančně zálohovanými smlouvami o úrovni služeb.

U Cosmos DB [rozhraní API pro více domovských](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)míst se vaše aplikace může automaticky seznámit s nejbližší oblastí Azure a odesílat do ní požadavky. Nejbližší oblast je identifikována Cosmos DB bez jakýchkoli změn konfigurace. Pokud by byla oblast nedostupná, Cosmos DB podporuje automatické převzetí služeb při selhání a funkce vícenásobné svou žádost automaticky směruje do nejbližší dostupné oblasti.

### <a name="multi-model-support"></a>Podpora více modelů

Cosmos DB je *multi-modelová datová platforma* , která umožňuje interakci s daty pomocí řady podporovaných modelů NoSQL, včetně dokumentů, párů klíč-hodnota, nejrůznějších reprezentace a grafů. Interně jsou data uložena v jednoduchém formátu [struktury](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs) tvořeném primitivními datovými typy, včetně řetězců, logických hodnot a čísel. Pro každý požadavek databázový stroj přeloží data na znázornění modelu, kterou jste vybrali. Můžete si vybrat z vlastního Cosmos DB rozhraní API založeného na SQL nebo kterékoli z [rozhraní API kompatibility](https://www.wikiwand.com/en/Cosmos_DB) zobrazených na obrázku 5-14.

![Poskytovatelé Cosmos DB](./media/cosmos-db-providers.png)

**Obrázek 5-14**: Poskytovatelé Cosmos DB

Všimněte si na obrázku 5-14, jak Cosmos DB podporuje [Table Storage](https://azure.microsoft.com/services/storage/tables/). Jak Cosmos DB, tak [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) sdílet stejný podkladový model tabulek a vystavit mnoho stejných operací s tabulkou. [Cosmos DB rozhraní API pro tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction) ale poskytuje řadu prémiových vylepšení, která nejsou k dispozici v rozhraní API pro Azure Storage. Tyto funkce jsou kontrastní na obrázku 5-15.

![rozhraní API pro tabulky Azure](./media/azure-table-api.png)

**Obrázek 5-15**: rozhraní API pro tabulky Azure

Aplikace napsané pro Azure Table Storage se můžou migrovat na Azure Cosmos DB pomocí rozhraní API pro tabulky bez jakýchkoli změn kódu.

V [brownfield] (https://en.wikipedia.org/wiki/Brownfield_(software_development) scénáře použití mohou vývojové týmy migrovat existující databáze Mongo, Gremlin nebo Cassandra do Cosmos DB s minimálními změnami stávajících dat nebo kódu aplikace. V případě scénářů [bezserverová](https://en.wikipedia.org/wiki/Greenfield_project) mohou vývojové týmy zvolit datový model, který nejlépe splňuje požadavky a předvolby, včetně plně podporovaných možností open source pro platformy MongoDB, Cassandra a Gremlin.

### <a name="consistency-models"></a>Modely konzistence

Dříve v části *relační versus NoSQL* jsme probrali předmět *konzistence dat*, což je termín, který odkazuje na integritu vašich dat. Distribuované databáze, které spoléhají na replikaci při vysoké dostupnosti, nízké latenci nebo obojí, musí mít zásadní kompromis mezi konzistencí čtení, dostupností a latencí.

Většina distribuovaných databází umožňuje vývojářům vybírat ze dvou modelů konzistence: [silná konzistence](https://en.wikipedia.org/wiki/Strong_consistency) a konečná [konzistence](https://en.wikipedia.org/wiki/Eventual_consistency). *Silná konzistence* je Gold Standard pro programovatelnost dat. Zaručuje, že výsledek dotazu vždycky vrátí nejaktuálnější data, a to i v případě, že systém musí nabývat latencí, která čeká na replikaci u všech kopií databáze. Na druhé straně systém nakonfigurovaný pro konečnou *konzistenci* vrátí data okamžitě, i když tato data nejsou nejaktuálnější kopie. Tato možnost umožňuje vyšší dostupnost, větší měřítko a vyšší výkon.

Azure Cosmos DB nabízí spektrum [pěti jasně definovaných modelů konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) znázorněných na obrázku 5-16. Tyto možnosti umožňují provést přesné volby a členitosti s ohledem na dostupnost a výkon na základě potřeb vaší aplikace. Tyto modely jsou dobře definované, intuitivní a jsou založené na smlouvách o úrovni služeb (SLA). 

![Cosmos DB úrovně konzistence](./media/cosmos-db-consistency-levels.png)

**Obrázek 5-16**: Cosmos DB úrovně konzistence

### <a name="partitioning"></a>Dělení

Azure Cosmos DB používá automatické [dělení](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) ke škálování databáze tak, aby splňovala požadavky vaší aplikace na výkon. 

Data můžete spravovat v Cosmos DB dat vytvořením [databází, kontejnerů a položek](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items), které jsou znázorněné na obrázku 5-17.

![Cosmos DB entit](./media/cosmos-db-entities.png)

**Obrázek 5-17**: Hierarchie Cosmos DB entit

Všimněte si, že na obrázku 5-17 můžete začít vytvořením databáze Cosmos DB v rámci účtu Azure. Tato databáze se stal jednotkou správy pro sadu kontejnerů. Kontejner je nezávislá seskupení položek, které se dají vyjádřit jako kolekce, tabulka nebo graf na základě vybraného poskytovatele rozhraní API (popsaného v předchozí části). Položky jsou data, která přidáte do kontejneru a jsou reprezentována jako dokumenty, řádky, uzly nebo okraje. Ve výchozím nastavení se všechny položky, které přidáte do kontejneru, automaticky indexují bez nutnosti explicitní správy indexů nebo schémat.

Chcete-li rozdělit kontejner, položky jsou rozděleny do samostatných dílčích množin nazývaných [logické oddíly](https://docs.microsoft.com/azure/cosmos-db/partition-data). Logické oddíly se vytvářejí na základě hodnoty klíče oddílu, který je spojený s každou položkou v kontejneru. Obrázek 5-18 ukazuje, jak všechny položky v logickém oddílu mají stejnou hodnotu klíče oddílu.

![Cosmos DB mechaniky pro dělení](./media/cosmos-db-partitioning.png)

**Obrázek 5-18**: Cosmos DB mechaniky pro dělení

Všimněte si, že na obrázku 5-18 každá položka zahrnuje klíč oddílu buď City, nebo letiště. Tento klíč oddílu určuje logický oddíl položky. Každý kód města je přiřazen logickému oddílu v kontejneru na levé straně a ty, které mají na kontejneru napravo kód letiště. Kombinování hodnoty klíče oddílu s hodnotou ID položky vytvoří index položky, který položku jednoznačně identifikuje.

Interně Cosmos DB automaticky spravuje umístění [logických oddílů](https://docs.microsoft.com/azure/cosmos-db/partition-data) na [fyzických oddílech](https://docs.microsoft.com/azure/cosmos-db/partition-data) , aby bylo možné efektivně splnit požadavky na škálovatelnost a výkon kontejneru. V rámci zvýšení propustnosti a požadavků na úložiště se Azure Cosmos DB přesune logické oddíly a znovu distribuuje zatížení mezi větším počtem serverů. Tyto operace Redistribuce jsou spravovány Cosmos DB a jsou prováděny bez přerušení nebo výpadků.

## <a name="azure-redis-cache"></a>Azure Redis Cache

Výhody ukládání do mezipaměti pro zlepšení výkonu a škálovatelnosti se dobře rozumí. 

Pro cloudovou nativní aplikaci je běžné umístění pro přidání do mezipaměti uvnitř brány rozhraní API. Brána slouží jako front-end pro všechny příchozí požadavky. Přidáním ukládání do mezipaměti můžete zvýšit výkon a rychlost odezvy vrácením dat uložených v mezipaměti a zabráněním zpátečním cestám do místní databáze nebo služby pro příjem dat. Obrázek 5-19 ukazuje architekturu ukládání do mezipaměti pro nativní cloudovou aplikaci.

![Ukládání do mezipaměti v nativní aplikaci cloudu](./media/caching-in-a-cloud-native-app.png)

**Obrázek 5-19**: Ukládání do mezipaměti v nativní aplikaci cloudu

Běžný vzor mezipaměti je model doplňování [mezipaměti](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). Pro příchozí požadavek nejprve vyhledáte mezipaměť pro odpověď, která je znázorněna v kroku #1 na obrázku 5-19. Pokud se najde, data se vrátí hned. Pokud data v mezipaměti neexistují (označovaná jako [neúspěšný](https://www.techopedia.com/definition/6308/cache-miss)zápis do mezipaměti), načte se z místní databáze nebo služby pro příjem dat (krok #2), zapsaná do mezipaměti pro budoucí požadavky (krok #3) a vrátí se volajícímu. K pravidelnému vyřazení dat uložených v mezipaměti musí být nutná péče, aby systém zůstal konzistentní a přesný.

Všimněte si také na obrázku 5-19, jak mezipaměť není implementována místně v rámci hranic služby, ale místo toho se využívá jako cloudová služba pro zálohování, jak je popsáno v kapitole 1.

[Azure Redis Cache](https://azure.microsoft.com/services/cache/) je služba pro ukládání dat do mezipaměti a službu Zprostředkovatel zasílání zpráv. Poskytuje přístup k datům pro aplikace s vysokou propustností a nízkou latencí. Je plně spravovaný Microsoftem, který je hostovaný v Azure a dostupný pro libovolnou aplikaci v rámci Azure i mimo ni.

Interně se mezipaměť Azure pro Redis zálohuje na open source [serveru Redis](https://redis.io/) a nativně podporuje datové struktury, jako jsou [řetězce](https://redis.io/topics/data-types#strings), [hodnoty hash](https://redis.io/topics/data-types#hashes), [seznamy](https://redis.io/topics/data-types#sets), [sady](https://redis.io/topics/data-types#sets)a [seřazené sady](https://redis.io/topics/data-types#sorted-sets). Pokud vaše aplikace používá Redis, bude fungovat s Azure cache pro Redis.

Mezipaměť Azure pro Redis se dá použít taky jako mezipaměť dat v paměti, distribuovaná nerelační databáze a zprostředkovatel zpráv. Je k dispozici ve třech různých cenových úrovních. Úroveň Premium nabízí mnoho funkcí na podnikové úrovni, jako je clustering, trvalost dat, geografická replikace a zabezpečení a izolace virtuální sítě.

>[!div class="step-by-step"]
>[Předchozí](data-patterns.md)
>[Další](resiliency.md) <!-- Next Chapter -->
