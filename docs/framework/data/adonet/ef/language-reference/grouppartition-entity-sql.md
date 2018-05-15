---
title: GROUPPARTITION (entita SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="dcfec-102">GROUPPARTITION (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="dcfec-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="dcfec-103">Vrátí kolekci argument hodnoty, které jsou k projekci mimo aktuální oddílu skupiny, ke kterému se vztahuje na agregaci.</span><span class="sxs-lookup"><span data-stu-id="dcfec-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="dcfec-104">`GroupPartition` Agregace je agregace se na základě skupiny a nemá žádný formulář na základě kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcfec-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcfec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcfec-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcfec-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="dcfec-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="dcfec-107">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz.</span><span class="sxs-lookup"><span data-stu-id="dcfec-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcfec-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcfec-108">Remarks</span></span>  
 <span data-ttu-id="dcfec-109">Následující dotaz vytvoří seznam produktů a kolekce pořadí počty řádek pro každý produkt:</span><span class="sxs-lookup"><span data-stu-id="dcfec-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="dcfec-110">Následující dva dotazy jsou sémanticky stejné:</span><span class="sxs-lookup"><span data-stu-id="dcfec-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="dcfec-111">`GROUPPARTITION` Operátor můžete použít ve spojení s uživatelem definované agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="dcfec-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="dcfec-112">`GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na sadu seskupené vstupní.</span><span class="sxs-lookup"><span data-stu-id="dcfec-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="dcfec-113">Tento odkaz lze použít kdekoli v dotazu kde GROUP BY je v oboru.</span><span class="sxs-lookup"><span data-stu-id="dcfec-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="dcfec-114">Například</span><span class="sxs-lookup"><span data-stu-id="dcfec-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="dcfec-115">S klauzulí regulární GROUP BY jsou výsledky seskupení skryté.</span><span class="sxs-lookup"><span data-stu-id="dcfec-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="dcfec-116">Výsledky můžete použít pouze v agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="dcfec-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="dcfec-117">Chcete-li zobrazit výsledky seskupení, budete muset korelovat výsledky seskupení a vstup nastavit pomocí poddotazu.</span><span class="sxs-lookup"><span data-stu-id="dcfec-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="dcfec-118">Následující dva dotazy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="dcfec-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="dcfec-119">Jak je vidět z příkladu, agregační operátor GROUPPARTITION je snazší získat odkaz na vstup nastaví po seskupení.</span><span class="sxs-lookup"><span data-stu-id="dcfec-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="dcfec-120">Operátor GROUPPARTITION můžete zadat jakýkoli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz v operátoru vstup při použití `expression` parametr.</span><span class="sxs-lookup"><span data-stu-id="dcfec-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="dcfec-121">Například všechny následující vstupní výrazy k oddílu skupiny jsou platné:</span><span class="sxs-lookup"><span data-stu-id="dcfec-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="dcfec-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcfec-122">Example</span></span>  
 <span data-ttu-id="dcfec-123">Následující příklad ukazuje, jak použít klauzuli GROUPPARTITION s klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="dcfec-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="dcfec-124">Skupiny klauzule GROUP BY `SalesOrderHeader` entity podle jejich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="dcfec-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="dcfec-125">Klauzule GROUPPARTITION pak projekty `TotalDue` vlastnosti pro každou skupinu, výsledkem je kolekce desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="dcfec-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
