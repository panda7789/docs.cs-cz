---
title: Technologie LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 86c7e9fae270e75d1ba7e9725ded22ea1961311a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911990"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je součástí .NET Framework verze 3,5, která poskytuje infrastrukturu run-time pro správu relačních dat jako objektů.  
  
> [!NOTE]
> Relační data se zobrazí jako kolekce dvourozměrných tabulek (*vztahů* nebo plochých *souborů*), kde společné sloupce vzájemně souvisejí s tabulkami. Aby bylo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] možné efektivně používat, musíte mít známé základní principy relačních databází.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Po spuštění aplikace se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží na SQL dotazy integrované do jazyka v objektovém modelu a pošle je do databáze za účelem provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede je zpět na objekty, se kterými můžete pracovat ve vlastním programovacím jazyce.  
  
 Vývojáři, kteří používají Visual Studio, obvykle používají Návrhář relací objektů, který poskytuje uživatelské rozhraní pro implementaci mnoha funkcí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroje.  
  
 Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , popisuje základní stavební kameny, procesy a techniky, které potřebujete pro sestavování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací. Můžete také vyhledat konkrétní problémy v Microsoft Docs a můžete se zúčastnit [fóra LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), kde můžete diskutovat o složitější témata podrobněji s odborníky. Nakonec [LINQ to SQL: dotaz integrovaný na jazyku .NET pro](https://go.microsoft.com/fwlink/?LinkId=93205) technologii podrobného dokumentu s podrobnostmi o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] relačních datech, který se dokončí s příklady Visual Basic a C# kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Poskytuje zúžený přehled [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spolu s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Poskytuje kroky pro mapování, dotazování, aktualizaci, ladění a podobné úkoly.  
  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Poskytuje referenční informace o několika aspektech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Témata zahrnují mapování typů SQL-CLR, standardní převod operátoru dotazu a další.  
  
 [Ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Obsahuje odkazy na Visual Basic a C# ukázky.  
  
## <a name="related-sections"></a>Související oddíly  
 [LINQ (Language-Integrated Query) –C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Poskytuje přehled technologie LINQ v C#.
 
 [LINQ (Language-Integrated Query) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Poskytuje přehled technologie LINQ v Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro uživatele Visual Basic.  
  
 [LINQ a ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Odkazuje na portál ADO.NET.  
  
 [LINQ to SQL návody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Uvádí seznam návodů, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]které jsou k dispozici pro.  
  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze používané v dokumentaci.  
  
 [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Popisuje, <xref:System.Web.UI.WebControls.LinqDataSource> jak ovládací prvek [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] zpřístupňuje webovým vývojářům prostřednictvím architektury ovládacího prvku zdroje dat ASP.NET.
