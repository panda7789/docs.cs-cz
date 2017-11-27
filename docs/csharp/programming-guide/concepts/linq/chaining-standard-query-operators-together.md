---
title: "Řetězení standardní operátory dotazu společně (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 47e936bffd79784b0ee6850bfc29d1d1f5b3224d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="44b2c-102">Řetězení standardní operátory dotazu společně (C#)</span><span class="sxs-lookup"><span data-stu-id="44b2c-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="44b2c-103">Toto je poslední téma v [kurz: řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="44b2c-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) tutorial.</span></span>  
  
 <span data-ttu-id="44b2c-104">Také můžete se propojit standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="44b2c-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="44b2c-105">Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také funguje opožděné způsobem.</span><span class="sxs-lookup"><span data-stu-id="44b2c-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="44b2c-106">Tímto se materializovat žádné mezilehlých výsledků.</span><span class="sxs-lookup"><span data-stu-id="44b2c-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b2c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b2c-107">Example</span></span>  
 <span data-ttu-id="44b2c-108">V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> metoda je volána před provedením volání `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="44b2c-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="44b2c-109"><xref:System.Linq.Enumerable.Where%2A> Metoda funguje v téměř úplně stejně jako opožděné metody použité v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="44b2c-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="44b2c-110">Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> metoda iteruje zdrojová kolekce, zjistí, že první položka nepředává predikátu a pak získá další položky, které předávají.</span><span class="sxs-lookup"><span data-stu-id="44b2c-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="44b2c-111">Vypočítá pak druhou položku.</span><span class="sxs-lookup"><span data-stu-id="44b2c-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="44b2c-112">Však základní Rada je stejný: zprostředkující kolekce nejsou materializována, pokud mají být.</span><span class="sxs-lookup"><span data-stu-id="44b2c-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="44b2c-113">Pokud se používají výrazy dotazů, se převedou na volání standardní operátory dotazu a stejné zásady platí.</span><span class="sxs-lookup"><span data-stu-id="44b2c-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="44b2c-114">Všechny příklady v této části, které se dotazuje dokumenty používají stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="44b2c-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="44b2c-115">Odložené provedení a opožděné vyhodnocení jsou některé základní koncepty, musíte pochopit efektivně používat LINQ (a technologie LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="44b2c-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="44b2c-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44b2c-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a><span data-ttu-id="44b2c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="44b2c-117">See Also</span></span>  
 [<span data-ttu-id="44b2c-118">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="44b2c-118">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
