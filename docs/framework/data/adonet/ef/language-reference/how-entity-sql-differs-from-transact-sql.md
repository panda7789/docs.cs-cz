---
title: Jak se liší od Transact-SQL Entity SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: d34c6933e0f19c73b954446fdf18cea7243eae0d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766293"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="bb778-102">Jak se liší od Transact-SQL Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb778-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="bb778-103">Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb778-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="bb778-104">Dědičnost a vztahy podpory</span><span class="sxs-lookup"><span data-stu-id="bb778-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-105"> pracuje přímo s koncepční entity schémata a podporuje konceptuálního modelu funkce jako je například dědičnosti a vztahy.</span><span class="sxs-lookup"><span data-stu-id="bb778-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="bb778-106">Při práci s použitím dědičnosti, je často užitečné k výběru instancí podtypu z kolekce instancí nadtyp.</span><span class="sxs-lookup"><span data-stu-id="bb778-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="bb778-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako `oftype` v C# pořadí) umožňuje používat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="bb778-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="bb778-108">Podpora pro kolekce</span><span class="sxs-lookup"><span data-stu-id="bb778-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-109"> kolekce se považuje za první třídy entity.</span><span class="sxs-lookup"><span data-stu-id="bb778-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="bb778-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bb778-110">For example:</span></span>  
  
