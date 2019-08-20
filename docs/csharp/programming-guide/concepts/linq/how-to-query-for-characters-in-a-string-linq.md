---
title: 'Postupy: Dotaz na znaky v řetězci (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 1212ebcf264aab756eca1acb81ae617c2218a065
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592889"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="aa925-102">Postupy: Dotaz na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aa925-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="aa925-103">Vzhledem k tomu, že <xref:System.Collections.Generic.IEnumerable%601> Třídaimplementujeobecnérozhraní,můžebýtlibovolnýřetězecdotazovánjakoposloupnostznaků.<xref:System.String></span><span class="sxs-lookup"><span data-stu-id="aa925-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="aa925-104">Nejedná se však o běžné použití LINQ.</span><span class="sxs-lookup"><span data-stu-id="aa925-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="aa925-105">Pro komplexní operace porovnávání vzorů použijte <xref:System.Text.RegularExpressions.Regex> třídu.</span><span class="sxs-lookup"><span data-stu-id="aa925-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa925-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa925-106">Example</span></span>  
 <span data-ttu-id="aa925-107">Následující příklad vyhledá řetězec, který určí počet číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="aa925-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="aa925-108">Všimněte si, že po prvním spuštění dotazu je dotaz znovu použit.</span><span class="sxs-lookup"><span data-stu-id="aa925-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="aa925-109">To je možné, protože samotný dotaz neukládá žádné skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="aa925-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa925-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aa925-110">Compiling the Code</span></span>  
 <span data-ttu-id="aa925-111">Vytvořte projekt C# konzolové aplikace se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="aa925-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa925-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa925-112">See also</span></span>

- [<span data-ttu-id="aa925-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="aa925-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="aa925-114">Postupy: Kombinování dotazů LINQ s regulárnímiC#výrazy ()</span><span class="sxs-lookup"><span data-stu-id="aa925-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
