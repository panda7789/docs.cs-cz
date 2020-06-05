---
title: Syntaxe výrazu dotazu pro standardní operátory dotazu
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: 69bb50007c04bf8d1ee1553a37aca542afbffab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396282"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)
Některé z často používaných standardních operátorů dotazů mají vyhrazenou syntaxi klíčového slova jazyka Visual Basic, která umožňuje jejich volání jako součást *výrazu dotazu*. Výraz dotazu je jiný, čitelnější způsob, jak vyjádřit dotaz, než je jeho ekvivalent *na základě metody* . Klauzule dotazového výrazu jsou přeloženy do volání metod dotazů v době kompilace.  
  
## <a name="query-expression-syntax-table"></a>Tabulka syntaxe výrazu dotazu  
 V následující tabulce jsou uvedeny standardní operátory dotazu, které mají ekvivalentní klauzule výrazu dotazu.  
  
|Metoda|Visual Basic syntaxe výrazu dotazu|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (Další informace naleznete v tématu [klauzule FROM](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (Další informace naleznete v tématu [klauzule DISTINCT](../../../language-reference/queries/distinct-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (Další informace najdete v tématu [klauzule GROUP by](../../../language-reference/queries/group-by-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (Další informace najdete v tématu [klauzule Group Join](../../../language-reference/queries/group-join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> -nebo-<br /><br /> `Join … [As …]In … On …`<br /><br /> (Další informace najdete v tématu [klauzule JOIN](../../../language-reference/queries/join-clause.md).)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (Další informace najdete v tématu [klauzule ORDER by](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (Další informace najdete v tématu [klauzule ORDER by](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (Další informace naleznete v tématu [Select klauzule](../../../language-reference/queries/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Vícenásobné `From` klauzule<br /><br /> (Další informace naleznete v tématu [klauzule FROM](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (Další informace naleznete v tématu [klauzule Skip](../../../language-reference/queries/skip-clause.md).)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (Další informace naleznete v tématu [klauzule Skip While](../../../language-reference/queries/skip-while-clause.md).)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (Další informace naleznete v tématu [přijmout klauzuli](../../../language-reference/queries/take-clause.md).)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (Další informace naleznete v tématu [klauzule vzít](../../../language-reference/queries/take-while-clause.md)v.)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (Další informace najdete v tématu [klauzule ORDER by](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (Další informace najdete v tématu [klauzule ORDER by](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (Další informace naleznete v tématu [Where – klauzule WHERE](../../../language-reference/queries/where-clause.md).)|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Klasifikace standardních operátorů dotazu podle způsobu provedení (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
