---
title: Relační vs. NoSQL data
description: Další informace o relačních datech a noSQL datech v cloudových nativních aplikacích
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 04693e30ba3848f1e51f1c69a75be5f18ead4cf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141416"
---
# <a name="relational-vs-nosql-data"></a>Relační vs. NoSQL data

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relační a NoSQL jsou dva typy databázových systémů běžně implementovaných v cloudových nativních aplikacích. Jsou sestaveny jinak, ukládají data jinak a mají odlišný přístup. V této části se podíváme na obojí. Později v této kapitole se podíváme na vznikající databázovou technologii nazvanou *NewSQL*.

*Relační databáze* jsou převládající technologií po celá desetiletí. Jsou zralé, osvědčené a široce implementované. Konkurenční databázové produkty, nástroje a odborné znalosti. Relační databáze poskytují úložiště souvisejících datových tabulek. Tyto tabulky mají pevné schéma, použití SQL (Strukturovaný dotazovací jazyk) pro správu dat a podporu acid záruky.

*Databáze no-SQL* odkazují na vysoce výkonná nerelační úložiště dat. Vynikají ve své snadné použití, škálovatelnost, odolnost a dostupnost charakteristiky. Namísto spojování tabulek normalizovaných dat noSQL ukládá nestrukturovaná nebo částečně strukturovaná data, často v párech klíč-hodnota nebo v dokumentech JSON. Databáze no-SQL obvykle neposkytují záruky ACID nad rámec jednoho oddílu databáze. Velkoobjemové služby, které vyžadují dobu odezvy sub sekundy, upřednostňují datové obchody NoSQL.

Dopad [noSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) technologií na distribuované systémy nativní pro cloud nelze přeceňovat. Šíření nových datových technologií v tomto prostoru narušilo řešení, která kdysi výhradně spoléhala na relační databáze.

NoSQL databáze obsahují několik různých modelů pro přístup a správu dat, každý vhodný pro konkrétní případy použití. Obrázek 5-9 představuje čtyři běžné modely.

![Datové modely NoSQL](./media/types-of-nosql-datastores.png)

**Obrázek 5-9**: Datové modely pro nosql databáze

| Model | Vlastnosti |
| :-------- | :-------- |
| Úložiště dokumentů | Data a metadata jsou uloženy hierarchicky v dokumentech založených na JSON uvnitř databáze. |
| Úložiště hodnot klíčů | Nejjednodušší databáze NoSQL, data jsou reprezentována jako kolekce párů klíč hodnota. |
| Úložiště se širokými sloupci | Související data jsou uložena jako sada vnořených párů klíč/hodnota v rámci jednoho sloupce. |
| Úložiště grafů | Data jsou uložena ve struktuře grafu jako vlastnosti uzlu, okraje a dat. |

## <a name="the-cap-theorem"></a>Teorém SZP

Jako způsob, jak pochopit rozdíly mezi těmito typy databází, zvažte cap teorém, sadu zásad používaných pro distribuované systémy, které ukládají stav. Obrázek 5-10 znázorňuje tři vlastnosti szp teorémy.

![SZP](./media/cap-theorem.png)

**Obrázek 5-10**. Teorém SZP

Teorem uvádí, že distribuované datové systémy nabídne kompromis mezi konzistence, dostupnost a tolerance oddílu. A, že každá databáze může zaručit pouze *dvě* ze tří vlastností:

- *Konzistence.* Každý uzel v clusteru reaguje s nejnovějšími daty, i v případě, že systém musí blokovat požadavek, dokud se neaktualizují všechny repliky. Pokud dotaz "konzistentní systém" pro položku, která je aktuálně aktualizuje, budete čekat na tuto odpověď, dokud všechny repliky úspěšně aktualizovat. Obdržíte však nejaktuálnější data.

- *Dostupnost.* Každý uzel vrátí okamžitou odpověď, i když tato odpověď není nejnovější data. Pokud dotaz "dostupný systém" pro položku, která se aktualizuje, dostanete nejlepší možnou odpověď služba může poskytnout v tomto okamžiku.

