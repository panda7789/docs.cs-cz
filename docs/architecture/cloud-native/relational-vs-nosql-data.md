---
title: Relační vs. NoSQL data
description: Přečtěte si o relačních a NoSQLch datech v cloudových nativních aplikacích
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 5ca40791f6c6a3d04f3a7d7d9d2dbf0f23196f8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794917"
---
# <a name="relational-vs-nosql-data"></a>Relační vs. NoSQL data

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relační a NoSQL jsou dva typy databázových systémů, které se běžně implementují v cloudových nativních aplikacích. Jsou sestavené jinak, ukládají data odlišně a přistupovali k různým. V této části se podíváme na obě. Později v této kapitole se podíváme na nově vydanou databázovou technologii s názvem *NewSQL*.

*Relační databáze* byly převládají na převážnou technologii pro desetiletí. Jsou vyspělé, prověřené a široce implementované. Konkurenční databázové produkty, nástroje a odbornost Abound. Relační databáze poskytují úložiště souvisejících tabulek dat. Tyto tabulky mají pevné schéma, pro správu dat použijte SQL (jazyk SQL (Structured Query Language)) a záruky na KYSELINu podporují.

*Žádné databáze SQL* neodkazují na vysoce výkonná a nerelační úložiště dat. Jsou v Excelu ve vlastnostech snadného použití, škálovatelnosti, odolnosti a dostupnosti. Namísto spojování tabulek normalizovaných dat NoSQL ukládá nestrukturovaná nebo částečně strukturovaná data, často do párů klíč-hodnota nebo dokumentů JSON. Žádné databáze SQL obvykle neposkytují zaručenou KYSELINu nad rámec jediného oddílu databáze. Vysoce výkonné služby, které vyžadují dobu odezvy sub Second NoSQL úložiště dat.

Dopad [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) technologií pro distribuované cloudové systémy nelze přestavovat. Navýšení nových datových technologií v tomto prostoru má přerušená řešení, která se po vás exkluzivně spoléhala na relační databáze.

Databáze NoSQL obsahují několik různých modelů pro přístup k datům a jejich správu, a to z jednotlivých sad na konkrétní případy použití. Obrázek 5-9 představuje čtyři běžné modely.

![Datové modely NoSQL](./media/types-of-nosql-datastores.png)

**Obrázek 5-9**: datové modely pro databáze NoSQL

| Model | Svých |
| :-------- | :-------- |
| Úložiště dokumentů | Data a metadata se ukládají hierarchicky v dokumentech založených na JSON v rámci databáze. |
| Úložiště hodnot klíčů | Nejjednodušším způsobem databáze NoSQL jsou data reprezentována jako kolekce párů klíč-hodnota. |
| Úložiště s nejrůznějšími sloupci | Související data se ukládají jako sada párů s vnořenými klíči a hodnotami v jednom sloupci. |
| Úložiště grafů | Data jsou uložena ve struktuře grafu jako vlastnosti uzlu, Edge a dat. |

## <a name="the-cap-theorem"></a>Věta CAP

Jako způsob, jak porozumět rozdílům mezi těmito typy databází, zvažte limit věta, což je sada zásad použitých pro distribuované systémy, ve kterých je uložený stav. Obrázek 5-10 ukazuje tři vlastnosti ZAKONČENí věta.

![CAP věta](./media/cap-theorem.png)

**Obrázek 5-10**. Věta CAP

Věta uvádí, že distribuované datové systémy budou nabízet kompromis mezi konzistencí, dostupností a tolerancí oddílů. A všechny databáze mohou zaručit pouze *dvě* ze tří vlastností:

- *Shody.* Každý uzel v clusteru odpoví nejnovějšími daty, a to i v případě, že systém musí požadavek blokovat, dokud se všechny repliky neaktualizují. Pokud pro položku, která se v tuto chvíli aktualizuje, použijete dotaz "konzistentní systém", budete čekat na tuto odpověď, dokud se všechny repliky úspěšně neaktualizují. Dostanete ale nejaktuálnější data.

