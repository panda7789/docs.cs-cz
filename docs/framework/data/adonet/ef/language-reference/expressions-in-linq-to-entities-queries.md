---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 234b3059f9109c23b8ecae4da37e15f7f094fbd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034187"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="83e50-102">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="83e50-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="83e50-103">Výraz je fragment kódu, který lze vyhodnotit na jednu hodnotu, objekt, metodu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83e50-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="83e50-104">Hodnota literálu, volání metody, operátor a jeho operandy nebo jednoduchý název může obsahovat výrazy.</span><span class="sxs-lookup"><span data-stu-id="83e50-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="83e50-105">Název proměnné, člen typu, parametr metody, obor názvů nebo typ může být jednoduché názvy.</span><span class="sxs-lookup"><span data-stu-id="83e50-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="83e50-106">Výrazy můžete použít operátory, které pak použít jako parametry nebo volání metody, jejíž parametry jsou zase další volání metody jiných výrazech.</span><span class="sxs-lookup"><span data-stu-id="83e50-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="83e50-107">Proto výrazy v rozsahu jednoduché až velmi složité.</span><span class="sxs-lookup"><span data-stu-id="83e50-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="83e50-108">V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, výrazy mohou obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> obor názvů, včetně výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="83e50-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="83e50-109">Výrazy, které lze použít v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy jsou množinou výrazy, které lze použít k dotazování [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83e50-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="83e50-110">Výrazy, které jsou součástí sady dotazů [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezené na operací podporované `ObjectQuery<T>` a podkladový zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="83e50-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="83e50-111">V následujícím příkladu se v porovnání `Where` klauzule je výraz:</span><span class="sxs-lookup"><span data-stu-id="83e50-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="83e50-112">Vytvoří konkrétní jazyk, jako je C# `unchecked`, nemají význam [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83e50-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83e50-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="83e50-113">In This Section</span></span>  
 [<span data-ttu-id="83e50-114">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="83e50-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="83e50-115">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="83e50-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="83e50-116">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="83e50-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="83e50-117">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="83e50-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="83e50-118">Relace, navigačních vlastností a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="83e50-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="83e50-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83e50-119">See also</span></span>

- [<span data-ttu-id="83e50-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="83e50-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
