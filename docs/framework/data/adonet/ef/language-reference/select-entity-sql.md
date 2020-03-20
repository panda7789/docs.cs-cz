---
title: SELECT (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149906"
---
# <a name="select-entity-sql"></a><span data-ttu-id="7875e-102">SELECT (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="7875e-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="7875e-103">Určuje prvky vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="7875e-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7875e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7875e-104">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="7875e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7875e-105">Arguments</span></span>  
 <span data-ttu-id="7875e-106">VŠE</span><span class="sxs-lookup"><span data-stu-id="7875e-106">ALL</span></span>  
 <span data-ttu-id="7875e-107">Určuje, že se ve výsledkové sadě mohou objevit duplikáty.</span><span class="sxs-lookup"><span data-stu-id="7875e-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="7875e-108">ALL je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7875e-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="7875e-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="7875e-109">DISTINCT</span></span>  
 <span data-ttu-id="7875e-110">Určuje, že se ve výsledkové sadě mohou objevit pouze jedinečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="7875e-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="7875e-111">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="7875e-111">VALUE</span></span>  
 <span data-ttu-id="7875e-112">Umožňuje zadat pouze jednu položku a nepřidá obálku řádku.</span><span class="sxs-lookup"><span data-stu-id="7875e-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="7875e-113">Libovolný platný výraz, který označuje počet prvních výsledků, které `top(expr)`se mají vrátit z dotazu formuláře .</span><span class="sxs-lookup"><span data-stu-id="7875e-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="7875e-114">Parametr LIMIT operátoru [OBJET](order-by-entity-sql.md) PODLE také umožňuje vybrat první n položek v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="7875e-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="7875e-115">Výraz formuláře:</span><span class="sxs-lookup"><span data-stu-id="7875e-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="7875e-116">`expr`jako `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="7875e-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="7875e-117">Literál nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="7875e-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7875e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7875e-118">Remarks</span></span>  
 <span data-ttu-id="7875e-119">Klauzule SELECT je vyhodnocena po vyhodnocených klauzulích [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)a [HAVING.](having-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="7875e-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="7875e-120">Select klauzule může odkazovat pouze na položky, které jsou aktuálně v oboru (z klauzule FROM nebo z vnějších oborů).</span><span class="sxs-lookup"><span data-stu-id="7875e-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="7875e-121">Pokud group by klauzule byla zadána, SELECT klauzule je povoleno pouze odkazovat na aliasy pro group by klíče.</span><span class="sxs-lookup"><span data-stu-id="7875e-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="7875e-122">Odkazování na položky klauzule FROM je povoleno pouze v souhrnných funkcích.</span><span class="sxs-lookup"><span data-stu-id="7875e-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="7875e-123">Seznam jednoho nebo více výrazů dotazu za klíčovým slovem SELECT se označuje jako seznam výběru nebo formálněji jako projekce.</span><span class="sxs-lookup"><span data-stu-id="7875e-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="7875e-124">Nejobecnější formou projekce je výraz jednoho dotazu.</span><span class="sxs-lookup"><span data-stu-id="7875e-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="7875e-125">Pokud vyberete `member1` člena z `collection1`kolekce , vytvoříte novou `member1` kolekci všech `collection1`hodnot pro každý objekt v , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7875e-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="7875e-126">Například pokud `customers` je kolekce `Customer` typu, který `Name` má vlastnost, která je typu `string`, výběr `Name` z `customers` přinese kolekci řetězců, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7875e-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="7875e-127">Je také možné použít syntaxi JOIN (ÚPLNÁ, VNITŘNÍ, LEVÁ, VNĚJŠÍ, ZAPNUTÁ A PRAVÁ).</span><span class="sxs-lookup"><span data-stu-id="7875e-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="7875e-128">ON je vyžadován pro vnitřní spojení a je nto povoleno pro křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="7875e-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="7875e-129">Klauzule pro výběr řádků a hodnot</span><span class="sxs-lookup"><span data-stu-id="7875e-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7875e-130">podporuje dvě varianty klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="7875e-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="7875e-131">První varianta, výběr řádku, je identifikována klíčovým slovem SELECT a lze ji použít k určení jedné nebo více hodnot, které by měly být promítnuty. Vzhledem k tomu, že obálka řádku je implicitně přidána kolem vrácených hodnot, je výsledkem výrazu dotazu vždy vícenásobná sada řádků.</span><span class="sxs-lookup"><span data-stu-id="7875e-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="7875e-132">Každý výraz dotazu v řádku select musí určit alias.</span><span class="sxs-lookup"><span data-stu-id="7875e-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="7875e-133">Pokud není zadán[!INCLUDE[esql](../../../../../../includes/esql-md.md)] žádný alias, pokusí se vygenerovat alias pomocí pravidel generování aliasu.</span><span class="sxs-lookup"><span data-stu-id="7875e-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="7875e-134">Druhá varianta klauzule SELECT, vyberte hodnotu, je identifikována klíčovým slovem SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="7875e-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="7875e-135">Umožňuje zadat pouze jednu hodnotu a nepřidá obálku řádku.</span><span class="sxs-lookup"><span data-stu-id="7875e-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="7875e-136">Výběr řádku je vždy vyjádřitelný z hlediska FUNKCE VALUE SELECT, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7875e-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="7875e-137">Všechny a odlišné modifikátory</span><span class="sxs-lookup"><span data-stu-id="7875e-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="7875e-138">Obě varianty SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in umožňují specifikaci modifikátoru ALL nebo DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="7875e-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="7875e-139">Pokud je zadán modifikátor DISTINCT, duplikáty jsou odstraněny z kolekce vytvořené výrazem dotazu (až do klauzule SELECT včetně).</span><span class="sxs-lookup"><span data-stu-id="7875e-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="7875e-140">Pokud je zadán modifikátor ALL, neprovede se žádná duplicitní eliminace; ALL je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7875e-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="7875e-141">Rozdíly od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7875e-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="7875e-142">Na rozdíl od [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL nepodporuje použití \* argument v select klauzule.</span><span class="sxs-lookup"><span data-stu-id="7875e-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="7875e-143">Místo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] toho umožňuje dotazy promítnout celé záznamy odkazem na aliasy kolekce z from klauzule FROM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7875e-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="7875e-144">Předchozí výraz dotazu Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je vyjádřen následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7875e-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="7875e-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="7875e-145">Example</span></span>  
 <span data-ttu-id="7875e-146">Následující dotaz ENTITY SQL používá operátor SELECT k určení prvků, které mají být vráceny dotazem.</span><span class="sxs-lookup"><span data-stu-id="7875e-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="7875e-147">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="7875e-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7875e-148">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="7875e-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7875e-149">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7875e-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7875e-150">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="7875e-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="7875e-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="7875e-151">See also</span></span>

- [<span data-ttu-id="7875e-152">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="7875e-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="7875e-153">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7875e-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7875e-154">Top</span><span class="sxs-lookup"><span data-stu-id="7875e-154">TOP</span></span>](top-entity-sql.md)