- *Tolerance oddílu.* Zaručuje, že systém bude nadále fungovat i v případě, že replikovaný datový uzel selže nebo ztratí připojení k jiným replikovaných datovým uzlům.

Relační databáze obvykle poskytují konzistenci a dostupnost, ale není tolerance oddílu. Obvykle se zřazují na jeden server a vertikálně škálují přidáním dalších prostředků do počítače.

Mnoho relačních databázových systémů podporuje integrované replikační funkce, kde lze vytvářet kopie primární databáze do jiných instancí sekundárního serveru. Operace zápisu jsou provedeny do primární instance a replikovány do každé sekundární. Při selhání primární instance může převzetí služeb při selhání sekundární poskytnout vysokou dostupnost. Sekundární lze také distribuovat operace čtení. Zatímco operace zápisu vždy jdou proti primární replice, operace čtení mohou být směrovány na některý z sekundárních ke snížení zatížení systému.

Data mohou být také horizontálně rozdělena mezi více uzlů, například s [horizontálním dělením](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Ale sharding dramaticky zvyšuje provozní režii plivání dat přes mnoho kusů, které nelze snadno komunikovat. To může být nákladné a časově náročné řídit. Může mít vliv na výkon, spojení tabulkových spojů a referenční integritu.

Pokud by repliky dat ztratily připojení k síti v "vysoce konzistentním" relačním databázovém clusteru, nebylo by možné do databáze zapisovat. Systém by odmítl operaci zápisu, protože nemůže replikovat tuto změnu do jiné repliky dat. Každá replika dat musí být před dokončením transakce aktualizována.

NoSQL databáze obvykle podporují vysokou dostupnost a toleranci oddílů. Oni horizontální horizontální, často napříč komoditními servery. Tento přístup poskytuje obrovskou dostupnost, a to jak v rámci zeměpisných oblastí, tak napříč zeměpisnými oblastmi, a to za snížené náklady. Rozdělení a replikace dat mezi těmito počítači nebo uzly, poskytující redundanci a odolnost proti chybám. Nevýhodou je konzistence. Změna dat na jednom uzlu NoSQL může nějakou dobu trvat, než se rozšíří do jiných uzlů. Uzel databáze NoSQL obvykle poskytne okamžitou odpověď na dotaz – i v případě, že data, která je zobrazena, jsou zastaralá a ještě nebyla aktualizována.

Pokud by repliky dat ztratily připojení v "vysoce dostupném" databázovém clusteru NoSQL, stále můžete dokončit operaci zápisu do databáze. Databázový cluster by umožnil operaci zápisu a aktualizoval každou repliku dat, jakmile bude k dispozici.

Tento druh výsledku se označuje jako konečná konzistence, což je charakteristika distribuovaných datových systémů, kde nejsou podporovány transakce ACID. Je to krátké zpoždění mezi aktualizací datové položky a časpotřebný k šíření této aktualizace do každého z uzlů repliky. Za normálních podmínek je zpoždění obvykle krátké, ale může se zvýšit, když vzniknou problémy. Co by se například stalo, kdybyste aktualizovali položku produktu v databázi NoSQL ve Spojených státech a dotazovali se na stejnou datovou položku z uzlu repliky v Evropě? Obdrželi byste starší informace o produktu, dokud cluster neaktualizuje evropský uzel se změnou produktu. Tím, že okamžitě vrátí výsledek dotazu a nečeká na všechny uzly repliky aktualizovat, získáte obrovské škálování a objem, ale s možností prezentace starších dat.

Vysoká dostupnost a rozsáhlá škálovatelnost jsou pro firmu často důležitější než silná konzistence. Vývojáři mohou implementovat techniky a vzory, jako jsou Sagas, CQRS a asynchronní zasílání zpráv, aby přijali konečnou konzistenci.

> V dnešní době je třeba dbát na to, aby byla omezena teoreta SZP. Objevil se nový typ databáze, nazvaný NewSQL, který rozšiřuje relační databázový stroj tak, aby podporoval jak horizontální škálovatelnost, tak škálovatelný výkon NoSQL systémů.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Důležité informace o relačních vs. noSQL systémech

Na základě specifických požadavků na data může mikroslužba založená na cloudu implementovat relační úložiště dat NoSQL nebo obojí.

|  Zvažte úložiště dat NoSQL, když: | Relační databázi zvažte v: |
| :-------- | :-------- |
| Máte velké objemové úlohy, které vyžadují rozsáhlé | Objem pracovního vytížení je konzistentní a vyžaduje střední až velké měřítko. |
| Vaše úlohy nevyžadují záruky ACID |  Jsou vyžadovány záruky ACID |
| Vaše data jsou dynamická a často se mění | Vaše data jsou předvídatelná a vysoce strukturovaná |
| Data mohou být vyjádřena bez relací | Data jsou nejlépe vyjádřena relační |  
| Potřebujete rychlé psaní a psát bezpečnost není kritická | Bezpečnost zápisu je požadavek |  
| Načítání dat je jednoduché a má tendenci být ploché | Pracujete se složitými dotazy a sestavami|
| Vaše data vyžadují široké geografické rozložení | Vaši uživatelé jsou centralizovanější |
| Vaše aplikace bude nasazena na komoditní hardware, například s veřejnými cloudy. | Vaše aplikace bude nasazena na velký, špičkový hardware |
|||

V dalších částech se podíváme na možnosti dostupné v cloudu Azure pro ukládání a správu vašich nativních dat v cloudu.

## <a name="database-as-a-service"></a>Databáze jako služba

Chcete-li začít, můžete zřídit virtuální počítač Azure a nainstalovat databázi volby pro každou službu. I když byste měli plnou kontrolu nad prostředím, zřekli byste se mnoha vestavěných funkcí cloudové platformy. Budete také zodpovědní za správu virtuálního počítače a databáze pro každou službu. Tento přístup by se mohl rychle stát časově náročným a nákladným.

Místo toho cloud nativní aplikace upřednostňují datové služby vystavené jako [databáze jako služba (DBaaS).](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) Tyto služby, plně spravované dodavatelem cloudu, poskytují integrované zabezpečení, škálovatelnost a monitorování. Místo toho, abyste službu vlastnili, jednoduše ji spotřebováváte jako [záložní službu](./definition.md#backing-services). Poskytovatel provozuje zdroj ve velkém měřítku a nese odpovědnost za výkon a údržbu.

Lze je nakonfigurovat napříč oblastmi dostupnosti cloudu a oblastmi, aby bylo dosaženo vysoké dostupnosti. Všechny podporují kapacitu just-in-time a model s průběžným platbou. Azure nabízí různé druhy možností spravované datové služby, z nichž každá má konkrétní výhody.

Nejprve se podíváme na relační služby DBaaS dostupné v Azure. Uvidíte, že vlajková loď společnosti Microsoft SQL Server databáze je k dispozici spolu s několika open-source možnosti. Pak budeme hovořit o datových službách NoSQL v Azure.

## <a name="azure-relational-databases"></a>Relační databáze Azure

Pro mikroslužby nativní pro cloud, které vyžadují relační data, Azure nabízí čtyři spravované relační databáze jako služby (DBaaS), jak je znázorněno na obrázku 5-11.

![Spravované relační databáze v Azure](./media/azure-managed-databases.png)

**Obrázek 5-11**. Spravované relační databáze dostupné v Azure

Na předchozím obrázku si všimněte, jak každý sedí na společné infrastruktuře DBaaS, která nabízí klíčové funkce bez dalších nákladů.

Tyto funkce jsou důležité zejména pro organizace, které zřčují velký počet databází, ale mají omezené prostředky pro jejich správu.
Databázi Azure můžete zřídit během několika minut výběrem množství procesorových jader, paměti a základního úložiště. Databázi můžete škálovat průběžně a dynamicky upravovat prostředky s malými až žádnými prostoji.

## <a name="azure-sql-database"></a>Databáze SQL Azure

Vývojové týmy s odbornými znalostmi v Microsoft SQL Serveru by měly zvážit [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Jedná se o plně spravovanou relační databázi jako službu (DBaaS) založenou na databázovém stroji serveru Microsoft SQL Server. Služba sdílí mnoho funkcí v místní verzi SQL Serveru a spouští nejnovější stabilní verzi databázového stroje SQL Server.

Pro použití s mikroslužbou nativní pro cloud je Azure SQL Database dostupná se třemi možnostmi nasazení:

- Jedna databáze představuje plně spravovanou databázi SQL spuštěnou na [serveru Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers) v cloudu Azure. Databáze je považována za [*obsaženou,*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) protože nemá žádné závislosti konfigurace na podkladovém databázovém serveru.
  
- [Spravovaná instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) je plně spravovaná instance databázového stroje Microsoft SQL Server, která poskytuje téměř 100% kompatibilitu s místním SQL Serverem. Tato možnost podporuje větší databáze s kapacitou až 35 TB a je umístěna ve [virtuální síti Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pro lepší izolaci.

- [Azure SQL Database bez serveru](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) je výpočetní vrstva pro jednu databázi, která se automaticky škáluje na základě poptávky po pracovním vytížení. Účtuje pouze za množství výpočetních prostředků použitých za sekundu. Služba je vhodná pro úlohy s přerušovanými, nepředvídatelnými vzory využití, proloženými obdobími nečinnosti. Výpočetní úroveň bez serveru také automaticky pozastaví databáze během neaktivních období, takže se účtují pouze poplatky za úložiště. Automaticky obnoví, když se vrátí aktivita.

Kromě tradičního zásobníku Microsoft SQL Server azure také obsahuje spravované verze tří oblíbených open source databází.

## <a name="open-source-databases-in-azure"></a>Open source databáze v Azure

Relační databáze s otevřeným zdrojovým kódem se staly oblíbenou volbou pro aplikace nativní pro cloud. Mnoho podniků je upřednostňuje před komerčními databázovými produkty, zejména pro úspory nákladů. Mnoho vývojových týmů se těší své flexibilitě, komunitně podporovanému rozvoji a ekosystému nástrojů a rozšíření. Open source databáze lze nasadit napříč více poskytovateli cloudu, což pomáhá minimalizovat obavy z uzamčení dodavatele.

Vývojáři můžou snadno sami hostovat jakoukoli otevřenou databázi na virtuálním počítači Azure. Při poskytování úplné kontroly, tento přístup vás staví na háku pro správu, monitorování a údržbu databáze a virtuálního počítači.

Microsoft však pokračuje ve svém závazku zachovat Azure "otevřenou platformu" tím, že nabízí několik populárních open source databází jako *plně spravované* služby DBaaS.

### <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) je open-source relační databáze a pilíř pro aplikace postavené na [zásobníku softwaru LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Široce vybraný pro *čtení těžkých* pracovních zátěží, je používán mnoha velkými organizacemi, včetně Facebooku, Twitteru a YouTube. Komunitní edice je k dispozici zdarma, zatímco edice Enterprise vyžaduje zakoupení licence. Produkt byl původně vytvořen v roce 1995 a v roce 2008 jej koupila společnost Sun Microsystems. Společnost Oracle získala v roce 2010 společnosti Sun a MySQL.

[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) je spravovaná relační databázová služba založená na modulu MySQL Server s otevřeným zdrojovým kódem. Používá edici MySQL Community. Server Azure MySQL je bod správy služby. Je to stejný server MySQL modul používaný pro místní nasazení. Modul můžete vytvořit jednu databázi na server nebo více databází na server, které sdílejí prostředky. Můžete pokračovat ve správě dat pomocí stejných open source nástrojů, aniž byste se museli učit nové dovednosti nebo spravovat virtuální počítače.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Server je další populární open-source databázový server. To bylo vytvořeno jako *vidlič na* MySQL, když Oracle koupil Sun Microsystems, který vlastnil MySQL. Záměrem bylo zajistit, aby MariaDB zůstala open-source. Vzhledem k tomu, že MariaDB je vidložkou MySQL, definice dat a tabulek jsou kompatibilní a klientské protokoly, struktury a rozhraní API jsou úzce propojeny.

MariaDB má silnou komunitu a je používán mnoha velkými podniky. Zatímco společnost Oracle nadále udržuje, vylepšuje a podporuje MySQL, nadace MariaDB spravuje MariaDB a umožňuje veřejné příspěvky k produktu a dokumentaci.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) je plně spravovaná relační databáze jako služba v cloudu Azure. Služba je založena na komunitním modulu mariodb. Dokáže zpracovat kritické úlohy s předvídatelným výkonem a dynamickou škálovatelností.

### <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL

[PostgreSQL](https://www.postgresql.org/) je open-source relační databáze s více než 30 lety aktivního vývoje. PostgresSQL má silnou pověst spolehlivosti a integrity dat. Je to funkce bohaté, kompatibilní s SQL a považovány za výkonnější než MySQL - zejména pro úlohy se složitými dotazy a těžkými zápisy. Mnoho velkých podniků, včetně Apple, Red Hat a Fujitsu, vytvořilo produkty pomocí PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) je plně spravovaná relační databázová služba založená na databázovém stroji Postgres s otevřeným zdrojovým kódem. Služba podporuje mnoho vývojových platforem, včetně C++, Java, Python, Node, C\#a PHP. Databáze PostgreSQL můžete do něj migrovat pomocí nástroje [rozhraní příkazového řádku](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) nebo služby Azure Data Migration Service.

Azure Database for PostgreSQL je k dispozici se dvěma možnostmi nasazení:

- Možnost nasazení [jednoho serveru](https://docs.microsoft.com/azure/postgresql/concepts-servers) je centrálním bodem správy pro více databází, do kterých můžete nasadit mnoho databází. Ceny jsou strukturovány pro server na základě jader a úložiště.

- Možnost [Hyperscale (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) je poháněna technologií Citus Data. Umožňuje vysoký výkon *horizontálním škálováním* jedné databáze napříč stovkami uzlů, aby poskytoval rychlý výkon a škálování. Tato možnost umožňuje modulu, aby se vešly více dat do paměti, paralelizovat dotazy napříč stovkami uzlů a indexovat data rychleji.

## <a name="nosql-data-in-azure"></a>Data NoSQL v Azure

Cosmos DB je plně spravovaná globálně distribuovaná databázová služba NoSQL v cloudu Azure. To bylo přijato mnoha velkých společností po celém světě, včetně Coca-Cola, Skype, ExxonMobil, a Liberty Mutual.

Pokud vaše služby vyžadují rychlou odezvu z libovolného místa na světě, vysokou dostupnost nebo elastickou škálovatelnost, Cosmos DB je skvělou volbou. Obrázek 5-12 ukazuje Cosmos DB.

![Přehled Cosmos DB](./media/cosmos-db-overview.png)

**Obrázek 5-12**: Přehled cosmos DB

Předchozí obrázek představuje mnoho integrovaných cloudových nativních funkcí, které jsou k dispozici v Cosmos DB. V této části se na ně podíváme blíže.

### <a name="global-support"></a>Globální podpora

Cloudové nativní aplikace mají často globální publikum a vyžadují globální škálování.

Databáze Cosmos můžete distribuovat napříč oblastmi nebo po celém světě, umísťovat data blízko uživatelů, zlepšovat dobu odezvy a snižovat latenci. Databázi můžete přidat nebo odebrat z oblasti, aniž byste pozastavili nebo znovu nasazovali služby. Na pozadí Cosmos DB transparentně replikuje data do každé z nakonfigurovaných oblastí.

Cosmos DB podporuje [aktivní/aktivní](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) clustering na globální úrovni, což umožňuje nakonfigurovat libovolnou oblast databáze tak, aby *podporovala zápisy i čtení*.

Protokol [Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) je důležitou funkcí v cosmos db, která umožňuje následující funkce:

- Neomezená elastická škálovatelnost zápisu a čtení.

- 99.999% dostupnost čtení a zápisu po celém světě.

- Zaručené čtení a zápisy podávané v méně než 10 milisekund v percentilu 99.

S Cosmos DB [Multi-Homing API](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), vaše mikroslužba je automaticky vědomi nejbližší oblasti Azure a odesílá požadavky na něj. Nejbližší oblast je identifikováncosmos DB bez jakékoli změny konfigurace. Pokud oblast přestane být k dispozici, funkce Multi-Homing automaticky směruje požadavky na nejbližší nejbližší dostupnou oblast.

### <a name="multi-model-support"></a>Podpora více modelů

Při replatforming monolitické aplikace na cloud nativní architekturu, vývojové týmy někdy muset migrovat open-source, NoSQL úložiště dat. Cosmos DB vám může pomoci zachovat vaše investice do těchto datových úložišť NoSQL s *vícemodelovou* datovou platformou. Obrázek 5-13 znázorňuje podporovaná [úložiště API kompatibility NoSQL](https://www.wikiwand.com/en/Cosmos_DB).

![Zprostředkovatelé Cosmos DB](./media/cosmos-db-providers.png)

**Obrázek 5-13**: Zprostředkovatelé Cosmos DB

Vývojové týmy mohou migrovat existující databáze Mongo, Gremlin nebo Cassandra do Cosmos DB s minimálními změnami dat nebo kódu. U nových aplikací si vývojové týmy můžou vybrat mezi možnostmi open source nebo integrovaným modelem rozhraní SQL API.

> Interně Cosmos ukládá data v jednoduchém formátu struktury tvořeném primitivními datovými typy. Pro každý požadavek databázový stroj převede primitivní data do reprezentace modelu, kterou jste vybrali.

Na předchozím obrázku 5-13 si poznamenejte možnost [Rozhraní API tabulky.](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Toto rozhraní API je vývoj Azure Table Storage. Oba sdílejí stejný základní model tabulky, ale rozhraní COSMOS DB Table API přidává vylepšení premium, která nejsou k dispozici v rozhraní AZURE Storage API. Tyto funkce jsou na obrázku 5-4 kontrastovány.

![Azure Table API](media/azure-table-api.png)

**Obrázek 5-14**: Zprostředkovatelé rozhraní API tabulky Azure

Mikroslužeb, které spotřebovávají úložiště Azure Table, můžou snadno migrovat do rozhraní COSMOS DB Table API. Nejsou vyžadovány žádné změny kódu.

### <a name="tunable-consistency"></a>Laditelná konzistence

Dříve v *relační vs. nosql* sekci jsme diskutovali o předmětu *konzistence dat*. Konzistence dat se vztahuje k *integritě* vašich dat. Cloudové nativní služby s distribuovanými daty spoléhají na replikaci a musí vytvořit zásadní kompromis mezi konzistencí čtení, dostupností a latencí.

Většina distribuovaných databází umožňuje vývojářům vybrat si mezi dvěma modely konzistence: silnou konzistenci a konečnou konzistenci. *Silná konzistence* je zlatým standardem programovatelnosti dat. Zaručuje, že dotaz bude vždy vracet nejnovější data – i v případě, že systém musí vynaložit latence čekání na aktualizaci replikovat ve všech kopiích databáze. Zatímco databáze nakonfigurovaná pro *konečnou konzistenci* vrátí data okamžitě, i když tato data nejsou nejaktuálnější kopií. Druhá možnost umožňuje vyšší dostupnost, větší škálování a vyšší výkon.

Azure Cosmos DB nabízí pět dobře definovaných [modelů konzistence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) uvedených na obrázku 5-15.

![Graf konzistence Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Obrázek 5-15**: Úrovně konzistence Cosmos DB

 Tyto možnosti umožňují provádět přesné volby a podrobné kompromisy pro konzistenci, dostupnost a výkon dat. Obrázek 5-16 popisuje každou úroveň.

![Úrovně konzistence Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Obrázek 5-16**: Popis úrovně konzistence cosmos db

V článku [Získání za 9-Ball: Cosmos DB úrovně konzistence vysvětlil](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness poskytuje vynikající vysvětlení pěti modelů.

### <a name="partitioning"></a>Dělení

Azure Cosmos DB zahrnuje automatické [dělení škálovat](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) databázi tak, aby vyhovovala potřebám výkonu vašich cloudových nativních služeb.

Data v datech Cosmos DB můžete spravovat vytvořením databází, kontejnerů a položek.

Kontejnery žijí v databázi Cosmos DB a představují seskupování položek bez schématu. Položky jsou data, která přidáte do kontejneru. Jsou reprezentovány jako dokumenty, řádky, uzly nebo hrany. Všechny položky přidané do kontejneru jsou automaticky indexovány.

Chcete-li rozdělit kontejner, položky jsou rozděleny do různých podmnožiny s názvem logické oddíly. Logické oddíly jsou naplněny na základě hodnoty klíče oddílu, který je přidružen ke každé položce v kontejneru. Obrázek 5-18 ukazuje dva kontejnery každý s logickým oddílem na základě hodnoty klíče oddílu.

![Mechanika dělení Cosmos DB](./media/cosmos-db-partitioning.png)

**Obrázek 5-18**: Mechanika dělení Cosmos DB

Na předchozím obrázku si všimněte, jak každá položka obsahuje klíč k oddílu "město" nebo "letiště". Klíč určuje logický oddíl položky. Položky s kódem města jsou přiřazeny kontejneru vlevo a položky s kódem letiště kontejneru vpravo. Kombinace hodnoty klíče oddílu s hodnotou ID vytvoří index položky, který jednoznačně identifikuje položku.

Interně Cosmos DB automaticky spravuje umístění [logických oddílů](https://docs.microsoft.com/azure/cosmos-db/partition-data) na fyzické oddíly k uspokojení škálovatelnosti a výkonu potřeb kontejneru. Jak se zvyšují požadavky na propustnost aplikací a úložiště, Azure Cosmos DB redistribuuje logické oddíly napříč větším počtem serverů. Redistribuční operace jsou spravovány cosmos DB a vyvolány bez přerušení nebo výpadků.

## <a name="newsql-databases"></a>NewSQL databáze

*NewSQL* je nově vznikající databázová technologie, která kombinuje distribuovanou škálovatelnost NoSQL se zárukami ACID relační databáze. NewSQL databáze jsou důležité pro obchodní systémy, které musí zpracovávat velké objemy dat, napříč distribuovanými prostředími, s plnou transakční podporou a dodržováním ACID. Zatímco databáze NoSQL může poskytovat masivní škálovatelnost, nezaručuje konzistenci dat. Občasné problémy z nekonzistentních dat mohou zatížit vývojový tým. Vývojáři musí vytvořit bezpečnostní opatření do svého kódu mikroslužeb pro správu problémů způsobených nekonzistentní data.

Cloud Native Computing Foundation (CNCF) obsahuje několik databázových projektů NewSQL.

| Project | Vlastnosti |
| :-------- | :-------- |
| Šváb DB |Acid kompatibilní, relační databáze, která se škáluje globálně. Přidejte nový uzel do clusteru a RoachDb se postará o vyvážení dat mezi instancemi a zeměpisnými oblastmi. Vytváří, spravuje a distribuuje repliky pro zajištění spolehlivosti. Je to open source a volně k dispozici.  |
| TiDB | Open source databáze, která podporuje hybridní transakční a analytické zpracování (HTAP) úlohy. Je kompatibilní s MySQL a nabízí horizontální škálovatelnost, silnou konzistenci a vysokou dostupnost.  TiDB se chová jako server MySQL. Můžete pokračovat v používání existujících klientských knihoven MySQL, aniž byste museli vyžadovat rozsáhlé změny kódu vaší aplikace. |
| JugabyteDB | Open source, vysoce výkonná, distribuovaná databáze SQL. Podporuje nízkou latenci dotazu, odolnost proti selhání a globální distribuci dat. YugabyteDB je kompatibilní s PostgressSQL a zpracovává horizontální navýšení úlohy RDBMS a oltp v internetovém měřítku. Produkt také podporuje NoSQL a je kompatibilní s Cassandra. |
|Vitess (Rak.) | Vitess je databázové řešení pro nasazování, škálování a správu velkých clusterů instancí MySQL. Může běžet ve veřejné nebo privátní cloudové architektuře. Kombinuje a rozšiřuje mnoho důležitých funkcí MySQL a funkce vertikální i horizontální horizontální podporu. Společnost Vitess, která vznikla na YouTube, slouží od roku 2011 veškerému databázovému provozu YouTube . |

Open source projekty na předchozím obrázku jsou k dispozici od Cloud Native Computing Foundation. Tři z nabídek jsou úplné databázové produkty, které zahrnují podporu .NET Core. Druhý, Vitess, je databázový clustering systém, který horizontálně škáluje velké clustery instancí MySQL.

Klíčovým cílem návrhu pro databáze NewSQL je pracovat nativně v Kubernetes, s využitím odolnosti a škálovatelnosti platformy.

Databáze NewSQL jsou navrženy tak, aby prosperovaly v dočasných cloudových prostředích, kde lze základní virtuální počítače restartovat nebo přeplánovat v okamžiku. Databáze jsou navrženy tak, aby přežily selhání uzlu bez ztráty dat ani výpadků. RoachDB, například, je schopen přežít ztrátu stroje udržováním tří konzistentnírepliky všech dat přes uzly v clusteru.

Kubernetes používá *konstrukci Services,* která umožňuje klientovi adresovat skupinu identických procesů newsql databází z jedné položky DNS. Oddělením instance databáze od adresy služby, ke které je přidružena, můžeme škálovat bez narušení existujících instancí aplikace. Odeslání požadavku na jakoukoli službu v daném okamžiku vždy přinese stejný výsledek.

V tomto scénáři jsou všechny instance databáze stejné. Neexistují žádné primární nebo sekundární vztahy. Techniky, jako *je konsensus replikace* nalézt v RoachRoachDB umožňují jakýkoli uzel databáze pro zpracování jakékoli žádosti. Pokud uzel, který obdrží požadavek s vyrovnáváním zatížení, obsahuje data, která potřebuje místně, okamžitě odpoví. Pokud tomu tak není, uzel se stane bránou a předá požadavek do příslušných uzlů získat správnou odpověď. Z pohledu klienta je každý uzel databáze stejný: Zobrazují se jako jedna *logická* databáze se zárukami konzistence systému s jedním počítačem, přestože mají desítky nebo dokonce stovky uzlů, které pracují na pozadí.

Podrobný přehled o mechanice za databázemi NewSQL najdete v článku [DASH: Four Properties of Kubernetes-Native Databases.](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

## <a name="data-migration-to-the-cloud"></a>Migrace dat do cloudu

Jedním z časově náročnějších úkolů je migrace dat z jedné datové platformy na jinou. [Služba migrace dat Azure](https://azure.microsoft.com/services/database-migration/) může pomoci urychlit takové úsilí. Může migrovat data z několika externích databázových zdrojů do datových platforem Azure s minimálními prostoji. Cílové platformy zahrnují následující služby:

- Databáze SQL Azure
- Azure Database for MySQL
- Azure Database for MariaDB
- Azure Database for PostgreSQL
- CosmosDB
  
Služba poskytuje doporučení, která vás provedou změnami potřebnými k provedení migrace, malé i velké.

>[!div class="step-by-step"]
>[Předchozí](Database-per-microservice.md)
>[další](azure-caching.md)
