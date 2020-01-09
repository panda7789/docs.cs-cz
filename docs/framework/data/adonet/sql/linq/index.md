---
title: Technologie LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 4553be9eeab8792197503d0b1de872f4494277b6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634622"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součást .NET Framework verze 3,5, která poskytuje infrastrukturu run-time pro správu relačních dat jako objektů.  
  
> [!NOTE]
> Relační data se zobrazí jako kolekce dvourozměrných tabulek (*vztahů* nebo *plochých souborů*), kde společné sloupce vzájemně souvisejí s tabulkami. Aby bylo možné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektivně používat, je nutné se seznámit se základními principy relačních databází.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Když je aplikace spuštěná, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se přeloží do SQL pro jazykově integrované dotazy v objektovém modelu a pošle je do databáze pro provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je přeloží zpět na objekty, se kterými můžete pracovat ve vlastním programovacím jazyce.  
  
 Vývojáři, kteří používají Visual Studio, obvykle používají Návrhář relací objektů, který poskytuje uživatelské rozhraní pro implementaci mnoha funkcí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], popisuje základní stavební kameny, procesy a techniky, které potřebujete při sestavování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ch aplikací. Můžete také vyhledat konkrétní problémy v Microsoft Docs a můžete se zúčastnit [fóra LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), kde můžete diskutovat o složitější témata podrobněji s odborníky. Nakonec [LINQ to SQL: dotaz integrovaný na jazyku .NET pro data dokumentu White Paper s relačními daty](https://go.microsoft.com/fwlink/?LinkId=93205) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii, který se C# doplní Visual Basic a příklady kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](getting-started.md)  
 Poskytuje zúžený přehled [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spolu s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Průvodce programováním](programming-guide.md)  
 Poskytuje kroky pro mapování, dotazování, aktualizaci, ladění a podobné úkoly.  
  
 [Odkazy](reference.md)  
 Poskytuje referenční informace o několika aspektech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Témata zahrnují mapování typů SQL-CLR, standardní převod operátoru dotazu a další.  
  
 [Ukázky](samples.md)  
 Obsahuje odkazy na Visual Basic a C# ukázky.  
  
## <a name="related-sections"></a>Související oddíly  
 [LINQ (Language-Integrated Query) – C# ](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Poskytuje přehled technologie LINQ v C#.
 
 [LINQ (Language-Integrated Query) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Poskytuje přehled technologie LINQ v Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje technologie LINQ pro uživatele Visual Basic.  
  
 [LINQ a ADO.NET](../../linq-and-ado-net.md)  
 Odkazuje na portál ADO.NET.  
  
 [LINQ to SQL návody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Zobrazí seznam návodů, které jsou k dispozici pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Stažení ukázkových databází](downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze používané v dokumentaci.  
  
 [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Popisuje, jak ovládací prvek <xref:System.Web.UI.WebControls.LinqDataSource> zveřejňuje LINQ (Language-Integrated Query) pro webové vývojáře prostřednictvím architektury správy zdrojů dat ASP.NET.
