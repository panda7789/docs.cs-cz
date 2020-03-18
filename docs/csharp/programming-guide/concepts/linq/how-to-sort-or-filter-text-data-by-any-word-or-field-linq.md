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
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="065b3-102">Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="065b3-102">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>
<span data-ttu-id="065b3-103">Následující příklad ukazuje, jak řadit řádky strukturovaného textu, například hodnoty oddělené čárkami, libovolným polem v řádku.</span><span class="sxs-lookup"><span data-stu-id="065b3-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="065b3-104">Pole může být dynamicky zadáno za běhu.</span><span class="sxs-lookup"><span data-stu-id="065b3-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="065b3-105">Předpokládejme, že pole v scores.csv představují id číslo studenta, následované řadou čtyř výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="065b3-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="065b3-106">Vytvoření souboru obsahujícího data</span><span class="sxs-lookup"><span data-stu-id="065b3-106">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="065b3-107">Zkopírujte data scores.csv z tématu [Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) a uložte je do složky řešení.</span><span class="sxs-lookup"><span data-stu-id="065b3-107">Copy the scores.csv data from the topic [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="065b3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="065b3-108">Example</span></span>  
  
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
  
 <span data-ttu-id="065b3-109">Tento příklad také ukazuje, jak vrátit proměnnou dotazu z metody.</span><span class="sxs-lookup"><span data-stu-id="065b3-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="065b3-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="065b3-110">Compiling the Code</span></span>  

<span data-ttu-id="065b3-111">Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="065b3-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="065b3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="065b3-112">See also</span></span>

- [<span data-ttu-id="065b3-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="065b3-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
