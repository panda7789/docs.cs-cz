---
title: Z (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 3cc02b4c51b32d0faace4d89d0c6c1f6923dd138
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879577"
---
# <a name="from-entity-sql"></a><span data-ttu-id="41193-102">Z (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="41193-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="41193-103">Určuje kolekci používané [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="41193-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41193-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41193-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="41193-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="41193-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="41193-106">Libovolný platný dotaz výraz, jehož výsledkem jsou použít jako zdroj v kolekci `SELECT` příkazu.</span><span class="sxs-lookup"><span data-stu-id="41193-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41193-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41193-107">Remarks</span></span>  
 <span data-ttu-id="41193-108">A `FROM` klauzule je čárkou oddělený seznam jednoho nebo víc `FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="41193-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="41193-109">`FROM` Klauzuli lze použít k určení pro jeden nebo více zdrojů `SELECT` příkazu.</span><span class="sxs-lookup"><span data-stu-id="41193-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="41193-110">Nejjednodušší forma `FROM` je klauzule výrazu jednoho dotazu, která identifikuje kolekci a použít jako zdroj v aliasu `SELECT` příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="41193-111">Z položky – klauzule</span><span class="sxs-lookup"><span data-stu-id="41193-111">FROM Clause Items</span></span>  
 <span data-ttu-id="41193-112">Každý `FROM` klauzule položka odkazuje na kolekci zdrojové v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="41193-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="41193-113">podporuje následující třídy `FROM` klauzule položky: jednoduché `FROM` klauzule položky `JOIN FROM` klauzule položky a `APPLY FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="41193-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="41193-114">Každá z těchto `FROM` klauzule položky je popsána podrobněji v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="41193-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="41193-115">Jednoduché položka klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="41193-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="41193-116">Nejjednodušší `FROM` položka klauzule je jediný výraz, který identifikuje kolekci a alias.</span><span class="sxs-lookup"><span data-stu-id="41193-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="41193-117">Výraz může být jednoduše sadu entit, nebo poddotaz nebo jiný výraz, který se o typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="41193-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="41193-118">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="41193-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="41193-119">Specifikace alias je volitelné.</span><span class="sxs-lookup"><span data-stu-id="41193-119">The alias specification is optional.</span></span> <span data-ttu-id="41193-120">Alternativní specifikace z výše uvedených položka klauzule from může být následující:</span><span class="sxs-lookup"><span data-stu-id="41193-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="41193-121">Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias založené na výrazu kolekce.</span><span class="sxs-lookup"><span data-stu-id="41193-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="41193-122">Připojte se k položka klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="41193-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="41193-123">A `JOIN FROM` položka klauzule představuje spojení mezi dvěma `FROM` klauzule položky.</span><span class="sxs-lookup"><span data-stu-id="41193-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="41193-124">podporuje různé spojení, vnitřní spojení, levé a pravé vnější spojení a plné vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="41193-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="41193-125">Jsou podporovány tyto spojení podobným způsobem, jakým jsou podporovány v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41193-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="41193-126">Stejně jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dva `FROM` součástí klauzule položky `JOIN` musí být nezávislé.</span><span class="sxs-lookup"><span data-stu-id="41193-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="41193-127">To znamená že nelze korelaci.</span><span class="sxs-lookup"><span data-stu-id="41193-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="41193-128">A `CROSS APPLY` nebo `OUTER APPLY` lze použít pro tyto případy.</span><span class="sxs-lookup"><span data-stu-id="41193-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="41193-129">Křížové spojení</span><span class="sxs-lookup"><span data-stu-id="41193-129">Cross Joins</span></span>  
 <span data-ttu-id="41193-130">A `CROSS JOIN` dotazu výraz vytvoří kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="41193-131">Vnitřní spojení</span><span class="sxs-lookup"><span data-stu-id="41193-131">Inner Joins</span></span>  
 <span data-ttu-id="41193-132">`INNER JOIN` Vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="41193-133">Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="41193-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="41193-134">Pokud ne `ON` je zadána podmínka, `INNER JOIN` degeneruje k `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="41193-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="41193-135">Levé vnější spojení a levé vnější spojení</span><span class="sxs-lookup"><span data-stu-id="41193-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="41193-136">`OUTER JOIN` Dotazu výraz vytvoří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="41193-137">Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="41193-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="41193-138">Pokud `ON` podmínka není splněna, výraz stále zpracovává jednu instanci elementu na levé straně spáruje elementu na pravé straně s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="41193-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="41193-139">A `RIGHT OUTER JOIN` podobným způsobem je možné vyjádřit.</span><span class="sxs-lookup"><span data-stu-id="41193-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="41193-140">Úplné vnější spojení</span><span class="sxs-lookup"><span data-stu-id="41193-140">Full Outer Joins</span></span>  
 <span data-ttu-id="41193-141">Explicitní `FULL OUTER JOIN` vytváří omezené kartézský součin dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="41193-142">Předchozí výrazu dotazu zpracovává kombinaci každý prvek kolekce na levé straně spáruje každý prvek v kolekci podle pravé, kde `ON` je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="41193-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="41193-143">Pokud `ON` podmínka není splněna, výraz stále zpracovává jeden výskyt elementu na levé straně spáruje elementu na pravé straně s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="41193-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="41193-144">Zpracovává také jednu instanci elementu na pravé straně spáruje elementu na levé straně, s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="41193-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41193-145">Chcete-li zachovat kompatibilitu s SQL-92 v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] vnější – klíčové slovo je volitelný.</span><span class="sxs-lookup"><span data-stu-id="41193-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="41193-146">Proto `LEFT JOIN`, `RIGHT JOIN`, a `FULL JOIN` jsou synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, a `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="41193-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="41193-147">POUŽITÍ klauzule položky</span><span class="sxs-lookup"><span data-stu-id="41193-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="41193-148">podporuje dva typy z `APPLY`: `CROSS APPLY` a `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="41193-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="41193-149">A `CROSS APPLY` vytvoří jedinečný párování jednotlivých elementů kolekce na levé straně s elementem kolekci vytvořenou testovaným vyhodnocení výrazu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="41193-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="41193-150">S `CROSS APPLY`, výraz na pravé straně je funkčně závislé na element na levé straně, jak je znázorněno v následujícím příkladu přiřazené kolekce:</span><span class="sxs-lookup"><span data-stu-id="41193-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="41193-151">Chování `CROSS APPLY` se podobá seznamu spojení.</span><span class="sxs-lookup"><span data-stu-id="41193-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="41193-152">Pokud výraz na pravé straně je vyhodnocen jako prázdnou kolekci, `CROSS APPLY` vytváří žádné párování pro tuto instanci elementu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="41193-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="41193-153">`OUTER APPLY` Vypadá podobně jako `CROSS APPLY`, s výjimkou párování se stále vytváří, i v případě, že výraz na pravé straně je vyhodnocen jako prázdnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="41193-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="41193-154">Následující je příkladem `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="41193-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="41193-155">Na rozdíl od v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], není nutné pro explicitní unnest krok [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41193-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41193-156">`CROSS` a `OUTER APPLY` operátory byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41193-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="41193-157">V některých případech může být kanálu dotazu jazyka Transact-SQL, který obsahuje `CROSS APPLY` a/nebo `OUTER APPLY` operátory.</span><span class="sxs-lookup"><span data-stu-id="41193-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="41193-158">Protože někteří poskytovatelé back-end, včetně verze SQL serveru starší než [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nepodporují tyto operátory, tyto dotazy se nedá spustit na těchto zprostředkovatelů back-endu.</span><span class="sxs-lookup"><span data-stu-id="41193-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="41193-159">Některé typické scénáře, které by mohly vést k výskytu `CROSS APPLY` a/nebo `OUTER APPLY` operátory v dotazu výstupu jsou následující: korelační poddotaz s stránkování; AnyElement přes korelační poddotaz nebo kolekci vytvořenou testovaným navigace; LINQ dotazy, které používají metody, které přijímají elementu selektoru; seskupení dotaz, ve kterém `CROSS APPLY` nebo `OUTER APPLY` jsou explicitně zadány; dotaz, který má `DEREF` vytvořit přes `REF` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="41193-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="41193-160">Více kolekcí v FROM – klauzule</span><span class="sxs-lookup"><span data-stu-id="41193-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="41193-161">`FROM` Klauzule může obsahovat více než jednu kolekci, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="41193-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="41193-162">V těchto případech kolekce se předpokládá, že spojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="41193-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="41193-163">Si můžete představte jako křížové spojení n způsobem.</span><span class="sxs-lookup"><span data-stu-id="41193-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="41193-164">V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`.</span><span class="sxs-lookup"><span data-stu-id="41193-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="41193-165">V předchozím příkladu je logicky ekvivalentní v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="41193-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="41193-166">Levá korelace</span><span class="sxs-lookup"><span data-stu-id="41193-166">Left Correlation</span></span>  
 <span data-ttu-id="41193-167">Položky v `FROM` klauzule mohou odkazovat na položky uvedené v předchozích klauzule.</span><span class="sxs-lookup"><span data-stu-id="41193-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="41193-168">V následujícím příkladu `C` a `D` jsou nezávislé kolekce, ale `c.Names` závisí na `C`:</span><span class="sxs-lookup"><span data-stu-id="41193-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="41193-169">To je logicky ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="41193-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="41193-170">Sémantika</span><span class="sxs-lookup"><span data-stu-id="41193-170">Semantics</span></span>  
 <span data-ttu-id="41193-171">Logicky, kolekce v `FROM` klauzule jsou považovány za součást `n`-způsobem křížové spojení (s výjimkou v případě 1způsob cross join).</span><span class="sxs-lookup"><span data-stu-id="41193-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="41193-172">Aliasy v `FROM` klauzule jsou zpracovávány zleva doprava a jsou přidány do aktuálního oboru pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="41193-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="41193-173">`FROM` Klauzule předpokládá, že je vytvořit multiset řádků.</span><span class="sxs-lookup"><span data-stu-id="41193-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="41193-174">Bude mít jedno pole pro každou položku v `FROM` klauzuli, která představuje jeden element z této položky kolekce.</span><span class="sxs-lookup"><span data-stu-id="41193-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="41193-175">`FROM` Vytvoří logicky klauzule multiset řádků typu řádku (c, d, e), kde pole jazyka c, d a e se předpokládá se, že element typu `C`, `D`, a `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="41193-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="41193-176">představuje alias pro každý jednoduchý `FROM` položka klauzule v oboru.</span><span class="sxs-lookup"><span data-stu-id="41193-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="41193-177">V následujícím z klauzule fragment, například názvy zavedené v oboru jsou c, d a e.</span><span class="sxs-lookup"><span data-stu-id="41193-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="41193-178">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzule pouze zavádí aliasy do oboru.</span><span class="sxs-lookup"><span data-stu-id="41193-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="41193-179">Všechny odkazy na sloupce (Vlastnosti) těchto kolekcí musí být kvalifikován s aliasem.</span><span class="sxs-lookup"><span data-stu-id="41193-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="41193-180">Stahují se klíče z vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="41193-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="41193-181">Některé typy dotazů, které vyžadují stahují do klíče z vnořeného dotazu nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="41193-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="41193-182">Například následující dotaz je neplatný:</span><span class="sxs-lookup"><span data-stu-id="41193-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="41193-183">Následující dotaz, ale není platný, protože vnořený dotaz nemá žádné klíče:</span><span class="sxs-lookup"><span data-stu-id="41193-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="41193-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41193-184">See also</span></span>

- [<span data-ttu-id="41193-185">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="41193-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="41193-186">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="41193-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="41193-187">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="41193-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
