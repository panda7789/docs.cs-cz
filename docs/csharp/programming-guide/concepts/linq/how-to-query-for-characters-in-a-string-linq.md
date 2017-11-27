---
title: "Postupy: dotazu na znaky v řetězci (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83d83ee9035624a988a3446267e8fc8231e86582
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="40c5d-102">Postupy: dotazu na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="40c5d-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="40c5d-103">Protože <xref:System.String> třída implementuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní, může být dotazován libovolný řetězec jako posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="40c5d-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="40c5d-104">Je to ale není běžně se používají LINQ.</span><span class="sxs-lookup"><span data-stu-id="40c5d-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="40c5d-105">Pro komplexní vzor odpovídající operace, použijte <xref:System.Text.RegularExpressions.Regex> třídy.</span><span class="sxs-lookup"><span data-stu-id="40c5d-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40c5d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40c5d-106">Example</span></span>  
 <span data-ttu-id="40c5d-107">V následujícím příkladu se dotazuje řetězec můžete určit počet číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="40c5d-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="40c5d-108">Všimněte si, že dotaz je "opakovaně" po provedení první.</span><span class="sxs-lookup"><span data-stu-id="40c5d-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="40c5d-109">To je možné, protože samotný dotaz neukládá skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="40c5d-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="40c5d-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="40c5d-110">Compiling the Code</span></span>  
 <span data-ttu-id="40c5d-111">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="40c5d-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c5d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="40c5d-112">See Also</span></span>  
 [<span data-ttu-id="40c5d-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="40c5d-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="40c5d-114">Postupy: kombinace dotazů LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="40c5d-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
