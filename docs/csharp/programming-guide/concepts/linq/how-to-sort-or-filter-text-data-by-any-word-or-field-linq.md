---
title: Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: e869d57c413d175c092cdc15a6fe54cab94e04b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347353"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)
Následující příklad ukazuje, jak řadit řádky strukturovaného textu, například hodnoty oddělené čárkami, libovolným polem v řádku. Pole může být dynamicky zadáno za běhu. Předpokládejme, že pole v scores.csv představují id číslo studenta, následované řadou čtyř výsledků testů.  
  
### <a name="to-create-a-file-that-contains-data"></a>Vytvoření souboru obsahujícího data  
  
1. Zkopírujte data scores.csv z tématu [Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) a uložte je do složky řešení.  
  
## <a name="example"></a>Příklad  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 Tento příklad také ukazuje, jak vrátit proměnnou dotazu z metody.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
