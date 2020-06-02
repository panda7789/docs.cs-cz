---
title: LINQ a ADO.NET
description: Naučte se, jak vytvořit dotazy založené na nastavení v kódu aplikace pomocí LINQ (Language-Integrated Query) v ADO.NET, aniž byste museli používat samostatný dotazovací jazyk.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: a663d36f1e07c53d20e22d051e38123bd8873f06
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286750"
---
# <a name="linq-and-adonet"></a>LINQ a ADO.NET

V dnešní době mnoho podnikových vývojářů musí používat dva (nebo více) programovacích jazyků: jazyk vysoké úrovně pro obchodní logiku a prezentační vrstvy (například Visual C# nebo Visual Basic) a dotazovací jazyk pro interakci s databází (například Transact-SQL). To vyžaduje, aby byl vývojář zdatní v několika jazycích, aby byl účinný, a také ve vývojovém prostředí způsobuje neshodu jazyka. Například aplikace, která používá rozhraní API pro přístup k datům pro spuštění dotazu proti databázi, určuje dotaz jako řetězcový literál pomocí uvozovek. Tento řetězec dotazu není pro kompilátor k dispozici a není kontrolován pro chyby, jako je například neplatná syntaxe nebo zda sloupce nebo řádky, na které odkazuje, skutečně existují. Neexistuje žádná kontrola parametrů dotazu ani žádná `IntelliSense` Podpora.  
  
 LINQ (Language-Integrated Query) umožňuje vývojářům vytvářet dotazy na základě sad v kódu aplikace, aniž by museli používat samostatný dotazovací jazyk. Dotazy LINQ můžete psát na různé vyčíslitelné zdroje dat (tedy zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní), jako jsou datové struktury v paměti, dokumenty XML, databáze SQL a <xref:System.Data.DataSet> objekty. I když jsou tyto vyčíslitelné zdroje dat implementovány různými způsoby, všichni zveřejňují stejnou syntaxi a jazykové konstrukce. Vzhledem k tomu, že dotazy mohou být vytvořeny v samotném programovacím jazyce, není nutné používat jiný dotazovací jazyk, který je vložen jako řetězcové literály, které nelze pochopit nebo ověřit kompilátorem. Integrace dotazů do programovacího jazyka také umožňuje programátorům v programu Visual Studio zvýšit produktivitu tím, že poskytuje typ pro dobu kompilace a kontrolu syntaxe a `IntelliSense` . Tyto funkce omezují nutnost ladění dotazů a opravy chyb.  
  
 Přenosu dat z tabulek SQL do objektů v paměti je často zdlouhavé a náchylné k chybám. Zprostředkovatel LINQ implementovaný pomocí LINQ to DataSet a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] převádí zdrojové <xref:System.Collections.IEnumerable> kolekce objektů založené na datech. Programátor vždy zobrazuje data jako <xref:System.Collections.IEnumerable> kolekci, při dotazování a při aktualizaci. `IntelliSense`Pro zápis dotazů na tyto kolekce je k dispozici plná podpora.  
  
 Existují tři samostatné technologie LINQ (ADO.NET Language-Integrated Query): LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] a LINQ to Entities. LINQ to DataSet poskytuje bohatší optimalizované dotazy přes <xref:System.Data.DataSet> a [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat se na SQL Server schémat databáze a LINQ to Entities umožňuje dotazovat se na model EDM (Entity Data Model).  
  
 Následující diagram poskytuje přehled o tom, jak technologie LINQ ADO.NET souvisejí s programovacími jazyky vysoké úrovně a zdroji dat s podporou LINQ.  
  
 ![Přehled LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Další informace o LINQ naleznete v tématu [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Následující části obsahují další informace o LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] a LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet>Je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET postaven, a je široce používána. LINQ to DataSet umožňuje vývojářům vytvářet bohatší možnosti dotazování <xref:System.Data.DataSet> pomocí stejného mechanismu formulace dotazů, který je k dispozici pro mnoho dalších zdrojů dat. Další informace najdete v tématu [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]je užitečným nástrojem pro vývojáře, kteří nepotřebují mapování na koncepční model. Pomocí [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] můžete použít programovací model LINQ přímo přes existující schéma databáze. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]umožňuje vývojářům generovat .NET Framework třídy, které reprezentují data. Namísto mapování na koncepční datový model jsou tyto generované třídy mapovány přímo na tabulky databáze, zobrazení, uložené procedury a uživatelsky definované funkce.  
  
 Pomocí [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] nástroje můžou vývojáři psát kód přímo proti schématu úložiště pomocí stejného vzorového programovacího modelu LINQ jako kolekce v paměti a <xref:System.Data.DataSet> kromě dalších zdrojů dat, jako je XML. Další informace najdete v tématu [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Většina aplikací je aktuálně napsána na relačních databázích. V určitém okamžiku budou tyto aplikace muset pracovat s daty zastoupenými v relačním formuláři. Schémata databáze nejsou vždy ideální pro sestavování aplikací a koncepční modely aplikace nejsou stejné jako logické modely databází. Model EDM (Entity Data Model) je koncepční datový model, který se dá použít k modelování dat určité domény, aby aplikace mohly pracovat s daty jako objekty. Další informace najdete v tématu [ADO.NET Entity Framework](./ef/index.md).  
  
 Prostřednictvím model EDM (Entity Data Model) jsou relační data vystavena jako objekty v prostředí .NET. Díky tomu je vrstva objektu ideálním cílem pro podporu LINQ, což vývojářům umožňuje formulovat dotazy z databáze z jazyka používaného k sestavení obchodní logiky. Tato funkce se označuje jako LINQ to Entities. Další informace najdete v tématu [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Viz také

- [LINQ to DataSet](linq-to-dataset.md)
- [Technologie LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [LINQ (Language Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
