---
title: Zprostředkující materializace (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253166"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="94db9-102">Zprostředkující materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="94db9-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="94db9-103">Pokud nejste opatrní, v některých situacích můžete významně změnit velikost paměti a profilu výkonu aplikace tím, že ve svých dotazech dojde k předčasnému materializování kolekcí.</span><span class="sxs-lookup"><span data-stu-id="94db9-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="94db9-104">Některé standardní operátory dotazu způsobují materializaci své zdrojové kolekce před tím, než budou vracet jediný element.</span><span class="sxs-lookup"><span data-stu-id="94db9-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="94db9-105">Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> první projde celou zdrojovou kolekcí a pak seřadí všechny položky a nakonec vyřadí první položku.</span><span class="sxs-lookup"><span data-stu-id="94db9-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="94db9-106">To znamená, že je nákladné získat první položku seřazené kolekce. u každé položky pak není nákladné.</span><span class="sxs-lookup"><span data-stu-id="94db9-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="94db9-107">To je smysl: To by nebylo možné, aby tento operátor dotazu jinak nepoužil.</span><span class="sxs-lookup"><span data-stu-id="94db9-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94db9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="94db9-108">Example</span></span>  
 <span data-ttu-id="94db9-109">Tento příklad změní předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="94db9-109">This example alters the previous example.</span></span> <span data-ttu-id="94db9-110">`AppendString` Metoda volá<xref:System.Linq.Enumerable.ToList%2A> před iterací ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="94db9-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="94db9-111">Příčinou je materializace.</span><span class="sxs-lookup"><span data-stu-id="94db9-111">This causes materialization.</span></span>  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
  
 <span data-ttu-id="94db9-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="94db9-112">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="94db9-113">V tomto příkladu vidíte, že volání z důvodu <xref:System.Linq.Enumerable.ToList%2A> `AppendString` vyčíslení celého zdroje před vyvoláním první položky.</span><span class="sxs-lookup"><span data-stu-id="94db9-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="94db9-114">Pokud by byl zdrojem velké pole, významně byste tím změnili profil paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="94db9-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="94db9-115">Standardní operátory dotazu je také možné zřetězit dohromady.</span><span class="sxs-lookup"><span data-stu-id="94db9-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="94db9-116">Toto je znázorněno v posledním tématu tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="94db9-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="94db9-117">Zřetězení standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="94db9-117">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="94db9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94db9-118">See also</span></span>

- [<span data-ttu-id="94db9-119">Kurz: Zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="94db9-119">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
