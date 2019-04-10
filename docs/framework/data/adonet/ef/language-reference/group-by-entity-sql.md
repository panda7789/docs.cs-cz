---
title: Seskupit podle (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 574d952e0183eb65c88864f2788eb7d698c9f2ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302943"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="eba91-102">Seskupit podle (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eba91-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="eba91-103">Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.</span><span class="sxs-lookup"><span data-stu-id="eba91-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba91-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="eba91-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eba91-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="eba91-106">Libovolný výraz platný dotaz, na kterém se provádí seskupení.</span><span class="sxs-lookup"><span data-stu-id="eba91-106">Any valid query expression on which grouping is performed.</span></span> `expression` <span data-ttu-id="eba91-107">může být vlastnost ani není agregační výraz, který odkazuje na vlastnost vrácené v klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="eba91-107">can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="eba91-108">Každý výraz v klauzuli GROUP BY musí vyhodnotit na typ, který může být porovnána shoda.</span><span class="sxs-lookup"><span data-stu-id="eba91-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="eba91-109">Tyto typy jsou obecně skalární primitivních elementů, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="eba91-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="eba91-110">Nelze seskupit podle kolekce.</span><span class="sxs-lookup"><span data-stu-id="eba91-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eba91-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eba91-111">Remarks</span></span>  
 <span data-ttu-id="eba91-112">Pokud agregační funkce jsou zahrnuty v klauzuli SELECT \<seznamu příkazu select >, GROUP BY vypočítá souhrnnou hodnotu pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="eba91-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="eba91-113">Je-li seskupit podle zadána, název každé vlastnosti v jakékoli jiné než agregované výraz v seznamu select, měly by být součástí seznamu GROUP BY nebo výraz GROUP BY musí přesně odpovídat výrazu seznamu příkazu select.</span><span class="sxs-lookup"><span data-stu-id="eba91-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba91-114">Pokud není zadána klauzule ORDER BY, nejsou skupiny vrácené v klauzuli GROUP BY v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="eba91-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="eba91-115">Chcete-li určit konkrétní pořadí dat, doporučujeme vždy používat klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="eba91-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="eba91-116">Pokud klauzule GROUP BY je zadán, buď explicitně nebo implicitně (například pomocí klauzule HAVING v dotazu), je skrytý v aktuálním oboru a zavedl nový obor.</span><span class="sxs-lookup"><span data-stu-id="eba91-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="eba91-117">Klauzule SELECT, klauzuli HAVING a ORDER BY – klauzule již nebude moci odkazovat na názvy elementů zadaný v klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="eba91-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="eba91-118">Mohou odkazovat pouze na výrazy seskupování sami.</span><span class="sxs-lookup"><span data-stu-id="eba91-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="eba91-119">K tomuto účelu můžete přiřadit nové názvy (aliasy) pro každý výraz seskupení.</span><span class="sxs-lookup"><span data-stu-id="eba91-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="eba91-120">Pokud není zadán žádný alias pro výraz grouping [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat pomocí pravidel pro vytvoření aliasu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eba91-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="eba91-121">Výrazy v klauzuli GROUP BY nemůže odkazovat na názvy definované výše v stejné klauzule GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="eba91-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="eba91-122">Kromě seskupení názvy můžete také určit agregace v klauzuli SELECT, klauzuli HAVING a ORDER BY – klauzule.</span><span class="sxs-lookup"><span data-stu-id="eba91-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="eba91-123">Agregace obsahuje výraz, který se vyhodnocuje pro každý prvek skupiny.</span><span class="sxs-lookup"><span data-stu-id="eba91-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="eba91-124">Agregační operátor snižuje hodnoty těchto výrazů (obvykle, ale ne vždy do jediné hodnoty).</span><span class="sxs-lookup"><span data-stu-id="eba91-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="eba91-125">Agregační výraz můžete vytvořit odkazy na původní názvy prvků viditelné v nadřazeném oboru nebo na nové názvy zavedené v klauzuli GROUP BY, samotného.</span><span class="sxs-lookup"><span data-stu-id="eba91-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="eba91-126">I když se v klauzuli SELECT, klauzuli HAVING a ORDER BY – klauzule zobrazí agregací, ve skutečnosti vyhodnocují se v rámci stejného oboru jako výrazy seskupování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eba91-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="eba91-127">Tento dotaz používá k vytvoření sestavy nákladů na všechny produkty, které jsou uspořádány v klauzuli GROUP BY rozděleno podle produktu.</span><span class="sxs-lookup"><span data-stu-id="eba91-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="eba91-128">Poskytuje název `name` produktu jako součást výrazu seskupení a pak odkazy, které název v seznamu SELECT.</span><span class="sxs-lookup"><span data-stu-id="eba91-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="eba91-129">Určuje také agregace `sum` v seznamu SELECT, který interně odkazuje cena a množství objednávky.</span><span class="sxs-lookup"><span data-stu-id="eba91-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="eba91-130">Každý výraz GROUP By klíče musí mít alespoň jeden odkaz na vstupní obor:</span><span class="sxs-lookup"><span data-stu-id="eba91-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="eba91-131">Příklad použití GROUP BY, naleznete v tématu [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eba91-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba91-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="eba91-132">Example</span></span>  
 <span data-ttu-id="eba91-133">Následující dotaz Entity SQL používá operátor GROUP BY k určení skupin, do kterých jsou objekty vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="eba91-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="eba91-134">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eba91-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eba91-135">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="eba91-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eba91-136">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eba91-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="eba91-137">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="eba91-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="eba91-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eba91-138">See also</span></span>

- [<span data-ttu-id="eba91-139">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eba91-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="eba91-140">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="eba91-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
