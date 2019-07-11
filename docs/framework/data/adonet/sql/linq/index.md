---
title: Technologie LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: dce706a9c09558bfb39f0d65bd56b57787488d06
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743271"
---
# <a name="linq-to-sql"></a>Technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí rozhraní .NET Framework verze 3.5, která poskytuje infrastrukturu prostředí run-time pro správu relačních dat jako objektů.  
  
> [!NOTE]
>  Relační data se zobrazí jako kolekce dvourozměrných tabulek (*vztahy* nebo *plochých souborů*), kde společné sloupce tabulky vzájemně souvisí. Chcete-li použít [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektivně, musí mít některé znalost základním principům relačních databází.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], datový model relační databáze je namapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá do SQL integrovaný jazyk dotazů v objektovém modelu a odesílá je do databáze pro spuštění. Když databázi vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede zpět na objekty, které můžete pracovat v programovacím jazyce.  
  
 Vývojáři obvykle pomocí sady Visual Studio pomocí Návrháře relací objektů, které poskytuje uživatelské rozhraní pro řadu funkcí, o implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] popisuje základní stavební bloky, procesy a postupy, které potřebujete pro vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace. Můžete také prohledat Microsoft Docs pro specifické problémy a se můžete zapojit [LINQ fórum](https://go.microsoft.com/fwlink/?LinkId=76488), kde můžete diskutovat o složitějších tématech podrobně s odborníky. Nakonec [technologie LINQ to SQL: .NET Language-Integrated dotazu pro relační Data](https://go.microsoft.com/fwlink/?LinkId=93205) dokument white paper o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, s příklady kódu jazyka Visual Basic a C#.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Poskytuje přehled zhuštěnému [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] společně s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Popisuje kroky pro mapování, vyhledávání, aktualizace, ladění a podobné úlohy.  
  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Poskytuje referenční informace o několik aspektů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mezi témata patří mapování typů SQL a CLR, standardní překladu – operátor dotazu a další.  
  
 [Ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Obsahuje odkazy na ukázky jazyka Visual Basic a C#.  
  
## <a name="related-sections"></a>Související oddíly  
 [Language-Integrated Query (LINQ) –C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Poskytuje přehled technologie LINQ v C#.
 
 [Language-Integrated Query (LINQ) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Poskytuje přehled technologie LINQ v jazyce Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Popisuje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologií pro uživatele jazyka Visual Basic.  
  
 [LINQ a ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Obsahuje odkazy na portálu pro ADO.NET.  
  
 [Technologie LINQ to SQL návody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Uvádí postupy, které jsou k dispozici pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Popisuje, jak stáhnout ukázkové databáze používané v dokumentaci.  
  
 [Přehled ovládacího prvku zdroje dat LinqDataSource webového serveru](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Popisuje, jak <xref:System.Web.UI.WebControls.LinqDataSource> řídit zpřístupňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] pro vývojáře webů prostřednictvím architektury ovládací prvek zdroje dat ASP.NET.
