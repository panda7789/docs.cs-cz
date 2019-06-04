---
title: Agregační funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: b01c7dca675e79c61b87bcc1fb30455286db3118
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489960"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="0e960-102">Agregační funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0e960-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="0e960-103">Agregace je konstrukce jazyka, který zestruční kolekce do skaláru jako součást operace skupiny.</span><span class="sxs-lookup"><span data-stu-id="0e960-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0e960-104">agregace přicházet ve dvou formách:</span><span class="sxs-lookup"><span data-stu-id="0e960-104">aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0e960-105">Kolekce funkcí, které může je použít kdekoli ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="0e960-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="0e960-106">To zahrnuje použití agregačních funkcí v projekce a predikátů, které fungují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="0e960-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="0e960-107">Kolekce funkcí jsou preferovaný způsob určení agregace v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e960-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="0e960-108">Skupina agregace ve výrazech dotazů, které mají klauzuli Group by.</span><span class="sxs-lookup"><span data-stu-id="0e960-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="0e960-109">Stejně jako v jazyce Transact-SQL přijměte agregace skupiny DISTINCT a všechny jako modifikátory agregační vstupem.</span><span class="sxs-lookup"><span data-stu-id="0e960-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0e960-110">Nejprve se pokusí o interpretovat výraz jako funkce kolekce a Pokud výraz v kontextu výrazu SELECT ji interpretuje jako agregace skupiny.</span><span class="sxs-lookup"><span data-stu-id="0e960-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0e960-111">definuje speciální agregační operátor volá [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0e960-111">defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="0e960-112">Tento operátor umožňuje získat odkaz na seskupené vstupní sady.</span><span class="sxs-lookup"><span data-stu-id="0e960-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="0e960-113">To umožňuje pokročilejší seskupení dotazů, kde lze použít výsledky v klauzuli GROUP BY v jiných míst než agregace skupiny nebo kolekce funkcí.</span><span class="sxs-lookup"><span data-stu-id="0e960-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="0e960-114">Kolekce funkcí</span><span class="sxs-lookup"><span data-stu-id="0e960-114">Collection Functions</span></span>  
 <span data-ttu-id="0e960-115">Kolekce funkcí pracovat s kolekcí a vracet skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0e960-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="0e960-116">Například pokud `orders` je kolekce všech `orders`, můžete vypočítat datum příjemce se následující výraz:</span><span class="sxs-lookup"><span data-stu-id="0e960-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="0e960-117">Agregace skupiny</span><span class="sxs-lookup"><span data-stu-id="0e960-117">Group Aggregates</span></span>  
 <span data-ttu-id="0e960-118">Agregace skupiny se počítá za výsledek skupiny definované v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="0e960-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="0e960-119">V klauzuli GROUP BY dělí data do skupin.</span><span class="sxs-lookup"><span data-stu-id="0e960-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="0e960-120">Pro každou skupinu ve výsledku se použije agregační funkce a samostatné agregace se počítá pomocí elementů v každé skupině jako vstupy do agregačního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="0e960-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="0e960-121">Když klauzule GROUP BY se používá ve výrazu SELECT, seskupení pouze názvy výrazů, agregace nebo konstantní výrazy může být k dispozici v projekci s, nebo ORDER BY – klauzule.</span><span class="sxs-lookup"><span data-stu-id="0e960-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="0e960-122">Následující příklad vypočítá průměrné množství, řazení pro jednotlivé produkty.</span><span class="sxs-lookup"><span data-stu-id="0e960-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="0e960-123">Je možné mít ve výrazu vyberte skupinu agregační bez explicitní klauzule GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="0e960-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="0e960-124">Všechny prvky bude považována za jednu skupinu ekvivalentní případu pro určení seskupení založené na konstantu.</span><span class="sxs-lookup"><span data-stu-id="0e960-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="0e960-125">Výrazy v klauzuli GROUP BY vyhodnocují se pomocí stejného oboru rozlišení názvů, které se staly viditelnými pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="0e960-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e960-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e960-126">See also</span></span>

- [<span data-ttu-id="0e960-127">Funkce</span><span class="sxs-lookup"><span data-stu-id="0e960-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
