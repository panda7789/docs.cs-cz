---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 19df566c254a3f3202eb3554ab43ee0d7c944181
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833754"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="71891-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="71891-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="71891-103">Vrátí kolekci hodnot argumentů, které jsou proložené z aktuálního oddílu skupiny, ke kterému se agregace vztahuje.</span><span class="sxs-lookup"><span data-stu-id="71891-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="71891-104">Agregace `GroupPartition` je agregovaná podle skupin a neobsahuje žádné formuláře založené na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="71891-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71891-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71891-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="71891-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71891-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="71891-107">Libovolný výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71891-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71891-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71891-108">Remarks</span></span>  
 <span data-ttu-id="71891-109">Následující dotaz vytvoří seznam produktů a kolekci množství řádků objednávky na jednotlivé produkty:</span><span class="sxs-lookup"><span data-stu-id="71891-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="71891-110">Následující dva dotazy jsou sémanticky stejné:</span><span class="sxs-lookup"><span data-stu-id="71891-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="71891-111">Operátor `GROUPPARTITION` lze použít ve spojení s uživatelsky definovanými agregačními funkcemi.</span><span class="sxs-lookup"><span data-stu-id="71891-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="71891-112">`GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na seskupenou vstupní sadu.</span><span class="sxs-lookup"><span data-stu-id="71891-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="71891-113">Tento odkaz lze použít kdekoli v dotazu, kde GROUP BY je v oboru.</span><span class="sxs-lookup"><span data-stu-id="71891-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="71891-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="71891-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="71891-115">Při běžném `GROUP BY`jsou výsledky seskupení skryté.</span><span class="sxs-lookup"><span data-stu-id="71891-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="71891-116">Výsledky můžete použít jenom v agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="71891-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="71891-117">Chcete-li zobrazit výsledky seskupení, je třeba sladit výsledky seskupení a vstupní sady pomocí poddotazu.</span><span class="sxs-lookup"><span data-stu-id="71891-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="71891-118">Následující dva dotazy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="71891-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="71891-119">Jak je vidět v příkladu, agregační operátor GROUPPARTITION usnadňuje získání odkazu na vstupní sadu po seskupení.</span><span class="sxs-lookup"><span data-stu-id="71891-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="71891-120">Operátor GROUPPARTITION může při použití parametru `expression` zadat libovolný výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve vstupu operátoru.</span><span class="sxs-lookup"><span data-stu-id="71891-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="71891-121">Například všechny následující vstupní výrazy pro oddíl skupiny jsou platné:</span><span class="sxs-lookup"><span data-stu-id="71891-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="71891-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="71891-122">Example</span></span>  
 <span data-ttu-id="71891-123">Následující příklad ukazuje, jak použít klauzuli GROUPPARTITION s klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="71891-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="71891-124">Klauzule GROUP BY `SalesOrderHeader` entitami podle jejich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="71891-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="71891-125">Klauzule GROUPPARTITION pak projektuje vlastnost `TotalDue` pro každou skupinu a výsledkem je kolekce desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="71891-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
