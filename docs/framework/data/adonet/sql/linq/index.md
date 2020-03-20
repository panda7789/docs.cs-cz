---
title: Technologie LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174313"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je součástí rozhraní .NET Framework verze 3.5, která poskytuje infrastrukturu za běhu pro správu relačních dat jako objektů.  
  
> [!NOTE]
> Relační data se zobrazí jako kolekce dvourozměrných tabulek *(relací* nebo *plochých souborů),* kde společné sloupce vzájemně propojí tabulky. Chcete-li efektivně používat, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musíte mít určitou znalost základních principů relačních databází.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aplikaci je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede do SQL jazykově integrované dotazy v objektovém modelu a odešle je do databáze pro spuštění. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede je zpět na objekty, které můžete pracovat s ve vlastním programovacím jazyce.  
  
 Vývojáři používající visual studio obvykle používají objekt relační návrháře, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]poskytuje uživatelské rozhraní pro implementaci mnoho funkcí .  
  
 Dokumentace, která je součástí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] této verze popisuje základní stavební bloky, procesy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a techniky, které potřebujete pro vytváření aplikací. Můžete také vyhledat konkrétní problémy v dokumentech společnosti Microsoft a můžete se zúčastnit [fóra LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), kde můžete podrobněji diskutovat o složitějších tématech s odborníky. Nakonec [LINQ na SQL: .NET Jazyk integrovaný dotaz pro relační data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) podrobnosti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, kompletní s příklady kódu jazyka A C#.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](getting-started.md)  
 Poskytuje zkrácený přehled [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spolu s informacemi o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tom, jak začít používat .  
  
 [Programovací příručka](programming-guide.md)  
 Obsahuje postup pro mapování, dotazování, aktualizaci, ladění a podobné úkoly.  
  
 [Referenční materiály](reference.md)  
 Obsahuje referenční informace o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]několika aspektech . Témata zahrnují mapování typů SQL-CLR, standardní překlad operátoru dotazů a další.  
  
 [ukázky](samples.md)  
 Obsahuje odkazy na ukázky jazyka Visual Basic a C#.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dotaz integrovaný jazykem (LINQ) – C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Obsahuje přehledy technologií LINQ v c#.

 [Dotaz integrovaný jazykem (LINQ) – visual basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Obsahuje přehledy technologií LINQ v jazyce Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje technologie LINQ pro uživatele jazyka Visual Basic.  
  
 [LINQ a ADO.NET](../../linq-and-ado-net.md)  
 Odkazy na portál ADO.NET.  
  
 [Návody linq až SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Seznam návodů, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]které jsou k dispozici pro .  
  
 [Stažení ukázkových databází](downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze použité v dokumentaci.  
  
 [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Popisuje, <xref:System.Web.UI.WebControls.LinqDataSource> jak ovládací prvek zpřístupňuje jazykově integrovaný dotaz (LINQ) webovým vývojářům prostřednictvím ASP.NET architektury ovládacího prvku zdroje dat.
