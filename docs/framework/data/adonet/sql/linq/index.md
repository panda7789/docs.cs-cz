---
title: Technologie LINQ to SQL
description: LINQ to SQL je komponentou .NET Framework, která poskytuje infrastrukturu run-time pro správu relačních dat jako objektů.
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 13502bfee3ee24764d190dace1512bc958343973
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286311"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je součástí .NET Framework verze 3,5, která poskytuje infrastrukturu run-time pro správu relačních dat jako objektů.  
  
> [!NOTE]
> Relační data se zobrazí jako kolekce dvourozměrných tabulek (*vztahů* nebo *plochých souborů*), kde společné sloupce vzájemně souvisejí s tabulkami. Aby [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bylo možné efektivně používat, musíte mít známé základní principy relačních databází.  
  
 V systému [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Po spuštění aplikace se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží na SQL dotazy integrované do jazyka v objektovém modelu a pošle je do databáze za účelem provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede je zpět na objekty, se kterými můžete pracovat ve vlastním programovacím jazyce.  
  
 Vývojáři, kteří používají Visual Studio, obvykle používají Návrhář relací objektů, který poskytuje uživatelské rozhraní pro implementaci mnoha funkcí nástroje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , popisuje základní stavební kameny, procesy a techniky, které potřebujete pro sestavování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací. Můžete také vyhledat konkrétní problémy v Microsoft Docs a můžete se zúčastnit [fóra LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), kde můžete diskutovat o složitější témata podrobněji s odborníky. Nakonec [LINQ to SQL: dotaz integrovaný na jazyku .NET pro](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) technologii podrobného dokumentu s relačními daty s podrobnostmi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , dokončete s příklady kódu Visual Basic a C#.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](getting-started.md)  
 Poskytuje zúžený přehled [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spolu s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Průvodce programováním](programming-guide.md)  
 Poskytuje kroky pro mapování, dotazování, aktualizaci, ladění a podobné úkoly.  
  
 [Odkaz](reference.md)  
 Poskytuje referenční informace o několika aspektech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Témata zahrnují mapování typů SQL-CLR, standardní převod operátoru dotazu a další.  
  
 [ukázky](samples.md)  
 Obsahuje odkazy na ukázky Visual Basic a C#.  
  
## <a name="related-sections"></a>Související oddíly  
 [LINQ (Language-Integrated Query)-C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Poskytuje přehled technologie LINQ v jazyce C#.

 [LINQ (Language-Integrated Query) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Poskytuje přehled technologie LINQ v Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje technologie LINQ pro uživatele Visual Basic.  
  
 [LINQ a ADO.NET](../../linq-and-ado-net.md)  
 Odkazuje na portál ADO.NET.  
  
 [LINQ to SQL návody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Uvádí seznam návodů, které jsou k dispozici pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Stažení ukázkových databází](downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze používané v dokumentaci.  
  
 [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Popisuje, jak <xref:System.Web.UI.WebControls.LinqDataSource> ovládací prvek zveřejňuje LINQ (Language-Integrated Query) pro webové vývojáře prostřednictvím architektury ASP.NET Data Source Control.
