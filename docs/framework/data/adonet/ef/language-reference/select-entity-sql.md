---
title: Vyberte (entita SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: f815c08b9be11efc71b04678d9780cabcdd69ab5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765981"
---
# <a name="select-entity-sql"></a><span data-ttu-id="7128c-102">Vyberte (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="7128c-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="7128c-103">Určuje prvky vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="7128c-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7128c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7128c-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="7128c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7128c-105">Arguments</span></span>  
 <span data-ttu-id="7128c-106">VŠECHNY</span><span class="sxs-lookup"><span data-stu-id="7128c-106">ALL</span></span>  
 <span data-ttu-id="7128c-107">Určuje, že duplicitní může zobrazit v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="7128c-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="7128c-108">VŠECHNY je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7128c-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="7128c-109">ODLIŠNÉ</span><span class="sxs-lookup"><span data-stu-id="7128c-109">DISTINCT</span></span>  
 <span data-ttu-id="7128c-110">Určuje, že můžete pouze jedinečné výsledky se zobrazí v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="7128c-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="7128c-111">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="7128c-111">VALUE</span></span>  
 <span data-ttu-id="7128c-112">Umožňuje zadat, pouze jedinou položku a nepřidá na řádek obálku.</span><span class="sxs-lookup"><span data-stu-id="7128c-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="7128c-113">Libovolný platný výraz, který označuje číslo, které první výsledků vrácených z dotazu, formuláře `top (``expr``)`.</span><span class="sxs-lookup"><span data-stu-id="7128c-113">Any valid expression that indicates the number of first results to return from the query, of the form `top (``expr``)`.</span></span>  
  
 <span data-ttu-id="7128c-114">Parametr LIMIT [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operátor také umožňuje vybrat prvních n položek v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="7128c-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="7128c-115">Výraz ve tvaru:</span><span class="sxs-lookup"><span data-stu-id="7128c-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="7128c-116">`expr` jako `identifier`&#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="7128c-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="7128c-117">Literál nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="7128c-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7128c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7128c-118">Remarks</span></span>  
 <span data-ttu-id="7128c-119">Klauzule SELECT vyhodnotí po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), a [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) byly vyhodnoceny klauzule.</span><span class="sxs-lookup"><span data-stu-id="7128c-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="7128c-120">Klauzule SELECT může odkazovat pouze na položky aktuálně oboru (z klauzule FROM nebo z vnějšího oborů).</span><span class="sxs-lookup"><span data-stu-id="7128c-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="7128c-121">Pokud byla zadána klauzule GROUP BY, klauzule SELECT je povoleno pouze tak, aby odkazovaly aliasy pro klíče GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="7128c-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="7128c-122">Odkazy na položky klauzule FROM je povolená jenom v agregačních funkcích.</span><span class="sxs-lookup"><span data-stu-id="7128c-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="7128c-123">Seznam následující klíčového slova vyberte jeden nebo více výrazů dotazu se označuje jako seznamu příkazu select nebo oficiálně jako projekce.</span><span class="sxs-lookup"><span data-stu-id="7128c-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="7128c-124">Většina Obecná forma projekce je výraz jeden dotaz.</span><span class="sxs-lookup"><span data-stu-id="7128c-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="7128c-125">Pokud vyberete členem `member1` z kolekce `collection1`, vytvoří novou kolekci všech `member1` hodnoty pro každý objekt v `collection1`, jak je popsáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7128c-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="7128c-126">Například pokud `customers` je kolekce typu `Customer` má vlastnost `Name` , je typu `string`, vyberete `Name` z `customers` předá kolekce řetězce, jak je znázorněno v následujícím příkladu .</span><span class="sxs-lookup"><span data-stu-id="7128c-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="7128c-127">Je také možné použití syntaxe spojení (FULL, vnitřní, vlevo, vnější, ON a vpravo).</span><span class="sxs-lookup"><span data-stu-id="7128c-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="7128c-128">Dále je potřeba pro vnitřní spojení a je nChcete-li povolena křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="7128c-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="7128c-129">Řádek a hodnota klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="7128c-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7128c-130"> podporuje dvě varianty klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="7128c-130"> supports two variants of the SELECT clause.</span></span> <span data-ttu-id="7128c-131">První variant, vyberte řádek, je identifikována vyberte – klíčové slovo a umožňuje určit jednu nebo více hodnot, které by měl použít k projekci se. Protože implicitně přidání řádek obálku kolem hodnot vrácených výsledkem výrazu dotazu je vždy multimnožina řádků.</span><span class="sxs-lookup"><span data-stu-id="7128c-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="7128c-132">Každý výraz dotazu v vyberte řádek zadejte alias.</span><span class="sxs-lookup"><span data-stu-id="7128c-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="7128c-133">Pokud není zadaný žádný alias,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generování alias pomocí pravidel pro vytvoření aliasu.</span><span class="sxs-lookup"><span data-stu-id="7128c-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="7128c-134">Další varianta klauzuli SELECT, vyberte hodnotu, je identifikován – klíčové slovo SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="7128c-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="7128c-135">Umožňuje zadat, pouze jednu hodnotu a nepřidává žádné další řádek obálku.</span><span class="sxs-lookup"><span data-stu-id="7128c-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="7128c-136">Vyberte řádek je vždy vyjádřit kombinací z hlediska hodnotu vyberte, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7128c-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="7128c-137">Všechny a odlišné modifikátory</span><span class="sxs-lookup"><span data-stu-id="7128c-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="7128c-138">Obě variant vyberte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] povolit specifikace všech nebo odlišné modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7128c-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="7128c-139">Pokud je zadán odlišné modifikátor, duplicitní položky se odstraní z kolekce vyprodukované výrazu dotazu (do a včetně klauzule SELECT).</span><span class="sxs-lookup"><span data-stu-id="7128c-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="7128c-140">Pokud se všechny modifikátor zadaný, ne duplicitní odstranění probíhá; VŠECHNY je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7128c-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="7128c-141">Rozdíl oproti Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7128c-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="7128c-142">Na rozdíl od jazyka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje použití \* argument v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="7128c-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="7128c-143">Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazy do projektu se celé záznamy odkazem aliasy kolekce z klauzule FROM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7128c-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="7128c-144">Předchozí [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazu dotazu je vyjádřena v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7128c-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="7128c-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="7128c-145">Example</span></span>  
 <span data-ttu-id="7128c-146">Následující dotaz Entity SQL používá operátor SELECT zadat prvky, které mají být vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="7128c-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="7128c-147">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7128c-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7128c-148">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="7128c-148">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7128c-149">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7128c-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="7128c-150">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="7128c-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="7128c-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="7128c-151">See Also</span></span>  
 [<span data-ttu-id="7128c-152">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="7128c-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="7128c-153">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7128c-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7128c-154">TOP</span><span class="sxs-lookup"><span data-stu-id="7128c-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
