---
title: Příklad odloženého provedení (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: a934645d0d7ad807e1524031ca3f023f7b11c5b4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594555"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="81ca9-102">Příklad odloženého provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="81ca9-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="81ca9-103">Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="81ca9-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81ca9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="81ca9-104">Example</span></span>  
 <span data-ttu-id="81ca9-105">Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="81ca9-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="81ca9-106">Příklad deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="81ca9-106">The example declares an array of three strings.</span></span> <span data-ttu-id="81ca9-107">Poté provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="81ca9-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="81ca9-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="81ca9-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="81ca9-109">Všimněte si, že při iteraci v kolekci `ConvertCollectionToUpperCase`, kterou vrátí, každá položka je načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="81ca9-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="81ca9-110">Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje ve `foreach` smyčce v `Main`.</span><span class="sxs-lookup"><span data-stu-id="81ca9-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="81ca9-111">Další téma v tomto kurzu znázorňuje zřetězení dotazů dohromady:</span><span class="sxs-lookup"><span data-stu-id="81ca9-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="81ca9-112">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="81ca9-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="81ca9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81ca9-113">See also</span></span>

- [<span data-ttu-id="81ca9-114">Kurz: Zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="81ca9-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
