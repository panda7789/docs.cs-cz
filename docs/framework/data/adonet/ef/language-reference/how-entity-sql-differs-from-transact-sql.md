---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 75ce0b00962526b76ea9f4b9fdfb0d1e1e564cdc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162734"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="b0860-102">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0860-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="b0860-103">Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0860-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="b0860-104">Dědičnost a vztahy podpory</span><span class="sxs-lookup"><span data-stu-id="b0860-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-105">pracuje přímo s konceptuálními schématy entity a podporuje funkce konceptuální model, jako je dědičnost a vztahy.</span><span class="sxs-lookup"><span data-stu-id="b0860-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="b0860-106">Při práci s dědičnosti, je často užitečné vybrat instance podtypu z kolekce instancí nadtyp.</span><span class="sxs-lookup"><span data-stu-id="b0860-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="b0860-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako `oftype` v C# pořadí) tuto možnost nabízí.</span><span class="sxs-lookup"><span data-stu-id="b0860-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="b0860-108">Podpora pro kolekce</span><span class="sxs-lookup"><span data-stu-id="b0860-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-109">kolekce se považuje za první třídy entit.</span><span class="sxs-lookup"><span data-stu-id="b0860-109">treats collections as first-class entities.</span></span> <span data-ttu-id="b0860-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0860-110">For example:</span></span>  
  
