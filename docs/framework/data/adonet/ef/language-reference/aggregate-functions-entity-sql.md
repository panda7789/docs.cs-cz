---
title: Agregační funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251340"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="51391-102">Agregační funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="51391-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="51391-103">Agregace je jazyková konstrukce, která rozhustí kolekci na skalární jako součást operace skupiny.</span><span class="sxs-lookup"><span data-stu-id="51391-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="51391-104">agregace se přidávají ve dvou formách:</span><span class="sxs-lookup"><span data-stu-id="51391-104">aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="51391-105">funkce kolekce, které mohou být použity kdekoli ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="51391-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="51391-106">To zahrnuje použití agregačních funkcí v projekcích a predikátech, které fungují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="51391-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="51391-107">Funkce kolekce jsou preferovaným režimem určení agregací v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51391-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="51391-108">Agregace skupin ve výrazech dotazů, které mají klauzuli GROUP BY</span><span class="sxs-lookup"><span data-stu-id="51391-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="51391-109">Podobně jako v jazyce Transact-SQL přijímají agregace skupin DISTINCT a ALL jako modifikátory do agregovaného vstupu.</span><span class="sxs-lookup"><span data-stu-id="51391-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="51391-110">Nejprve se pokusí interpretovat výraz jako funkci kolekce a pokud je výraz v kontextu výrazu SELECT, je interpretován jako agregace skupiny.</span><span class="sxs-lookup"><span data-stu-id="51391-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="51391-111">definuje speciální agregační operátor s názvem [GROUPPARTITION](grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="51391-111">defines a special aggregate operator called [GROUPPARTITION](grouppartition-entity-sql.md).</span></span> <span data-ttu-id="51391-112">Tento operátor vám umožní získat odkaz na seskupenou vstupní sadu.</span><span class="sxs-lookup"><span data-stu-id="51391-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="51391-113">To umožňuje pokročilejší dotazování seskupení, kde výsledky klauzule GROUP BY lze použít na místech jiných než agregačních nebo agregačních funkcí.</span><span class="sxs-lookup"><span data-stu-id="51391-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="51391-114">Funkce kolekce</span><span class="sxs-lookup"><span data-stu-id="51391-114">Collection Functions</span></span>  
 <span data-ttu-id="51391-115">Funkce kolekce pracuje na kolekcích a vrací skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51391-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="51391-116">Například pokud `orders` je kolekce všech `orders`, můžete vypočítat nejbližší datum expedice následujícím výrazem:</span><span class="sxs-lookup"><span data-stu-id="51391-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="51391-117">Agregace skupin</span><span class="sxs-lookup"><span data-stu-id="51391-117">Group Aggregates</span></span>  
 <span data-ttu-id="51391-118">Agregace skupin se počítají na základě skupinového výsledku definovaného klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="51391-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="51391-119">Klauzule GROUP BY seskupuje data do skupin.</span><span class="sxs-lookup"><span data-stu-id="51391-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="51391-120">Pro každou skupinu ve výsledku se použije agregační funkce a samostatná agregace se vypočítává pomocí prvků v každé skupině jako vstupů do agregačního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="51391-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="51391-121">Pokud je ve výrazu SELECT použita klauzule GROUP BY, mohou být v klauzuli projekce, HAVING nebo ORDER BY přítomny pouze názvy výrazů seskupení, agregace nebo konstantní výrazy.</span><span class="sxs-lookup"><span data-stu-id="51391-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="51391-122">Následující příklad vypočítá průměrné množství objednaného pro každý produkt.</span><span class="sxs-lookup"><span data-stu-id="51391-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="51391-123">Je možné mít agregovanou skupinu bez explicitní klauzule GROUP BY ve výrazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="51391-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="51391-124">Všechny elementy budou považovány za jednu skupinu, která odpovídá případu zadání seskupení na základě konstanty.</span><span class="sxs-lookup"><span data-stu-id="51391-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="51391-125">Výrazy používané v klauzuli GROUP BY jsou vyhodnocovány pomocí stejného oboru překladu názvů, který by byl viditelný pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="51391-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51391-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51391-126">See also</span></span>

- [<span data-ttu-id="51391-127">Funkce</span><span class="sxs-lookup"><span data-stu-id="51391-127">Functions</span></span>](functions-entity-sql.md)
