---
title: Výkon zřetězené dotazů (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336362"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="08ef1-102">Výkon zřetězené dotazů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="08ef1-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="08ef1-103">Jednou z nejdůležitějších výhod LINQ (a technologie LINQ to XML) je, že zřetězené dotazy můžete provést i jediný rozsáhlejších, složitějších dotaz.</span><span class="sxs-lookup"><span data-stu-id="08ef1-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="08ef1-104">Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="08ef1-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="08ef1-105">Například v následujícím kódu jednoduchý `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="08ef1-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 <span data-ttu-id="08ef1-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="08ef1-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="08ef1-107">Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace v rámci odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="08ef1-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="08ef1-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Má osa v podstatě stejný výkon jako iterace v rámci odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="08ef1-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="08ef1-109"><xref:System.Xml.Linq.XContainer.Elements%2A> je implementovaný jako iterace s odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="08ef1-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="08ef1-110">To znamená, že některé činnosti provede kromě iterace v rámci odkazovaného seznamu, jako například přidělování objekt iterator a udržování přehledu o stavu spuštění.</span><span class="sxs-lookup"><span data-stu-id="08ef1-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="08ef1-111">Tato práce je možné rozdělit do dvou kategorií: práce, kterou je provést v době je nastavený iterator a práci, kterou se provádí při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="08ef1-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="08ef1-112">Instalační program práce malé, pevné množství práce, a práci při každé iteraci je úměrná počet položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="08ef1-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="08ef1-113">V `query1`, `where` klauzule způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="08ef1-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="08ef1-114">Tato metoda je také implementovaný jako iterace.</span><span class="sxs-lookup"><span data-stu-id="08ef1-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="08ef1-115">Instalační program pracovní se skládá z vytvoření instance delegáta, který bude odkazovat výrazu lambda, plus normální instalace pro iterace.</span><span class="sxs-lookup"><span data-stu-id="08ef1-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="08ef1-116">Přičemž při každém opakování se nazývá delegát provést predikátu.</span><span class="sxs-lookup"><span data-stu-id="08ef1-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="08ef1-117">Instalační program práci a práci při každé iteraci je podobná objem práce při iterace v rámci ose.</span><span class="sxs-lookup"><span data-stu-id="08ef1-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="08ef1-118">V `query1`, klauzule select způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Select%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="08ef1-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="08ef1-119">Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="08ef1-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="08ef1-120">V `query2`, i `where` klauzule a `select` klauzule mají stejný profil výkonu jako v `query1`.</span><span class="sxs-lookup"><span data-stu-id="08ef1-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="08ef1-121">Iterace prostřednictvím `query2` je proto přímo úměrné k počet položek ve zdroji prvního, jinými slovy, lineární doba dotazu.</span><span class="sxs-lookup"><span data-stu-id="08ef1-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="08ef1-122">Odpovídající příklad jazyka Visual Basic by měla mít stejný profil výkonu.</span><span class="sxs-lookup"><span data-stu-id="08ef1-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="08ef1-123">Další informace o iterátory najdete v tématu [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="08ef1-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="08ef1-124">Podrobnější kurz řetězení dotazy společně, najdete v části [kurz: řetězení dotazy společně](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="08ef1-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ef1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="08ef1-125">See Also</span></span>  
 [<span data-ttu-id="08ef1-126">Výkon (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="08ef1-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
