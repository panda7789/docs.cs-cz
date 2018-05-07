---
title: Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: 48ca1173439559832ac7e578eac1e11c2bf34be2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)
Některé více často používaných standardní operátory dotazu mít vyhrazené C# – klíčové slovo syntaxe jazyka umožňující volat v rámci *dotaz výrazu*. Výraz dotazu je jiné, srozumitelnější formu vyjadřující dotazu než jeho *na základě metod* ekvivalentní. Klauzule výraz dotazu jsou převedeny do volání metody dotazů v době kompilace.  
  
## <a name="query-expression-syntax-table"></a>Tabulky Syntax výraz dotazu  
 Následující tabulka uvádí operátory standardní dotazu, které mají výraz klauzule ekvivalentní dotazu.  
  
|Metoda|Syntaxe výrazu dotazu jazyka C#|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Používejte například proměnnou rozsahu explicitně typu:<br /><br /> `from int i in numbers`<br /><br /> (Další informace najdete v tématu [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -nebo-<br /><br /> `group … by … into …`<br /><br /> (Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Další informace najdete v tématu [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Více `from` klauzule.<br /><br /> (Další informace najdete v tématu [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klasifikace standardních operátorů dotazu podle metody provedení (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
