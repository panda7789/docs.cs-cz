---
title: Dotazování na znaky v řetězci (LINQ) (C#)
description: Můžete zadat dotaz na řetězec jako posloupnost znaků v LINQ. V tomto příkladu jazyka C# se dotazuje na řetězec, který určuje počet číslic, které obsahuje.
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 3512be7c30843fcd8e881eab59761706a84a3ac8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104553"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="bf2bf-104">Dotazování na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bf2bf-104">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="bf2bf-105">Vzhledem k tomu <xref:System.String> , že třída implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, může být libovolný řetězec dotazován jako posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-105">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="bf2bf-106">Nejedná se však o běžné použití LINQ.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-106">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="bf2bf-107">Pro komplexní operace porovnávání vzorů použijte <xref:System.Text.RegularExpressions.Regex> třídu.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-107">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2bf-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf2bf-108">Example</span></span>  
 <span data-ttu-id="bf2bf-109">Následující příklad vyhledá řetězec, který určí počet číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-109">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="bf2bf-110">Všimněte si, že po prvním spuštění dotazu je dotaz znovu použit.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-110">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="bf2bf-111">To je možné, protože samotný dotaz neukládá žádné skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-111">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf2bf-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bf2bf-112">Compiling the Code</span></span>  
 <span data-ttu-id="bf2bf-113">Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2bf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf2bf-114">See also</span></span>

- [<span data-ttu-id="bf2bf-115">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="bf2bf-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="bf2bf-116">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="bf2bf-116">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
