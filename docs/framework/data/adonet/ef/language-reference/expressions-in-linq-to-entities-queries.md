---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250976"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="59d6b-102">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="59d6b-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="59d6b-103">Výraz je fragment kódu, který lze vyhodnotit na jedinou hodnotu, objekt, metodu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="59d6b-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="59d6b-104">Výrazy mohou obsahovat hodnotu literálu, volání metody, operátor a jeho operandy nebo jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="59d6b-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="59d6b-105">Jednoduché názvy mohou být název proměnné, typ členu, parametr metody, obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="59d6b-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="59d6b-106">Výrazy mohou používat operátory, které zase používají jiné výrazy jako parametry, nebo volání metody, jejichž parametry jsou zapínají jiné volání metody.</span><span class="sxs-lookup"><span data-stu-id="59d6b-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="59d6b-107">Výrazy mohou proto být v rozsahu od jednoduchých až po velmi složité.</span><span class="sxs-lookup"><span data-stu-id="59d6b-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="59d6b-108">V LINQ to Entities dotazy mohou výrazy obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> oboru názvů, včetně výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="59d6b-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="59d6b-109">Výrazy, které lze použít v LINQ to Entities dotazů, jsou nadmnožinou výrazů, které lze použít k dotazování na [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59d6b-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="59d6b-110">Výrazy, které jsou součástí dotazů proti, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezeny na operace podporované `ObjectQuery<T>` nástrojem a podkladovým zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="59d6b-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="59d6b-111">V následujícím příkladu je porovnání v `Where` klauzuli výrazem:</span><span class="sxs-lookup"><span data-stu-id="59d6b-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="59d6b-112">Konkrétní jazykové konstrukce, jako C# `unchecked`například, nemají v LINQ to Entities žádný význam.</span><span class="sxs-lookup"><span data-stu-id="59d6b-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59d6b-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="59d6b-113">In This Section</span></span>  
 [<span data-ttu-id="59d6b-114">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="59d6b-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="59d6b-115">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="59d6b-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="59d6b-116">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="59d6b-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="59d6b-117">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="59d6b-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="59d6b-118">Relace, navigační vlastnosti a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="59d6b-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="59d6b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59d6b-119">See also</span></span>

- [<span data-ttu-id="59d6b-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="59d6b-120">ADO.NET Entity Framework</span></span>](../index.md)
