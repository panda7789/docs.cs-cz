---
title: Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)
description: Naučte se používat LINQ v jazyce C# k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v jednom seznamu, ale nejsou v druhém.
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 24509488d91f9861ee9bf84277238bea7031e5f6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105086"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)
Tento příklad ukazuje, jak použít LINQ k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v names1.txt, ale ne v names2.txt.  
  
### <a name="to-create-the-data-files"></a>Vytvoření datových souborů  
  
1. Zkopírujte names1.txt a names2.txt do složky řešení, jak je znázorněno v tématu [jak kombinovat a porovnat kolekce řetězců (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).  
  
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
  
 Některé typy operací dotazů v jazyce C#, například, <xref:System.Linq.Enumerable.Except%2A> , <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> a <xref:System.Linq.Enumerable.Concat%2A> , lze vyjádřit pouze v syntaxi založené na metodě.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
