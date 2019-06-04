---
title: Příklad odloženého provedení (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: c9ac87cf2b2af4114e5a20c211b4a6b3f7fced6b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486106"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="50259-102">Příklad odloženého provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="50259-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="50259-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení vliv na spuštění vašich dotazech LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="50259-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50259-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="50259-104">Example</span></span>  
 <span data-ttu-id="50259-105">Následující příklad ukazuje pořadí provádění, když použijete metodu rozšíření, která používá odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="50259-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="50259-106">V příkladu deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="50259-106">The example declares an array of three strings.</span></span> <span data-ttu-id="50259-107">Pak Iteruje přes kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="50259-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="50259-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="50259-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="50259-109">Všimněte si, že při procházení kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`, každá položka je načten z řetězcového pole zdroje a převedený na velká písmena před další položky se načtou ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="50259-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="50259-110">Uvidíte, že celého pole řetězce není před každou položku v kolekci vrácené, jsou zpracovávána v převedený na velká písmena `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="50259-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="50259-111">Další téma v tomto kurzu ukazuje řetězení dotazů dohromady:</span><span class="sxs-lookup"><span data-stu-id="50259-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="50259-112">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="50259-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="50259-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50259-113">See also</span></span>

- [<span data-ttu-id="50259-114">Kurz: Zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="50259-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
