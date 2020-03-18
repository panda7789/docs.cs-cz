---
title: Výkon zřetězených dotazů (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253125"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="bb6d2-102">Výkon zřetězených dotazů (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bb6d2-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="bb6d2-103">Jednou z nejdůležitějších výhod LINQ (a LINQ na XML) je, že zřetězené dotazy lze provádět, stejně jako jeden větší, složitější dotaz.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="bb6d2-104">Zřetězený dotaz je dotaz, který používá jiný dotaz jako jeho zdroj.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="bb6d2-105">Například v následujícím jednoduchém `query2` `query1` kódu má jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="bb6d2-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="bb6d2-106">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bb6d2-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="bb6d2-107">Tento zřetězený dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="bb6d2-108">Osa <xref:System.Xml.Linq.XContainer.Elements%2A> má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="bb6d2-109"><xref:System.Xml.Linq.XContainer.Elements%2A>implementována jako iterátor s odloženým prováděním.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="bb6d2-110">To znamená, že provádí některé práce kromě iterace prostřednictvím propojeného seznamu, jako je například přidělení objektu iterátoru a sledování stavu spuštění.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="bb6d2-111">Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v době, kdy je nastaven iterátor a práce, která se provádí během každé iterace.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="bb6d2-112">Instalační práce je malé, pevné množství práce a práce vykonaná během každé iterace je úměrná počtu položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="bb6d2-113">V `query1`aplikaci klauzule `where` způsobí, <xref:System.Linq.Enumerable.Where%2A> že dotaz volá metodu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="bb6d2-114">Tato metoda je také implementována jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="bb6d2-115">Instalační práce se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, plus normální nastavení pro iterátor.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="bb6d2-116">S každou iterací delegát je volána ke spuštění predikátu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="bb6d2-117">Práce na nastavení a práce vykonaná během každé iterace je podobná práci vykonanou při iteraci přes osu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="bb6d2-118">V `query1`aplikaci klauzule select způsobí, že dotaz zavolá metodu. <xref:System.Linq.Enumerable.Select%2A></span><span class="sxs-lookup"><span data-stu-id="bb6d2-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="bb6d2-119">Tato metoda má stejný profil <xref:System.Linq.Enumerable.Where%2A> výkonu jako metoda.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="bb6d2-120">V `query2`oblasti `where` mají klauzule i klauzule `select` stejný `query1`profil výkonnosti jako v .</span><span class="sxs-lookup"><span data-stu-id="bb6d2-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="bb6d2-121">Iterace `query2` prostřednictvím je tedy přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy lineární čas.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="bb6d2-122">Odpovídající příklad jazyka visual basic by mít stejný profil výkonu.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="bb6d2-123">Další informace o iterátorech naleznete v tématu [yield](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="bb6d2-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="bb6d2-124">Podrobnější návod na řetězení dotazů společně naleznete v [tématu Výuka: Řetězení dotazů společně](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bb6d2-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
