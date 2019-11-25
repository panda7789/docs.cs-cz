---
title: Vrácení dotazu z metody
description: Jak vrátit dotaz.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972512"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="a61c5-103">Postup vrácení dotazu z metody (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a61c5-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="a61c5-104">Tento příklad ukazuje, jak vrátit dotaz z metody jako návratovou hodnotu a jako parametr `out`.</span><span class="sxs-lookup"><span data-stu-id="a61c5-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="a61c5-105">Objekty dotazů jsou sestavitelné, což znamená, že můžete vracet dotaz z metody.</span><span class="sxs-lookup"><span data-stu-id="a61c5-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="a61c5-106">Objekty, které reprezentují dotazy, neukládají výslednou kolekci, ale v případě potřeby pak kroky k vyprodukování výsledků.</span><span class="sxs-lookup"><span data-stu-id="a61c5-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="a61c5-107">Výhodou vrácení objektů dotazů z metod je, že je lze dále sestavit nebo upravit.</span><span class="sxs-lookup"><span data-stu-id="a61c5-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="a61c5-108">Proto všechny vrácené hodnoty nebo parametry `out` metody, která vrací dotaz, musí mít také tento typ.</span><span class="sxs-lookup"><span data-stu-id="a61c5-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="a61c5-109">Pokud metoda materializuje dotaz do konkrétního <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje se za vracené výsledky dotazu místo dotazu samotného.</span><span class="sxs-lookup"><span data-stu-id="a61c5-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="a61c5-110">Proměnnou dotazu, která je vrácena z metody, lze stále sestavit nebo upravit.</span><span class="sxs-lookup"><span data-stu-id="a61c5-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a61c5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a61c5-111">Example</span></span>  
 <span data-ttu-id="a61c5-112">V následujícím příkladu vrátí první metoda dotaz jako návratovou hodnotu a druhá metoda vrátí dotaz jako parametr `out`.</span><span class="sxs-lookup"><span data-stu-id="a61c5-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="a61c5-113">Všimněte si, že v obou případech se jedná o dotaz, který je vrácen, nikoli výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="a61c5-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="a61c5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a61c5-114">See also</span></span>

- [<span data-ttu-id="a61c5-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a61c5-115">Language Integrated Query (LINQ)</span></span>](index.md)
