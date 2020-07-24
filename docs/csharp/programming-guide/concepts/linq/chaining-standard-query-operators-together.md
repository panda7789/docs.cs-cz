---
title: Zřetězení standardních operátorů dotazu (C#)
description: Tento příklad ukazuje, jak lze v jazyce C# také zřetězit standardní operátory dotazu. Dotaz nevyhodnotit mezilehlé výsledky.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104067"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="9d137-104">Zřetězení standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="9d137-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="9d137-105">Toto je poslední téma v [kurzu: zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="9d137-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="9d137-106">Standardní operátory dotazu je také možné zřetězit dohromady.</span><span class="sxs-lookup"><span data-stu-id="9d137-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="9d137-107">Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a funguje také opožděným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9d137-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="9d137-108">Žádné mezilehlé výsledky nejsou materializované.</span><span class="sxs-lookup"><span data-stu-id="9d137-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d137-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d137-109">Example</span></span>  
 <span data-ttu-id="9d137-110">V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> je metoda volána před voláním `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="9d137-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="9d137-111"><xref:System.Linq.Enumerable.Where%2A>Metoda pracuje téměř přesně stejným způsobem jako opožděné metody používané v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString` .</span><span class="sxs-lookup"><span data-stu-id="9d137-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="9d137-112">Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> Metoda prochází ze své zdrojové kolekce, určuje, že první položka neprojde predikátem, a poté získá další položku, která je předána.</span><span class="sxs-lookup"><span data-stu-id="9d137-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="9d137-113">Následně výsledkem bude druhá položka.</span><span class="sxs-lookup"><span data-stu-id="9d137-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="9d137-114">Základní nápad je ale stejný: zprostředkující kolekce nejsou materializované, pokud je nemusíte.</span><span class="sxs-lookup"><span data-stu-id="9d137-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="9d137-115">Pokud jsou výrazy dotazu použity, jsou převedeny na volání standardních operátorů dotazu a platí stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="9d137-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="9d137-116">Všechny příklady v této části, které se dotazují na dokumenty Office Open XML, používají stejný princip.</span><span class="sxs-lookup"><span data-stu-id="9d137-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="9d137-117">Odložené provádění a opožděné hodnocení jsou některé ze základních konceptů, které je potřeba pochopit, abyste mohli efektivně používat LINQ (a LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="9d137-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="9d137-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9d137-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
