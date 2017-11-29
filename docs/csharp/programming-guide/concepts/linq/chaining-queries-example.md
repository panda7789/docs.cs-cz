---
title: "Řetězení příklad dotazů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74d3dcaca686487d79a90f28faf4d9c00218f6a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="9550c-102">Řetězení příklad dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="9550c-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="9550c-103">Tento příklad vychází z předchozího příkladu a zobrazuje, co se stane, když jste řetězu společně dva dotazy, které obě používají odložené provedení a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9550c-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9550c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9550c-104">Example</span></span>  
 <span data-ttu-id="9550c-105">V tomto příkladu je zavádí další metodou rozšíření, `AppendString`, který připojí zadaný řetězec na každý řetězec ve zdrojové kolekci a pak vypočítá nových řetězců.</span><span class="sxs-lookup"><span data-stu-id="9550c-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="9550c-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9550c-106">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="9550c-107">V tomto příkladu vidíte, že každá metoda rozšíření funguje postupně pro každou položku ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="9550c-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="9550c-108">Co by měl být vymazat z tohoto příkladu je, že i když budeme mít zřetězen dohromady dotazy, které vrací kolekce, jsou materializována žádné zprostředkující kolekce.</span><span class="sxs-lookup"><span data-stu-id="9550c-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="9550c-109">Místo toho každá položka předat z jedné opožděné metody na další.</span><span class="sxs-lookup"><span data-stu-id="9550c-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="9550c-110">Výsledkem mnohem menší nároky paměti než přístup, které by nejprve trvat jedno pole řetězců, a poté vytvořit druhé pole řetězců, které mají byl převeden na velká písmena a nakonec vytvořte třetí pole řetězců, kde má každý řetězec vykřičníku body, přidá se k němu.</span><span class="sxs-lookup"><span data-stu-id="9550c-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="9550c-111">Další téma v tomto kurzu znázorňuje zprostředkující materialization:</span><span class="sxs-lookup"><span data-stu-id="9550c-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
-   [<span data-ttu-id="9550c-112">Zprostředkující Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="9550c-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="9550c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9550c-113">See Also</span></span>  
 [<span data-ttu-id="9550c-114">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="9550c-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
