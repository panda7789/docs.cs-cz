---
title: Z (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833822"
---
# <a name="from-entity-sql"></a><span data-ttu-id="594a4-102">Z (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="594a4-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="594a4-103">Určuje kolekci používanou v příkazech [Select](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="594a4-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="594a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="594a4-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="594a4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="594a4-105">Arguments</span></span>

`expression` \
<span data-ttu-id="594a4-106">Libovolný platný výraz dotazu, který vydává kolekci, která se má použít jako zdroj v příkazu `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="594a4-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="594a4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="594a4-107">Remarks</span></span>

<span data-ttu-id="594a4-108">Klauzule `FROM` je čárkami oddělený seznam jedné nebo více položek klauzule `FROM`.</span><span class="sxs-lookup"><span data-stu-id="594a4-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="594a4-109">Klauzuli `FROM` lze použít k zadání jednoho nebo více zdrojů pro příkaz `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="594a4-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="594a4-110">Nejjednodušší tvar klauzule `FROM` je jeden výraz dotazu, který identifikuje kolekci a alias použitý jako zdroj v příkazu `SELECT`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="594a4-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="594a4-111">Položky klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="594a4-111">FROM Clause Items</span></span>

<span data-ttu-id="594a4-112">Každá položka klauzule `FROM` odkazuje na zdrojovou kolekci v dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="594a4-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="594a4-113">podporuje následující třídy položek klauzule `FROM`: jednoduché položky klauzule `FROM`, položky klauzule `JOIN FROM` a položky klauzule `APPLY FROM`.</span><span class="sxs-lookup"><span data-stu-id="594a4-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="594a4-114">Každá z těchto položek klauzule `FROM` je podrobněji popsána v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="594a4-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="594a4-115">Jednoduchá položka klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="594a4-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="594a4-116">Nejjednodušší položka klauzule `FROM` je jeden výraz, který identifikuje kolekci a alias.</span><span class="sxs-lookup"><span data-stu-id="594a4-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="594a4-117">Výraz může být jednoduše sada entit nebo poddotaz nebo jakýkoli jiný výraz, který je typem kolekce.</span><span class="sxs-lookup"><span data-stu-id="594a4-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="594a4-118">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="594a4-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="594a4-119">Specifikace aliasu je volitelná.</span><span class="sxs-lookup"><span data-stu-id="594a4-119">The alias specification is optional.</span></span> <span data-ttu-id="594a4-120">Alternativní specifikace předchozí položky klauzule FROM by mohla být následující:</span><span class="sxs-lookup"><span data-stu-id="594a4-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="594a4-121">Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí vygenerovat alias na základě výrazu kolekce.</span><span class="sxs-lookup"><span data-stu-id="594a4-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="594a4-122">PROPOJIT položku klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="594a4-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="594a4-123">Položka klauzule `JOIN FROM` představuje spojení mezi dvěma položkami klauzule `FROM`.</span><span class="sxs-lookup"><span data-stu-id="594a4-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="594a4-124">podporuje křížová spojení, vnitřní spojení, levé a pravé vnější spojení a úplné vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="594a4-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="594a4-125">Všechna tato spojení jsou podporovaná podobným způsobem, jakým jsou podporované v jazyce Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="594a4-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="594a4-126">Stejně jako v jazyce Transact-SQL musí být dvě položky klauzule `FROM` zapojené do `JOIN` nezávislé.</span><span class="sxs-lookup"><span data-stu-id="594a4-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="594a4-127">To znamená, že nelze provést korelaci.</span><span class="sxs-lookup"><span data-stu-id="594a4-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="594a4-128">V těchto případech lze použít `CROSS APPLY` nebo `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="594a4-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="594a4-129">Vzájemné spojení</span><span class="sxs-lookup"><span data-stu-id="594a4-129">Cross Joins</span></span>

<span data-ttu-id="594a4-130">Výraz dotazu `CROSS JOIN` vytvoří produkt kartézském ze dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="594a4-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="594a4-131">Vnitřní spojení</span><span class="sxs-lookup"><span data-stu-id="594a4-131">Inner Joins</span></span>

<span data-ttu-id="594a4-132">@No__t-0 vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="594a4-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="594a4-133">Předchozí výraz dotazu zpracuje kombinaci každého prvku na levé straně spárované s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá.</span><span class="sxs-lookup"><span data-stu-id="594a4-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="594a4-134">Pokud není zadána žádná podmínka `ON`, `INNER JOIN` se vygeneruje do `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="594a4-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="594a4-135">Levé vnější spojení a pravé vnější spojení</span><span class="sxs-lookup"><span data-stu-id="594a4-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="594a4-136">Výraz dotazu `OUTER JOIN` vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="594a4-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="594a4-137">Předchozí výraz dotazu zpracuje kombinaci každého prvku na levé straně spárované s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá.</span><span class="sxs-lookup"><span data-stu-id="594a4-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="594a4-138">Pokud je `ON` podmínka NEPRAVDA, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="594a4-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="594a4-139">Podobným způsobem může být vyjádření `RIGHT OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="594a4-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="594a4-140">Úplné vnější spojení</span><span class="sxs-lookup"><span data-stu-id="594a4-140">Full Outer Joins</span></span>

<span data-ttu-id="594a4-141">Explicitní `FULL OUTER JOIN` vytvoří omezený kartézském produkt dvou kolekcí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="594a4-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="594a4-142">Předchozí výraz dotazu zpracuje kombinaci každého prvku na levé straně spárované s každým prvkem kolekce na pravé straně, kde je podmínka `ON` pravdivá.</span><span class="sxs-lookup"><span data-stu-id="594a4-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="594a4-143">Pokud je podmínka `ON` nepravdivá, výraz stále zpracovává jednu instanci elementu vlevo spárovaného proti elementu na pravé straně s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="594a4-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="594a4-144">Také zpracovává jednu instanci prvku na pravé straně spárovánou s elementem vlevo s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="594a4-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="594a4-145">Aby se zachovala kompatibilita s SQL-92, je klíčové slovo OUTER v jazyce Transact-SQL volitelné.</span><span class="sxs-lookup"><span data-stu-id="594a4-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="594a4-146">Proto jsou `LEFT JOIN`, `RIGHT JOIN` a `FULL JOIN` synonyma pro `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` a `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="594a4-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="594a4-147">Položka klauzule APPLy</span><span class="sxs-lookup"><span data-stu-id="594a4-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="594a4-148">podporuje dva druhy `APPLY`: `CROSS APPLY` a `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="594a4-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="594a4-149">@No__t-0 vytvoří jedinečné párování každého prvku kolekce na levé straně s prvkem kolekce vytvořeným vyhodnocením výrazu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="594a4-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="594a4-150">Pomocí `CROSS APPLY` je výraz na pravé straně funkčně závislý na elementu na levé straně, jak je znázorněno v následujícím příkladu přidružené kolekce:</span><span class="sxs-lookup"><span data-stu-id="594a4-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="594a4-151">Chování `CROSS APPLY` se podobá seznamu spojení.</span><span class="sxs-lookup"><span data-stu-id="594a4-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="594a4-152">Pokud je výraz na pravé straně vyhodnocen jako prázdná kolekce, nevytvoří `CROSS APPLY` žádné párování pro tuto instanci elementu vlevo.</span><span class="sxs-lookup"><span data-stu-id="594a4-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="594a4-153">@No__t-0 se podobá `CROSS APPLY` s tím rozdílem, že párování je stále vytvořeno i v případě, že je výraz na pravé straně vyhodnocen jako prázdná kolekce.</span><span class="sxs-lookup"><span data-stu-id="594a4-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="594a4-154">Následuje příklad `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="594a4-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="594a4-155">Na rozdíl od jazyka Transact-SQL není nutné explicitní krok unvnořování v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="594a4-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="594a4-156">v SQL Server 2005 byly představeny operátory `CROSS` a `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="594a4-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="594a4-157">V některých případech může kanál dotazů vydávat Transact-SQL, který obsahuje operátory `CROSS APPLY` a/nebo `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="594a4-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="594a4-158">Vzhledem k tomu, že někteří poskytovatelé back-end, včetně verzí SQL Server starších než SQL Server 2005, tyto operátory nepodporují, takové dotazy nelze na těchto back-end poskytovateli spustit.</span><span class="sxs-lookup"><span data-stu-id="594a4-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="594a4-159">Některé typické scénáře, které by mohly vést k přítomnosti operátorů `CROSS APPLY` nebo `OUTER APPLY` ve výstupním dotazu, jsou následující: korelační poddotaz se stránkováním; AnyElement přes korelační poddotaz nebo přes kolekci vytvořenou navigací; Dotazy LINQ používající seskupovací metody, které přijímají selektor elementu; dotaz, ve kterém jsou explicitně zadány `CROSS APPLY` nebo `OUTER APPLY`; dotaz, který má konstrukci `DEREF` nad konstrukcí `REF`.</span><span class="sxs-lookup"><span data-stu-id="594a4-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="594a4-160">Více kolekcí v klauzuli FROM</span><span class="sxs-lookup"><span data-stu-id="594a4-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="594a4-161">Klauzule `FROM` může obsahovat více než jednu kolekci oddělenou čárkami.</span><span class="sxs-lookup"><span data-stu-id="594a4-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="594a4-162">V těchto případech se předpokládá, že se kolekce spojí dohromady.</span><span class="sxs-lookup"><span data-stu-id="594a4-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="594a4-163">Ty si můžete představit jako n-Way KŘÍŽové spojení.</span><span class="sxs-lookup"><span data-stu-id="594a4-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="594a4-164">V následujícím příkladu jsou `C` a `D` nezávislé kolekce, ale `c.Names` jsou závislé na `C`.</span><span class="sxs-lookup"><span data-stu-id="594a4-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="594a4-165">Předchozí příklad je logicky shodný s následujícím příkladem:</span><span class="sxs-lookup"><span data-stu-id="594a4-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="594a4-166">Levá korelace</span><span class="sxs-lookup"><span data-stu-id="594a4-166">Left Correlation</span></span>
 <span data-ttu-id="594a4-167">Položky v klauzuli `FROM` mohou odkazovat na položky zadané v předchozích klauzulích.</span><span class="sxs-lookup"><span data-stu-id="594a4-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="594a4-168">V následujícím příkladu jsou `C` a `D` nezávislé kolekce, ale `c.Names` jsou závislé na `C`:</span><span class="sxs-lookup"><span data-stu-id="594a4-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="594a4-169">To je logicky ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="594a4-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="594a4-170">Sémantiku</span><span class="sxs-lookup"><span data-stu-id="594a4-170">Semantics</span></span>

<span data-ttu-id="594a4-171">Logicky, kolekce v klauzuli `FROM` se považují za součást @no__t -1 křížové spojení (kromě případu, kdy se jedná o jednosměrné křížové spojení).</span><span class="sxs-lookup"><span data-stu-id="594a4-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="594a4-172">Aliasy v klauzuli `FROM` jsou zpracovávány zleva doprava a jsou přidány do aktuálního rozsahu pro pozdější použití reference.</span><span class="sxs-lookup"><span data-stu-id="594a4-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="594a4-173">Klauzule `FROM` se předpokládá pro vytvoření multiset řádků.</span><span class="sxs-lookup"><span data-stu-id="594a4-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="594a4-174">Pro každou položku v klauzuli `FROM` bude k dispozici jedno pole, které představuje jeden prvek z této položky kolekce.</span><span class="sxs-lookup"><span data-stu-id="594a4-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="594a4-175">Klauzule `FROM` logicky vytvoří multiset řádků typu řádek (c, d, e), kde se předpokládá, že pole c, d a e jsou typu prvku `C`, `D` a `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="594a4-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="594a4-176">zavádí alias pro každou jednoduchou položku klauzule `FROM` v oboru.</span><span class="sxs-lookup"><span data-stu-id="594a4-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="594a4-177">Například v následujícím fragmentu klauzule FROM, názvy zavedené do rozsahu jsou c, d a e.</span><span class="sxs-lookup"><span data-stu-id="594a4-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="594a4-178">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (na rozdíl od jazyka Transact-SQL) klauzule `FROM` zavádí pouze aliasy do oboru.</span><span class="sxs-lookup"><span data-stu-id="594a4-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="594a4-179">Všechny odkazy na sloupce (vlastnosti) těchto kolekcí musí být kvalifikovány s aliasem.</span><span class="sxs-lookup"><span data-stu-id="594a4-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="594a4-180">Přijímání klíčů z vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="594a4-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="594a4-181">Některé typy dotazů, které vyžadují přijetí klíčů z vnořeného dotazu, nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="594a4-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="594a4-182">Například následující dotaz je platný:</span><span class="sxs-lookup"><span data-stu-id="594a4-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="594a4-183">Následující dotaz však není platný, protože vnořený dotaz nemá žádné klíče:</span><span class="sxs-lookup"><span data-stu-id="594a4-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="594a4-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="594a4-184">See also</span></span>

- [<span data-ttu-id="594a4-185">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="594a4-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="594a4-186">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="594a4-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="594a4-187">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="594a4-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
