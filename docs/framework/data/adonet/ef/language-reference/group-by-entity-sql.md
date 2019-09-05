---
title: Seskupit podle (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 641231825ca00c6accd19039ba1ec403208a077e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250898"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="ecddb-102">Seskupit podle (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ecddb-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="ecddb-103">Určuje skupiny, do kterých se mají umístit objekty vrácené výrazem dotazu ([Select](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="ecddb-103">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecddb-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ecddb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ecddb-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="ecddb-106">Libovolný platný výraz dotazu, na kterém je prováděno seskupování.</span><span class="sxs-lookup"><span data-stu-id="ecddb-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="ecddb-107">`expression`může se jednat o vlastnost nebo neagregovaný výraz, který odkazuje na vlastnost vrácenou klauzulí FROM.</span><span class="sxs-lookup"><span data-stu-id="ecddb-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="ecddb-108">Každý výraz v klauzuli GROUP BY musí být vyhodnocen jako typ, který lze porovnat s rovností.</span><span class="sxs-lookup"><span data-stu-id="ecddb-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="ecddb-109">Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="ecddb-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="ecddb-110">Nelze seskupit podle kolekce.</span><span class="sxs-lookup"><span data-stu-id="ecddb-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecddb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecddb-111">Remarks</span></span>  
 <span data-ttu-id="ecddb-112">Pokud jsou agregační funkce zahrnuté v klauzuli \<SELECT, vyberte seznam >, Group by vypočítá souhrnnou hodnotu pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="ecddb-113">Pokud je zadána možnost GROUP BY, každý název vlastnosti v jakémkoli neagregačním výrazu v seznamu SELECT by měl být zahrnut do seznamu GROUP by, nebo výraz GROUP BY musí přesně odpovídat výrazu SELECT list.</span><span class="sxs-lookup"><span data-stu-id="ecddb-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecddb-114">Pokud není zadána klauzule ORDER BY, skupiny vrácené klauzulí GROUP BY nejsou v žádném konkrétním pořadí.</span><span class="sxs-lookup"><span data-stu-id="ecddb-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="ecddb-115">K určení konkrétního pořadí dat doporučujeme vždy použít klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="ecddb-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="ecddb-116">Pokud je zadána klauzule GROUP BY, ať už explicitně nebo implicitně (například v klauzuli HAVING v dotazu), je aktuální obor skrytý a zavedený nový obor.</span><span class="sxs-lookup"><span data-stu-id="ecddb-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="ecddb-117">Klauzule SELECT, klauzule HAVING a klauzule ORDER BY již nebudou moci odkazovat na názvy prvků zadané v klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="ecddb-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="ecddb-118">Můžete odkazovat pouze na samotné výrazy seskupení.</span><span class="sxs-lookup"><span data-stu-id="ecddb-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="ecddb-119">Chcete-li to provést, můžete každému výrazu seskupení přiřadit nové názvy (aliasy).</span><span class="sxs-lookup"><span data-stu-id="ecddb-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="ecddb-120">Pokud pro seskupovací výraz není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroj se pokusí vygenerovat jeden pomocí pravidel generování aliasů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="ecddb-121">Výrazy v klauzuli GROUP BY nemůžou odkazovat na názvy definované dříve v klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="ecddb-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="ecddb-122">Kromě seskupení názvů můžete také zadat agregace v klauzuli SELECT, klauzuli HAVING a klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="ecddb-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="ecddb-123">Agregace obsahuje výraz, který je vyhodnocen pro každý prvek skupiny.</span><span class="sxs-lookup"><span data-stu-id="ecddb-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="ecddb-124">Agregační operátor omezuje hodnoty všech těchto výrazů (obvykle ale ne vždy na jednu hodnotu).</span><span class="sxs-lookup"><span data-stu-id="ecddb-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="ecddb-125">Agregační výraz může vytvořit odkazy na původní názvy elementů, které jsou viditelné v nadřazeném oboru, nebo na kterýkoli z nových názvů zavedených klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="ecddb-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="ecddb-126">I když se agregace zobrazují v klauzuli SELECT, klauzule HAVING a klauzule ORDER by, jsou ve skutečnosti vyhodnoceny v rámci stejného oboru jako výrazy seskupení, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="ecddb-127">Tento dotaz pomocí klauzule GROUP BY vytvoří sestavu nákladů na všechny seřazené produkty, které jsou rozdělené podle produktu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="ecddb-128">Poskytuje název `name` produktu jako součást seskupovacího výrazu a pak odkazuje na tento název v seznamu SELECT.</span><span class="sxs-lookup"><span data-stu-id="ecddb-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="ecddb-129">Určuje také agregaci `sum` v seznamu SELECT, který interně odkazuje na cenu a množství řádku objednávky.</span><span class="sxs-lookup"><span data-stu-id="ecddb-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="ecddb-130">Každý výraz GROUP by musí obsahovat alespoň jeden odkaz na vstupní rozsah:</span><span class="sxs-lookup"><span data-stu-id="ecddb-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="ecddb-131">Příklad použití klauzule GROUP BY naleznete v tématu [having](having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ecddb-131">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecddb-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecddb-132">Example</span></span>  
 <span data-ttu-id="ecddb-133">Následující Entity SQL dotaz používá operátor GROUP BY k určení skupin, do kterých jsou objekty vraceny dotazem.</span><span class="sxs-lookup"><span data-stu-id="ecddb-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="ecddb-134">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ecddb-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ecddb-135">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="ecddb-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ecddb-136">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="ecddb-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ecddb-137">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="ecddb-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="ecddb-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecddb-138">See also</span></span>

- [<span data-ttu-id="ecddb-139">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ecddb-139">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ecddb-140">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="ecddb-140">Query Expressions</span></span>](query-expressions-entity-sql.md)
