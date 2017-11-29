---
title: "Seskupování dat (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4aef8d10eaffb384fe919ffa6a1e742cb837f540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-c"></a>Seskupování dat (C#)
Seskupení odkazuje na operaci ukládání dat do skupin tak, aby elementy v každé skupině sdílejí společný atribut.  
  
 Následující obrázek znázorňuje výsledky seskupování posloupnost znaků. Klíč pro každou skupinu je znak.  
  
 ![Operace seskupení LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 V následující části jsou uvedené metody operátor standardní dotazů, které seskupují datové prvky.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Prvky skupiny, které sdílejí společný atribut. Každá skupina je reprezentována <xref:System.Linq.IGrouping%602> objektu.|`group … by`<br /><br /> -nebo-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.|Nelze použít.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá `group by` klauzule na celá čísla skupinu v seznamu podle toho, zda jsou popisných.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md)  
 [Postupy: vytvoření vnořené skupiny](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Postupy: seskupování souborů podle přípony (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [Postupy: seskupení výsledků dotazu](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Postupy: provádění poddotazů na skupinách](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
