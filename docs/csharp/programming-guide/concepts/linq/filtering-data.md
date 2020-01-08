---
title: Filtrování dat (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346995"
---
# <a name="filtering-data-c"></a>Filtrování dat (C#)
Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce. Označuje se také jako výběr.  
  
 Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků. Predikát pro operaci filtrování určuje, že znak musí být "A".  
  
 ![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Only|Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.|Nelze použít.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Vybere hodnoty, které jsou založeny na funkci predikátu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 V následujícím příkladu je použita klauzule `where` pro filtrování z pole, které mají konkrétní délku.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [where – klauzule](../../../language-reference/keywords/where-clause.md)
- [Dynamické určování filtrů predikátů při běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Postup dotazování na metadata sestavení s reflexí (LINQ)C#()](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Dotazování na soubory se zadaným atributem nebo názvem (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
