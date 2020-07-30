---
title: Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)
description: Naučte se řadit nebo filtrovat textová data podle libovolného slova nebo pole. Podívejte se na příklad řazení řádků strukturovaného textu podle libovolného pole na řádku.
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: f27ce44f4b0b05bc9094b7e108af8f65170bb58a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301317"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)
Následující příklad ukazuje, jak řadit řádky strukturovaného textu, například hodnoty oddělené čárkami, podle libovolného pole na řádku. Pole lze dynamicky určit za běhu. Předpokládejte, že pole v scores.csv reprezentují ID studenta, následované řadou čtyř výsledků testů.  
  
### <a name="to-create-a-file-that-contains-data"></a>Vytvoření souboru, který obsahuje data  
  
1. Zkopírujte data scores.csv z tématu [Postup připojení obsahu z nepodobných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) a uložte je do složky řešení.  
  
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

Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (C#)](./linq-and-strings.md)
