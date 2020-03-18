---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167904"
---
# <a name="sorting-data-c"></a>Řazení dat (C#)
Operace řazení objednávky prvky sekvence na základě jednoho nebo více atributů. První kritérium řazení provádí primární řazení na prvky. Zadáním druhého kritéria řazení můžete třídit prvky v rámci každé primární skupiny řazení.  
  
 Následující obrázek znázorňuje výsledky abecední operace řazení na posloupnost znaků:
  
 ![Grafika znázorněná abecední řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Standardní metody operátoru dotazu, které řadí data jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Orderby|Seřadí hodnoty vzestupně.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|Orderbydescending|Seřadí hodnoty v sestupném pořadí.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|Thenby|Provádí sekundární řazení ve vzestupném pořadí.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|Thenbydescending|Provádí sekundární řazení v sestupném pořadí.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Obrátí pořadí prvků v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="primary-sort-examples"></a>Příklady primárního řazení  
  
#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení  
 Následující příklad ukazuje, jak `orderby` použít klauzuli v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a>Primární sestupně řazení  
 Následující příklad ukazuje, jak `orderby descending` použít klauzuli v dotazu LINQ seřadit řetězce podle jejich první písmeno, v sestupném pořadí.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a>Příklady sekundárního řazení  
  
#### <a name="secondary-ascending-sort"></a>Sekundární vzestupné řazení  
 Následující příklad ukazuje, jak `orderby` použít klauzuli v dotazu LINQ k provedení primárního a sekundárního druhu řetězců v poli. Řetězce jsou seřazeny především podle délky a sekundárně podle prvního písmene řetězce, a to jak ve vzestupném pořadí.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a>Sekundární sestupně řazení  
 Následující příklad ukazuje, jak `orderby descending` použít klauzuli v dotazu LINQ k provedení primárnířazení, vzestupně a sekundární řazení v sestupném pořadí. Řetězce jsou seřazeny především podle délky a sekundárně podle prvního písmene řetězce.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [orderby – klauzule](../../../language-reference/keywords/orderby-clause.md)
- [Řazení výsledků klauzule join](../../../linq/order-the-results-of-a-join-clause.md)
- [Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
