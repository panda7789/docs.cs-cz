---
title: 'Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: 243ff37e38b2e88b55962980e91a1ab6dcebab3c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304867"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)
Následující příklad ukazuje způsob řazení řádků strukturovaných textu, jako je například textový soubor s oddělovači, podle libovolného pole v řádku. Pole může být určen dynamicky za běhu. Předpokládejme, že pole v scores.csv představují student získal identifikační číslo, za nímž následuje řadu čtyři skóre v testech.  
  
### <a name="to-create-a-file-that-contains-data"></a>Chcete-li vytvořit soubor, který obsahuje data  
  
1. Kopírování dat scores.csv z tématu [jak: Připojte se k obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) a uloží ho do složky vašeho řešení.  
  
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
  
 Tento příklad také ukazuje, jak vrátit proměnné dotazu z metody.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
