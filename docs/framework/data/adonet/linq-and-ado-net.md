---
title: LINQ a ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 312eb4b1c0512ca1244daec5bcda3ed864c3646d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878334"
---
# <a name="linq-and-adonet"></a>LINQ a ADO.NET
V současné době celá řada vývojářů firmy musí používat dva (nebo více) programovacích jazyků: jazyka vysoké úrovně pro obchodní logiku a prezentační vrstvy (jako je Visual C# nebo Visual Basic) a dotazovací jazyk pro interakci s databází (například [!INCLUDE[tsql](../../../../includes/tsql-md.md)]). To vyžaduje vývojář bude zdatní v několika jazycích, aby byl Efektivní a zároveň způsobí, že jazyk neshody ve vývojovém prostředí. Aplikace, která používá data přístup k rozhraní API při spuštění dotazu proti databázi například určuje dotaz jako řetězcový literál s použitím uvozovek. Tento řetězec dotazu bez číst kompilátoru a nepovolenou chyby, jako je například neplatnou syntaxi nebo zda skutečně existují sloupce nebo řádky, na které odkazuje. Neexistuje žádný typ kontroly parametrů dotazu a ne `IntelliSense` buď podporují.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] umožňuje vývojářům tvoří dotazy založené na sadě v jejich kódu aplikaci bez nutnosti použít samostatný dotazovací jazyk. Můžete napsat [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy na různých zdrojů dat vyčíslitelné (to znamená, že zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní), jako jsou datové struktury v paměti, XML dokumenty, databáze SQL a <xref:System.Data.DataSet> objekty. I když tyto zdroje dat vyčíslitelné jsou implementované různé způsoby, všechny zveřejňovaly konstrukce stejné syntaxe a jazyk. Kvůli dotazy mohou být v programovacím jazyce, není nutné používat jiné dotazovací jazyk, který je vložený jako řetězcové literály, které nelze chápat nebo ověřit pomocí kompilátoru. Integrace dotazy v programovacím jazyce také umožňuje programátorům sady Visual Studio vyšší produktivity díky typu v době kompilace a kontroly syntaxe a `IntelliSense`. Tyto funkce tak snížit potřeba ladění dotazů v odhalování a opravování chyb.  
  
 Přenos dat z tabulek SQL do objektů v paměti je často zdlouhavé a náchylné k chybě. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Poskytovatele implementované [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] převede zdrojová data do <xref:System.Collections.IEnumerable>– na základě kolekcí objektů. Programátor vždy zobrazí data jako <xref:System.Collections.IEnumerable> kolekce, jak při dotazování a při aktualizaci. Úplné `IntelliSense` podpora se poskytuje pro psaní dotazů vůči těchto kolekcí.  
  
 Existují tři samostatné ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] technologie: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] poskytuje širší, optimalizované dotazování <xref:System.Data.DataSet> a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat schémata databáze systému SQL Server, a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] umožňuje dotazování [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Následující obrázek poskytuje základní informace o tom, jak technologie ADO.NET, LINQ souvisí vysoké úrovně programovacích jazyků a zdroje dat LINQ povolena.  
  
 ![Technologie LINQ to ADO.NET přehled](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Další informace o dotazech technologie LINQ, naleznete v tématu [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Následující části obsahují další informace o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je klíčovým prvkem odpojené programovací model, který je založený na ADO.NET a velmi často používá. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje vývojářům vytvářet bohatších možností dotazování <xref:System.Data.DataSet> pomocí stejný mechanismus možností formulování dotazu, který je k dispozici pro mnoha dalším datovým zdrojům. Další informace najdete v tématu [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] je užitečný nástroj pro vývojáře, kteří nevyžadují žádné mapování pro koncepční model. S použitím [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], můžete použít [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programovací model přímo přes existující schéma databáze. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje vývojářům pro generování tříd rozhraní .NET Framework, jež reprezentují data. Místo mapování koncepční datový model, tyto vygenerované třídy mapují přímo na databázových tabulek, zobrazení, uložených procedur a uživatelem definované funkce.  
  
 S [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], vývojářům psát kód přímo proti schématu úložiště pomocí stejných [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programovací model jako kolekce v paměti a <xref:System.Data.DataSet>, kromě jiných zdrojů dat, jako je například XML. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Většina aplikací jsou aktuálně zapsaných nad rámec relačních databází. V určitém okamžiku tyto aplikace potřebovat pro interakci s daty reprezentovány ve formě relační. Databázová schémata nejsou vždy ideální pro vytváření aplikací a konceptuálních modelů aplikace nejsou stejné jako logických modelů z databází. [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Je koncepční datový model, který slouží k modelování dat v určité doméně tak, aby aplikace můžete pracovat s daty jako objekty. Zobrazit [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) Další informace.  
  
 Až [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], je přístupný relačních dat jako objektů v prostředí .NET. Tím je objekt vrstvy ideální cíl pro [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] podporu umožňující vývojářům formulovali dotazy na databázi z jazyk používaný k vytváření obchodní logiku. Tato schopnost je známá jako [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Zobrazit [technologii LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) Další informace.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [LINQ (Language Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
