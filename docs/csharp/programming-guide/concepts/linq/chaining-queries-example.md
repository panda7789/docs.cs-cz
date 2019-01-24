---
title: Příklad řetězení dotazů (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: b77de6b1e5bd81ac70165640aecf0d4ce89be03d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677345"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="0bd03-102">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0bd03-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="0bd03-103">Tento příklad vychází z předchozího příkladu a ukazuje, co se stane, když je řetězec společně dva dotazy, které obě používají odložené provedení a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="0bd03-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bd03-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bd03-104">Example</span></span>  
 <span data-ttu-id="0bd03-105">V tomto příkladu se používá jinou metodu rozšíření, `AppendString`, který připojí zadaný řetězec do každého řetězce ve zdrojové kolekci a pak provede nové řetězce.</span><span class="sxs-lookup"><span data-stu-id="0bd03-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="0bd03-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0bd03-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="0bd03-107">V tomto příkladu vidíte, že funguje každá metoda rozšíření postupně pro každou položku v kolekci zdroje.</span><span class="sxs-lookup"><span data-stu-id="0bd03-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="0bd03-108">Co by mělo být jasné z tohoto příkladu je, že i když jsme mají zřetězit, dotazy, které vrací kolekce, jsou materializovaného zprostředkující se žádné kolekce.</span><span class="sxs-lookup"><span data-stu-id="0bd03-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="0bd03-109">Místo toho každá položka je předán z jedné metody opožděné na další.</span><span class="sxs-lookup"><span data-stu-id="0bd03-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="0bd03-110">Výsledkem mnohem menší nároky na paměť než přístupu, které by nejdřív proveďte jedno pole řetězců, pak vytvořte druhé pole řetězců, které byly převedeny na velká písmena a nakonec vytvořit třetí pole řetězců, kde má každý řetězec vykřičník body připojí k němu.</span><span class="sxs-lookup"><span data-stu-id="0bd03-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="0bd03-111">Další téma v tomto kurzu ukazuje přechodná materializace:</span><span class="sxs-lookup"><span data-stu-id="0bd03-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
-   [<span data-ttu-id="0bd03-112">Přechodná Materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="0bd03-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="0bd03-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bd03-113">See also</span></span>

- [<span data-ttu-id="0bd03-114">Kurz: Zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0bd03-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
