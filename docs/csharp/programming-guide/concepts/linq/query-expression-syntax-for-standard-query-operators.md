---
title: Syntaxe výrazu dotazu pro standardní operátory dotazů (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: dac63ae165b88924cb0e91336571173f764569ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591425"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Syntaxe výrazu dotazu pro standardní operátory dotazů (C#)
Některé z nejčastěji používaných operátorů standardní dotaz mají vyhrazené c# jazyk syntaxe, která umožňuje jejich volání jako součást *výrazu dotazu*. Výraz dotazu je jiná, čitelnější forma vyjádření dotazu než jeho ekvivalent *založený na metodách.* Klauzule výrazu dotazu jsou přeloženy do volání metody dotazu v době kompilace.  
  
## <a name="query-expression-syntax-table"></a>Tabulka syntaxe výrazu dotazu  
 V následující tabulce jsou uvedeny standardní operátory dotazů, které mají ekvivalentní klauzule výrazu dotazu.  
  
|Metoda|Syntaxe výrazu dotazu jazyka C#|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Použijte explicitně zadalicí proměnnou rozsahu, například:<br /><br /> `from int i in numbers`<br /><br /> (Další informace naleznete [v článku z klauzule](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -nebo-<br /><br /> `group … by … into …`<br /><br /> (Další informace naleznete v [tématu group clause](../../../language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Další informace naleznete v tématu [join clause](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Další informace naleznete v tématu [join clause](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Další informace naleznete v [klauzuli orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Další informace naleznete v [klauzuli orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Další informace naleznete v [tématu select clause](../../../language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Více `from` klauzulí.<br /><br /> (Další informace naleznete [v článku z klauzule](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Další informace naleznete v [klauzuli orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Další informace naleznete v [klauzuli orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Další informace naleznete v tématu [where clause](../../../language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
