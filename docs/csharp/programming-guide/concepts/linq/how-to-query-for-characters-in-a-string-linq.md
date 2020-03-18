---
title: Jak dotaz ovat znaky v řetězci (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345684"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="90904-102">Jak dotaz ovat znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="90904-102">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="90904-103">Vzhledem <xref:System.String> k tomu, <xref:System.Collections.Generic.IEnumerable%601> že třída implementuje obecné rozhraní, může být libovolný řetězec dotazován jako posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="90904-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="90904-104">To však není běžné použití LINQ.</span><span class="sxs-lookup"><span data-stu-id="90904-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="90904-105">Pro operace porovnávání složitých vzorů použijte třídu. <xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="90904-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90904-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="90904-106">Example</span></span>  
 <span data-ttu-id="90904-107">Následující příklad dotazuje řetězec určit počet číselných číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="90904-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="90904-108">Všimněte si, že dotaz je "znovu použít" po jeho prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="90904-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="90904-109">To je možné, protože dotaz sám neukládá žádné skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="90904-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="90904-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="90904-110">Compiling the Code</span></span>  
 <span data-ttu-id="90904-111">Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="90904-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90904-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="90904-112">See also</span></span>

- [<span data-ttu-id="90904-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="90904-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="90904-114">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="90904-114">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
