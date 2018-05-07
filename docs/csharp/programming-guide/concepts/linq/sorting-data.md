---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 6e223ecbfc68e904762bff998b3bd37f88607f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sorting-data-c"></a>Řazení dat (C#)
Operace řazení řadí elementy pořadí na základě jednoho nebo více atributů. První kritérium řazení provede primární řazení elementů. Zadáním druhý kritérium řazení lze seřadit elementů v rámci jednotlivých skupin primární řazení.  
  
 Následující obrázek znázorňuje výsledky operace abecedním řazení na posloupnost znaků.  
  
 ![LINQ řazení operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Operátor metody standardní dotazů, které řazení dat jsou uvedené v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Řadit podle|Seřadí hodnoty ve vzestupném pořadí.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Seřadí hodnoty v sestupném pořadí.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Provede sekundární řazení ve vzestupném pořadí.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Provede sekundární řazení v sestupném pořadí.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Obrátí pořadí prvků v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="primary-sort-examples"></a>Příklady primární řazení  
  
#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení  
 Následující příklad ukazuje, jak používat `orderby` klauzuli v dotazu LINQ pro řazení řetězců v pole podle délka řetězce ve vzestupném pořadí.  
  
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
 Další příklad ukazuje, jak používat `orderby``descending` klauzuli v dotazu LINQ řetězce seřadit podle jejich první písmeno v sestupném pořadí.  
  
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
 Následující příklad ukazuje, jak používat `orderby` klauzuli v dotazu LINQ provádět primární a sekundární řazení řetězců v pole. Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.  
  
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
 Další příklad ukazuje, jak používat `orderby``descending` klauzuli v dotazu LINQ provést primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí. Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce.  
  
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
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [orderby – klauzule](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [Postupy: řazení výsledků Klauzule Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
