---
title: Z (entita SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: de2ad24e5c6399ed1ca91e3907da4a66c056e337
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="from-entity-sql"></a><span data-ttu-id="8e584-102">Z (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8e584-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="8e584-103">Určuje kolekci použít v [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="8e584-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e584-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e584-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e584-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e584-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8e584-106">Libovolný platný dotaz výraz, který poskytuje kolekci, použít jako zdroj v `SELECT` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e584-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e584-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e584-107">Remarks</span></span>  
 <span data-ttu-id="8e584-108">A `FROM` klauzule je textový soubor s oddělovači seznam jedné nebo více `FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="8e584-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="8e584-109">`FROM` Klauzuli lze použít k zadání jednoho nebo více zdrojů pro `SELECT` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e584-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="8e584-110">Nejjednodušší forma `FROM` klauzule je výraz jeden dotaz, který identifikuje kolekce a použít jako zdroj v alias `SELECT` příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="8e584-111">Z klauzule položek</span><span class="sxs-lookup"><span data-stu-id="8e584-111">FROM Clause Items</span></span>  
 <span data-ttu-id="8e584-112">Každý `FROM` položka klauzule odkazuje na kolekci zdrojové v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="8e584-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8e584-113"> podporuje následující třídy `FROM` položky klauzule: jednoduchý `FROM` položky klauzule `JOIN FROM` klauzule položky a `APPLY FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="8e584-113"> supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="8e584-114">Každá z těchto `FROM` klauzule položky je podrobně popsaná v další v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="8e584-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="8e584-115">Jednoduché z klauzule položky</span><span class="sxs-lookup"><span data-stu-id="8e584-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="8e584-116">Nejjednodušším `FROM` položka klauzule je jeden výraz, který identifikuje do kolekce a alias.</span><span class="sxs-lookup"><span data-stu-id="8e584-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="8e584-117">Výraz může být jednoduše sadu entit nebo poddotazu nebo jiných výraz, který je typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="8e584-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="8e584-118">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="8e584-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="8e584-119">Alias specifikace je volitelná.</span><span class="sxs-lookup"><span data-stu-id="8e584-119">The alias specification is optional.</span></span> <span data-ttu-id="8e584-120">Alternativní specifikaci výše z klauzule položky může být následující:</span><span class="sxs-lookup"><span data-stu-id="8e584-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="8e584-121">Pokud není zadaný žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generovat alias na základě kolekce výrazu.</span><span class="sxs-lookup"><span data-stu-id="8e584-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="8e584-122">PŘIPOJENÍ z položka klauzule</span><span class="sxs-lookup"><span data-stu-id="8e584-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="8e584-123">A `JOIN FROM` položka klauzule představuje spojení mezi dvěma `FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="8e584-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8e584-124"> podporuje křížové spojení, vnitřní spojení, levé a pravé vnější spojení a úplné vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="8e584-124"> supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="8e584-125">Všechny tyto spojení jsou podporované podobně jako způsob, jakým jsou podporovány v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e584-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8e584-126">Jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dva `FROM` součástí klauzule položky `JOIN` musí být nezávislé.</span><span class="sxs-lookup"><span data-stu-id="8e584-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="8e584-127">To znamená že nelze korelaci.</span><span class="sxs-lookup"><span data-stu-id="8e584-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="8e584-128">A `CROSS APPLY` nebo `OUTER APPLY` lze použít pro tyto případy.</span><span class="sxs-lookup"><span data-stu-id="8e584-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="8e584-129">Křížové spojení</span><span class="sxs-lookup"><span data-stu-id="8e584-129">Cross Joins</span></span>  
 <span data-ttu-id="8e584-130">A `CROSS JOIN` dotazu výraz vytváří kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="8e584-131">Vnitřní spojení</span><span class="sxs-lookup"><span data-stu-id="8e584-131">Inner Joins</span></span>  
 <span data-ttu-id="8e584-132">`INNER JOIN` Vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="8e584-133">Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="8e584-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="8e584-134">Pokud žádné `ON` je zadaná podmínka, `INNER JOIN` degeneruje k `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="8e584-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="8e584-135">Levé vnější spojení a levé vnější spojení</span><span class="sxs-lookup"><span data-stu-id="8e584-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="8e584-136">`OUTER JOIN` Dotazu výraz vytvoří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="8e584-137">Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="8e584-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="8e584-138">Pokud `ON` podmínka vyhodnocena jako false, výraz stále zpracovává jednu instanci elementu na levé straně spárovat proti element na pravé straně, se hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8e584-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="8e584-139">A `RIGHT OUTER JOIN` podobným způsobem je možné vyjádřit.</span><span class="sxs-lookup"><span data-stu-id="8e584-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="8e584-140">Úplné vnější spojení</span><span class="sxs-lookup"><span data-stu-id="8e584-140">Full Outer Joins</span></span>  
 <span data-ttu-id="8e584-141">Explicitního `FULL OUTER JOIN` vytváří omezené kartézský součin dvou kolekce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="8e584-142">Předchozí výrazu dotazu zpracovává kombinaci každý element kolekce na levé straně spárovat proti každý element v kolekci podle pravé, kde `ON` je splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="8e584-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="8e584-143">Pokud `ON` podmínka vyhodnocena jako false, výraz stále zpracovává jednu instanci elementu na levé straně spárovat proti element na pravé straně, se hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8e584-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="8e584-144">Zpracuje také jednu instanci prvku na pravé straně spárovat proti elementu na levé straně, se hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8e584-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e584-145">Zachování kompatibility s SQL-92 v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] – klíčové slovo vnější je volitelný.</span><span class="sxs-lookup"><span data-stu-id="8e584-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="8e584-146">Proto `LEFT JOIN`, `RIGHT JOIN`, a `FULL JOIN` jsou synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, a `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="8e584-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="8e584-147">POUŽÍT položka klauzule</span><span class="sxs-lookup"><span data-stu-id="8e584-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8e584-148"> podporuje dva typy z `APPLY`: `CROSS APPLY` a `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="8e584-148"> supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="8e584-149">A `CROSS APPLY` vytváří jedinečný párování každého prvku kolekce na levé straně s elementem kolekce vyprodukované vyhodnocení výrazu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="8e584-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="8e584-150">S `CROSS APPLY`, výraz na pravé straně je funkčně závislé na elementu na levé straně, jak je znázorněno v následujícím příkladu přiřazené kolekce:</span><span class="sxs-lookup"><span data-stu-id="8e584-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="8e584-151">Chování `CROSS APPLY` je podobná seznamu spojení.</span><span class="sxs-lookup"><span data-stu-id="8e584-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="8e584-152">Pokud je výsledkem výrazu na pravé straně prázdnou kolekci, `CROSS APPLY` neprodukuje žádný dvojic u dané instance elementu vlevo.</span><span class="sxs-lookup"><span data-stu-id="8e584-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="8e584-153">`OUTER APPLY` Vypadá takto: `CROSS APPLY`, s výjimkou párování se stále vytvářejí i v případě, že na pravé straně vyhodnocen jako prázdnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="8e584-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="8e584-154">Tady je příklad `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="8e584-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="8e584-155">Na rozdíl od v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], není nutné explicitní příkazu unnest krok v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e584-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e584-156">`CROSS` a `OUTER APPLY` operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e584-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="8e584-157">V některých případech může být kanálu dotazu jazyka Transact-SQL, který obsahuje `CROSS APPLY` nebo `OUTER APPLY` operátory.</span><span class="sxs-lookup"><span data-stu-id="8e584-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="8e584-158">Protože někteří poskytovatelé back-end, včetně verze systému SQL Server starších než [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, takové dotazy se nedá spustit na tyto zprostředkovatele back-end.</span><span class="sxs-lookup"><span data-stu-id="8e584-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="8e584-159">Některé typické scénáře, které mohou vést k přítomnost `CROSS APPLY` nebo `OUTER APPLY` operátory v dotazu výstupní jsou následující: korelační poddotaz s stránkování; AnyElement přes korelační poddotazu nebo přes kolekci vyprodukované navigační; LINQ dotazy, které používají seskupování metody, které přijímají selektorem elementu; dotaz, ve kterém `CROSS APPLY` nebo `OUTER APPLY` jsou explicitně určena; dotaz, který má `DEREF` vytvořit přes `REF` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8e584-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="8e584-160">Více kolekcí v od – klauzule</span><span class="sxs-lookup"><span data-stu-id="8e584-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="8e584-161">`FROM` Klauzule může obsahovat více než jednu kolekci oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="8e584-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="8e584-162">V těchto případech kolekce se předpokládá, že se propojeny.</span><span class="sxs-lookup"><span data-stu-id="8e584-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="8e584-163">Vezměte v úvahu tyto jako n způsob křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="8e584-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="8e584-164">V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`.</span><span class="sxs-lookup"><span data-stu-id="8e584-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="8e584-165">V předchozím příkladu je logicky ekvivalentní v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8e584-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="8e584-166">Levá korelace</span><span class="sxs-lookup"><span data-stu-id="8e584-166">Left Correlation</span></span>  
 <span data-ttu-id="8e584-167">Položky v `FROM` klauzule mohou odkazovat na položky zadaná v dřívější klauzule.</span><span class="sxs-lookup"><span data-stu-id="8e584-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="8e584-168">V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`:</span><span class="sxs-lookup"><span data-stu-id="8e584-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="8e584-169">To je logicky ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="8e584-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="8e584-170">Sémantika</span><span class="sxs-lookup"><span data-stu-id="8e584-170">Semantics</span></span>  
 <span data-ttu-id="8e584-171">Logicky, kolekcí v `FROM` klauzule jsou považovány za součást `n`-způsobem křížové spojení (s výjimkou v případě 1způsob křížové spojení).</span><span class="sxs-lookup"><span data-stu-id="8e584-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="8e584-172">Aliasy v `FROM` klauzule jsou zpracovávány zleva doprava a jsou přidány do aktuálního oboru pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="8e584-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="8e584-173">`FROM` Klauzule se předpokládá, že k vytvoření multimnožina řádků.</span><span class="sxs-lookup"><span data-stu-id="8e584-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="8e584-174">Bude jedno pole pro každou položku v `FROM` klauzuli, která představuje jeden element z této kolekce položky.</span><span class="sxs-lookup"><span data-stu-id="8e584-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="8e584-175">`FROM` Vytvoří logicky klauzule multimnožina řádků typu řádku (c, d, e), kde pole c, d a e považují za element typu `C`, `D`, a `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="8e584-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8e584-176"> představuje alias pro každý jednoduchý `FROM` položka klauzule v oboru.</span><span class="sxs-lookup"><span data-stu-id="8e584-176"> introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="8e584-177">Například v následujícím z klauzule fragment, jsou do oboru názvů c, d a e.</span><span class="sxs-lookup"><span data-stu-id="8e584-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="8e584-178">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzule pouze zavádí zástupci do oboru.</span><span class="sxs-lookup"><span data-stu-id="8e584-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="8e584-179">Všechny odkazy na sloupce (Vlastnosti) těchto kolekcí musí být kvalifikovaný pomocí alias.</span><span class="sxs-lookup"><span data-stu-id="8e584-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="8e584-180">Stahování se klíče z vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="8e584-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="8e584-181">Některé typy dotazů, které vyžadují stahování až klíče ze vnořeném dotazu nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="8e584-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="8e584-182">Například následující dotaz je neplatný:</span><span class="sxs-lookup"><span data-stu-id="8e584-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="8e584-183">Následující dotaz však není platný, protože vnořený dotaz nemá žádné klíče:</span><span class="sxs-lookup"><span data-stu-id="8e584-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e584-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e584-184">See Also</span></span>  
 [<span data-ttu-id="8e584-185">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8e584-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="8e584-186">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="8e584-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="8e584-187">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8e584-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
