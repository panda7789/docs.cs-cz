---
title: Přehled Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 0934afa96a88b48d8af2d613e83ba793e2f75e71
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248594"
---
# <a name="entity-framework-overview"></a>Přehled Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je sada technologií v ADO.NET, která podporuje vývoj softwarových aplikací orientovaných na data. Architekti a vývojáři aplikací orientovaných na data mají struggled potřebnou k dosažení dvou velmi odlišných cílů. Musí modelovat entity, vztahy a logiku obchodních problémů, které řeší, a musí také pracovat s datovými stroji, které se používají k ukládání a načítání dat. Data mohou být rozložená do více systémů úložišť, z nichž každá má vlastní protokoly. i aplikace, které pracují s jediným systémem úložiště, musí vyvážit požadavky systému úložiště na požadavky na zápis efektivního a udržovatelného kódu aplikace.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje vývojářům pracovat s daty ve formě objektů a vlastností specifických pro doménu, jako jsou například zákazníci a zákaznické adresy, aniž by se museli týkat podkladových databázových tabulek a sloupců, kde jsou tato data uložena. . [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]Díky tomu mohou vývojáři pracovat na vyšší úrovni abstrakce, když pracují s daty a mohou vytvářet a spravovat aplikace orientované na data s menším množstvím kódu než v tradičních aplikacích. Vzhledem k tomu, že [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] jesoučást.NETFramework,aplikacemohouběžetnajakémkolipočítači,nakterémjenainstalovaná.NETFrameworkodverze3,5SP1.[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]

