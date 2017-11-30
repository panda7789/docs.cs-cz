---
title: "Odložené provedení příklad (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b902c58f801a6e157a971335895670e8a8bf2181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="e8d54-102">Odložené provedení příklad (C#)</span><span class="sxs-lookup"><span data-stu-id="e8d54-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="e8d54-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.</span><span class="sxs-lookup"><span data-stu-id="e8d54-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8d54-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8d54-104">Example</span></span>  
 <span data-ttu-id="e8d54-105">Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="e8d54-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="e8d54-106">V příkladu deklaruje pole tři řetězců.</span><span class="sxs-lookup"><span data-stu-id="e8d54-106">The example declares an array of three strings.</span></span> <span data-ttu-id="e8d54-107">Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="e8d54-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="e8d54-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e8d54-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="e8d54-109">Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.</span><span class="sxs-lookup"><span data-stu-id="e8d54-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="e8d54-110">Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="e8d54-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="e8d54-111">Další téma v tomto kurzu znázorňuje řetězení dotazy společně:</span><span class="sxs-lookup"><span data-stu-id="e8d54-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
-   [<span data-ttu-id="e8d54-112">Řetězení příklad dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e8d54-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="e8d54-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8d54-113">See Also</span></span>  
 [<span data-ttu-id="e8d54-114">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="e8d54-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
