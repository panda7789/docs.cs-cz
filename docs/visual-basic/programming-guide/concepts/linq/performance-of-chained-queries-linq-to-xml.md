---
title: Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 69ed09addb50ac45e7b46cd0322d4df076b5875b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834955"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="afb93-102">Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb93-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="afb93-103">Jednou z nejdůležitějších výhod LINQ (a LINQ to XML) je to, že zřetězené dotazy můžou provádět i jeden větší a složitější dotaz.</span><span class="sxs-lookup"><span data-stu-id="afb93-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="afb93-104">Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz.</span><span class="sxs-lookup"><span data-stu-id="afb93-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="afb93-105">Například v následujícím jednoduchém kódu `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="afb93-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="afb93-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="afb93-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="afb93-107">Tento řetězový dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="afb93-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="afb93-108">Osa <xref:System.Xml.Linq.XContainer.Elements%2A> má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="afb93-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="afb93-109"><xref:System.Xml.Linq.XContainer.Elements%2A> se implementuje jako iterátor s odloženým vykonání.</span><span class="sxs-lookup"><span data-stu-id="afb93-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="afb93-110">To znamená, že kromě iterace v propojeném seznamu funguje i několik práce, jako je například přidělení objektu iterátoru a udržování přehledu o stavu provádění.</span><span class="sxs-lookup"><span data-stu-id="afb93-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="afb93-111">Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v okamžiku nastavení iterátoru, a práce, která se provádí během každé iterace.</span><span class="sxs-lookup"><span data-stu-id="afb93-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="afb93-112">Nastavení práce je malé, pevné množství práce a práce prováděná během každé iterace je úměrná počtu položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="afb93-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="afb93-113">V `query1` klauzule `Where` způsobí, že dotaz vyvolá metodu <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="afb93-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="afb93-114">Tato metoda je také implementována jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="afb93-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="afb93-115">Nastavení práce se skládá z vytváření instancí delegáta, který bude odkazovat na výraz lambda, a také na normální nastavení iterátoru.</span><span class="sxs-lookup"><span data-stu-id="afb93-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="afb93-116">Při každé iteraci se volá delegát, který spustí predikát.</span><span class="sxs-lookup"><span data-stu-id="afb93-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="afb93-117">Nastavení práce a práce provedené během každé iterace jsou podobné práci, kterou jste provedli při iteraci přes osu.</span><span class="sxs-lookup"><span data-stu-id="afb93-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="afb93-118">V `query1` klauzule SELECT způsobí, že dotaz volá metodu <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="afb93-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="afb93-119">Tato metoda má stejný profil výkonu jako metoda <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="afb93-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="afb93-120">V `query2` má klauzule `Where` i klauzule `Select` stejný profil výkonu jako v `query1`.</span><span class="sxs-lookup"><span data-stu-id="afb93-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="afb93-121">Iterace prostřednictvím `query2` je proto přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy, lineárním časem.</span><span class="sxs-lookup"><span data-stu-id="afb93-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="afb93-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afb93-122">See also</span></span>

- [<span data-ttu-id="afb93-123">Výkon (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb93-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
