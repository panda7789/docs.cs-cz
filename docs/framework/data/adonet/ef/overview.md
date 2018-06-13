---
title: Přehled Entity Framework
ms.date: 03/30/2017
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 8b07fb9b80d5d0d13967c807198194b3a2228202
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759891"
---
# <a name="entity-framework-overview"></a>Přehled Entity Framework
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je sada technologií v ADO.NET, které podporují vývoj aplikací orientovaných na data softwaru. Architekty a vývojáře aplikací orientovaných na data jste měli problémy s potřeba dosáhnout dva velmi různé cíle. Se musí modelu entity, vztahy a logiku z obchodních problémů, které jsou v řešení problémů a také musí pracovat s moduly data používá k ukládání a načítání dat. Data může span více úložných systémů, každou s vlastní protokoly; i aplikace, které pracují s systémem jedno úložiště, musíte vyvážit požadavky na úložiště systému podle požadavků zápisu kódu aplikace efektivní a udržovatelný.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje vývojářům pracovat s daty v podobě objektů specifické pro doménu a vlastnosti, jako je například zákazníků a adresy zákazníků, aniž by museli sami se týkají s základní databázových tabulek a sloupců, kde tato data jsou ukládána . Pomocí [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vývojáři mohou využívat na vyšší úrovni abstrakce, když se vypořádat s daty a můžete vytvářet a udržovat aplikace orientované na data s méně kódu než v tradiční aplikace. Protože [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace se dají spustit na libovolném počítači, na kterém [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od verze 3.5 SP1 je nainstalována.  
  
 Následující části v tomto tématu obsahují další podrobnosti o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   [Poskytnutí životnosti modely](#LifeToModels)  
  
-   [Mapování objektů na Data](#MappingObjectsToData)  
  
-   [Přístup k a změna dat Entity](#AccessingData)  
  
-   [Zprostředkovatelé dat](#DataProviders)  
  
-   [Nástroje modelu Entity Data](#Tools)  
  
-   [Více učení](#LearnMore)  
  
<a name="LifeToModels"></a>   
## <a name="giving-life-to-models"></a>Poskytnutí životnosti modely  
 Návrh dlouhodobě a běžné přístup při vytváření aplikace nebo služba je aplikace nebo služby rozdělení na tři části: modelu domény, model pro logické a fyzické modelu. Model domény definuje entity a vztahy v systému, který je modelovaných. Logické model pro relační databázi normalizuje entity a vztahy do tabulky s omezení cizího klíče. Model fyzické adresy možnosti modul konkrétní datové zadáním podrobnosti úložiště, jako je například vytváření oddílů a indexování.  
  
 Fyzické modelu je vylepšení ve správci databází za účelem zlepšení výkonu, ale programátory především psaní kódu aplikace mohou omezit na práci s modelem logické zápis dotazů SQL a volání uložené procedury. Modely domény jsou obvykle používány jako nástroj k zaznamenání a komunikaci požadavky na aplikace, často jako už netečný diagramy, které jsou zobrazit a popsané v počátečních fázích projektu a pak opuštění. Mnoho vývojové týmy přeskočit vytvoření konceptuálního modelu a začněte tím, že zadáte tabulky, sloupce a klíče v relační databázi.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Dává životnosti modely tím, že umožňuje vývojářům dotazu entity a vztahy v modelu domény (volá *koncepční* modelu v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) při spoléhat na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] přeložit ty na datové zdroje specifické příkazy operací. Tím se uvolní pevně zakódované závislosti na určitý zdroj dat aplikace.  
  
 Při práci s Code First, konceptuálního modelu je namapována na modelu úložiště v kódu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Lze odvodit konceptuálního modelu na základě typů objektů a další konfigurace, které definujete. Mapování metadat je generován během běhu založené na kombinaci jak definované typy domény a další informace o konfiguraci, kterou zadáte v kódu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] generuje databáze podle potřeby založené na metadatech. Další informace najdete v tématu [vytvoření a mapování konceptuálního modelu](http://go.microsoft.com/fwlink/?LinkID=235382).  
  
 Při práci s nástroje Entity Data Model, vyjádřené v jazyce XML schémata konceptuální model modelu úložiště a mapování mezi nimi a definované v souborech, které mají odpovídající přípony názvů:  
  
-   Koncepční schéma definition language (CSDL) definuje konceptuálního modelu. Je CSDL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]na implementaci [datového modelu Entity](../../../../../docs/framework/data/adonet/entity-data-model.md). Přípona souboru je .csdl.  
  
-   Store schema definition language (SSDL) definuje modelu úložiště, který se označuje taky jako logické modelu. Přípona souboru je ssdl.  
  
-   Specifikace jazyka mapování (MSL) definuje mapování mezi úložištěm a konceptuálních modelech. Přípona souboru je .msl.  
  
 Mapování a modelu úložiště můžete změnit podle potřeby a bez nutnosti změny konceptuální model, datové třídy nebo kód aplikace. Protože úložiště modely jsou specifické pro zprostředkovatele, můžete v různých zdrojů dat. pracovat se konzistentní konceptuálního modelu.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Používá tyto modelu a mapování soubory vytvořit, číst, aktualizovat a odstranit operace u entity a vztahy v konceptuálním modelu se ekvivalentní operací ve zdroji dat. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i podporuje mapování entity v konceptuálním modelu k uloženým procedurám v datovém zdroji. Další informace najdete v tématu [CSDL, SSDL a specifikace MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).  
  
<a name="MappingObjectsToData"></a>   
## <a name="mapping-objects-to-data"></a>Mapování objektů na Data  
 Objektově orientované programování představuje výzvu pro interakci s dat úložných systémů. I když je organizace třídy často zrcadlí organizace relační databáze tabulek, přizpůsobit není ideální. Více tabulek normalizovaný často odpovídají jedné třídy a vztahy mezi třídami jsou často reprezentované jinak než jsou reprezentované relace mezi tabulkami. Například představují odběratele pro prodejní objednávky `Order` třída může použít vlastnost, která obsahuje odkaz na instanci `Customer` třída, při `Order` řádku tabulky v databázi obsahuje sloupec cizího klíče (nebo sadu sloupců) s hodnotou, která odpovídá hodnotu primárního klíče v `Customer` tabulky. A `Customer` třída může mít vlastnost s názvem `Orders` obsahující kolekci instancí `Order` třída, při `Customer` nemá porovnatelný z hlediska sloupec tabulky v databázi. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje vývojářům možnost představují vztahy tímto způsobem, nebo přesněji model vztahy vyjádřen v databázi.  
  
 Existující řešení jste se pokusili přemostění tohoto rozdílu, který se často označuje "odpor neshoda", pouze mapování objektově orientované třídy a vlastnosti, které chcete relační tabulky a sloupce. Místo provedení tento tradiční přístup, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapuje relační tabulky, sloupce a omezení cizích klíčů v logické modely na entity a vztahy v konceptuálních modelech. To umožňuje větší flexibilitu v definování objektů i optimalizace logického modelu. [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Nástroje vytvořit rozšiřitelné datové třídy, na základě konceptuálního modelu. Tyto třídy jsou částečné třídy, které lze rozšířit s další členy, které přidá vývojář. Ve výchozím nastavení třídy, které jsou generovány pro konkrétní konceptuální model odvozeny od základní třídy, které poskytují služby pro vyhodnocování entity jako objekty a pro sledování a ukládají se změny. Vývojáři mohou pomocí těchto tříd pro práci s entity a vztahy jako objekty spojené přidružení. Vývojářům můžete také upravit třídy, které jsou generovány pro koncepční model. Další informace najdete v tématu [práce s objekty](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
<a name="AccessingData"></a>   
## <a name="accessing-and-changing-entity-data"></a>Přístup k a změna dat Entity  
 Více než jenom další objekt relační mapování řešení, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] je zásadně o povolení aplikací pro přístup a měnit data, která je reprezentována jako entity a vztahy v konceptuálním modelu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Převede objekt dotazy pro typy entit reprezentovanou v konceptuálním modelu do dotazy specifické pro zdroj dat na základě informací v souborech mapování a modelu. Výsledky dotazu jsou materializována do objektů, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] spravuje. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nabízí tyto způsoby pro dotazování Koncepční model a vrátí objekty:  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Poskytuje podporu Language-Integrated Query (LINQ) pro dotazování typy entit, které jsou definované v konceptuálním modelu. Další informace najdete v tématu [technologie LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt nezávislé na úložiště SQL, který pracuje přímo s entity v konceptuálním modelu, které podporují [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] koncepty. [!INCLUDE[esql](../../../../../includes/esql-md.md)] se používá současně s dotazy na objekt a které jsou spouštěny pomocí zprostředkovatel EntityClient. Další informace najdete v tématu [Entity SQL přehled](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje data zprostředkovatel EntityClient. Tento zprostředkovatel spravuje připojení, překládá dotazy entity do dotazy specifické pro zdroj dat a vrátí čtecí modul dat, který [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] používá k vyhodnotit entity data do objektů. Pokud objekt materialization není vyžadováno, zprostředkovatel EntityClient lze také použít jako standardní [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatele dat povolením, spouštět [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy a využívat čtecí modul vrácený dat jen pro čtení. Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Následující diagram znázorňuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architektura pro přístup k datům:  
  
 ![Diagram architektury entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")  
  
 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Nástroje můžete vytvořit třídy odvozené od `System.Data.Objects.ObjectContext` nebo `System.Data.Entity.DbContext` představující kontejneru entit v konceptuálním modelu. Tento objekt kontextu zajišťuje funkce pro sledování změn a správu identit, souběžnosti a vztahy. Tato třída také zpřístupní `SaveChanges` metody, která zapisuje vložení, aktualizace a odstraní ke zdroji dat. Jako jsou dotazy jsou tyto změny buď provedené příkazy, které jsou automaticky generovány v systému nebo uložené procedury, které jsou určené vývojářům.  
  
<a name="DataProviders"></a>   
## <a name="data-providers"></a>Zprostředkovatelé dat  
 `EntityClient` Zprostředkovatele rozšiřuje [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatele modelu podle přístup k datům z hlediska koncepční entity a vztahy. Se provádí dotazy, které používají [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] poskytuje základní dotazovací jazyk, který umožňuje `EntityClient` ke komunikaci s databází. Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje aktualizované SqlClient pro zprostředkovatele dat, která podporuje kanonický strom příkazů. Další informace najdete v tématu [SqlClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).  
  
<a name="Tools"></a>   
## <a name="entity-data-model-tools"></a>Nástroje modelu Entity Data  
 Společně s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modul runtime, [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] zahrnuje mapování a modelování nástroje. Další informace najdete v tématu [modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).  
  
<a name="LearnMore"></a>   
## <a name="learning-more"></a>Více učení  
 Následující témata umožňují další informace o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
 [Začínáme](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 Zadejte informace o tom, jak zprovoznění a rychle používá [rychlý Start](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675), který ukazuje, jak vytvořit jednoduchou [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
 [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)  
 Definuje řadu podmínek, které jsou zavedené službou datového modelu Entity a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a které se používají v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci.  
  
 [Prostředky Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md)  
 Obsahuje odkazy na koncepční témata a odkazy na externí témata a prostředky pro vytvoření [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
