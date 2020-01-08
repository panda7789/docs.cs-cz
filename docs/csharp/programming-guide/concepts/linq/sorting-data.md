---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346459"
---
# <a name="sorting-data-c"></a>Řazení dat (C#)
Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů. První kritérium řazení provede primární řazení pro prvky. Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.  
  
 Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků: 
  
 ![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Seřadí hodnoty ve vzestupném pořadí.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Seřadí hodnoty v sestupném pořadí.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Provede sekundární řazení ve vzestupném pořadí.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Provede sekundární řazení v sestupném pořadí.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Obrátí pořadí prvků v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="primary-sort-examples"></a>Primární příklady řazení  
  
#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení  
 Následující příklad ukazuje, jak použít klauzuli `orderby` v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.  
  
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
  
#### <a name="primary-descending-sort"></a>Primární sestupné řazení  
 Další příklad ukazuje, jak použít klauzuli `orderby descending` v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.  
  
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
  
### <a name="secondary-sort-examples"></a>Sekundární příklady řazení  
  
#### <a name="secondary-ascending-sort"></a>Sekundární vzestupné řazení  
 Následující příklad ukazuje, jak použít klauzuli `orderby` v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli. Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.  
  
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
  
#### <a name="secondary-descending-sort"></a>Sekundární sestupné řazení  
 Další příklad ukazuje, jak použít klauzuli `orderby descending` v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí. Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [orderby – klauzule](../../../language-reference/keywords/orderby-clause.md)
- [Řazení výsledků klauzule join](../../../linq/order-the-results-of-a-join-clause.md)
- [Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
