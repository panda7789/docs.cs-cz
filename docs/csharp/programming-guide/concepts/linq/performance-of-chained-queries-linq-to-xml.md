---
title: Výkon zřetězených dotazů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253125"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="58fd3-102">Výkon zřetězených dotazů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58fd3-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="58fd3-103">Jednou z nejdůležitějších výhod LINQ (a LINQ to XML) je to, že zřetězené dotazy můžou provádět i jeden větší a složitější dotaz.</span><span class="sxs-lookup"><span data-stu-id="58fd3-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="58fd3-104">Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz.</span><span class="sxs-lookup"><span data-stu-id="58fd3-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="58fd3-105">Například v následujícím jednoduchém kódu `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="58fd3-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="58fd3-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58fd3-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="58fd3-107">Tento řetězový dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="58fd3-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osa má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="58fd3-109"><xref:System.Xml.Linq.XContainer.Elements%2A>je implementován jako iterátor s odloženým vykonání.</span><span class="sxs-lookup"><span data-stu-id="58fd3-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="58fd3-110">To znamená, že kromě iterace v propojeném seznamu funguje i několik práce, jako je například přidělení objektu iterátoru a udržování přehledu o stavu provádění.</span><span class="sxs-lookup"><span data-stu-id="58fd3-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="58fd3-111">Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v okamžiku nastavení iterátoru, a práce, která se provádí během každé iterace.</span><span class="sxs-lookup"><span data-stu-id="58fd3-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="58fd3-112">Nastavení práce je malé, pevné množství práce a práce prováděná během každé iterace je úměrná počtu položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="58fd3-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="58fd3-113">V `query1` `where` klauzuli klauzule způsobí, <xref:System.Linq.Enumerable.Where%2A> že dotaz volá metodu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="58fd3-114">Tato metoda je také implementována jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="58fd3-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="58fd3-115">Nastavení práce se skládá z vytváření instancí delegáta, který bude odkazovat na výraz lambda, a také na normální nastavení iterátoru.</span><span class="sxs-lookup"><span data-stu-id="58fd3-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="58fd3-116">Při každé iteraci se volá delegát, který spustí predikát.</span><span class="sxs-lookup"><span data-stu-id="58fd3-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="58fd3-117">Nastavení práce a práce provedené během každé iterace jsou podobné práci, kterou jste provedli při iteraci přes osu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="58fd3-118">V `query1`klauzuli select způsobí, že dotaz <xref:System.Linq.Enumerable.Select%2A> vyvolá metodu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="58fd3-119">Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58fd3-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="58fd3-120">V `query2`systémumá `query1`klauzule i klauzule stejný profil výkonu jako v. `select` `where`</span><span class="sxs-lookup"><span data-stu-id="58fd3-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="58fd3-121">Iterace prostřednictvím `query2` je proto přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy, lineárním časem.</span><span class="sxs-lookup"><span data-stu-id="58fd3-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="58fd3-122">Odpovídající příklad Visual Basic by měl stejný profil výkonu.</span><span class="sxs-lookup"><span data-stu-id="58fd3-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="58fd3-123">Další informace o iterátorech najdete v tématu [yield](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="58fd3-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="58fd3-124">Podrobnější kurz o zřetězení dotazů společně najdete v [kurzu: Zřetězení dotazů dohromady](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="58fd3-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
