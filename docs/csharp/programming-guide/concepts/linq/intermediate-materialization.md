---
title: "Zprostředkující Materialization (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 46d347921e24bc5504c69534d7b5c087818a6c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="27752-102">Zprostředkující Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="27752-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="27752-103">Pokud si nejste opatrní, v některých situacích můžete výrazně změnit profilem paměti a výkon vaší aplikace tak, že předčasné materialization kolekcí v dotazech.</span><span class="sxs-lookup"><span data-stu-id="27752-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="27752-104">Některé standardní operátory dotazu způsobit materialization jejich zdrojové kolekci před je jediným elementem.</span><span class="sxs-lookup"><span data-stu-id="27752-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="27752-105">Například <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> nejprve iteruje jeho celý zdrojový kolekce, pak seřadí všechny položky a nakonec vypočítá první položka.</span><span class="sxs-lookup"><span data-stu-id="27752-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="27752-106">To znamená, že je nákladné získat první položka uspořádanou kolekci; Každá položka po tomto datu není nákladné.</span><span class="sxs-lookup"><span data-stu-id="27752-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="27752-107">To dává smysl: by bylo možné pro tento dotaz operátor neurčí jinak.</span><span class="sxs-lookup"><span data-stu-id="27752-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27752-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="27752-108">Example</span></span>  
 <span data-ttu-id="27752-109">Tento příklad mění předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="27752-109">This example alters the previous example.</span></span> <span data-ttu-id="27752-110">`AppendString` Volání metod <xref:System.Linq.Enumerable.ToList%2A> před iterace v rámci zdroji.</span><span class="sxs-lookup"><span data-stu-id="27752-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="27752-111">To způsobí, že materialization.</span><span class="sxs-lookup"><span data-stu-id="27752-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="27752-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="27752-112">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="27752-113">V tomto příkladu můžete uvidíte, že volání <xref:System.Linq.Enumerable.ToList%2A> způsobí, že `AppendString` výčet jeho celý zdrojový před je první položka.</span><span class="sxs-lookup"><span data-stu-id="27752-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="27752-114">Pokud zdroj byly velké pole, by to výrazně změnit paměti profil aplikace.</span><span class="sxs-lookup"><span data-stu-id="27752-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="27752-115">Standardní operátory dotazu lze také zřetězen dohromady.</span><span class="sxs-lookup"><span data-stu-id="27752-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="27752-116">To ukazuje poslední téma v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="27752-116">The final topic in this tutorial illustrates this.</span></span>  
  
-   [<span data-ttu-id="27752-117">Řetězení standardní operátory dotazu společně (C#)</span><span class="sxs-lookup"><span data-stu-id="27752-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="27752-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="27752-118">See Also</span></span>  
 [<span data-ttu-id="27752-119">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="27752-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
