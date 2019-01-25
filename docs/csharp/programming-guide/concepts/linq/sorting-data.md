---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: dfa0a4a030cab8ec33c90d8edaef0d6070755034
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721952"
---
# <a name="sorting-data-c"></a>Řazení dat (C#)
Operace řazení Seřadí prvky pořadí na základě jednoho nebo více atributů. První kritérium řazení provede primární řazení elementů. Zadáním druhý kritérium řazení, lze řazení elementů v rámci jednotlivých skupin primární řazení.  
  
 Následující obrázek znázorňuje výsledky operace abecední řazení na sekvenci znaků.  
  
 ![Řazení operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Standardní metody operátoru dotazu, které řazení dat jsou uvedené v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Řadit podle|Seřadí hodnoty ve vzestupném pořadí.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Seřadí v sestupném pořadí.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Provede sekundární řazení ve vzestupném pořadí.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Provádí sekundární seřadit v sestupném pořadí.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|reverzní|Obrátí pořadí prvků v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="primary-sort-examples"></a>Příklady primárních řazení  
  
#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení  
 Následující příklad ukazuje způsob použití `orderby` klauzule v dotazu LINQ a řetězce v poli řadit délka řetězce ve vzestupném pořadí.  
  
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
 Následující příklad ukazuje, jak používat `orderby descending` klauzule v dotazu LINQ a řetězce řadit v sestupném pořadí podle jejich první písmeno.  
  
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
  
### <a name="secondary-sort-examples"></a>Příklady sekundární řazení  
  
#### <a name="secondary-ascending-sort"></a>Sekundární vzestupné řazení  
 Následující příklad ukazuje způsob použití `orderby` klauzule v dotazu LINQ provádět primární a sekundární řazení řetězců v poli. Řetězce jsou seřazeny podle délky primárně a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.  
  
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
 Následující příklad ukazuje, jak používat `orderby descending` klauzule v dotazu LINQ provádět primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí. Řetězce jsou seřazeny především podle délky a sekundárně první písmeno řetězce.  
  
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
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [orderby – klauzule](../../../../csharp/language-reference/keywords/orderby-clause.md)
- [Postupy: Řazení výsledků Klauzule Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
