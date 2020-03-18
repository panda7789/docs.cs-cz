---
title: Ukládání výsledků dotazu do paměti
description: Jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633566"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="eda7e-103">Ukládání výsledků dotazu do paměti</span><span class="sxs-lookup"><span data-stu-id="eda7e-103">Store the results of a query in memory</span></span>

<span data-ttu-id="eda7e-104">Dotaz je v podstatě sada pokynů, jak načíst a uspořádat data.</span><span class="sxs-lookup"><span data-stu-id="eda7e-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="eda7e-105">Dotazy jsou prováděny líně, protože každá následující položka ve výsledku je požadována.</span><span class="sxs-lookup"><span data-stu-id="eda7e-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="eda7e-106">Při použití `foreach` k iterace výsledků položky jsou vráceny jako přístup.</span><span class="sxs-lookup"><span data-stu-id="eda7e-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="eda7e-107">Chcete-li vyhodnotit dotaz a uložit `foreach` jeho výsledky bez spuštění smyčky, stačí zavolat jednu z následujících metod na proměnné dotazu:</span><span class="sxs-lookup"><span data-stu-id="eda7e-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="eda7e-108">Doporučujeme při ukládání výsledků dotazu přiřadit vrácený objekt kolekce nové proměnné, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="eda7e-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="eda7e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="eda7e-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="eda7e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="eda7e-110">See also</span></span>

- [<span data-ttu-id="eda7e-111">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="eda7e-111">Language Integrated Query (LINQ)</span></span>](index.md)
