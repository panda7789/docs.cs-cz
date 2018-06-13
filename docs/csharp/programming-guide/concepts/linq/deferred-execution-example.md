---
title: Odložené provedení příklad (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 8613f2335e5b3cb2a012f5309307e081b9400709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335923"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="a54d6-102">Odložené provedení příklad (C#)</span><span class="sxs-lookup"><span data-stu-id="a54d6-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="a54d6-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.</span><span class="sxs-lookup"><span data-stu-id="a54d6-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a54d6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a54d6-104">Example</span></span>  
 <span data-ttu-id="a54d6-105">Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="a54d6-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="a54d6-106">V příkladu deklaruje pole tři řetězců.</span><span class="sxs-lookup"><span data-stu-id="a54d6-106">The example declares an array of three strings.</span></span> <span data-ttu-id="a54d6-107">Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="a54d6-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="a54d6-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a54d6-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="a54d6-109">Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.</span><span class="sxs-lookup"><span data-stu-id="a54d6-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="a54d6-110">Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="a54d6-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="a54d6-111">Další téma v tomto kurzu znázorňuje řetězení dotazy společně:</span><span class="sxs-lookup"><span data-stu-id="a54d6-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
-   [<span data-ttu-id="a54d6-112">Řetězení příklad dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="a54d6-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="a54d6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a54d6-113">See Also</span></span>  
 [<span data-ttu-id="a54d6-114">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="a54d6-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
