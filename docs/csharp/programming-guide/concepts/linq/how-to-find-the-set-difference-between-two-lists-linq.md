---
title: 'Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 9e2a42a466a71d4e351df89398be197197a54042
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140986"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)
Tento příklad ukazuje, jak použít LINQ k porovnání dvou seznamů řetězců a výstupu těchto řádků, které jsou v names1. txt, ale ne v names2. txt.  
  
### <a name="to-create-the-data-files"></a>Vytvoření datových souborů  
  
1. Zkopírujte names1. txt a names2. txt do složky řešení, jak je znázorněno v tématu [jak kombinovat a porovnat kolekce řetězců (LINQC#) ()](./how-to-combine-and-compare-string-collections-linq.md).  
  
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
  
 Některé typy operací dotazů v C#, například <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>a <xref:System.Linq.Enumerable.Concat%2A>, lze vyjádřit pouze v syntaxi založené na metodě.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt C# konzolové aplikace s direktivami `using` pro obory názvů System. Linq a System.IO.  
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (C#)](./linq-and-strings.md)
