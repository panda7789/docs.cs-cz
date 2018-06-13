---
title: Ukládání výsledků dotazu do paměti
description: Tom, jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279630"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="8db06-103">Ukládání výsledků dotazu do paměti</span><span class="sxs-lookup"><span data-stu-id="8db06-103">Store the results of a query in memory</span></span>

<span data-ttu-id="8db06-104">Dotaz je v podstatě sadu pokyny, jak získat a uspořádat data.</span><span class="sxs-lookup"><span data-stu-id="8db06-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="8db06-105">Dotazy jsou líné, provést, protože každá další položka ve výsledku se požaduje.</span><span class="sxs-lookup"><span data-stu-id="8db06-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="8db06-106">Při použití `foreach` položky k iteraci výsledky, se vrátí jako získat přístup.</span><span class="sxs-lookup"><span data-stu-id="8db06-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="8db06-107">K vyhodnocení dotazu a ukládat své výsledky bez spuštění `foreach` cykly, stačí jeden z následujících metod zavolat na proměnnou dotazu:</span><span class="sxs-lookup"><span data-stu-id="8db06-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="8db06-108">Doporučujeme vám, že při ukládání výsledků dotazu je vrácená kolekce objekt přiřadit nové proměnné jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8db06-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="8db06-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8db06-109">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="8db06-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8db06-110">See Also</span></span>  
 [<span data-ttu-id="8db06-111">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="8db06-111">LINQ Query Expressions</span></span>](index.md)
