---
title: Aggregation Operations (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 72268e27fdf6d573279e98438fd884a076e0c8a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669028"
---
# <a name="aggregation-operations-visual-basic"></a>Aggregation Operations (Visual Basic)
Operace agregace vypočítá jedinou hodnotu z kolekce hodnot. Příklad operace agregace je výpočet denní teplota z za měsíc denní teplotní hodnoty.  
  
 Následující obrázek ukazuje výsledky dvou různých agregační operace na sekvenci čísel. První operace sečte čísla. Druhou operaci vrátí maximální hodnotu v pořadí.  
  
 ![Obrázek, na kterém agregační operace LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Aggregate|Provede vlastní agregační operace na hodnotách kolekce.|Není k dispozici.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Průměr|Vypočítá průměrnou hodnotu kolekci hodnot.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|Vrátí počet prvků v kolekci, volitelně pouze elementy, které splňují funkce predikátu.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Vrátí počet prvků v velkou kolekci volitelně pouze elementy, které splňují funkce predikátu.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maximum|Určuje maximální hodnotu v kolekci.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Minimum|Určuje minimální hodnota v kolekci.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Součet|Vypočítá součet hodnot v kolekci.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="average"></a>Průměr  
 Následující příklad kódu používá `Aggregate Into Average` klauzule v jazyce Visual Basic k výpočtu průměrná teplota v poli čísel, které představují teploty.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Count  
 Následující příklad kódu používá `Aggregate Into Count` klauzule v jazyce Visual Basic mají spočítat počet hodnot v poli, které jsou větší než nebo rovna hodnotě 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Následující příklad kódu používá `Aggregate Into LongCount` klauzule počet hodnot v poli.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maximum  
 Následující příklad kódu používá `Aggregate Into Max` klauzule a vypočítat maximální teploty v poli čísel, které představují teploty.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Minimum  
 Následující příklad kódu používá `Aggregate Into Min` klauzule a vypočítat minimální teploty v poli čísel, které představují teploty.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Součet  
 Následující příklad kódu používá `Aggregate Into Sum` klauzule a vypočítat celkové náklady množství z pole hodnot, které představují výdaje.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Postupy: Výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Postupy: Počet, SUMA nebo průměr dat](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Postupy: Dotaz na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Postupy: Dotaz pro celkový počet bajtů v sadě složek (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
