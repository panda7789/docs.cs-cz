---
title: Příklad odloženého provedení (C#)
description: Informace o tom, jak odložené provádění a opožděné vyhodnocení ovlivňuje provádění vašich LINQ to XML dotazů v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 65ba4cc150f2fc9d8f44aee352987ea0eeaab0a5
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103953"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="2c5cf-103">Příklad odloženého provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5cf-103">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="2c5cf-104">Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2c5cf-104">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c5cf-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c5cf-105">Example</span></span>  
 <span data-ttu-id="2c5cf-106">Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="2c5cf-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="2c5cf-107">Příklad deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="2c5cf-107">The example declares an array of three strings.</span></span> <span data-ttu-id="2c5cf-108">Poté provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="2c5cf-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="2c5cf-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c5cf-109">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="2c5cf-110">Všimněte si, že při iteraci v kolekci `ConvertCollectionToUpperCase` , kterou vrátí, každá položka je načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="2c5cf-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="2c5cf-111">Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje ve `foreach` smyčce v `Main` .</span><span class="sxs-lookup"><span data-stu-id="2c5cf-111">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="2c5cf-112">Další téma v tomto kurzu znázorňuje zřetězení dotazů dohromady:</span><span class="sxs-lookup"><span data-stu-id="2c5cf-112">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="2c5cf-113">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5cf-113">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c5cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c5cf-114">See also</span></span>

- [<span data-ttu-id="2c5cf-115">Kurz: zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5cf-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
