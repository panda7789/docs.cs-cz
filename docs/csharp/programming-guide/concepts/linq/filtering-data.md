---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: ad8c167cf1b084c5e05bec84cd5c2f3f05716d03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="filtering-data-c"></a>Filtrování dat (C#)
Filtrování odkazuje na operaci omezit tak, aby obsahovala pouze elementy, které splňují zadanou podmínku sadu výsledků dotazu. Je také označované jako výběr.  
  
 Následující obrázek znázorňuje výsledky filtrování posloupnost znaků. Predikát pro filtrování operaci Určuje, že znak musí být "A".  
  
 ![LINQ filtrování operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 Operátor metody standardní dotazu, které provedení výběru jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Vybere hodnoty, v závislosti na jejich schopnost převést na zadaný typ.|Nelze použít.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Vybere hodnoty, které jsou založeny na funkce predikátu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad používá `where` klauzule vyfiltrujete z pole tyto řetězce, které mají určité délky.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [where – klauzule](../../../../csharp/language-reference/keywords/where-clause.md)  
 [Postupy: dynamické určování filtrů predikátů při běhu](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [Postupy: vytvoření dotazu na Metadata sestavení s reflexí (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [Postupy: dotaz pro soubory s konkrétním atributem či názvem (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
