---
title: Příklad zřetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205417"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="4591b-102">Příklad zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="4591b-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="4591b-103">Tento příklad vychází z předchozího příkladu a ukazuje, co se stane, když zřetězení dohromady dva dotazy, které oba používají odložené spuštění a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="4591b-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4591b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4591b-104">Example</span></span>  
 <span data-ttu-id="4591b-105">V tomto příkladu je zavedena `AppendString`jiná metoda rozšíření , která připojí zadaný řetězec ke každému řetězci ve zdrojové kolekci a pak dává nové řetězce.</span><span class="sxs-lookup"><span data-stu-id="4591b-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="4591b-106">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4591b-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="4591b-107">V tomto příkladu uvidíte, že každá metoda rozšíření pracuje jeden po druhém pro každou položku ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="4591b-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="4591b-108">Co by mělo být jasné z tohoto příkladu je, že i když jsme zřetězené společně dotazy, které výnos kolekce, žádné zprostředkující kolekce jsou materialized.</span><span class="sxs-lookup"><span data-stu-id="4591b-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="4591b-109">Místo toho každá položka je předánz jedné opožděné metody na další.</span><span class="sxs-lookup"><span data-stu-id="4591b-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="4591b-110">Výsledkem je mnohem menší nároky na paměť než přístup, který by nejprve trvat jedno pole řetězců, pak vytvořit druhé pole řetězců, které byly převedeny na velká písmena a nakonec vytvořit třetí pole řetězců, kde každý řetězec má vykřičník připojených bodů.</span><span class="sxs-lookup"><span data-stu-id="4591b-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="4591b-111">Další téma v tomto kurzu ilustruje zprostředkující materializaci:</span><span class="sxs-lookup"><span data-stu-id="4591b-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="4591b-112">Zprostředkující materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="4591b-112">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="4591b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4591b-113">See also</span></span>

- [<span data-ttu-id="4591b-114">Kurz: Řetězení dotazů dohromady (C#)</span><span class="sxs-lookup"><span data-stu-id="4591b-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
