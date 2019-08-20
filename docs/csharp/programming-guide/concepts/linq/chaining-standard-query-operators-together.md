---
title: Zřetězení standardních operátorů dotazů (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 89cf7f526bdc60881e901d7ca8f556e97488b220
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594837"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="77ca4-102">Zřetězení standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="77ca4-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="77ca4-103">Toto je poslední téma v [tomto kurzu: Zřetězení dotazů spolu (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) kurz.</span><span class="sxs-lookup"><span data-stu-id="77ca4-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="77ca4-104">Standardní operátory dotazu je také možné zřetězit dohromady.</span><span class="sxs-lookup"><span data-stu-id="77ca4-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="77ca4-105">Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a funguje také opožděným způsobem.</span><span class="sxs-lookup"><span data-stu-id="77ca4-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="77ca4-106">Žádné mezilehlé výsledky nejsou materializované.</span><span class="sxs-lookup"><span data-stu-id="77ca4-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77ca4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="77ca4-107">Example</span></span>  
 <span data-ttu-id="77ca4-108">V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> je metoda volána před voláním `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="77ca4-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="77ca4-109">Metoda pracuje téměř přesně stejným způsobem jako opožděné metody používané v předchozích příkladech v tomto `ConvertCollectionToUpperCase` kurzu a `AppendString`. <xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="77ca4-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="77ca4-110">Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> Metoda prochází ze své zdrojové kolekce, určuje, že první položka neprojde predikátem, a poté získá další položku, která je předána.</span><span class="sxs-lookup"><span data-stu-id="77ca4-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="77ca4-111">Následně výsledkem bude druhá položka.</span><span class="sxs-lookup"><span data-stu-id="77ca4-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="77ca4-112">Základní nápad je však stejný: Mezilehlé kolekce nejsou materializované, pokud je nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="77ca4-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="77ca4-113">Pokud jsou výrazy dotazu použity, jsou převedeny na volání standardních operátorů dotazu a platí stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="77ca4-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="77ca4-114">Všechny příklady v této části, které se dotazují na dokumenty Office Open XML, používají stejný princip.</span><span class="sxs-lookup"><span data-stu-id="77ca4-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="77ca4-115">Odložené provádění a opožděné hodnocení jsou některé ze základních konceptů, které je potřeba pochopit, abyste mohli efektivně používat LINQ (a LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="77ca4-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
            where s.CompareTo("D") >= 0  
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
  
 <span data-ttu-id="77ca4-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="77ca4-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  