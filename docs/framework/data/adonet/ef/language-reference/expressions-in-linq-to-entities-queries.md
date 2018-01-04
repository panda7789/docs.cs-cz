---
title: "Výrazy v technologii LINQ to Entities dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6c1460aa78e112d29a4c500c54661b63de03e953
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="8ee8e-102">Výrazy v technologii LINQ to Entities dotazy</span><span class="sxs-lookup"><span data-stu-id="8ee8e-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="8ee8e-103">Výraz je fragment kódu, který lze vyhodnotit na hodnotu typu single, objekt, metodu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="8ee8e-104">Výrazy může obsahovat literálovou hodnotou, volání metod, operátor a jejími operandy nebo jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="8ee8e-105">Název proměnné, typ, parametru metody, obor názvů nebo člena typu může být jednoduché názvy.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="8ee8e-106">Výrazy můžete použít operátory, které pak použít jiné výrazy jako parametry nebo volání metod, jejíž parametry jsou naopak další volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="8ee8e-107">Proto výrazy může jít o jednoduché pro velmi složité.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="8ee8e-108">V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, výrazy může obsahovat nic povolenou typů v rámci <xref:System.Linq.Expressions> obor názvů, včetně výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="8ee8e-109">Výrazy, které mohou být používány [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy jsou nadmnožinou výrazy, které lze použít k dotazu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ee8e-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="8ee8e-110">Výrazy, které jsou součástí dotazů vůči [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezeny na operací podporované `ObjectQuery<T>` a na podkladový zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="8ee8e-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="8ee8e-111">V následujícím příkladu, v porovnání `Where` klauzule je výraz:</span><span class="sxs-lookup"><span data-stu-id="8ee8e-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="8ee8e-112">Vytvoří konkrétní jazyk, například C# `unchecked`, mít žádný význam v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ee8e-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ee8e-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8ee8e-113">In This Section</span></span>  
 [<span data-ttu-id="8ee8e-114">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="8ee8e-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="8ee8e-115">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="8ee8e-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="8ee8e-116">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8ee8e-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="8ee8e-117">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="8ee8e-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="8ee8e-118">Navigační vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8ee8e-118">Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a><span data-ttu-id="8ee8e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ee8e-119">See Also</span></span>  
 [<span data-ttu-id="8ee8e-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8ee8e-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
