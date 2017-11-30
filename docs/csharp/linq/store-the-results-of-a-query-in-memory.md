---
title: "Ukládání výsledků dotazu do paměti"
description: "Tom, jak ukládat výsledky."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="e8b6c-104">Ukládání výsledků dotazu do paměti</span><span class="sxs-lookup"><span data-stu-id="e8b6c-104">Store the results of a query in memory</span></span>

<span data-ttu-id="e8b6c-105">Dotaz je v podstatě sadu pokyny, jak získat a uspořádat data.</span><span class="sxs-lookup"><span data-stu-id="e8b6c-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="e8b6c-106">Dotazy jsou líné, provést, protože každá další položka ve výsledku se požaduje.</span><span class="sxs-lookup"><span data-stu-id="e8b6c-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="e8b6c-107">Při použití `foreach` položky k iteraci výsledky, se vrátí jako získat přístup.</span><span class="sxs-lookup"><span data-stu-id="e8b6c-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="e8b6c-108">K vyhodnocení dotazu a ukládat své výsledky bez spuštění `foreach` cykly, stačí jeden z následujících metod zavolat na proměnnou dotazu:</span><span class="sxs-lookup"><span data-stu-id="e8b6c-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="e8b6c-109">Doporučujeme vám, že při ukládání výsledků dotazu je vrácená kolekce objekt přiřadit nové proměnné jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e8b6c-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b6c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8b6c-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="e8b6c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8b6c-111">See Also</span></span>  
 [<span data-ttu-id="e8b6c-112">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="e8b6c-112">LINQ Query Expressions</span></span>](index.md)
