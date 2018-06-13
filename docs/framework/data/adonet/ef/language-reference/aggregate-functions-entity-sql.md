---
title: Agregační funkce (entita SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 63e366f323b38a24c4d067681b47d8a8b96125b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765578"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="1b343-102">Agregační funkce (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="1b343-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="1b343-103">Agregace je jazyk konstruktor, který zestruční jako součást skupiny operace kolekci do skalární hodnota.</span><span class="sxs-lookup"><span data-stu-id="1b343-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1b343-104"> agregace má ve dvou formách:</span><span class="sxs-lookup"><span data-stu-id="1b343-104"> aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1b343-105"> Kolekce funkcí, které je možné použít kdekoli výrazu.</span><span class="sxs-lookup"><span data-stu-id="1b343-105"> collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="1b343-106">To zahrnuje použití agregačních funkcí ve projekce a predikáty, které fungují u kolekcí.</span><span class="sxs-lookup"><span data-stu-id="1b343-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="1b343-107">Funkce kolekce je preferovaným režimem zadávání agregací ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b343-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="1b343-108">Skupiny agregace ve výrazech dotazů, které mají klauzule GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1b343-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="1b343-109">Jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], skupiny agregace přijmout DISTINCT a všechny jako modifikátory agregační vstupu.</span><span class="sxs-lookup"><span data-stu-id="1b343-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1b343-110"> Nejprve se pokusí interpretovat výraz jako funkce kolekce a Pokud výraz v kontextu výrazu, vyberte ji interpretuje jako skupiny agregace.</span><span class="sxs-lookup"><span data-stu-id="1b343-110"> first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1b343-111"> definuje speciální agregační operátor s názvem [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1b343-111"> defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="1b343-112">Tento operátor umožňuje získat odkaz na sadu seskupené vstupní.</span><span class="sxs-lookup"><span data-stu-id="1b343-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="1b343-113">To umožňuje pokročilejší seskupení dotazů, kde lze v místech než agregační skupiny nebo kolekce funkce výsledky v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1b343-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="1b343-114">Kolekce funkcí</span><span class="sxs-lookup"><span data-stu-id="1b343-114">Collection Functions</span></span>  
 <span data-ttu-id="1b343-115">Kolekce funkcí pracovat kolekce a vrátit skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b343-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="1b343-116">Například pokud `orders` je kolekce všech `orders`, můžete vypočítat nejdřívější datum expedice s následující výraz:</span><span class="sxs-lookup"><span data-stu-id="1b343-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="1b343-117">Agreguje skupiny</span><span class="sxs-lookup"><span data-stu-id="1b343-117">Group Aggregates</span></span>  
 <span data-ttu-id="1b343-118">Skupiny agregace jsou vypočteny přes výsledku skupinu podle definice v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1b343-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="1b343-119">V klauzuli GROUP BY oddíly dat do skupin.</span><span class="sxs-lookup"><span data-stu-id="1b343-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="1b343-120">Pro každou skupinu ve výsledku se použije agregační funkce a samostatné agregace se vypočítává pomocí elementů v každé skupině jako vstupy pro agregační výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1b343-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="1b343-121">Když klauzule GROUP BY se používá ve výrazu SELECT, pouze seskupování názvy výrazů, agregací nebo konstantní výrazy může být k dispozici v projekci, s, nebo klauzule ORDER.</span><span class="sxs-lookup"><span data-stu-id="1b343-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="1b343-122">Následující příklad vypočítá průměrné množství řazení pro každý produkt.</span><span class="sxs-lookup"><span data-stu-id="1b343-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="1b343-123">Je možné, že ve výrazu vyberte skupinu agregační bez explicitní klauzule GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1b343-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="1b343-124">Všechny elementy bude považována za jednu skupinu ekvivalentní v případě zadání seskupení založené na konstanta.</span><span class="sxs-lookup"><span data-stu-id="1b343-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="1b343-125">Pomocí stejného oboru rozlišení názvů, který staly viditelnými pro výraz klauzule WHERE se vyhodnotí výrazy použitého v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1b343-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b343-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b343-126">See Also</span></span>  
 [<span data-ttu-id="1b343-127">Funkce</span><span class="sxs-lookup"><span data-stu-id="1b343-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