-   <span data-ttu-id="b0860-111">Výrazy kolekce jsou platné v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="b0860-112">`in` a `exists` poddotazy mají byl zobecněn umožňující žádných kolekcí.</span><span class="sxs-lookup"><span data-stu-id="b0860-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="b0860-113">Poddotaz je jeden typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0860-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="b0860-114">`e1 in e2` a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukty, které tyto operace provést.</span><span class="sxs-lookup"><span data-stu-id="b0860-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="b0860-115">Množinové operace, jako například `union`, `intersect`, a `except`, nyní pracují s kolekcí.</span><span class="sxs-lookup"><span data-stu-id="b0860-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="b0860-116">Spojení pracovat s kolekcí.</span><span class="sxs-lookup"><span data-stu-id="b0860-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="b0860-117">Podpora pro výrazy</span><span class="sxs-lookup"><span data-stu-id="b0860-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-118">má poddotazy (tabulky) a výrazy (řádků a sloupců).</span><span class="sxs-lookup"><span data-stu-id="b0860-118">has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="b0860-119">Pro podporu kolekce a vnořené kolekce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] všechno, co je výraz.</span><span class="sxs-lookup"><span data-stu-id="b0860-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-120">více než podporuje složení [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]– každý výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="b0860-120">is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="b0860-121">Dotaz výrazy vždy způsobit kolekcí předpokládané typů a mohou být použity kdekoli je povolen výraz kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0860-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="b0860-122">Informace o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], naleznete v tématu [nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b0860-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="b0860-123">Následující položky jsou všechny platné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy:</span><span class="sxs-lookup"><span data-stu-id="b0860-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="b0860-124">Jednotné zacházení s poddotazy</span><span class="sxs-lookup"><span data-stu-id="b0860-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="b0860-125">Zadaný jeho důraz na tabulky, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] provádí kontextové výklad poddotazy.</span><span class="sxs-lookup"><span data-stu-id="b0860-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="b0860-126">Například poddotaz v `from` klauzule se považuje za multiset (tabulka).</span><span class="sxs-lookup"><span data-stu-id="b0860-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="b0860-127">Ale stejné poddotaz používané `select` klauzule je považována za skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="b0860-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="b0860-128">Obdobně poddotaz použit na levé straně `in` – operátor se považuje za skalární poddotazu, zatímco pravé straně se očekává multiset – poddotaz.</span><span class="sxs-lookup"><span data-stu-id="b0860-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-129">Eliminuje tyto rozdíly.</span><span class="sxs-lookup"><span data-stu-id="b0860-129">eliminates these differences.</span></span> <span data-ttu-id="b0860-130">Výraz má jednotné interpretace, které nejsou závislé na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="b0860-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-131">bere v úvahu všech poddotazech bude multiset – poddotazy.</span><span class="sxs-lookup"><span data-stu-id="b0860-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="b0860-132">Pokud je poddotazu, skalární hodnota [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje `anyelement` operátor, který funguje na kolekce (v tomto případě poddotazu) a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0860-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="b0860-133">Jak se vyhnout implicitní převody pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="b0860-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="b0860-134">Související vedlejším účinkem jednotné zacházení s poddotazy je implicitní převod poddotazů na skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b0860-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="b0860-135">Konkrétně v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], použita třída multiset řádků (s jedním polem) je implicitně převést na skalární hodnota, jejíž datový typ je, že pole.</span><span class="sxs-lookup"><span data-stu-id="b0860-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-136">Toto implicitní převod není podporován.</span><span class="sxs-lookup"><span data-stu-id="b0860-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-137">poskytuje operátora ANYELEMENT extrahovat hodnotu singleton z kolekce a `select value` klauzule vyhnout se vytváření Obálka řádků během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="b0860-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="b0860-138">Vyberte hodnotu: Jak se vyhnout obálky implicitní řádek</span><span class="sxs-lookup"><span data-stu-id="b0860-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="b0860-139">V klauzuli select [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] poddotaz implicitně vytvoří obálku kolem položky řádku v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="b0860-140">Z toho vyplývá, že nemůžeme vytvořit kolekce skaláry nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="b0860-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-141">umožňuje implicitní převod mezi rowtype s jedním polem a hodnotu singleton stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="b0860-141">allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-142">poskytuje `select value` klauzule vynechat konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="b0860-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="b0860-143">Možné zadat pouze jednu položku `select value` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="b0860-144">Při použití těchto klauzulí žádný řádek obálky je postavena na položky v `select` klauzule a kolekce na požadovaný tvar může vytvářet, například: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="b0860-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-145">také poskytuje konstruktoru řádku k vytvoření libovolné řádky.</span><span class="sxs-lookup"><span data-stu-id="b0860-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="b0860-146">`select` použije jeden nebo více prvků v projekci a výsledky datového záznamu vložením polí, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b0860-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="b0860-147">Levá korelace a aliasy</span><span class="sxs-lookup"><span data-stu-id="b0860-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="b0860-148">V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], výrazy v daném oboru (jako jedna klauzule `select` nebo `from`) nemůže odkazovat na výrazy, které jsou definované výše ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="b0860-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="b0860-149">Některé dialekty SQL (včetně [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) podporují omezené formuláře z nich najdete v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-150">zobecňuje levé korelace v `from` klauzule a rovnoměrně je zpracovává.</span><span class="sxs-lookup"><span data-stu-id="b0860-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="b0860-151">Výrazy v `from` klauzule můžete odkazovat starší definice (definice na levé straně) v klauzuli stejné bez nutnosti další syntaxi.</span><span class="sxs-lookup"><span data-stu-id="b0860-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-152">také ukládá další omezení pro dotazy zahrnující `group by` klauzule.</span><span class="sxs-lookup"><span data-stu-id="b0860-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="b0860-153">Výrazy v `select` klauzule a `having` klauzule takové dotazy mohou odkazovat pouze na `group by` klíče účtů prostřednictvím jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="b0860-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="b0860-154">Následující konstruktor je platný v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b0860-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="b0860-155">Chcete-li to provést v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b0860-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="b0860-156">(Vlastnosti) odkazujících sloupců z tabulky (kolekce)</span><span class="sxs-lookup"><span data-stu-id="b0860-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="b0860-157">Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovaný pomocí aliasu tabulky.</span><span class="sxs-lookup"><span data-stu-id="b0860-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="b0860-158">Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platná v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0860-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="b0860-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Je formulář</span><span class="sxs-lookup"><span data-stu-id="b0860-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="b0860-160">Jsou nepovinné v aliasu tabulky `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="b0860-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="b0860-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-162">umožňuje následující tvar:</span><span class="sxs-lookup"><span data-stu-id="b0860-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="b0860-163">Navigace prostřednictvím objektů</span><span class="sxs-lookup"><span data-stu-id="b0860-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-164">používá "." zápis pro odkazujících sloupců (řádek) tabulky.</span><span class="sxs-lookup"><span data-stu-id="b0860-164">uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-165">rozšiřuje tento zápis (si z programovacích jazyků) pro podporu navigace prostřednictvím vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="b0860-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="b0860-166">Například pokud `p` je výraz, zadejte osobu, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování na město adresa této osoby.</span><span class="sxs-lookup"><span data-stu-id="b0860-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="b0860-167">Žádná podpora pro \*</span><span class="sxs-lookup"><span data-stu-id="b0860-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-168">podporuje nekvalifikované \* syntaxe jako alias pro celý řádek a úplný \* syntaxe (t.\*) jako zástupce pro pole tabulky.</span><span class="sxs-lookup"><span data-stu-id="b0860-168">supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="b0860-169">Kromě toho [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umožňuje speciální Count (\*) agregace, který obsahuje hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="b0860-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-170">nepodporuje \* konstrukce.</span><span class="sxs-lookup"><span data-stu-id="b0860-170">does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-171">dotazy ve formátu `select * from T` a `select T1.* from T1, T2...` může být vyjádřena v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b0860-171">queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="b0860-172">Kromě toho tato konstrukce zpracování dědičnosti (hodnota dodávek), zatímco `select *` varianty jsou omezeny na nejvyšší úrovni vlastnosti deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="b0860-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-173">nepodporuje `count(*)` agregace.</span><span class="sxs-lookup"><span data-stu-id="b0860-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="b0860-174">Místo nich se používá `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="b0860-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="b0860-175">Změny Seskupit podle</span><span class="sxs-lookup"><span data-stu-id="b0860-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-176">podporuje aliasing z `group by` klíče.</span><span class="sxs-lookup"><span data-stu-id="b0860-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="b0860-177">Výrazy v `select` klauzule a `having` klauzule musí odkazovat `group by` klíče účtů prostřednictvím tyto aliasy.</span><span class="sxs-lookup"><span data-stu-id="b0860-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="b0860-178">Například to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxi:</span><span class="sxs-lookup"><span data-stu-id="b0860-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="b0860-179">.. je ekvivalentní následujícímu [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b0860-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="b0860-180">Na základě kolekce agregace</span><span class="sxs-lookup"><span data-stu-id="b0860-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-181">podporuje dva typy agregací.</span><span class="sxs-lookup"><span data-stu-id="b0860-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="b0860-182">Na základě kolekce agregace pracovat s kolekcí a vytvářet agregovaný výsledek.</span><span class="sxs-lookup"><span data-stu-id="b0860-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="b0860-183">Toto může vyskytovat kdekoli v dotazu a nevyžadují, aby `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b0860-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="b0860-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0860-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-185">také podporuje agregaci SQL-style.</span><span class="sxs-lookup"><span data-stu-id="b0860-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="b0860-186">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0860-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="b0860-187">ORDER BY – klauzule využití</span><span class="sxs-lookup"><span data-stu-id="b0860-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="b0860-188">Umožňuje klauzule ORDER BY zadán pouze v vrchní POLOŽKU...</span><span class="sxs-lookup"><span data-stu-id="b0860-188">allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="b0860-189">Z...</span><span class="sxs-lookup"><span data-stu-id="b0860-189">FROM ..</span></span> <span data-ttu-id="b0860-190">Pokud blok.</span><span class="sxs-lookup"><span data-stu-id="b0860-190">WHERE block.</span></span> <span data-ttu-id="b0860-191">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz klauzule ORDER BY a může být umístěna kdekoli v dotazu, ale není zachováváno pořadí v vnořeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="b0860-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="b0860-192">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="b0860-192">Identifiers</span></span>  
 <span data-ttu-id="b0860-193">V [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], kolace aktuální databázi podle porovnání identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b0860-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="b0860-194">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifikátory jsou vždy malá a velká písmena a rozlišovat diakritiku (to znamená, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a výslovnost příslušných hlásek bez; například "a" se nerovná "ấ").</span><span class="sxs-lookup"><span data-stu-id="b0860-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-195">zpracovává verzích zpravodaje, které se zobrazí stejná, ale jsou z různých znakových stránek jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="b0860-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="b0860-196">Další informace najdete v tématu [vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b0860-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="b0860-197">Funkce jazyka Transact-SQL není k dispozici v Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0860-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="b0860-198">Následující [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkce není k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0860-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="b0860-199">DML</span><span class="sxs-lookup"><span data-stu-id="b0860-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-200">aktuálně nepodporuje příkazy DML (vložení, aktualizace nebo odstranění).</span><span class="sxs-lookup"><span data-stu-id="b0860-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="b0860-201">DDL</span><span class="sxs-lookup"><span data-stu-id="b0860-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-202">nepodporuje DDL v aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="b0860-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="b0860-203">imperativní programování</span><span class="sxs-lookup"><span data-stu-id="b0860-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-204">nepodporuje imperativní programování, na rozdíl od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0860-204">provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b0860-205">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="b0860-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="b0860-206">Funkce seskupování</span><span class="sxs-lookup"><span data-stu-id="b0860-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-207">ještě neposkytuje podporu pro seskupení funkce (například CUBE, ROLLUP a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="b0860-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="b0860-208">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="b0860-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-209">Ne (ještě) poskytuje podporu pro analytických funkcí.</span><span class="sxs-lookup"><span data-stu-id="b0860-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="b0860-210">Integrovaných funkcí, operátorů</span><span class="sxs-lookup"><span data-stu-id="b0860-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-211">podporuje podmnožinu [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]integrovaných v funkcí a operátorů.</span><span class="sxs-lookup"><span data-stu-id="b0860-211">supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="b0860-212">Tyto operátory a funkce můžou být podporovanou poskytovateli hlavní úložiště.</span><span class="sxs-lookup"><span data-stu-id="b0860-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-213">používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b0860-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="b0860-214">Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat integrované a funkce, uživatelem definované existující úložiště pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používat.</span><span class="sxs-lookup"><span data-stu-id="b0860-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="b0860-215">Pomocné parametry</span><span class="sxs-lookup"><span data-stu-id="b0860-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-216">neposkytuje mechanismy pro pomocné parametry dotazu.</span><span class="sxs-lookup"><span data-stu-id="b0860-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="b0860-217">Dávkové zpracování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="b0860-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-218">dávkování výsledků dotazu není podporována.</span><span class="sxs-lookup"><span data-stu-id="b0860-218">does not support batching query results.</span></span> <span data-ttu-id="b0860-219">Například tady je platný [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (odeslání v dávce):</span><span class="sxs-lookup"><span data-stu-id="b0860-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="b0860-220">Ale ekvivalentní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se nepodporuje:</span><span class="sxs-lookup"><span data-stu-id="b0860-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0860-221">podporuje pouze jeden příkaz dotazu výsledek ze kterého vznikne jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="b0860-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0860-222">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0860-222">See also</span></span>

- [<span data-ttu-id="b0860-223">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0860-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="b0860-224">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="b0860-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