## <a name="give-life-to-models"></a>Udělení životnosti modelům
 Dlouhodobě zavazuje chránit a běžný přístup k návrhu při sestavování aplikace nebo služby je rozdělení aplikace nebo služby na tři části: doménový model, logický model a fyzický model. Model domény definuje entity a vztahy v systému, který je právě modelován. Logický model relační databáze normalizuje entity a vztahy na tabulky s omezeními cizího klíče. Fyzický model řeší možnosti konkrétního datového modulu zadáním podrobností úložiště, jako je vytváření oddílů a indexování.

 Fyzický model je vydaný správcem databáze za účelem zlepšení výkonu, ale programátory, kteří píší kód aplikace, jsou primárně omezeni na práci s logickým modelem, a to psaním dotazů SQL a voláním uložených procedur. Doménové modely se obecně používají jako nástroj pro zachytávání a oznamování požadavků aplikace, často jako inertní diagramy, které jsou prohlíženy a popsány v počátečních fázích projektu a pak byly opuštěny. Řada vývojových týmů přeskočí vytvoření koncepčního modelu a začne zadáním tabulek, sloupců a klíčů v relační databázi.

 Dává možnost života modelům tím, že umožňuje vývojářům dotazovat se na entity a vztahy v doménovém modelu (označované jako *koncepční* model v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a přitom se spoléhat na to, že tyto operace přeloží na zdroj dat – [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] konkrétní příkazy. To uvolňuje aplikace od pevně zakódovaných závislostí na konkrétním zdroji dat.

 Při práci s Code First konceptuální model je mapován na model úložiště v kódu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Může odvodit koncepční model založený na typech objektů a dalších konfiguracích, které definujete. Metadata mapování se generují za běhu na základě kombinace způsobu, jakým jste definovali typy domén a další konfigurační informace, které zadáte v kódu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]vygeneruje databázi podle potřeby na základě metadat. Další informace najdete v tématu [Vytvoření a mapování koncepčního modelu](https://go.microsoft.com/fwlink/?LinkID=235382).

 Při práci s nástroji model EDM (Entity Data Model) jsou koncepční model, model úložiště a mapování mezi těmito dvěma vyjádřeny ve schématech založených na jazyce XML a definovány v souborech, které mají odpovídající přípony názvů:

- Konceptuální schéma definicí jazyk (CSDL) definuje koncepční model. CSDL je [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]implementace [model EDM (Entity Data Model)](../entity-data-model.md). Přípona souboru je. csdl.

- Služba SSDL (Schema Definition Language) definuje model úložiště, který se také nazývá logický model. Přípona souboru je. ssdl.

- Služba Mapping Specification Language (MSL) definuje mapování mezi úložištěm a koncepčními modely. Přípona souboru je. MSL.

Model a mapování úložiště se mohou podle potřeby měnit, aniž by vyžadovaly změny koncepčního modelu, datových tříd nebo kódu aplikace. Vzhledem k tomu, že modely úložiště jsou specifické pro konkrétního zprostředkovatele, můžete pracovat s konzistentním koncepčním modelem napříč různými zdroji dat.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Používá tyto modely a mapování souborů k vytváření, čtení, aktualizaci a odstraňování operací s entitami a vztahy v koncepčním modelu s ekvivalentními operacemi ve zdroji dat. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Dokonce podporuje entity mapování v koncepčním modelu s uloženými procedurami ve zdroji dat. Další informace najdete v tématu [specifikace CSDL, SSDL a MSL](./language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Mapování objektů na data
 Objektově orientované programování představuje výzvu pro interakci se systémy ukládání dat. I když organizace tříd často odráží organizaci relačních databázových tabulek, přizpůsobení není ideální. Více normalizovaných tabulek často odpovídá jedné třídě a vztahy mezi třídami jsou často reprezentovány jinak než vztahy mezi tabulkami. Například pro reprezentaci zákazníka pro prodejní objednávku `Order` může třída použít vlastnost, která obsahuje odkaz na instanci `Customer` třídy, zatímco `Order` řádek tabulky v databázi obsahuje sloupec cizího klíče (nebo sadu sloupců). s hodnotou, která odpovídá hodnotě primárního klíče v `Customer` tabulce. Třída může mít vlastnost s názvem `Orders` , která obsahuje `Order` kolekci instancí třídy, zatímco `Customer` tabulka v databázi nemá porovnatelný sloupec. `Customer` [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje vývojářům flexibilitu k tomu, aby představovala relace tímto způsobem, nebo aby přesněji modeloval vztahy, které jsou v databázi reprezentovány.

 Stávající řešení se pokusila přemostění této mezery, což se často označuje jako "Neshoda neshody", a to pouze mapováním objektově orientovaných tříd a vlastností na relační tabulky a sloupce. Místo toho, aby se tento tradiční přístup [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vybral, jsou v logických modelech omezení relačních tabulek, sloupců a cizích klíčů na entity a vztahy v koncepčních modelech. To umožňuje větší flexibilitu při definování objektů a optimalizaci logického modelu. Nástroje model EDM (Entity Data Model) generují rozšiřitelné datové třídy založené na koncepčním modelu. Tyto třídy jsou částečné třídy, které lze rozšířit o další členy, které vývojář přidá. Ve výchozím nastavení třídy, které jsou generovány pro konkrétní koncepční model, jsou odvozeny ze základních tříd, které poskytují služby pro entity vyhodnocování jako objekty a pro sledování a ukládání změn. Vývojáři můžou tyto třídy použít pro práci s entitami a vztahy jako objekty související s přidruženími. Vývojáři mohou také přizpůsobit třídy, které jsou generovány pro koncepční model. Další informace naleznete v tématu [práce s objekty](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Přístup k datům entit a jejich změna

Více než jenom jiné řešení relačního mapování objektů, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] je zásadní postup, který aplikacím umožňuje přístup k datům, která jsou reprezentována jako entity a vztahy v koncepčním modelu, a mění je. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Používá informace v modelu a mapování souborů k převodu dotazů na objekty proti typům entit reprezentovaným v koncepčním modelu do dotazů specifických pro zdroj dat. Výsledky dotazu jsou vyhodnoceny na objekty, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] které spravuje. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Poskytuje následující možnosti pro dotazování koncepčního modelu a návratových objektů:

- LINQ to Entities. Poskytuje podporu LINQ (Language-Integrated Query) pro dotazování typů entit, které jsou definovány v koncepčním modelu. Další informace najdete v tématu [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt SQL nezávisle na úložišti, který pracuje přímo s entitami v koncepčním modelu a který podporuje model EDM (Entity Data Model) konceptů. [!INCLUDE[esql](../../../../../includes/esql-md.md)]se používá s dotazy objektů a dotazy, které jsou spouštěny pomocí poskytovatele EntityClient. Další informace najdete v tématu [přehled Entity SQL](./language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje poskytovatele dat EntityClient. Tento zprostředkovatel spravuje připojení, překládá dotazy entit na dotazy specifické pro zdroj dat a vrací čtečku dat, kterou [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] používá k vyhodnotit dat entit do objektů. Pokud není materializace objektů vyžadováno, může být zprostředkovatel EntityClient použit také jako standardní poskytovatel dat ADO.NET tím, že umožňuje aplikacím provádět [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy a využívat vrácenou čtečku dat jen pro čtení. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).

Následující diagram znázorňuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architekturu pro přístup k datům:

![Diagram architektury Entity Framework](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Nástroje model EDM (Entity Data Model) mohou generovat třídu odvozenou z `System.Data.Objects.ObjectContext` nebo `System.Data.Entity.DbContext` , která představuje kontejner entity v koncepčním modelu. Tento kontext objektu poskytuje zařízení pro sledování změn a správu identit, souběžnosti a vztahů. Tato třída také zpřístupňuje `SaveChanges` metodu, která zapisuje vložení, aktualizace a odstranění do zdroje dat. Podobně jako dotazy jsou tyto změny provedeny buď pomocí příkazů automaticky generovaných systémem, nebo uloženými procedurami, které jsou určeny vývojářem.

## <a name="data-providers"></a>Zprostředkovatelé dat

`EntityClient` Poskytovatel rozšiřuje model poskytovatele ADO.NET přístupem k datům z pojmů koncepčních entit a vztahů. Spouští dotazy, které používají [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)]poskytuje základní dotazovací jazyk, který umožňuje `EntityClient` komunikaci s databází. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje aktualizované zprostředkovatel dat SqlClient podporující kanonické stromy příkazů. Další informace najdete v tématu [SqlClient pro Entity Framework](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Nástroje entity data model

Visual Studio obsahuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nástroje pro mapování a modelování společně s modulem runtime. Další informace najdete v tématu [modelování a mapování](modeling-and-mapping.md).

## <a name="learn-more"></a>Víc se uč

Další informace o najdete v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]těchto tématech:

[Začínáme](getting-started.md) – poskytuje informace o tom, jak rychle začít pracovat pomocí [rychlého](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))startu, který ukazuje, jak vytvořit jednoduchou [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikaci.

[Entity Framework terminologie](terminology.md) – definuje mnohé z podmínek, které jsou představeny model EDM (Entity Data Model) a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a používané v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci.

[Prostředky Entity Framework](resources.md) – obsahuje odkazy na koncepční témata a odkazy na externí témata a zdroje pro vytváření [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikací.

## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](index.md)
