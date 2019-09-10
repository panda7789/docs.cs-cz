---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854455"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="5abaa-102">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5abaa-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="5abaa-103">Výraz je fragment kódu, který lze vyhodnotit na jedinou hodnotu, objekt, metodu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5abaa-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="5abaa-104">Výrazy mohou obsahovat hodnotu literálu, volání metody, operátor a jeho operandy nebo jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="5abaa-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="5abaa-105">Jednoduché názvy mohou být název proměnné, typ členu, parametr metody, obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="5abaa-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="5abaa-106">Výrazy mohou používat operátory, které zase používají jiné výrazy jako parametry, nebo volání metody, jejichž parametry jsou zapínají jiné volání metody.</span><span class="sxs-lookup"><span data-stu-id="5abaa-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="5abaa-107">Výrazy mohou proto být v rozsahu od jednoduchých až po velmi složité.</span><span class="sxs-lookup"><span data-stu-id="5abaa-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="5abaa-108">V LINQ to Entities dotazy mohou výrazy obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> oboru názvů, včetně výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="5abaa-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="5abaa-109">Výrazy, které lze použít v LINQ to Entities dotazů, jsou nadmnožinou výrazů, které lze použít k dotazování Entity Framework. výrazy, které jsou součástí dotazů proti Entity Framework jsou omezeny na operace podporované `ObjectQuery<T>` a podkladový zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="5abaa-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="5abaa-110">V následujícím příkladu je porovnání v `Where` klauzuli výrazem:</span><span class="sxs-lookup"><span data-stu-id="5abaa-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="5abaa-111">Konkrétní jazykové konstrukce, jako C# `unchecked`například, nemají v LINQ to Entities žádný význam.</span><span class="sxs-lookup"><span data-stu-id="5abaa-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5abaa-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5abaa-112">In This Section</span></span>  
 [<span data-ttu-id="5abaa-113">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="5abaa-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="5abaa-114">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="5abaa-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="5abaa-115">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="5abaa-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="5abaa-116">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="5abaa-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="5abaa-117">Relace, navigační vlastnosti a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="5abaa-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="5abaa-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5abaa-118">See also</span></span>

- [<span data-ttu-id="5abaa-119">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5abaa-119">ADO.NET Entity Framework</span></span>](../index.md)