- *Dostupnosti.* Každý uzel vrátí okamžitou odezvu, i když tato odpověď není nejaktuálnější data. Pokud pro položku, která se aktualizuje, vydáte dotaz "dostupný systém", dostanete nejlepší možnou odpověď, kterou může služba poskytnout v daném okamžiku.

- *Tolerance oddílu.* Garantuje, že systém bude i nadále fungovat i v případě, že replikovaný uzel dat selhává nebo ztratí připojení k ostatním replikovaným datovým uzlům.

Relační databáze obvykle poskytují konzistenci a dostupnost, ale ne toleranci oddílů. Obvykle jsou zřízené na jeden server a vertikálně se škálují přidáním dalších prostředků do počítače.

Řada relačních databázových systémů podporuje integrované funkce replikace, ve kterých lze kopie primární databáze vytvořit do jiných sekundárních instancí serveru. Operace zápisu jsou provedeny u primární instance a replikovány do všech sekundárních. Po selhání může primární instance převzít služby při selhání sekundární, aby poskytovala vysokou dostupnost. Sekundární lze také použít k distribuci operací čtení. Zatímco operace zápisu vždy přecházejí na primární repliku, operace čtení se dají směrovat do kterékoli sekundární lokality, aby se snížilo zatížení systému.

Data je také možné horizontálně rozdělit na více uzlů, například pomocí [horizontálního dělení](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Horizontálního dělení významně zvyšuje provozní režii spittingmi daty napříč mnoha částmi, které nemůžou snadno komunikovat. Správa může být náročná a časově náročná. Může to mít vliv na výkon, spojení tabulek a referenční integritu.

Pokud by repliky dat ztratily připojení k síti v clusteru relačních databází s vysokou konzistencí, nebudete moct zapisovat do databáze. Systém by zamítl operaci zápisu, protože nemůže replikovat tuto změnu do jiné repliky dat. Každá replika dat musí být před dokončením transakce aktualizována.

Databáze NoSQL obvykle podporují vysokou dostupnost a odolnost oddílů. Horizontální horizontální navýšení kapacity, často i u komoditních serverů. Tento přístup poskytuje obrovské dostupnosti v rámci i napříč geografickými oblastmi s nižšími náklady. Můžete rozdělit a replikovat data na těchto počítačích nebo uzlech a zajistit tak redundanci a odolnost proti chybám. Nevýhodou je konzistence. Změna dat v jednom uzlu NoSQL může trvat delší dobu, než se rozšíří do jiných uzlů. Obvykle uzel databáze NoSQL poskytne okamžitou odezvu na dotaz, i když data, která jsou uvedena, jsou zastaralá a zatím se neaktualizovala.

Pokud by repliky dat ztratily připojení v clusteru NoSQL s vysokou dostupností, mohli jste do databáze ještě dokončit operaci zápisu. Cluster pro databáze umožní operaci zápisu a aktualizuje všechny repliky dat, jakmile budou k dispozici.

Tento druh výsledku se označuje jako konečná konzistence, což je charakteristické množství distribuovaných datových systémů, kde se nepodporují transakce s KYSELINou. Jedná se o krátké zpoždění mezi aktualizací datové položky a časem potřebným k rozšíření této aktualizace na každý uzel repliky. Za normálních podmínek je prodleva obvykle krátká, ale může se zvýšit, když dojde k problémům. Například k tomu, co se stane, když byste chtěli aktualizovat položku produktu v databázi NoSQL v USA a dotazovat stejnou datovou položku z uzlu repliky v Evropě? Obdržíte předchozí informace o produktu, dokud cluster neaktualizuje Evropský uzel se změnou produktu. Když okamžitě vrátíte výsledek dotazu a nečekáte na aktualizaci všech uzlů repliky, získáte mimořádně velké množství a objem, ale s možností prezentace starších dat.

Vysoká dostupnost a obrovské škálovatelnost jsou často důležitější pro podnikání, než je silná konzistence. Vývojáři můžou implementovat techniky a vzory, jako je Sagas, CQRS, a asynchronní zasílání zpráv, které zajišťují konečnou konzistenci.

> Současné době se musí věnovat pozornost, když conidering omezení CAP věta. Zjistil se nový typ databáze s názvem NewSQL, který rozšiřuje relační databázový stroj tak, aby podporoval jak horizontální škálovatelnost, tak i škálovatelný výkon systémů NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Požadavky na relační a NoSQL systémy

V závislosti na konkrétních požadavcích na data může mikroslužba založená na cloudu implementovat relační úložiště NoSQL nebo obojí.

|  NoSQL úložiště dat zvažte v těchto případech: | Vezměte v úvahu relační databázi v těchto případech: | 
| :-------- | :-------- |
| Máte vysoké objemové úlohy, které vyžadují velké škálování. | Váš objem úloh je konzistentní a vyžaduje střední až velké měřítko. |
| Vaše úlohy nevyžadují záruky KYSELosti. |  Jsou vyžadovány záruky KYSELosti. |
| Vaše data jsou dynamická a často se mění. | Vaše data jsou předvídatelná a vysoce strukturovaná |
| Data je možné vyjádřit bez relací. | Data jsou nejlépe vyjádřená jako poměrná. |  
| Potřebujete rychlé zápisy a bezpečnost zápisu nejsou kritické. | Bezpečnost zápisu je požadavek |  
| Načítání dat je jednoduché a má tendenci být ploché. | Pracujete se složitými dotazy a sestavami.|
| Vaše data vyžadují rozsáhlou geografickou distribuci. | Vaši uživatelé jsou centralizovaná | 
| Vaše aplikace se nasadí do komoditního hardwaru, například s veřejnými cloudy. | Vaše aplikace bude nasazená na rozsáhlý hardware s vysokým konečným použitím | 
|||

V dalších částech prozkoumáme možnosti dostupné v cloudu Azure pro ukládání a správu nativních dat cloudu.

## <a name="database-as-a-service"></a>Databáze jako služba

Začněte tím, že zřídíte virtuální počítač Azure a nainstalujete pro každou službu databázi s volbou. I když máte plnou kontrolu nad prostředím, nebudete mít k dispozici mnoho vestavěných funkcí cloudové platformy. Zodpovídáte také za správu virtuálního počítače a databáze pro každou službu. Tento přístup může být rychle náročný na čas a nákladný.

Místo toho aplikace cloudových nativních aplikací upřednostní datové služby, které jsou vystavené jako [databáze jako služba (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/). Tyto služby jsou plně spravované dodavatelem cloudu a poskytují integrované zabezpečení, škálovatelnost a monitorování. Místo vlastnícího službu ji stačí využít jako [záložní službu](./definition.md#backing-services). Poskytovatel pracuje se škálováním prostředku a nese zodpovědnost za výkon a údržbu.

Je možné je nakonfigurovat napříč zónami a oblastmi dostupnosti cloudu, abyste dosáhli vysoké dostupnosti. Všechny podporují kapacitu za běhu a model průběžných plateb. Azure nabízí různé druhy možností služby Managed data Service, z nichž každá má konkrétní výhody.

Nejprve se podíváme na relační služby DBaaS dostupné v Azure. Uvidíte, že je k dispozici databáze Microsoft nejdůležitější SQL Server a zároveň s několika možnostmi open source. Pak budeme mluvit o službách NoSQL Data Services v Azure.

## <a name="azure-relational-databases"></a>Relační databáze Azure

Pro nativní mikroslužby cloudu, které vyžadují relační data, Azure nabízí čtyři nabídky spravovaných relačních databází jako služby (DBaaS), které jsou uvedené na obrázku 5-11.

![Spravované relační databáze v Azure](./media/azure-managed-databases.png)

**Obrázek 5-11**. Spravované relační databáze dostupné v Azure

Na předchozím obrázku si všimněte, jak každá je umístěna na běžné infrastruktuře DBaaS, která zahrnuje klíčové funkce bez dalších poplatků.

Tyto funkce jsou obzvláště důležité pro organizace, které zřídí velký počet databází, ale mají omezené prostředky pro jejich správu.
Databázi Azure můžete zřídit v řádu minut tak, že vyberete velikost procesorových jader, paměti a základního úložiště. Databázi můžete škálovat průběžně a dynamicky upravovat prostředky s malým až žádným výpadkem.

## <a name="azure-sql-database"></a>Azure SQL Database

Vývojové týmy s odbornými znalostmi v Microsoft SQL Server by měly uvažovat [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Je to plně spravovaná relační databáze jako služba (DBaaS) založená na databázovém stroji Microsoft SQL Server. Služba sdílí mnoho funkcí, které se nacházejí v místní verzi SQL Server a spouští nejnovější stabilní verzi databázového stroje SQL Server.

Pro použití s nativní mikroslužbou cloudu je Azure SQL Database k dispozici se třemi možnostmi nasazení:

- Izolovaná databáze představuje plně spravovaný SQL Database běžící na [Azure SQL Databasem serveru](https://docs.microsoft.com/azure/sql-database/sql-database-servers) v cloudu Azure. Databáze je považována za [*obsaženou*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) , protože nemá žádné závislosti konfigurace na podkladovém databázovém serveru.
  
- [Spravovaná instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) je plně spravovaná instance Microsoft SQL Server databázového stroje, která poskytuje kompatibilitu s téměř 100% a místní SQL Server. Tato možnost podporuje větší databáze, až 35 TB a je umístěná v [Virtual Network Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pro lepší izolaci.

- [Azure SQL Database bez serveru](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) je výpočetní vrstva pro izolovanou databázi, která se automaticky škáluje podle požadavků na zatížení. Účtuje se jenom za využité množství výpočetní služby za sekundu. Služba je vhodná pro úlohy, které mají občasné a nepředvídatelné vzorce použití, prokládány s tečkami nečinnosti. Výpočetní vrstva bez serveru taky automaticky pozastaví databáze během neaktivních období, takže se účtují jenom poplatky za úložiště. Automaticky pokračuje při návratu aktivity.

Kromě tradičního Microsoft SQL Serverového zásobníku nabízí Azure taky spravované verze tří oblíbených open source databází.

## <a name="open-source-databases-in-azure"></a>Open source databáze v Azure

Open Source relační databáze se stávají oblíbenou volbou pro cloudové nativní aplikace. Mnoho podniků jim dává přednost prostřednictvím komerčních databázových produktů, zejména za účelem úspory nákladů. Řada vývojových týmů nabízí flexibilitu, vývoj v komunitě a ekosystém nástrojů a rozšíření. Open-source databáze je možné nasadit napříč několika poskytovateli cloudu, což pomáhá minimalizovat obavy z toho, že je zamčený dodavatel.

Vývojáři můžou snadno hostovat všechny otevřené zdrojové databáze na virtuálním počítači Azure. Při poskytování úplného řízení vám tento přístup vede na zavěšení pro správu, monitorování a údržbu databáze a virtuálního počítače.

Společnost Microsoft ale nadále zavazuje, aby Azure otevřela platformu tím, že nabízí několik oblíbených open source databází jako *plně spravovaných* služeb DBaaS Services.

### <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) je open source relační databáze a pilíř pro aplikace postavené na [softwarovém zásobníku lamp](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Široce se vybralo pro *čtení těžkých* úloh, používá se v mnoha velkých organizacích, včetně Facebooku, Twitteru a YouTube. Edice Community je dostupná zdarma, ale edice Enterprise vyžaduje nákup licence. Produkt byl původně vytvořen v 1995. Sun Microsystems byl zakoupen v 2008. Oracle získal Sun a MySQL v 2010.

[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) je spravovaná relační databázová služba založená na Open Source stroji serveru MySQL. Používá verzi MySQL Community Edition. Server Azure MySQL je bod správy pro službu. Je to stejný stroj serveru MySQL, který se používá pro místní nasazení. Modul může vytvořit izolovanou databázi na jeden server nebo více databází na jeden server, který sdílí prostředky. Můžete dál spravovat data pomocí stejných open source nástrojů, aniž byste se museli učit nové dovednosti nebo spravovat virtuální počítače.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Server je dalším oblíbeným Open Source databázovým serverem. Byla vytvořena jako *rozvětvení* MySQL, když společnost Oracle koupila Sun Microsystems, která vlastní MySQL. Záměrem je zajistit, aby MariaDB zůstaly open source. Protože MariaDB je rozvětvení MySQL, definice dat a tabulek jsou kompatibilní a klientské protokoly, struktury a rozhraní API jsou Close-spojit.

MariaDB má silnou komunitu a používá se v mnoha velkých podnicích. I když Oracle nadále udržuje, vylepšuje a podporuje MySQL, MariaDB Foundation spravuje MariaDB a povoluje veřejné příspěvky na produkt a dokumentaci.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) je plně spravovaná relační databáze jako služba v cloudu Azure. Služba je založená na serverovém stroji MariaDB Community Edition. Může zpracovávat klíčové úlohy s předvídatelným výkonem a dynamickou škálovatelností.

### <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL

[PostgreSQL](https://www.postgresql.org/) je open source relační databáze s více než 30 lety aktivního vývoje. PostgresSQL má silnou pověst pro spolehlivost a integritu dat. Je to bohatě funkční a kompatibilní s SQL a považuje se za více výkonných procesů než MySQL – zejména pro úlohy se složitými dotazy a velkým zápisem. Řada velkých podniků, včetně Apple, Red Hat a Fujitsu, vytvořila produkty s využitím PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) je plně spravovaná služba relačních databází založená na Open Source databázovém stroji Postgres. Služba podporuje spoustu vývojových platforem, C++včetně jazyků Java, Python, Node, C\#a php. K migraci databází PostgreSQL můžete použít nástroj [rozhraní příkazového řádku](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) nebo službu Azure Data Migration Service.

Azure Database for PostgreSQL je k dispozici se dvěma možnostmi nasazení: 

- Možnost nasazení [jednoho serveru](https://docs.microsoft.com/azure/postgresql/concepts-servers) je centrálním bodem správy pro více databází, na které můžete nasadit mnoho databází. Ceny jsou strukturované podle serveru založeného na jádrech a úložišti.

- [Možnost Citus ()](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) využívá technologii Citus (data Technology). Umožňuje vysoký výkon díky *horizontálnímu škálování* izolované databáze napříč stovkami uzlů, aby bylo možné zajistit rychlý výkon a škálování. Tato možnost umožňuje modulu přizpůsobovat více dat v paměti, paralelizovat dotazy napříč stovkami uzlů a rychleji indexovat data. 

## <a name="nosql-data-in-azure"></a>NoSQL data v Azure

Cosmos DB je plně spravovaná globálně distribuovaná služba NoSQL Database v cloudu Azure. Byl přijat mnoha velkými společnostmi po celém světě, včetně Coca-Coly, Skype, ExxonMobilu a svobody vzájemného.

Pokud vaše služby vyžadují rychlou odezvu odkudkoli v celém světě, vysoké dostupnosti nebo elastické škálovatelnosti, Cosmos DB je skvělou volbou. Obrázek 5-12 ukazuje Cosmos DB.

![Přehled Cosmos DB](./media/cosmos-db-overview.png)

**Obrázek 5-12**: Přehled Cosmos DB

Předchozí obrázek představuje mnoho z vestavěných cloudových možností, které jsou k dispozici v Cosmos DB. V této části se podíváme na tyto.

### <a name="global-support"></a>Globální podpora

Nativní aplikace pro Cloud mají často globální cílovou skupinu a vyžadují globální škálování.

Databáze Cosmos můžete distribuovat do různých oblastí nebo po celém světě, umístit data blízko uživatelům, zlepšit dobu odezvy a snížit latenci. Databázi můžete přidat nebo odebrat z oblasti, aniž byste museli pozastavit nebo znovu nasazovat služby. Na pozadí Cosmos DB transparentně replikuje data do každé z nakonfigurovaných oblastí.

Cosmos DB podporuje clustering [aktivní/aktivní](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) na globální úrovni, což vám umožní nakonfigurovat libovolné oblasti databáze tak, aby podporovaly *zápis i čtení*.

Protokol s [více hlavními servery](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) je důležitou funkcí v Cosmos DB, která umožňuje následující funkce:

- Neomezený pružný zápis a škálovatelnost pro čtení.

- 99,999% dostupnost čtení a zápisu všech po celém světě.

- Garantuje čtení a zápisy poskytované za méně než 10 milisekund v 99 percentilu.

U Cosmos DB [rozhraní API pro více domovských](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)míst vaše mikroslužba automaticky ví nejbližší oblast Azure a pošle do ní požadavky. Nejbližší oblast je identifikována Cosmos DB bez jakýchkoli změn konfigurace. Pokud by se oblast stala nedostupnou, funkce vícenásobné připojení bude automaticky směrovat požadavky do nejbližší dostupné oblasti.

### <a name="multi-model-support"></a>Podpora více modelů

Při replatformování aplikací monolitické do nativní architektury cloudu budou vývojové týmy někdy muset migrovat úložiště dat open source NoSQL. Cosmos DB vám může přispět k zachování investic do těchto dataNoSQL úložiště pomocí datové platformy s *více modely* . Obrázek 5-13 ukazuje podporovaná [rozhraní NoSQL Compatibility API](https://www.wikiwand.com/en/Cosmos_DB).

![Poskytovatelé Cosmos DB](./media/cosmos-db-providers.png)

**Obrázek 5-13**: poskytovatelé Cosmos DB

Vývojové týmy můžou migrovat existující databáze Mongo, Gremlin nebo Cassandra do Cosmos DB s minimálními změnami dat nebo kódu. Pro nové aplikace mohou vývojové týmy volit mezi možnostmi Open Source nebo integrovaným modelem rozhraní SQL API.

> Interně Cosmos ukládá data v jednoduchém formátu struktury, který se skládá z primitivních datových typů. Pro každý požadavek databázový stroj přeloží primitivní data na znázornění modelu, který jste vybrali.

Na předchozím obrázku 5-13 Poznamenejte si možnost [rozhraní API pro tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction) . Toto rozhraní API je vývojem Azure Table Storage. Oba sdílejí stejný základní model tabulek, ale Cosmos DB rozhraní API pro tabulky v rozhraní API pro Azure Storage přidává vylepšení Premium, která nejsou k dispozici. Tyto funkce jsou kontrastní na obrázku 5-4.

![rozhraní API pro tabulky Azure](media/azure-table-api.png)

**Obrázek 5-14**: poskytovatelé Azure rozhraní API pro tabulky

Mikroslužby, které využívají službu Azure Table Storage, můžou snadno migrovat do Cosmos DB rozhraní API pro tabulky. Nevyžadují se žádné změny kódu.

### <a name="tunable-consistency"></a>Přizpůsobitelné konzistence

Dříve v části *relační vs. NoSQL* jsme probrali předmět *konzistence dat*. Konzistence dat odkazuje na *integritu* dat. Cloudové nativní služby s distribuovanými daty spoléhají na replikaci a musí učinit zásadní kompromis mezi konzistencí, dostupností a latencí při čtení.

Většina distribuovaných databází umožňuje vývojářům vybírat ze dvou modelů konzistence: silná konzistence a konečná konzistence. *Silná konzistence* je Gold Standard pro programovatelnost dat. Zaručuje, že dotaz bude vždycky vracet nejaktuálnější data, i když systém musí nabývat latencí, která čeká na replikaci na všechny kopie databáze. I když databáze konfigurovaná pro konečnou *konzistenci* vrátí data okamžitě, a to i v případě, že tato data nejsou nejaktuálnější kopie. Druhá možnost umožňuje vyšší dostupnost, větší měřítko a vyšší výkon.

Azure Cosmos DB nabízí pět jasně definovaných [modelů konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) zobrazených na obrázku 5-15.

![Cosmos DB graf konzistence](./media/cosmos-consistency-level-graph.png)

**Obrázek 5-15**: Cosmos DB úrovní konzistence

 Tyto možnosti umožňují provést přesné volby a podrobné kompromisy týkající se konzistence, dostupnosti a výkonu pro vaše data. Obrázek 5-16 popisuje jednotlivé úrovně.

![Cosmos DB úrovně konzistence](./media/cosmos-db-consistency-levels.png)

**Obrázek 5-16**: Cosmos DB popis úrovně konzistence

V článku [Seznámení s 9 kuličkou: Vysvětlené Cosmos dB úrovně konzistence](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)Microsoft Cloud Developer poradce Jeremy Likeness poskytuje skvělé vysvětlení pěti modelů.

### <a name="partitioning"></a>Dělení

Azure Cosmos DB přiděluje automatické [dělení](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) pro škálování databáze, aby splňovaly požadavky na výkon cloudových služeb, které jsou nativní.

Data můžete spravovat v Cosmos DB dat vytvořením databází, kontejnerů a položek.

Kontejnery jsou živé v Cosmos DB databázi a reprezentují nezávislá seskupení položek schématu. Položky jsou data, která přidáte do kontejneru. Jsou reprezentovány jako dokumenty, řádky, uzly nebo hrany. Všechny položky přidané do kontejneru jsou automaticky indexovány.

Chcete-li rozdělit kontejner, položky jsou rozděleny do samostatných dílčích množin nazývaných logické oddíly. Logické oddíly se naplní na základě hodnoty klíče oddílu, který je spojený s každou položkou v kontejneru. Obrázek 5-18 ukazuje dva kontejnery s logickým oddílem na základě hodnoty klíče oddílu.

![Cosmos DB mechaniky pro dělení](./media/cosmos-db-partitioning.png)

**Obrázek 5-18**: mechanismy Cosmos DBho dělení

Všimněte si, že v předchozí ukázce každá položka zahrnuje klíč oddílu buď City, nebo letiště. Klíč určuje logický oddíl položky. Položky s kódem města jsou přiřazeny ke kontejneru vlevo a položky s kódem letiště do kontejneru na pravé straně. Kombinování hodnoty klíče oddílu s hodnotou ID vytvoří index položky, který položku jednoznačně identifikuje.

Interně Cosmos DB automaticky spravuje umístění [logických oddílů](https://docs.microsoft.com/azure/cosmos-db/partition-data) na fyzických oddílech, aby splňovala požadavky na škálovatelnost a výkon kontejneru. Po zvýšení propustnosti aplikací a požadavků na úložiště Azure Cosmos DB redistribuuje logické oddíly mezi větším počtem serverů. Operace Redistribuce se spravují pomocí Cosmos DB a vyvolají se bez přerušení nebo výpadku.

## <a name="newsql-databases"></a>Databáze NewSQL

*NewSQL* je rozvíjející se Databázová technologie, která kombinuje distribuovanou škálovatelnost NOSQL s kyselými zárukami relační databáze. Databáze NewSQL jsou důležité pro obchodní systémy, které musí zpracovávat velké objemy dat napříč distribuovanými prostředími, a to s plnou mezitransakční podporou a dodržováním předpisů v KYSELINě. I když databáze NoSQL může poskytovat obrovské škálovatelnost, nezaručí konzistenci dat. Občasné problémy z nekonzistentních dat můžou nacházet zatížení vývojového týmu. Vývojáři musí pro svůj kód mikroslužeb vytvořit ochranu a spravovat tak problémy způsobené nekonzistentními daty.

Cloud Native Computing Foundation (CNCF) obsahuje několik databázových projektů NewSQL.

| Projekt | Svých |
| :-------- | :-------- |
| Cockroach DB |Kompatibilní s KYSELINou, relační databáze, která se globálně škáluje. Přidání nového uzlu do clusteru a CockroachDB se postará o vyrovnávání dat napříč instancemi a geografickými oblastmi. Vytváří, spravuje a distribuuje repliky k zajištění spolehlivosti. Je to open source a volně dostupný.  |
| TiDB | Open-source databáze, která podporuje úlohy hybridního transakčního a analytického zpracování (HTAP). Je kompatibilní s MySQL a nabízí horizontální škálovatelnost, silnou konzistenci a vysokou dostupnost.  TiDB funguje jako server MySQL. Můžete dál používat existující klientské knihovny MySQL, aniž byste museli v aplikaci provádět rozsáhlé změny kódu. |
| YugabyteDB | Open Source a vysoce výkonná distribuovaná databáze SQL. Podporuje nízkou latenci dotazů, odolnost proti chybám a globální distribuci dat. YugabyteDB je kompatibilní s PostgressSQL a zpracovává RDBMS a škálovatelné úlohy OLTP pro škálování na více instancí. Produkt také podporuje NoSQL a je kompatibilní s Cassandra. |
|Vitess | Vitess je databázové řešení pro nasazování, škálování a správu velkých clusterů instancí MySQL. Dá se spustit ve veřejné nebo privátní architektuře cloudu. Kombinuje a rozšiřuje mnoho důležitých funkcí MySQL a nabízí vertikální i horizontální podporu horizontálního dělení. Pocházelo na YouTube, Vitess obsluhuje veškerý provoz databáze YouTube od 2011. |

Open source projekty na předchozím obrázku jsou k dispozici v rámci Cloud Native Computing Foundation. Tři nabídky jsou úplné databázové produkty, které zahrnují podporu .NET Core. Druhý Vitess je systém clusteringu databáze, který horizontálně škáluje velké clustery instancí MySQL. 

Klíčovým cílem pro databáze NewSQL je nativně pracovat v Kubernetes s využitím odolnosti a škálovatelnosti platformy.

Databáze NewSQL jsou navržené tak, aby se i v dočasných cloudových prostředích, kde se můžou základní virtuální počítače restartovat nebo přeplánovat v momentě. Databáze jsou navržené tak, aby zadržely selhání uzlu bez ztráty dat ani výpadků. CockroachDB může například zachovávat ztrátu počítačů tím, že zachovává tři konzistentní repliky všech dat napříč uzly v clusteru.

Kubernetes používá *konstrukci služeb* , aby klient mohl adresovat skupinu stejných procesů NewSQL databází z jedné položky DNS. Ododdělením instancí databáze od adresy služby, ke které je přidružená, můžeme škálovat bez přerušení stávajících instancí aplikací. Odeslání žádosti do jakékoli služby v daném okamžiku vždy vrátí stejný výsledek.

V tomto scénáři jsou všechny instance databáze stejné. Neexistují žádné primární ani sekundární relace. Techniky, jako je například *replikace* v CockroachDB, umožňují jakémukoli databázovému uzlu zpracovat jakoukoli žádost. Pokud uzel, který obdrží požadavek s vyrovnáváním zatížení, obsahuje data, která potřebuje místně, odpoví okamžitě. V takovém případě se uzel stává bránou a předá požadavek příslušnému uzlu, aby získal správnou odpověď. V perspektivě klienta je každý uzel databáze stejný: zobrazí se jako jediná *logická* databáze se zárukami konzistence v rámci jednoho počítačového systému, i když má spoustu nebo dokonce stovek uzlů, které pracují na pozadí.

Podrobný pohled na NewSQL databáze najdete v článku [pomlčka: čtyři vlastnosti databáze Kubernetes-Native](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) .

## <a name="data-migration-to-the-cloud"></a>Migrace dat do cloudu

Jedna z více časově náročných úkolů migruje data z jedné datové platformy do druhé. [Služba Azure Data Migration](https://azure.microsoft.com/services/database-migration/) může přispět k urychlení tohoto úsilí. Může migrovat data z několika externích databázových zdrojů do datových platforem Azure s minimálními výpadky. Cílové platformy zahrnují následující služby:

- Azure SQL Database
- Azure Database for MySQL
- Azure Database for MariaDB
- Azure Database for PostgreSQL
- CosmosDB
  
Služba poskytuje doporučení, která vás provedou změnami potřebnými ke spuštění migrace, jak malé, tak i velké.

>[!div class="step-by-step"]
>[Předchozí](Database-per-microservice.md)
>[Další](azure-caching.md)
