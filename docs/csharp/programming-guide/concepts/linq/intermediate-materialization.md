---
title: Zprostředkující materializace (C#)
description: Tento příklad v jazyce C# ukazuje zprostředkující materializaci, kde dotaz způsobí, že AppendString vytvoří výčet celého zdroje před tím, než vrátí první položku.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165721"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="3c1de-103">Zprostředkující materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="3c1de-103">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="3c1de-104">Pokud nejste opatrní, v některých situacích můžete významně změnit velikost paměti a profilu výkonu aplikace tím, že ve svých dotazech dojde k předčasnému materializování kolekcí.</span><span class="sxs-lookup"><span data-stu-id="3c1de-104">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="3c1de-105">Některé standardní operátory dotazu způsobují materializaci své zdrojové kolekce před tím, než budou vracet jediný element.</span><span class="sxs-lookup"><span data-stu-id="3c1de-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="3c1de-106">Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> první projde celou zdrojovou kolekcí a pak seřadí všechny položky a nakonec vyřadí první položku.</span><span class="sxs-lookup"><span data-stu-id="3c1de-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="3c1de-107">To znamená, že je nákladné získat první položku seřazené kolekce. u každé položky pak není nákladné.</span><span class="sxs-lookup"><span data-stu-id="3c1de-107">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="3c1de-108">To je vhodné: může být nemožné, aby tento operátor dotazu jinak nepoužil.</span><span class="sxs-lookup"><span data-stu-id="3c1de-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1de-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c1de-109">Example</span></span>  
 <span data-ttu-id="3c1de-110">Tento příklad změní předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="3c1de-110">This example alters the previous example.</span></span> <span data-ttu-id="3c1de-111">`AppendString`Metoda volá <xref:System.Linq.Enumerable.ToList%2A> před iterací ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="3c1de-111">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="3c1de-112">Příčinou je materializace.</span><span class="sxs-lookup"><span data-stu-id="3c1de-112">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="3c1de-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3c1de-113">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="3c1de-114">V tomto příkladu vidíte, že volání z důvodu vyčíslení <xref:System.Linq.Enumerable.ToList%2A> `AppendString` celého zdroje před vyvoláním první položky.</span><span class="sxs-lookup"><span data-stu-id="3c1de-114">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="3c1de-115">Pokud by byl zdrojem velké pole, významně byste tím změnili profil paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c1de-115">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="3c1de-116">Standardní operátory dotazu je také možné zřetězit dohromady.</span><span class="sxs-lookup"><span data-stu-id="3c1de-116">Standard query operators can also be chained together.</span></span> <span data-ttu-id="3c1de-117">Toto je znázorněno v posledním tématu tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3c1de-117">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="3c1de-118">Zřetězení standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="3c1de-118">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c1de-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c1de-119">See also</span></span>

- [<span data-ttu-id="3c1de-120">Kurz: zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="3c1de-120">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
