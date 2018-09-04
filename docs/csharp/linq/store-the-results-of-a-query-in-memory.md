---
title: Store výsledky dotazu v paměti
description: Jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 98a300b2c11eb037ed4ce34caea2673a4e0f8e6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525227"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="ee878-103">Store výsledky dotazu v paměti</span><span class="sxs-lookup"><span data-stu-id="ee878-103">Store the results of a query in memory</span></span>

<span data-ttu-id="ee878-104">Dotaz je v podstatě sadu pokynů pro načtení a organizujte data.</span><span class="sxs-lookup"><span data-stu-id="ee878-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="ee878-105">Dotazy jsou laxně, provést, protože je požadována každé následné položky ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="ee878-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="ee878-106">Při použití `foreach` k iteraci výsledky, položky se vrátí jako přistupovat.</span><span class="sxs-lookup"><span data-stu-id="ee878-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="ee878-107">K vyhodnocení dotazu a uložit jeho výsledky bez spuštění `foreach` smyčky, stačí zavolat jednu z následujících metod v proměnné dotazu:</span><span class="sxs-lookup"><span data-stu-id="ee878-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="ee878-108">Doporučujeme vám, že při ukládání výsledků dotazu, přiřadíte objekt vrácený kolekce do nové proměnné jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ee878-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="ee878-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee878-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="ee878-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee878-110">See also</span></span>

- [<span data-ttu-id="ee878-111">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="ee878-111">Language Integrated Query (LINQ)</span></span>](index.md)