---
title: Vrácení dotazu z metody
description: Postup vrácení dotazu.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274947"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="d317f-103">Postupy: Vrácení dotazu z metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d317f-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="d317f-104">Tento příklad ukazuje, jak jako návratová hodnota a jako vrácení dotazu z metody `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="d317f-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="d317f-105">Objekty dotazu jsou složení, což znamená, že se můžete vrátit dotazu z metody.</span><span class="sxs-lookup"><span data-stu-id="d317f-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="d317f-106">Objekty, které představují dotazy neukládejte výsledné kolekce, ale spíš kroky nepřineslo výsledky v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="d317f-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="d317f-107">Výhodou vrácení objekty dotazu z metody je, aby mohly být další sestavit a upravit.</span><span class="sxs-lookup"><span data-stu-id="d317f-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="d317f-108">Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí také mít typu.</span><span class="sxs-lookup"><span data-stu-id="d317f-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="d317f-109">Pokud bude metodu realizována dotazu do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje vracejí výsledky dotazu místo samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="d317f-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="d317f-110">Proměnné dotazu, která je vrácena z metody můžete stále složené nebo upravil.</span><span class="sxs-lookup"><span data-stu-id="d317f-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d317f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d317f-111">Example</span></span>  
 <span data-ttu-id="d317f-112">V následujícím příkladu, první metoda vrací dotaz jako typ návratové hodnoty, a druhá metoda vrací dotaz jako `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="d317f-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="d317f-113">Všimněte si, že v obou případech je dotaz, který se vrátí, nebyl výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="d317f-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="d317f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d317f-114">See Also</span></span>  
 [<span data-ttu-id="d317f-115">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d317f-115">LINQ Query Expressions</span></span>](index.md)
