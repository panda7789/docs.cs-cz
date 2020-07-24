---
title: Příklad řetězení dotazů (C#)
description: Tento příklad ukazuje, co se stane při zřetězení dvou dotazů, které používají odložené provádění a opožděné vyhodnocení v jazyce C#.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105543"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="c4b35-103">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b35-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="c4b35-104">Tento příklad sestaví v předchozím příkladu a ukazuje, co se stane, když zřetězení dvou dotazů, které používají odložené provádění a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c4b35-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b35-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4b35-105">Example</span></span>  
 <span data-ttu-id="c4b35-106">V tomto příkladu je zavedena jiná rozšiřující metoda, `AppendString` která připojí zadaný řetězec ke každému řetězci ve zdrojové kolekci a následně vytvoří nové řetězce.</span><span class="sxs-lookup"><span data-stu-id="c4b35-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c4b35-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4b35-107">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="c4b35-108">V tomto příkladu vidíte, že každá metoda rozšíření funguje postupně pro každou položku ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="c4b35-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="c4b35-109">To, co by mělo být z tohoto příkladu jasné, je, že i když jsme zřetězené dotazy, které poskytují kolekce, nematerializují žádné zprostředkující kolekce.</span><span class="sxs-lookup"><span data-stu-id="c4b35-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="c4b35-110">Místo toho je každá položka předána z jedné opožděné metody do další.</span><span class="sxs-lookup"><span data-stu-id="c4b35-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="c4b35-111">To vede k mnohem menšímu nároky na paměť než k přístupu, který by nejdřív přijal jedno pole řetězců, pak vytvoří druhé pole řetězců, které se převedlo na velká písmena, a nakonec vytvoří třetí pole řetězců, kde se ke každému řetězci připojí vykřičník.</span><span class="sxs-lookup"><span data-stu-id="c4b35-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="c4b35-112">Další téma v tomto kurzu ilustruje mezilehlé vymaterializování:</span><span class="sxs-lookup"><span data-stu-id="c4b35-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="c4b35-113">Zprostředkující materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b35-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4b35-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4b35-114">See also</span></span>

- [<span data-ttu-id="c4b35-115">Kurz: zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b35-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
