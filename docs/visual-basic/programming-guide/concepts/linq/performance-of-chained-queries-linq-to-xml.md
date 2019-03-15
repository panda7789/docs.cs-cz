---
title: Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8634ca224f5892918721996114649c392a5080a0
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845573"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="27afd-102">Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27afd-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="27afd-103">Jednou z vašich nejdůležitějších výhod LINQ (a LINQ to XML) je, že zřetězených dotazů můžete provádět i pomocí jediného dotazu větší a složitější.</span><span class="sxs-lookup"><span data-stu-id="27afd-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="27afd-104">Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="27afd-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="27afd-105">Například v následujícím jednoduchého kódu `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="27afd-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="27afd-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="27afd-106">This example produces the following output:</span></span>

```
4
```

<span data-ttu-id="27afd-107">Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="27afd-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="27afd-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Osy je v podstatě stejný výkon jako iterace propojeného seznamu.</span><span class="sxs-lookup"><span data-stu-id="27afd-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="27afd-109"><xref:System.Xml.Linq.XContainer.Elements%2A> je implementován jako iterátor s odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="27afd-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="27afd-110">To znamená, že nemusí nějakou práci navíc iterace propojeného seznamu, například přidělování objekt iterátoru a sledování stavu spuštění.</span><span class="sxs-lookup"><span data-stu-id="27afd-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="27afd-111">Tuto práci je možné rozdělit do dvou kategorií: práce, která se provádí v době iterátor nastaven a práce, která se provádí při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="27afd-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="27afd-112">Nastavení je malý, pevné množství práce a práci při každé iteraci je přímo úměrný počtu položek v kolekci zdroje.</span><span class="sxs-lookup"><span data-stu-id="27afd-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="27afd-113">V `query1`, `Where` klauzule dotazu pro volání způsobí, že <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="27afd-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="27afd-114">Tato metoda je také implementováno jako iterátor.</span><span class="sxs-lookup"><span data-stu-id="27afd-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="27afd-115">Nastavení se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, a navíc normální instalace iterátor.</span><span class="sxs-lookup"><span data-stu-id="27afd-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="27afd-116">S každou iterací delegáta je volána k provedení predikát.</span><span class="sxs-lookup"><span data-stu-id="27afd-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="27afd-117">Instalační program práce a práce při každé iteraci je podobný práci během iterace na ose.</span><span class="sxs-lookup"><span data-stu-id="27afd-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="27afd-118">V `query1`, klauzule select způsobí, že dotaz tak, aby volání <xref:System.Linq.Enumerable.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="27afd-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="27afd-119">Tato metoda má stejný profil výkonu, jako <xref:System.Linq.Enumerable.Where%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="27afd-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="27afd-120">V `query2`, obojí `Where` klauzule a `Select` klauzule mají stejný profil výkonu jako v `query1`.</span><span class="sxs-lookup"><span data-stu-id="27afd-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="27afd-121">Iterace přes `query2` tedy přímo úměrné k počet položek ve zdroji prvního dotazu jinými slovy, lineárním čase.</span><span class="sxs-lookup"><span data-stu-id="27afd-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="27afd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27afd-122">See also</span></span>

- [<span data-ttu-id="27afd-123">Výkon (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27afd-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
