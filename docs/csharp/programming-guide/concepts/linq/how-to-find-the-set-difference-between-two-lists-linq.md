---
title: Jak najít nastavený rozdíl mezi dvěma seznamy (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 03fae5451ee395487e73ed7c38d465c3f891e0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169178"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Jak najít nastavený rozdíl mezi dvěma seznamy (LINQ) (C#)
Tento příklad ukazuje, jak pomocí LINQ porovnat dva seznamy řetězců a výstup ty řádky, které jsou v names1.txt, ale ne v names2.txt.  
  
### <a name="to-create-the-data-files"></a>Vytvoření datových souborů  
  
1. Zkopírujte názvy1.txt a names2.txt do složky řešení, jak je znázorněno v [obrázku Jak kombinovat a porovnávat kolekce řetězců (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Příklad  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 Některé typy dotazovacích operací v <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Distinct%2A>c#, například , , <xref:System.Linq.Enumerable.Union%2A>a <xref:System.Linq.Enumerable.Concat%2A>, lze vyjádřit pouze v syntaxi založené na metodě.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
