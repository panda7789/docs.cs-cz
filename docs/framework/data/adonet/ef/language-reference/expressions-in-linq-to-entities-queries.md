---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 0b77fc4c2a7c7df6efc9f4d8ce4001c39250ab94
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539903"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="82d80-102">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="82d80-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="82d80-103">Výraz je fragment kódu, který lze vyhodnotit na jednu hodnotu, objekt, metodu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="82d80-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="82d80-104">Hodnota literálu, volání metody, operátor a jeho operandy nebo jednoduchý název může obsahovat výrazy.</span><span class="sxs-lookup"><span data-stu-id="82d80-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="82d80-105">Název proměnné, člen typu, parametr metody, obor názvů nebo typ může být jednoduché názvy.</span><span class="sxs-lookup"><span data-stu-id="82d80-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="82d80-106">Výrazy můžete použít operátory, které pak použít jako parametry nebo volání metody, jejíž parametry jsou zase další volání metody jiných výrazech.</span><span class="sxs-lookup"><span data-stu-id="82d80-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="82d80-107">Proto výrazy v rozsahu jednoduché až velmi složité.</span><span class="sxs-lookup"><span data-stu-id="82d80-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="82d80-108">V dotazech LINQ to Entities, výrazy mohou obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> obor názvů, včetně výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="82d80-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="82d80-109">Výrazy, které můžete použít v LINQ dotazy na entity jsou nadmnožinou výrazů, které lze použít k dotazování [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82d80-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="82d80-110">Výrazy, které jsou součástí sady dotazů [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezené na operací podporované `ObjectQuery<T>` a podkladový zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="82d80-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="82d80-111">V následujícím příkladu se v porovnání `Where` klauzule je výraz:</span><span class="sxs-lookup"><span data-stu-id="82d80-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="82d80-112">Konkrétní jazykové konstrukce, jako například C# `unchecked`, nemají význam v technologii LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="82d80-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82d80-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="82d80-113">In This Section</span></span>  
 [<span data-ttu-id="82d80-114">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="82d80-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="82d80-115">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="82d80-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="82d80-116">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="82d80-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="82d80-117">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="82d80-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="82d80-118">Relace, navigačních vlastností a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="82d80-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="82d80-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82d80-119">See also</span></span>

- [<span data-ttu-id="82d80-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="82d80-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
