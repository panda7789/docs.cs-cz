---
title: Přechodná Materializace (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 065a7e0ffadaa48d400d4f4e3e045014b3658213
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667428"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="e46e4-102">Přechodná Materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="e46e4-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="e46e4-103">Pokud si nejste pozor, v některých situacích je možné výrazně změnit profil paměti a výkonu vaší aplikace tak, že předčasné materializace kolekce v dotazech.</span><span class="sxs-lookup"><span data-stu-id="e46e4-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="e46e4-104">Některé operátory standardního dotazu způsobit materializace kolekce zdroje před získávání jeden element.</span><span class="sxs-lookup"><span data-stu-id="e46e4-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="e46e4-105">Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> nejprve Iteruje přes kolekci jeho celý zdrojový pak seřadí všechny položky a nakonec vrací první položky.</span><span class="sxs-lookup"><span data-stu-id="e46e4-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="e46e4-106">To znamená, že se jedná o nákladné získat první položku uspořádanou kolekci; Každá položka po tomto datu není nákladné.</span><span class="sxs-lookup"><span data-stu-id="e46e4-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="e46e4-107">To dává smysl: Bylo by možné pro daný operátor dotazu postupovat jinak.</span><span class="sxs-lookup"><span data-stu-id="e46e4-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e46e4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e46e4-108">Example</span></span>  
 <span data-ttu-id="e46e4-109">Tento příklad upravuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="e46e4-109">This example alters the previous example.</span></span> <span data-ttu-id="e46e4-110">`AppendString` Volání metody <xref:System.Linq.Enumerable.ToList%2A> před provede iterace přes zdrojové.</span><span class="sxs-lookup"><span data-stu-id="e46e4-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="e46e4-111">To způsobí, že materializace.</span><span class="sxs-lookup"><span data-stu-id="e46e4-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="e46e4-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e46e4-112">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="e46e4-113">V tomto příkladu vidíte, že volání <xref:System.Linq.Enumerable.ToList%2A> způsobí, že `AppendString` výčet jeho celý zdrojový před získávání první položky.</span><span class="sxs-lookup"><span data-stu-id="e46e4-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="e46e4-114">Pokud zdroj velkého pole, by to výrazně změnit paměti profilu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e46e4-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="e46e4-115">Také je možné zřetězit standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="e46e4-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="e46e4-116">V posledním tématu v tomto kurzu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="e46e4-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="e46e4-117">Zřetězení standardních dotazovacích operátorů pohromadě (C#)</span><span class="sxs-lookup"><span data-stu-id="e46e4-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="e46e4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e46e4-118">See also</span></span>

- [<span data-ttu-id="e46e4-119">Kurz: Zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e46e4-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
