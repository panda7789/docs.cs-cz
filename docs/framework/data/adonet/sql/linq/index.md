---
title: Technologie LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 257db62fcdaba454f528c2eecedfef735291f4af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355230"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] verze 3.5, který poskytuje běhové infrastrukturu pro správu relačních dat jako objekty.  
  
> [!NOTE]
>  Relační data se zobrazí jako kolekce dvourozměrná tabulek (*vztahů* nebo *ploché soubory*), kde společné sloupce tabulky vzájemně souvisejí. Chcete-li použít [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektivně, musí mít některé znalost základní principy relačních databází.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], datový model relační databáze je namapována na objektový model vyjádřené v programovací jazyk vývojář. Když je aplikace spuštěná, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy language-integrated ve model objektu do SQL a odešle je do databáze pro provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží je zpět na objekty, které můžete pracovat v programovacím jazyce.  
  
 Vývojáři obvykle pomocí sady Visual Studio pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], který poskytuje uživatelské rozhraní pro implementaci řadu funkcí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] popisuje základní stavební bloky, procesy a postupy potřebné pro vytvoření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace. Můžete také prohledat Microsoft Docs pro specifické problémy a se můžete zapojit [LINQ fórum](http://go.microsoft.com/fwlink/?LinkId=76488), kde můžete složitější témata podrobně popisují s odborníky. Nakonec [technologie LINQ to SQL: .NET Language-Integrated dotaz na relační Data](http://go.microsoft.com/fwlink/?LinkId=93205) dokumentu white paper podrobnosti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie kompletní s příklady kódu jazyka Visual Basic a C#.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Obsahuje přehled zhuštěné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] společně s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Popisuje kroky pro mapování, dotazování, aktualizaci, ladění a podobných úloh.  
  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Poskytuje referenční informace o několik aspektů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Témata zahrnují mapování typu SQL CLR, operátor překlad dotazu na standardní a další.  
  
 [Ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Obsahuje odkazy na ukázky jazyka Visual Basic a C#.  
  
## <a name="related-sections"></a>Související oddíly  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Obsahuje přehled [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie.  
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro uživatele jazyka Visual Basic.  
  
 [Technologie LINQ to ADO.NET](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 Obsahuje odkazy na [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portálu.  
  
 [Technologie LINQ to SQL návody](http://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 Uvádí postupy, které jsou k dispozici pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze používají v dokumentaci.  
  
 [Přehled technologie LinqDataSource](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 Popisuje, jak <xref:System.Web.UI.WebControls.LinqDataSource> řízení zpřístupňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] na vývojáři webů prostřednictvím [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektury datové zdroje.
