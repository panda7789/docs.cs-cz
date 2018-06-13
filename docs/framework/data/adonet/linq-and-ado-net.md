---
title: LINQ a ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 1385b2d9b49a7615810025141e111b7d7bf71eac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766124"
---
# <a name="linq-and-adonet"></a>LINQ a ADO.NET
V současné době celá řada vývojářů firmy, musíte použít dva (nebo více) programovacích jazyků: vysoké úrovně jazyk pro obchodní logiky a prezentační vrstvy (například Visual C# nebo Visual Basic) a dotazovacího jazyka pro interakci s databází (například [!INCLUDE[tsql](../../../../includes/tsql-md.md)]). To vyžaduje vývojáři být znalosti v několika jazycích účinný a také způsobí, že jazyk neshody ve vývojovém prostředí. Například aplikace, která používá přístup k datům rozhraní API při spuštění dotazu oproti databázi Určuje dotaz jako řetězcový literál pomocí uvozovek. Tento řetězec dotazu je zrušení čitelná kompilátoru a není zaškrtnuto políčko pro chyby, jako je například Neplatná syntaxe nebo jestli skutečně existuje sloupců a řádků, které odkazuje. Neexistuje žádný typ kontroly parametry dotazu ale žádné `IntelliSense` buď podporují.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] umožňuje vývojářům formuláři dotazy založené na sadě z jejich kódu aplikace, aniž byste museli použít samostatné dotazovací jazyk. Můžete napsat [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy pro různé zdroje dat vyčíslitelná (to znamená, zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní), jako jsou například datové struktury v paměti, dokumentů XML, databáze SQL a <xref:System.Data.DataSet> objekty. I když tyto zdroje dat vyčíslitelná jsou implementované v různých způsobů, budou všechny vystavit stejné konstrukce syntaxe a jazyka. Protože dotazy můžete vytvořen v programovacím jazyce sám sebe, nemáte použít jiný dotazovací jazyk, který je vložený jako textové literály, které nelze ověřit pomocí kompilátoru nebo rozumí. Integraci dotazy do programovací jazyk také umožňuje sadě Visual Studio programátorům zajistit vyšší produktivitu tím, že poskytuje typ kompilaci a kontrolu syntaxe a `IntelliSense`. Tyto funkce snížení nároků na ladění dotazu a opravy chyb.  
  
 Přenášení dat z tabulek SQL do objektů v paměti je často zdlouhavé a náchylné k chybě. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Zprostředkovatele implementované [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] převede zdrojová data do <xref:System.Collections.IEnumerable>– na základě kolekcí objektů. Programátorů vždy zobrazení dat jako <xref:System.Collections.IEnumerable> kolekce, když dotazujete i při aktualizaci. Úplné `IntelliSense` podpora je k dispozici pro zápis dotazů vůči těchto kolekcí.  
  
 Existují tři samostatné ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] technologie: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] poskytuje bohatší, optimalizované dotazování přes <xref:System.Data.DataSet> a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje prohledávat přímo schémat databáze systému SQL Server, a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] umožňuje zadat dotaz [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Následující diagram přehledně jak technologie ADO.NET LINQ vztahují k vysoké úrovně programovací jazyky a podporou LINQ datových zdrojů.  
  
 ![Technologie LINQ to ADO.NET přehled](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Obecné informace o funkcích jazyka LINQ najdete v tématu [Úvod do LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e). Informace o použití LINQ ve svých aplikacích najdete v tématu [NOT IN sestavení: Obecné LINQ Průvodce programováním](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049), který obsahuje podrobné informace o tom, jak používat technologie LINQ.  
  
 Následující části obsahují další informace o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je klíčovým prvkem odpojené programování modelu, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] je založená na a se často používá. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje vývojářům vytvářet bohatší možnosti dotazu do <xref:System.Data.DataSet> pomocí stejné mechanismus formulování dotazu, který je k dispozici pro mnoho další datové zdroje. Další informace najdete v tématu [LINQ na DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] je užitečným nástrojem pro vývojáře, kteří nevyžadují mapování pro konceptuální model. Pomocí [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], můžete použít [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programovací model přímo přes existující schéma databáze. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje vývojářům generovat [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy, které představují data. Místo mapování pro konceptuální datový model, tyto generované třídy map přímo do databázové tabulky, zobrazení, uložené procedury a funkce definované uživatelem.  
  
 S [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], mohou vývojáři psát kód přímo pro schéma úložiště používající stejný [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programovací vzor jako kolekce v paměti a <xref:System.Data.DataSet>, kromě jiných zdrojů dat, jako je například XML. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Většinu aplikací se teď zapisují nad relačních databází. V určitém okamžiku tyto aplikace muset pracovat s daty v relačním formátu. Schémata databáze nejsou vždy ideální pro vytváření aplikací a konceptuální modely aplikace nejsou stejná jako logické modely databází. [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Je koncepční datového modelu, který slouží k modelu dat konkrétní domény, takže aplikace mohou spolupracovat s daty jako objekty. V tématu [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) Další informace.  
  
 Prostřednictvím [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], relačních dat je k dispozici jako objekty v prostředí .NET. Díky tomu objekt vrstvy ideální cíl pro [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] podpory, což vývojářům formulovali dotazy na databázi z jazyk používaný k vytvoření obchodní logiku. Tato funkce se označuje jako [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. V tématu [technologie LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
