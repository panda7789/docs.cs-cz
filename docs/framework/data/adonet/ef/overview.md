---
title: Přehled Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: e6c96326991c6f883ad670393bb5c2691f8ad29e
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307346"
---
# <a name="entity-framework-overview"></a>Přehled Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je sada technologií ADO.NET, které podporují vývoj softwarových aplikací orientovaných na data. Architektům a vývojářům aplikací, orientovaných na data mají za s potřebou dosáhnout velmi odlišné dva cíle. Musí modelují entit, vztahy a logiky z obchodních problémů, které jsou řešení a musí také pracovat datových modulů, které umožňuje ukládat a načítat data. Data může zahrnovat více úložných systémů, každý s vlastní protokoly dokonce i aplikací, které pracují s jediným úložištěm systému musí zajistit rovnováhu mezi požadavky na systém úložiště podle požadavků zápisu aplikace efektivnější a udržovatelný kód.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje vývojářům pracovat s daty ve formě specifického pro doménu objektů a vlastností, jako je například Zákazníci a adresy zákazníků, bez nutnosti starat podkladové databázové tabulky a sloupce, kde jsou tato data uložena . S [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], když uživatelé s daty a můžete vytvářet a udržovat aplikace orientované na data s méně kódu než v tradičních aplikacích mohou vývojáři pracovat na vyšší úrovni abstrakce. Vzhledem k tomu, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] je součástí rozhraní .NET Framework [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace se můžou spouštět na libovolném počítači, na kterém je nainstalováno rozhraní .NET Framework počínaje verzí 3.5 SP1.

## <a name="give-life-to-models"></a>Životnost Rozdat modelů
 Návrh dlouhodobě a běžné přístup při vytváření aplikace nebo služba je dělení aplikace nebo služby do tří částí: doménový model, modelu logické a fyzické modelu. Doménový model definuje entity a relace v systému, který je právě modelovat. Logický model pro relační databázi normalizuje entity a relace do tabulky s omezeními cizího klíče. Modelem fyzické adresy možnosti modulu konkrétní data tak, že zadáte podrobnosti o úložišti, jako je například vytváření oddílů a indexování.

 Fyzické modelu je kontrast správci databáze ke zlepšení výkonu, ale programátory, kteří vytvářejí kód aplikace, především omezit pracovat se službou logického modelu psaní dotazů SQL a volání uložené procedury. Doménových modelů se obecně používají jako nástroj pro zachytávání a požadavky aplikace, často jako už netečný diagramy, které jsou zobrazit popsané v raných fázích projekt a potom opuštěných komunikaci. Mnoho vývojových týmů vytvářet Koncepční model a začněte tak, že zadáte tabulky, sloupce a klíče v relační databázi.

 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje životnosti k modelům protože vývojářům umožňuje dotazování entit a vztahů v doménovém modelu (volá *koncepční* model [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) zároveň spoléhají na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] přeložit ty operace pro datové zdroje specifické příkazy. Tím se uvolní pevně zakódované závislosti na určitý zdroj dat aplikace.

 Při práci s Code First, konceptuálního modelu je namapována na úložiště modelu v kódu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Lze odvodit Koncepční model založený na typy objektů a další konfigurace, které definujete. Za běhu, které jsou založené na kombinaci jak definované typy domén a další konfigurační informace, které zadáte v kódu je vygenerována metadata mapování. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] na základě metadat generuje databáze podle potřeby. Další informace najdete v tématu [vytváření a mapování koncepční Model](https://go.microsoft.com/fwlink/?LinkID=235382).

 Při práci s nástroje Entity Data Model, vyjádřené ve formátu XML schémata konceptuálního modelu, model úložiště a mapování mezi těmito dvěma a definovaných v souborech, které mají odpovídající název rozšíření:

- Konceptuální schéma definici jazyka (CSDL) definuje konceptuálního modelu. Je CSDL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]provádění [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md). Přípona souboru je .csdl.

- Store schema definition language (SSDL) definuje modelu úložiště, který se označuje taky jako logické modelu. Přípona souboru je ssdl.

- Mapování specification language (MSL) definuje mapování mezi úložištěm a konceptuálních modelů. Přípona souboru je .msl.

