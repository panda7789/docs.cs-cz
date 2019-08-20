---
title: Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: dac63ae165b88924cb0e91336571173f764569ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591425"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)
Některé z často používaných standardních operátorů dotazů mají vyhrazenou C# syntaxi klíčového slova jazyka, která umožňuje jejich volání jako součást *výrazu dotazu*. Výraz dotazu je jiný, čitelnější způsob, jak vyjádřit dotaz, než je jeho ekvivalent *na základě metody* . Klauzule dotazového výrazu jsou přeloženy do volání metod dotazů v době kompilace.  
  
## <a name="query-expression-syntax-table"></a>Tabulka syntaxe výrazu dotazu  
 V následující tabulce jsou uvedeny standardní operátory dotazu, které mají ekvivalentní klauzule výrazu dotazu.  
  
|Metoda|C#Syntaxe výrazu dotazu|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Použijte explicitně typovou proměnnou rozsahu, například:<br /><br /> `from int i in numbers`<br /><br /> (Další informace naleznete v tématu [klauzule FROM](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -nebo-<br /><br /> `group … by … into …`<br /><br /> (Další informace naleznete v tématu [Group Group](../../../language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Další informace naleznete v tématu [Select klauzule](../../../language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Více `from` klauzulí.<br /><br /> (Další informace naleznete v tématu [klauzule FROM](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Další informace naleznete v tématu [Where – klauzule WHERE](../../../language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Klasifikace standardních operátorů dotazu podle způsobu provedení (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
