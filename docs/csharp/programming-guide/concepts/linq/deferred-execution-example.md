---
title: Příklad odloženého spuštění (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204130"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="22730-102">Příklad odloženého spuštění (C#)</span><span class="sxs-lookup"><span data-stu-id="22730-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="22730-103">Toto téma ukazuje, jak odložené spuštění a opožděné vyhodnocení ovlivňují provádění dotazů LINQ na dotazy XML.</span><span class="sxs-lookup"><span data-stu-id="22730-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22730-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="22730-104">Example</span></span>  
 <span data-ttu-id="22730-105">Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené spuštění.</span><span class="sxs-lookup"><span data-stu-id="22730-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="22730-106">Příklad deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="22730-106">The example declares an array of three strings.</span></span> <span data-ttu-id="22730-107">Potom iterace prostřednictvím kolekce `ConvertCollectionToUpperCase`vrácené .</span><span class="sxs-lookup"><span data-stu-id="22730-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="22730-108">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="22730-108">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="22730-109">Všimněte si, že při iterace prostřednictvím kolekce vrácené `ConvertCollectionToUpperCase`, každá položka je načtena ze zdrojového pole řetězce a převedena na velká písmena před další položkou je načten ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="22730-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="22730-110">Můžete vidět, že celé pole řetězců není převedenna velká písmena před každou položku `foreach` v `Main`vrácené kolekci je zpracována ve smyčce v .</span><span class="sxs-lookup"><span data-stu-id="22730-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="22730-111">Další téma v tomto kurzu ilustruje řetězení dotazů dohromady:</span><span class="sxs-lookup"><span data-stu-id="22730-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="22730-112">Příklad zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="22730-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="22730-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="22730-113">See also</span></span>

- [<span data-ttu-id="22730-114">Kurz: Řetězení dotazů dohromady (C#)</span><span class="sxs-lookup"><span data-stu-id="22730-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
