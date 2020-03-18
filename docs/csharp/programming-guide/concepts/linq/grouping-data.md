---
title: Seskupování dat (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635740"
---
# <a name="grouping-data-c"></a>Seskupování dat (C#)
Seskupení odkazuje na operaci vkládání dat do skupin tak, aby prvky v každé skupině sdílejí společný atribut.  
  
 Následující obrázek znázorňuje výsledky seskupování posloupnosti znaků. Klíčem pro každou skupinu je znak.  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Seskupí prvky, které sdílejí společný atribut. Každá skupina je <xref:System.Linq.IGrouping%602> reprezentována objektem.|`group … by`<br /><br /> -nebo-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|Vyhledávání|Vloží prvky <xref:System.Linq.Lookup%602> do (slovníku 1:N) na základě funkce voliče klíčů.|Neužívá se.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu `group by` používá klauzuli k seskupení celá čísla v seznamu podle toho, zda jsou sudé nebo liché.  
  
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

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [group – klauzule](../../../language-reference/keywords/group-clause.md)
- [Vytvoření vnořené skupiny](../../../linq/create-a-nested-group.md)
- [Jak seskupit soubory podle přípony (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Seskupení výsledků dotazu](../../../linq/group-query-results.md)
- [Provádění poddotazů na skupinách](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [Jak rozdělit soubor do mnoha souborů pomocí skupin (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
