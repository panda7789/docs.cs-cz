---
title: Zřetězení operátorů standardních dotazů dohromady (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204206"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="6a533-102">Zřetězení operátorů standardních dotazů dohromady (C#)</span><span class="sxs-lookup"><span data-stu-id="6a533-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="6a533-103">Toto je poslední téma v [kurzu: Řetězení dotazy společně (C#).](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="6a533-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="6a533-104">Standardní operátory dotazu lze také zřetězit dohromady.</span><span class="sxs-lookup"><span data-stu-id="6a533-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="6a533-105">Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také pracuje v líné způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a533-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="6a533-106">Nezhmotňují se žádné průběžné výsledky.</span><span class="sxs-lookup"><span data-stu-id="6a533-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a533-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a533-107">Example</span></span>  
 <span data-ttu-id="6a533-108">V tomto příkladu je metoda `ConvertCollectionToUpperCase`volána před voláním <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="6a533-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="6a533-109">Metoda <xref:System.Linq.Enumerable.Where%2A> funguje téměř přesně stejným způsobem jako opožděné metody použité v `ConvertCollectionToUpperCase` předchozích příkladech v tomto kurzu a `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="6a533-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="6a533-110">Jeden rozdíl je, že <xref:System.Linq.Enumerable.Where%2A> v tomto případě metoda iterates prostřednictvím své zdrojové kolekce, určuje, že první položka neprojde predikáta a pak získá další položku, která přejde.</span><span class="sxs-lookup"><span data-stu-id="6a533-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="6a533-111">Potom dává druhou položku.</span><span class="sxs-lookup"><span data-stu-id="6a533-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="6a533-112">Základní myšlenka je však stejná: Zprostředkující kolekce se nezhmotňují, pokud nemusí být.</span><span class="sxs-lookup"><span data-stu-id="6a533-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="6a533-113">Při použití výrazů dotazu jsou převedeny na volání standardních operátorů dotazů a platí stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="6a533-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="6a533-114">Všechny příklady v této části, které se dotazují na dokumenty Office Open XML, používají stejný princip.</span><span class="sxs-lookup"><span data-stu-id="6a533-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="6a533-115">Odložené spuštění a opožděné vyhodnocení jsou některé základní koncepty, které je nutné pochopit efektivně používat LINQ (a LINQ na XML).</span><span class="sxs-lookup"><span data-stu-id="6a533-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="6a533-116">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6a533-116">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
