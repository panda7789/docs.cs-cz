---
title: Agregační operace
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 8e2c9698de67dc4def348a03c9d69713a6130f31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383790"
---
# <a name="aggregation-operations-visual-basic"></a>Agregační operace (Visual Basic)
Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Ukázka operace agregace počítá průměrnou denní teplotu z hodnoty denních teplot v měsíci.  
  
 Následující ilustrace znázorňuje výsledky dvou různých agregačních operací na sekvenci čísel. První operace Sečte čísla. Druhá operace vrátí maximální hodnotu v sekvenci.  
  
 ![Ilustrace znázorňující agregační operace LINQ](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Agregace|Provede vlastní agregační operaci na hodnotách kolekce.|Neužívá se.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Průměr|Vypočítá průměrnou hodnotu kolekce hodnot.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Počet|Spočítá prvky v kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Spočítá prvky ve velké kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maximum|Určuje maximální hodnotu v kolekci.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Minimum|Určuje minimální hodnotu v kolekci.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Součet|Vypočítá součet hodnot v kolekci.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="average"></a>Průměr  
 Následující příklad kódu používá `Aggregate Into Average` klauzuli v Visual Basic k výpočtu průměrné teploty v poli čísel, která představuje teploty.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Počet  
 Následující příklad kódu používá `Aggregate Into Count` klauzuli v Visual Basic k určení počtu hodnot v poli, které jsou větší nebo rovno 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Následující příklad kódu používá `Aggregate Into LongCount` klauzuli pro počítání počtu hodnot v poli.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maximum  
 Následující příklad kódu používá `Aggregate Into Max` klauzuli pro výpočet maximální teploty v poli čísel, která představuje teploty.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Minimum  
 Následující příklad kódu používá `Aggregate Into Min` klauzuli pro výpočet minimální teploty v poli čísel, která představuje teploty.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Součet  
 Následující příklad kódu používá `Aggregate Into Sum` klauzuli pro výpočet celkové částky výdajů z pole hodnot, které reprezentují výdaje.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Aggregate – klauzule](../../../language-reference/queries/aggregate-clause.md)
- [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Postupy: počítání, suma nebo průměr dat](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Postupy: vytvoření dotazu na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Postupy: vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
