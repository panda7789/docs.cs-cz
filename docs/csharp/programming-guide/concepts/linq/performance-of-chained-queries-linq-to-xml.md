---
title: Výkon zřetězených dotazů (LINQ to XML) (C#)
description: Přečtěte si o výkonu zřetězených dotazů. Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz.
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 1e9173e85845dd085f4d7bf6deec7eb498acd7f3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302851"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="c0d4d-104">Výkon zřetězených dotazů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c0d4d-104">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="c0d4d-105">Jednou z nejdůležitějších výhod LINQ (a LINQ to XML) je to, že zřetězené dotazy můžou provádět i jeden větší a složitější dotaz.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-105">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="c0d4d-106">Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-106">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="c0d4d-107">Například v následujícím jednoduchém kódu `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="c0d4d-107">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="c0d4d-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c0d4d-108">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="c0d4d-109">Tento řetězový dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-109">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="c0d4d-110"><xref:System.Xml.Linq.XContainer.Elements%2A>Osa má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-110">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="c0d4d-111"><xref:System.Xml.Linq.XContainer.Elements%2A>je implementován jako iterátor s odloženým vykonání.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-111"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="c0d4d-112">To znamená, že kromě iterace v propojeném seznamu funguje i několik práce, jako je například přidělení objektu iterátoru a udržování přehledu o stavu provádění.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-112">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="c0d4d-113">Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v okamžiku nastavení iterátoru, a práce, která se provádí během každé iterace.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-113">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="c0d4d-114">Nastavení práce je malé, pevné množství práce a práce prováděná během každé iterace je úměrná počtu položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-114">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="c0d4d-115">V `query1` `where` klauzuli klauzule způsobí, že dotaz volá <xref:System.Linq.Enumerable.Where%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-115">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="c0d4d-116">Tato metoda je také implementována jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-116">This method is also implemented as an iterator.</span></span> <span data-ttu-id="c0d4d-117">Nastavení práce se skládá z vytváření instancí delegáta, který bude odkazovat na výraz lambda, a také na normální nastavení iterátoru.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-117">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="c0d4d-118">Při každé iteraci se volá delegát, který spustí predikát.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-118">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="c0d4d-119">Nastavení práce a práce provedené během každé iterace jsou podobné práci, kterou jste provedli při iteraci přes osu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-119">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="c0d4d-120">V `query1` klauzuli select způsobí, že dotaz vyvolá <xref:System.Linq.Enumerable.Select%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-120">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="c0d4d-121">Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-121">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="c0d4d-122">V systému `query2` `where` má klauzule i `select` klauzule stejný profil výkonu jako v `query1` .</span><span class="sxs-lookup"><span data-stu-id="c0d4d-122">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="c0d4d-123">Iterace prostřednictvím `query2` je proto přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy, lineárním časem.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-123">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="c0d4d-124">Odpovídající příklad Visual Basic by měl stejný profil výkonu.</span><span class="sxs-lookup"><span data-stu-id="c0d4d-124">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="c0d4d-125">Další informace o iterátorech najdete v tématu [yield](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="c0d4d-125">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="c0d4d-126">Podrobnější kurz o zřetězení dotazů společně najdete v tématu [kurz: zřetězení dotazů](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c0d4d-126">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