Mapování a model úložiště můžete změnit podle potřeby a bez nutnosti změn na konceptuální model, datových tříd nebo kód aplikace. Vzhledem k tomu, že úložiště modely jsou specifické pro zprostředkovatele, můžete v různých zdrojích dat pracovat s konceptuálními modely konzistentní vzhledem k aplikacím.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Na základě těchto modelů a mapování souborů, které chcete vytvořit, číst, aktualizovat a odstranit operací s entitami a relacemi v konceptuálním modelu na ekvivalentní operace ve zdroji dat. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i v konceptuálním modelu na uložené procedury ve zdroji dat podporuje mapování entit. Další informace najdete v tématu [CSDL, SSDL a MSL specifikace](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Map – objekty k datům
 Objektově orientované programování představuje výzvu pro interakci s dat úložných systémů. I když organizace třídy často zrcadlí uspořádání tabulek relační databáze, přizpůsobit není ideální. Více normalizované tabulky často odpovídají jedné třídy a vztahy mezi třídami jsou často reprezentované jinak než jsou reprezentovány relace mezi tabulkami. Například k reprezentaci zákazníka pro prodejní objednávky `Order` použít vlastnost, která obsahuje odkaz na instanci třídy `Customer` třídy, při `Order` řádek tabulky v databázi obsahuje sloupec cizího klíče (nebo sadu sloupců) s hodnotou, která odpovídá hodnoty primárního klíče `Customer` tabulky. A `Customer` třída může mít vlastnost s názvem `Orders` , který obsahuje kolekci instancí `Order` třídy, zatímco `Customer` nemá srovnatelné sloupec tabulky v databázi. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vývojářům poskytuje flexibilitu představují relace tímto způsobem, nebo lépe modelování vztahů, jako jsou reprezentovány v databázi.

 Existující řešení jste se pokusili překonání tohoto rozdílu, která se často nazývá "vzniklé vzájemné napětí nesoulad", pouze mapování objektově orientované třídy a vlastnosti do relační tabulky a sloupce. Namísto využití této tradiční přístup [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapuje relačních tabulek, sloupců a omezení cizího klíče v logických modelů entit a vztahů v konceptuálních modelech. Díky tomu větší flexibilitu v definování objektů a optimalizaci logického modelu. Nástroje modelu Entity Data Model generovat extensible datových tříd na základě koncepčního modelu. Tyto třídy jsou částečné třídy, které je možné rozšířit pomocí další členy, které vývojář přidá. Ve výchozím nastavení třídy, které jsou generovány pro konkrétní konceptuálního modelu odvození ze základních tříd, které poskytují služby pro materializaci entity jako objekty a sledování a ukládají se změny. Vývojáři mohou pomocí těchto tříd pro práci s entitami a relacemi jako objekty související s pomocí přidružení. Vývojáři mohli také upravovat třídy, které jsou generovány pro koncepční model. Další informace najdete v tématu [práce s objekty](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Přístup a změny dat entity

Víc než jenom další řešení objektově relační mapování [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] spočívá v podstatě umožňuje aplikacím získávat přístup a měnit data, která je reprezentována jako entit a vztahů v konceptuálním modelu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Přeložit objekt dotazy na typy entit, které jsou reprezentovány v konceptuálním modelu na dotazy specifická pro zdroj dat na základě informací v modelu a souborů mapování. Výsledky dotazu jsou materializovaného do objektů, které [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] spravuje. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nabízí tyto způsoby pro dotazování Koncepční model a vrátí objekty:

- [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Poskytuje podporu Language-Integrated Query (LINQ) pro dotazování na typy entit, které jsou definované v konceptuálním modelu. Další informace najdete v tématu [technologii LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt SQL, který pracuje přímo s entitami v konceptuálním modelu a koncepty modelu Entity Data Model, který podporuje nezávislý na úložišti. [!INCLUDE[esql](../../../../../includes/esql-md.md)] se používá současně s dotazy objektu a dotazy, které jsou spouštěny pomocí zprostředkovatel EntityClient. Další informace najdete v tématu [přehled Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje zprostředkovatel EntityClient data. Tento zprostředkovatel spravuje připojení, překládá dotazy entity do dotazy specifická pro zdroj dat a vrátí čtecí modul dat, který [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] používá sloučit entity data do objektů. Když materializace objektů není vyžadována, zprostředkovatel EntityClient lze také jako standardní zprostředkovatele dat ADO.NET povolením spouštět [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazuje a využívat čtecí modul vrácený dat jen pro čtení. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

Následující diagram znázorňuje, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architektury pro přístup k datům:

![Diagram architektury entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Nástroje Entity Data Model můžete vygenerovat třídu odvozenou z `System.Data.Objects.ObjectContext` nebo `System.Data.Entity.DbContext` , který představuje kontejner entit v konceptuálním modelu. Tento objekt kontextu poskytuje funkce pro sledování změn a správu identit, souběžnost a vztahy. Tato třída také poskytuje `SaveChanges` metody, která zapisuje operace vložení, aktualizace a odstranění ke zdroji dat. Jako jsou dotazy se změny provedou buď příkazy automaticky generovány v systému nebo uložené procedury, které jsou určeny vývojáře.

## <a name="data-providers"></a>Zprostředkovatelé dat

`EntityClient` Poskytovatele rozšiřuje tím, že přístup k datům z hlediska koncepční entit a vztahů, podle modelu poskytovatele ADO.NET. Provádění dotazů, které používají [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] poskytuje základní dotazovací jazyk umožňující `EntityClient` ke komunikaci s databází. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje aktualizovanou SqlClient pro zprostředkovatele dat, který podporuje kanonické stromy příkazů. Další informace najdete v tématu [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Nástroje modelu entity data

Spolu s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modulu runtime, sady Visual Studio obsahuje nástroje pro modelování a mapování. Další informace najdete v tématu [modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).

## <a name="learn-more"></a>Víc se uč

Další informace o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], naleznete v tématu:

[Začínáme se službou](../../../../../docs/framework/data/adonet/ef/getting-started.md) – poskytuje informace o tom, jak rychle zprovoznit a spuštěná rychle pomocí [rychlý Start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), který ukazuje, jak vytvořit jednoduchou [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.

[Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md) – definuje řadu, která vznikají zavlečením modelu Entity Data Model a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a které se používají v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci.

[Prostředky Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md) – obsahuje odkazy na koncepční témata a obsahuje odkazy na externí témata a materiály týkající se vytváření [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.

## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
