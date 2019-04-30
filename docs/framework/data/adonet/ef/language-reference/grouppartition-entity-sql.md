---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774722"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="70acc-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="70acc-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="70acc-103">Vrátí kolekci hodnot argumentů, které se vykreslují mimo aktuální skupiny oddílů, ke kterému se vztahuje agregace.</span><span class="sxs-lookup"><span data-stu-id="70acc-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="70acc-104">`GroupPartition` Agregace je agregovat na základě skupiny a nemá žádný formulář na základě kolekce.</span><span class="sxs-lookup"><span data-stu-id="70acc-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70acc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70acc-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="70acc-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="70acc-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="70acc-107">Žádné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazu.</span><span class="sxs-lookup"><span data-stu-id="70acc-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70acc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70acc-108">Remarks</span></span>  
 <span data-ttu-id="70acc-109">Následující dotaz vytvoří seznam produktů a kolekce řádek množství objednávek za jednotlivé produkty:</span><span class="sxs-lookup"><span data-stu-id="70acc-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="70acc-110">Následující dva dotazy jsou sémanticky stejné:</span><span class="sxs-lookup"><span data-stu-id="70acc-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="70acc-111">`GROUPPARTITION` Operátor můžete použít ve spojení s uživatelsky definované agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="70acc-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="70acc-112">`GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na seskupené vstupní sady.</span><span class="sxs-lookup"><span data-stu-id="70acc-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="70acc-113">Tento odkaz můžete je použít kdekoli v dotazu kde GROUP BY je v oboru.</span><span class="sxs-lookup"><span data-stu-id="70acc-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="70acc-114">Například</span><span class="sxs-lookup"><span data-stu-id="70acc-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="70acc-115">Pomocí regulárních KLAUZULE GROUP jsou skryté výsledky seskupení.</span><span class="sxs-lookup"><span data-stu-id="70acc-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="70acc-116">Výsledky můžete použít pouze v agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="70acc-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="70acc-117">Chcete-li zobrazit výsledky seskupení, budete muset můžete provádět korelaci výsledků seskupení a vstupní nastavení s použitím poddotaz.</span><span class="sxs-lookup"><span data-stu-id="70acc-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="70acc-118">Následující dva dotazy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="70acc-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="70acc-119">Jak je vidět z příkladu, agregační operátor GROUPPARTITION je snazší získat odkaz na sadu po seskupení vstupů.</span><span class="sxs-lookup"><span data-stu-id="70acc-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="70acc-120">Operátor GROUPPARTITION můžete určit kterékoli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz v operátoru vstup při použití `expression` parametru.</span><span class="sxs-lookup"><span data-stu-id="70acc-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="70acc-121">Například všechny následující vstupní výrazy do oddílu skupiny jsou platné:</span><span class="sxs-lookup"><span data-stu-id="70acc-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="70acc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="70acc-122">Example</span></span>  
 <span data-ttu-id="70acc-123">Následující příklad ukazuje způsob použití klauzule GROUPPARTITION s klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="70acc-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="70acc-124">Skupiny klauzule GROUP BY `SalesOrderHeader` entity podle jejich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="70acc-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="70acc-125">Klauzule GROUPPARTITION pak projektů `TotalDue` vlastností pro každou skupinu, výsledkem je kolekce desetinná čísla.</span><span class="sxs-lookup"><span data-stu-id="70acc-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
