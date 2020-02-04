---
title: LINQ a ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: e24473f68fe5ccd993c5d205660ea8f397b6f797
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980090"
---
# <a name="linq-and-adonet"></a>LINQ a ADO.NET
V současné době mnoho podnikových vývojářů musí používat dva (nebo více) programovacích jazyků: jazyk vysoké úrovně pro obchodní logiku a prezentační vrstvy (například vizuál C# nebo Visual Basic) a dotazovací jazyk pro interakci s databází (například Transact-SQL). To vyžaduje, aby byl vývojář zdatní v několika jazycích, aby byl účinný, a také ve vývojovém prostředí způsobuje neshodu jazyka. Například aplikace, která používá rozhraní API pro přístup k datům pro spuštění dotazu proti databázi, určuje dotaz jako řetězcový literál pomocí uvozovek. Tento řetězec dotazu není čitelný pro kompilátor a není kontrolován pro chyby, jako je například neplatná syntaxe nebo zda sloupce nebo řádky, na které odkazuje, skutečně existují. Neexistují žádné typy parametrů dotazu ani žádná podpora `IntelliSense`, ani to.  
  
 LINQ (Language-Integrated Query) umožňuje vývojářům vytvářet dotazy na základě sad v kódu aplikace, aniž by museli používat samostatný dotazovací jazyk. Můžete napsat dotazy LINQ na různé výčtové zdroje dat (tj. zdroj dat, který implementuje rozhraní <xref:System.Collections.IEnumerable>), jako jsou datové struktury v paměti, dokumenty XML, databáze SQL a objekty <xref:System.Data.DataSet>. I když jsou tyto vyčíslitelné zdroje dat implementovány různými způsoby, všichni zveřejňují stejnou syntaxi a jazykové konstrukce. Vzhledem k tomu, že dotazy mohou být vytvořeny v samotném programovacím jazyce, není nutné používat jiný dotazovací jazyk, který je vložen jako řetězcové literály, které nelze pochopit nebo ověřit kompilátorem. Integrace dotazů do programovacího jazyka také umožňuje programátorům v programu Visual Studio zvýšit produktivitu tím, že poskytuje typ pro dobu kompilace a kontrolu syntaxe a `IntelliSense`. Tyto funkce omezují nutnost ladění dotazů a opravy chyb.  
  
 Přenosu dat z tabulek SQL do objektů v paměti je často zdlouhavé a náchylné k chybám. Zprostředkovatel LINQ implementovaný pomocí LINQ to DataSet a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] převádí zdrojová data na kolekce objektů založené na <xref:System.Collections.IEnumerable>. Programátor vždycky zobrazuje data jako kolekci <xref:System.Collections.IEnumerable> při dotazování a při aktualizaci. Pro zápis dotazů na tyto kolekce je k dispozici plná podpora `IntelliSense`.  
  
 Existují tři samostatné technologie LINQ (ADO.NET Language-Integrated Query): LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]a LINQ to Entities. LINQ to DataSet poskytuje bohatší optimalizované dotazování přes <xref:System.Data.DataSet> a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat se na SQL Server schémat databáze a LINQ to Entities umožňuje dotazování na model EDM (Entity Data Model).  
  
 Následující diagram poskytuje přehled o tom, jak technologie LINQ ADO.NET souvisejí s programovacími jazyky vysoké úrovně a zdroji dat s podporou LINQ.  
  
 ![Přehled LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Další informace o LINQ naleznete v tématu [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Následující části obsahují další informace o LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]a LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET postaven, a je široce používána. LINQ to DataSet umožňuje vývojářům vytvářet bohatší možnosti dotazování do <xref:System.Data.DataSet> pomocí stejného mechanismu formulace dotazů, který je k dispozici pro mnoho dalších zdrojů dat. Další informace najdete v tématu [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] je užitečný nástroj pro vývojáře, kteří nepotřebují mapování na koncepční model. Pomocí [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]můžete použít programovací model LINQ přímo v existujícím schématu databáze. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje vývojářům generovat .NET Framework třídy, které reprezentují data. Namísto mapování na koncepční datový model jsou tyto generované třídy mapovány přímo na tabulky databáze, zobrazení, uložené procedury a uživatelsky definované funkce.  
  
 S [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]můžou vývojáři psát kód přímo proti schématu úložiště pomocí stejného vzoru programování LINQ, jako jsou kolekce v paměti a <xref:System.Data.DataSet>, kromě dalších zdrojů dat, jako je XML. Další informace najdete v tématu [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Většina aplikací je aktuálně napsána na relačních databázích. V určitém okamžiku budou tyto aplikace muset pracovat s daty zastoupenými v relačním formuláři. Schémata databáze nejsou vždy ideální pro sestavování aplikací a koncepční modely aplikace nejsou stejné jako logické modely databází. Model EDM (Entity Data Model) je koncepční datový model, který se dá použít k modelování dat určité domény, aby aplikace mohly pracovat s daty jako objekty. Další informace najdete v tématu [ADO.NET Entity Framework](./ef/index.md) .  
  
 Prostřednictvím model EDM (Entity Data Model) jsou relační data vystavena jako objekty v prostředí .NET. Díky tomu je vrstva objektu ideálním cílem pro podporu LINQ, což vývojářům umožňuje formulovat dotazy z databáze z jazyka používaného k sestavení obchodní logiky. Tato funkce se označuje jako LINQ to Entities. Další informace najdete v tématu [LINQ to Entities](./ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Viz také:

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
