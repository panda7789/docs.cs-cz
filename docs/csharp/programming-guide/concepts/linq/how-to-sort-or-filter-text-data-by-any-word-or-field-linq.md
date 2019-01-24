---
title: 'Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: 1b2378a3f9d589640d50ca3cc80d5e82ba386bd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54747970"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="bfa07-102">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bfa07-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="bfa07-103">Následující příklad ukazuje způsob řazení řádků strukturovaných textu, jako je například textový soubor s oddělovači, podle libovolného pole v řádku.</span><span class="sxs-lookup"><span data-stu-id="bfa07-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="bfa07-104">Pole může být určen dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="bfa07-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="bfa07-105">Předpokládejme, že pole v scores.csv představují student získal identifikační číslo, za nímž následuje řadu čtyři skóre v testech.</span><span class="sxs-lookup"><span data-stu-id="bfa07-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="bfa07-106">Chcete-li vytvořit soubor, který obsahuje data</span><span class="sxs-lookup"><span data-stu-id="bfa07-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="bfa07-107">Kopírování dat scores.csv z tématu [jak: Připojte se k obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) a uloží ho do složky vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="bfa07-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfa07-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfa07-108">Example</span></span>  
  
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
  
 <span data-ttu-id="bfa07-109">Tento příklad také ukazuje, jak vrátit proměnné dotazu z metody.</span><span class="sxs-lookup"><span data-stu-id="bfa07-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bfa07-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bfa07-110">Compiling the Code</span></span>  

 <span data-ttu-id="bfa07-111">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="bfa07-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa07-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfa07-112">See also</span></span>

- [<span data-ttu-id="bfa07-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="bfa07-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