-   <span data-ttu-id="bb778-111">Jsou platné v kolekci výrazy `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="bb778-112">`in` a `exists` poddotazy jste zobecnili umožňující žádných kolekcí.</span><span class="sxs-lookup"><span data-stu-id="bb778-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="bb778-113">Poddotaz je jeden typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb778-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="bb778-114">`e1 in e2` a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukce k provádění těchto operací.</span><span class="sxs-lookup"><span data-stu-id="bb778-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="bb778-115">Nastavte operace, jako je třeba `union`, `intersect`, a `except`, nyní fungovat na kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb778-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="bb778-116">Spojení pracovat kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb778-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="bb778-117">Podpora pro výrazy</span><span class="sxs-lookup"><span data-stu-id="bb778-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-118"> má poddotazy (tabulky) a výrazy (řádků a sloupců).</span><span class="sxs-lookup"><span data-stu-id="bb778-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="bb778-119">Pro podporu kolekcí a vnořené kolekcí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] všechno, co je výraz.</span><span class="sxs-lookup"><span data-stu-id="bb778-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-120"> složení více než [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]– každých výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="bb778-120"> is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="bb778-121">Dotaz výrazy vždy mít za následek kolekcí předpokládané typů a mohou být použity kdekoli je povolen výraz kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb778-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="bb778-122">Informace o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], najdete v části [nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bb778-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="bb778-123">Následující položky jsou všechny platné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy:</span><span class="sxs-lookup"><span data-stu-id="bb778-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="bb778-124">Jednotné zacházení s poddotazy</span><span class="sxs-lookup"><span data-stu-id="bb778-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="bb778-125">Zadané jeho důraz na tabulky, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] provede kontextové výklad poddotazy.</span><span class="sxs-lookup"><span data-stu-id="bb778-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="bb778-126">Například poddotazu v `from` klauzule se považuje za multimnožina (tabulky).</span><span class="sxs-lookup"><span data-stu-id="bb778-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="bb778-127">Ale stejné poddotazu používán `select` se považuje za skalární poddotazu klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="bb778-128">Podobně poddotaz použit na levé straně `in` operátor se považuje za skalární poddotazu, zatímco pravé straně se očekává multiset poddotazu.</span><span class="sxs-lookup"><span data-stu-id="bb778-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-129"> Eliminuje tyto rozdíly.</span><span class="sxs-lookup"><span data-stu-id="bb778-129"> eliminates these differences.</span></span> <span data-ttu-id="bb778-130">Výraz obsahuje jednotný výklad, která není závislá na kontext, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="bb778-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-131"> zvažuje všech poddotazech být multiset poddotazy.</span><span class="sxs-lookup"><span data-stu-id="bb778-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="bb778-132">Pokud se požaduje skalární hodnotu poddotazu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `anyelement` operátor, který funguje na kolekci (v tomto případě je poddotaz) a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb778-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="bb778-133">Zamezení implicitní Coercions pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="bb778-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="bb778-134">Související vedlejším účinkem jednotné zacházení s poddotazy je implicitní převod poddotazy skalárních hodnot.</span><span class="sxs-lookup"><span data-stu-id="bb778-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="bb778-135">Konkrétně v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multimnožina řádků (s jedním polem) je implicitně převést na skalární hodnotu s datovým typem je, že pole.</span><span class="sxs-lookup"><span data-stu-id="bb778-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-136"> nepodporuje tento implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="bb778-136"> does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-137"> poskytuje operátor ANYELEMENT extrahovat hodnotu singleton z kolekce a `select value` klauzule Vyhněte se vytváření obálce řádek během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="bb778-137"> provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="bb778-138">Vyberte hodnotu: Zamezení implicitní řádek obálky</span><span class="sxs-lookup"><span data-stu-id="bb778-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="bb778-139">V klauzuli select [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] poddotazu implicitně vytvoří řádek obálku kolem položky v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bb778-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="bb778-140">To znamená, že nemůžeme vytvořit kolekcí skalárních hodnot nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="bb778-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-141"> umožňuje implicitní vynucení mezi rowtype s jedno pole a hodnotu singleton stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="bb778-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-142"> poskytuje `select value` klauzule tak, aby přeskočil konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="bb778-142"> provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="bb778-143">Možné zadat jen jednu položku `select value` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="bb778-144">Pokud se používá tato klauzule, žádný řádek obálky je postavena na položky v `select` klauzule a kolekce požadovaný tvar může být vytvořil, například: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="bb778-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-145"> také poskytuje konstruktor row můžete vytvořit libovolný řádků.</span><span class="sxs-lookup"><span data-stu-id="bb778-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="bb778-146">`select` přijímá jeden či více elementů v projekci a má za následek záznam dat s poli, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bb778-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="bb778-147">Levá korelace a aliasy</span><span class="sxs-lookup"><span data-stu-id="bb778-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="bb778-148">V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], výrazy v daném oboru (jako jedna klauzule `select` nebo `from`) nemůže odkazovat na výrazy definovaného dříve ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="bb778-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="bb778-149">Některé dialekty SQL (včetně [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) podporují omezené formy v `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-150"> Umožňuje zobecnit v levém korelací `from` klauzuli a pracuje s nimi jednotně.</span><span class="sxs-lookup"><span data-stu-id="bb778-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="bb778-151">Výrazy v `from` klauzule odkazovat v klauzuli stejné bez nutnosti další syntaxe starší definice (definice doleva).</span><span class="sxs-lookup"><span data-stu-id="bb778-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-152"> také ukládá další omezení na dotazy zahrnující `group by` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-152"> also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="bb778-153">Výrazy v `select` klauzule a `having` klauzule takové dotazy mohou odkazovat pouze na `group by` klíče prostřednictvím jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="bb778-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="bb778-154">Platí následující konstrukce v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bb778-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="bb778-155">To uděláte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bb778-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="bb778-156">(Vlastnosti) odkazujících sloupců tabulky (kolekce)</span><span class="sxs-lookup"><span data-stu-id="bb778-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="bb778-157">Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovaný pomocí tabulky alias.</span><span class="sxs-lookup"><span data-stu-id="bb778-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="bb778-158">Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platný v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb778-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="bb778-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formulář</span><span class="sxs-lookup"><span data-stu-id="bb778-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="bb778-160">Aliasy tabulky jsou v volitelný `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="bb778-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="bb778-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-162"> Umožňuje také následující tvar:</span><span class="sxs-lookup"><span data-stu-id="bb778-162"> allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="bb778-163">Navigace prostřednictvím objektů</span><span class="sxs-lookup"><span data-stu-id="bb778-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-164"> používá "." zápis pro sloupce (řádek) odkazující na tabulku.</span><span class="sxs-lookup"><span data-stu-id="bb778-164"> uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-165"> rozšiřuje tento zápis (vždy pouze vypůjčí na programovací jazyky) pro podporu navigační prostřednictvím vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="bb778-165"> extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="bb778-166">Například pokud `p` je výraz, který typ osoba, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování na město adresy této osoby.</span><span class="sxs-lookup"><span data-stu-id="bb778-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="bb778-167">Žádná podpora pro \*</span><span class="sxs-lookup"><span data-stu-id="bb778-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-168"> podporuje nekvalifikované \* syntaxe jako alias pro celý řádek a kvalifikovaný \* syntaxe (t.\*) jako zástupce pro pole této tabulky.</span><span class="sxs-lookup"><span data-stu-id="bb778-168"> supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="bb778-169">Kromě toho [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umožňuje speciální Count (\*) agregace, který obsahuje hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="bb778-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-170"> nepodporuje \* konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bb778-170"> does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-171"> dotazy, formuláře `select * from T` a `select T1.* from T1, T2...` může být vyjádřený v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bb778-171"> queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="bb778-172">Kromě toho tyto konstrukce zpracování dědičnosti (hodnota dodávek), zatímco `select *` variant jsou omezeny na deklarovaný typ vlastnosti nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="bb778-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-173"> nepodporuje `count(*)` agregační.</span><span class="sxs-lookup"><span data-stu-id="bb778-173"> does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="bb778-174">Místo nich se používá `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="bb778-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="bb778-175">Změny Seskupit podle</span><span class="sxs-lookup"><span data-stu-id="bb778-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-176"> podporuje aliasy z `group by` klíče.</span><span class="sxs-lookup"><span data-stu-id="bb778-176"> supports aliasing of `group by` keys.</span></span> <span data-ttu-id="bb778-177">Výrazy v `select` klauzule a `having` klauzule musí odkazovat `group by` klíče přes tyto aliasy.</span><span class="sxs-lookup"><span data-stu-id="bb778-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="bb778-178">Například to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:</span><span class="sxs-lookup"><span data-stu-id="bb778-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="bb778-179">.. je ekvivalentní pro následující [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bb778-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="bb778-180">Na základě kolekce agregace</span><span class="sxs-lookup"><span data-stu-id="bb778-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-181"> podporuje dva druhy agregace.</span><span class="sxs-lookup"><span data-stu-id="bb778-181"> supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="bb778-182">Na základě kolekce agregace pracovat kolekce a vytvoření agregované výsledku.</span><span class="sxs-lookup"><span data-stu-id="bb778-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="bb778-183">To může vyskytovat kdekoli v dotazu a nevyžadují `group by` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bb778-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="bb778-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bb778-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-185"> podporuje také agreguje stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="bb778-185"> also supports SQL-style aggregates.</span></span> <span data-ttu-id="bb778-186">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bb778-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="bb778-187">ORDER BY – klauzule využití</span><span class="sxs-lookup"><span data-stu-id="bb778-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="bb778-188"> Umožňuje klauzule ORDER BY zadat pouze v nejhornější SELECT...</span><span class="sxs-lookup"><span data-stu-id="bb778-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="bb778-189">Z...</span><span class="sxs-lookup"><span data-stu-id="bb778-189">FROM ..</span></span> <span data-ttu-id="bb778-190">KDE blok.</span><span class="sxs-lookup"><span data-stu-id="bb778-190">WHERE block.</span></span> <span data-ttu-id="bb778-191">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít výraz vnořené klauzule ORDER BY a mohou být umístěny kdekoli v dotazu, ale řazení v vnořený dotaz není zachován.</span><span class="sxs-lookup"><span data-stu-id="bb778-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="bb778-192">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="bb778-192">Identifiers</span></span>  
 <span data-ttu-id="bb778-193">V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], porovnání identifikátoru je založena na kolaci aktuální databáze.</span><span class="sxs-lookup"><span data-stu-id="bb778-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="bb778-194">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifikátory jsou vždy aktivní a malých písmen a rozlišovat znaky s diakritikou (tedy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a příslušných; například "a" není rovno "ấ").</span><span class="sxs-lookup"><span data-stu-id="bb778-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-195"> zpracovává verzích písmena, která zobrazí stejné, ale jsou z jiné znakové stránky jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="bb778-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="bb778-196">Další informace najdete v tématu [vstup znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bb778-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="bb778-197">Příkaz Transact-SQL funkce není k dispozici v entitě SQL</span><span class="sxs-lookup"><span data-stu-id="bb778-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="bb778-198">Následující [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkce není k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb778-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="bb778-199">DML</span><span class="sxs-lookup"><span data-stu-id="bb778-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-200"> aktuálně poskytuje žádná podpora pro příkazy DML (vložení, aktualizaci, odstranění).</span><span class="sxs-lookup"><span data-stu-id="bb778-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="bb778-201">DDL</span><span class="sxs-lookup"><span data-stu-id="bb778-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-202"> poskytuje žádná podpora pro DDL v aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="bb778-202"> provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="bb778-203">Imperativní programování</span><span class="sxs-lookup"><span data-stu-id="bb778-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-204"> poskytuje žádná podpora pro imperativní programování, na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb778-204"> provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bb778-205">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="bb778-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="bb778-206">Funkce seskupování</span><span class="sxs-lookup"><span data-stu-id="bb778-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-207"> ještě neposkytuje podporu pro seskupování funkce (například CUBE, ROLLUP a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="bb778-207"> does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="bb778-208">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="bb778-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-209"> Ne (ještě) poskytuje podporu pro analytické funkce.</span><span class="sxs-lookup"><span data-stu-id="bb778-209"> does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="bb778-210">Integrované funkce, operátory</span><span class="sxs-lookup"><span data-stu-id="bb778-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-211"> podporuje podmnožinu [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]je součástí funkce a operátory.</span><span class="sxs-lookup"><span data-stu-id="bb778-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="bb778-212">Tyto operátory a funkce budou pravděpodobně podporovat poskytovatelé hlavní úložiště.</span><span class="sxs-lookup"><span data-stu-id="bb778-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-213"> používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="bb778-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="bb778-214">Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat předdefinované a vlastní existující uloží funkce, pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používat.</span><span class="sxs-lookup"><span data-stu-id="bb778-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="bb778-215">Pomocné parametry</span><span class="sxs-lookup"><span data-stu-id="bb778-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-216"> neposkytuje mechanismy pro pomocné parametry dotazu.</span><span class="sxs-lookup"><span data-stu-id="bb778-216"> does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="bb778-217">Dávkování výsledky dotazu</span><span class="sxs-lookup"><span data-stu-id="bb778-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-218"> nepodporuje dávkování výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="bb778-218"> does not support batching query results.</span></span> <span data-ttu-id="bb778-219">Například následující platí [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (odesílajícím jako dávku):</span><span class="sxs-lookup"><span data-stu-id="bb778-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="bb778-220">Ale ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není podporována:</span><span class="sxs-lookup"><span data-stu-id="bb778-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="bb778-221"> podporuje pouze jeden příkaz dotazu generovala výsledek za příkaz.</span><span class="sxs-lookup"><span data-stu-id="bb778-221"> only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb778-222">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb778-222">See Also</span></span>  
 [<span data-ttu-id="bb778-223">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb778-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="bb778-224">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="bb778-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
