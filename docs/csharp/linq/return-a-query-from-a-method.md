---
title: "Vrácení dotazu z metody"
description: "Postup vrácení dotazu."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="31669-104">Postupy: Vrácení dotazu z metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="31669-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="31669-105">Tento příklad ukazuje, jak jako návratová hodnota a jako vrácení dotazu z metody `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="31669-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="31669-106">Objekty dotazu jsou složení, což znamená, že se můžete vrátit dotazu z metody.</span><span class="sxs-lookup"><span data-stu-id="31669-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="31669-107">Objekty, které představují dotazy neukládejte výsledné kolekce, ale spíš kroky nepřineslo výsledky v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="31669-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="31669-108">Výhodou vrácení objekty dotazu z metody je, aby mohly být další sestavit a upravit.</span><span class="sxs-lookup"><span data-stu-id="31669-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="31669-109">Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí také mít typu.</span><span class="sxs-lookup"><span data-stu-id="31669-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="31669-110">Pokud bude metodu realizována dotazu do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje vracejí výsledky dotazu místo samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="31669-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="31669-111">Proměnné dotazu, která je vrácena z metody můžete stále složené nebo upravil.</span><span class="sxs-lookup"><span data-stu-id="31669-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31669-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="31669-112">Example</span></span>  
 <span data-ttu-id="31669-113">V následujícím příkladu, první metoda vrací dotaz jako typ návratové hodnoty, a druhá metoda vrací dotaz jako `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="31669-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="31669-114">Všimněte si, že v obou případech je dotaz, který se vrátí, nebyl výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="31669-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="31669-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="31669-115">See Also</span></span>  
 [<span data-ttu-id="31669-116">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="31669-116">LINQ Query Expressions</span></span>](index.md)
