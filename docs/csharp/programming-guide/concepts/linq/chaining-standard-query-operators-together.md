---
title: Zřetězení standardních dotazovacích operátorů pohromadě (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 71b364d76860b5daa21ea176947d9cfe9d49b308
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668439"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="7ff89-102">Zřetězení standardních dotazovacích operátorů pohromadě (C#)</span><span class="sxs-lookup"><span data-stu-id="7ff89-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="7ff89-103">Toto je poslední téma v [kurzu: Zřetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="7ff89-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) tutorial.</span></span>  
  
 <span data-ttu-id="7ff89-104">Také je možné zřetězit standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="7ff89-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="7ff89-105">Například můžete interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor a také funguje opožděné způsobem.</span><span class="sxs-lookup"><span data-stu-id="7ff89-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="7ff89-106">Žádné mezilehlých výsledků jsou materializovaného tímto plánem.</span><span class="sxs-lookup"><span data-stu-id="7ff89-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ff89-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ff89-107">Example</span></span>  
 <span data-ttu-id="7ff89-108">V tomto příkladu <xref:System.Linq.Enumerable.Where%2A> metoda je volána před voláním `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="7ff89-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="7ff89-109"><xref:System.Linq.Enumerable.Where%2A> Metoda funguje v téměř stejným způsobem jako opožděné metod používaných v předchozích příkladech v tomto kurzu `ConvertCollectionToUpperCase` a `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="7ff89-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="7ff89-110">Jedním rozdílem je, že v tomto případě <xref:System.Linq.Enumerable.Where%2A> metoda prochází dochází k rozdělení kolekce, zjistí, že první položka nepředává predikátu a potom získá další položky, které předávají.</span><span class="sxs-lookup"><span data-stu-id="7ff89-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="7ff89-111">Pak bude vrácen druhé položky.</span><span class="sxs-lookup"><span data-stu-id="7ff89-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="7ff89-112">Základní myšlenka je však stejný: Pokud mají být nejsou vyhodnocena zprostředkující kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ff89-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="7ff89-113">V případě – výrazy dotazů používají, jsou převedeny na volání do standardních operátorů pro dotazování a stejné zásady platí.</span><span class="sxs-lookup"><span data-stu-id="7ff89-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="7ff89-114">Všechny příklady v této části, které jsou dotazování na dokumenty Office Open XML používat stejný princip.</span><span class="sxs-lookup"><span data-stu-id="7ff89-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="7ff89-115">Odložené provedení a opožděné vyhodnocení jsou některé základní koncepty, musíte porozumět efektivně používat LINQ (a LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="7ff89-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="7ff89-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7ff89-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ff89-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ff89-117">See also</span></span>

- [<span data-ttu-id="7ff89-118">Kurz: Zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="7ff89-118">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
