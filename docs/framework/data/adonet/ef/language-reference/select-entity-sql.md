---
title: VYBRAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249205"
---
# <a name="select-entity-sql"></a><span data-ttu-id="14bb0-102">VYBRAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14bb0-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="14bb0-103">Určuje prvky vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="14bb0-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14bb0-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="14bb0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="14bb0-105">Arguments</span></span>  
 <span data-ttu-id="14bb0-106">VŠEM</span><span class="sxs-lookup"><span data-stu-id="14bb0-106">ALL</span></span>  
 <span data-ttu-id="14bb0-107">Určuje, že se duplikáty můžou objevit v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="14bb0-108">Výchozí hodnota je ALL.</span><span class="sxs-lookup"><span data-stu-id="14bb0-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="14bb0-109">ZNAK</span><span class="sxs-lookup"><span data-stu-id="14bb0-109">DISTINCT</span></span>  
 <span data-ttu-id="14bb0-110">Určuje, že v sadě výsledků se můžou vyskytovat jenom jedinečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="14bb0-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="14bb0-111">OSA</span><span class="sxs-lookup"><span data-stu-id="14bb0-111">VALUE</span></span>  
 <span data-ttu-id="14bb0-112">Povoluje zadání pouze jedné položky a nepřidá se na obálku řádku.</span><span class="sxs-lookup"><span data-stu-id="14bb0-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="14bb0-113">Libovolný platný výraz, který určuje počet prvních výsledků, které se mají vrátit z dotazu formuláře `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="14bb0-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="14bb0-114">Parametr LIMIT operátoru [ORDER by](order-by-entity-sql.md) také umožňuje vybrat prvních n položek v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="14bb0-115">Výraz formuláře:</span><span class="sxs-lookup"><span data-stu-id="14bb0-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="14bb0-116">`expr`jako `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="14bb0-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="14bb0-117">Literál nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="14bb0-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14bb0-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14bb0-118">Remarks</span></span>  
 <span data-ttu-id="14bb0-119">Klauzule SELECT je vyhodnocena po vyhodnocení klauzulí [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)a [having](having-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="14bb0-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="14bb0-120">Klauzule SELECT může odkazovat pouze na položky aktuálně nacházející se v oboru (z klauzule FROM nebo z vnějších oborů).</span><span class="sxs-lookup"><span data-stu-id="14bb0-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="14bb0-121">Pokud je zadána klauzule GROUP BY, klauzule SELECT je povolena pouze pro odkazy na aliasy pro skupinu podle klíčů.</span><span class="sxs-lookup"><span data-stu-id="14bb0-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="14bb0-122">Odkazování na položky klauzule FROM je povoleno pouze v agregačních funkcích.</span><span class="sxs-lookup"><span data-stu-id="14bb0-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="14bb0-123">Seznam jednoho nebo více výrazů dotazů za klíčovým slovem SELECT je známý jako seznam pro výběr, nebo je ve formě projekce složitější.</span><span class="sxs-lookup"><span data-stu-id="14bb0-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="14bb0-124">Nejobecnější forma projekce je jeden výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="14bb0-125">Pokud vyberete člena `member1` z kolekce `collection1`, vytvoří se `member1` nová kolekce všech hodnot pro každý objekt v `collection1`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="14bb0-126">Například `customers` Pokud je kolekce typu `Name` `Name` `Customer` , která má vlastnost, která je typu `string`, výběr z `customers` bude vracet kolekci řetězců, jak je znázorněno v následujícím příkladu. .</span><span class="sxs-lookup"><span data-stu-id="14bb0-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="14bb0-127">Také je možné použít syntaxi spojení (FULL, vnitřní, levý, vnější, ZAPNUTý a pravý).</span><span class="sxs-lookup"><span data-stu-id="14bb0-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="14bb0-128">ON se vyžaduje pro vnitřní spojení a u vzájemných spojení je k v-nChcete-li povolený.</span><span class="sxs-lookup"><span data-stu-id="14bb0-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="14bb0-129">Klauzule SELECT pro řádek a hodnotu</span><span class="sxs-lookup"><span data-stu-id="14bb0-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="14bb0-130">podporuje dvě varianty klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="14bb0-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="14bb0-131">První varianta, výběr řádku, je identifikována klíčovým slovem SELECT a lze ji použít k zadání jedné nebo více hodnot, které by měly být vyhodnoceny jako neočekávané. Vzhledem k tomu, že se obálka řádku implicitně přidala kolem vrácených hodnot, je výsledek výrazu dotazu vždycky multiset řádků.</span><span class="sxs-lookup"><span data-stu-id="14bb0-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="14bb0-132">Každý výraz dotazu v řádku SELECT musí určovat alias.</span><span class="sxs-lookup"><span data-stu-id="14bb0-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="14bb0-133">Pokud není zadán žádný alias,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] aplikace se pokusí vygenerovat alias pomocí pravidel generování aliasů.</span><span class="sxs-lookup"><span data-stu-id="14bb0-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="14bb0-134">Druhá varianta klauzule SELECT, hodnota SELECT, je identifikována klíčovým slovem SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="14bb0-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="14bb0-135">Umožňuje zadat pouze jednu hodnotu a nepřidá obálku řádku.</span><span class="sxs-lookup"><span data-stu-id="14bb0-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="14bb0-136">Výběr řádku je vždy vyhodnotit ve smyslu hodnoty SELECT, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="14bb0-137">Modifikátory All a DISTINCT</span><span class="sxs-lookup"><span data-stu-id="14bb0-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="14bb0-138">Obě varianty výběru v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňují specifikaci modifikátoru All nebo DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="14bb0-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="14bb0-139">Je-li zadán modifikátor DISTINCT, jsou duplicity odstraněny z kolekce vytvořené výrazem dotazu (až do klauzule SELECT).</span><span class="sxs-lookup"><span data-stu-id="14bb0-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="14bb0-140">Pokud je zadán modifikátor ALL, není provedeno žádné duplicitní eliminace; Výchozí hodnota je ALL.</span><span class="sxs-lookup"><span data-stu-id="14bb0-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="14bb0-141">Rozdíly v jazyce Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="14bb0-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="14bb0-142">Na rozdíl od jazyka Transact- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SQL nepodporuje použití argumentu \* v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="14bb0-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="14bb0-143">Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazům vydávat celé záznamy odkazem na aliasy kolekce z klauzule FROM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="14bb0-144">Předchozí výraz dotazu Transact-SQL je vyjádřen v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobu.</span><span class="sxs-lookup"><span data-stu-id="14bb0-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="14bb0-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="14bb0-145">Example</span></span>  
 <span data-ttu-id="14bb0-146">Následující Entity SQL dotaz používá operátor SELECT k určení prvků, které mají být vráceny dotazem.</span><span class="sxs-lookup"><span data-stu-id="14bb0-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="14bb0-147">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="14bb0-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="14bb0-148">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="14bb0-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="14bb0-149">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="14bb0-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="14bb0-150">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="14bb0-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="14bb0-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14bb0-151">See also</span></span>

- [<span data-ttu-id="14bb0-152">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="14bb0-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="14bb0-153">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14bb0-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="14bb0-154">TOP</span><span class="sxs-lookup"><span data-stu-id="14bb0-154">TOP</span></span>](top-entity-sql.md)
