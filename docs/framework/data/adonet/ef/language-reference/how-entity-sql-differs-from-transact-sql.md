---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833713"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="c5dea-102">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5dea-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="c5dea-103">Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c5dea-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="c5dea-104">Podpora dědičnosti a vztahů</span><span class="sxs-lookup"><span data-stu-id="c5dea-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-105">funguje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.</span><span class="sxs-lookup"><span data-stu-id="c5dea-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="c5dea-106">Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp.</span><span class="sxs-lookup"><span data-stu-id="c5dea-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="c5dea-107">Tato funkce poskytuje operátor [OfType](oftype-entity-sql.md) v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobně jako @no__t- C# 2 v sekvencích).</span><span class="sxs-lookup"><span data-stu-id="c5dea-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="c5dea-108">Podpora pro kolekce</span><span class="sxs-lookup"><span data-stu-id="c5dea-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-109">zpracovává kolekce jako entity první třídy.</span><span class="sxs-lookup"><span data-stu-id="c5dea-109">treats collections as first-class entities.</span></span> <span data-ttu-id="c5dea-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5dea-110">For example:</span></span>  
  
- <span data-ttu-id="c5dea-111">Výrazy kolekce jsou platné v klauzuli `from`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="c5dea-112">poddotazy `in` a `exists` byly zobecněny, aby umožňovaly všechny kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5dea-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="c5dea-113">Poddotaz je jeden druh kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5dea-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="c5dea-114">`e1 in e2` a `exists(e)` jsou konstrukce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provedení těchto operací.</span><span class="sxs-lookup"><span data-stu-id="c5dea-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="c5dea-115">Nastavení operací, například `union`, `intersect` a `except`, nyní fungují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="c5dea-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="c5dea-116">Spojení se spouštějí na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="c5dea-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="c5dea-117">Podpora pro výrazy</span><span class="sxs-lookup"><span data-stu-id="c5dea-117">Support for Expressions</span></span>  
 <span data-ttu-id="c5dea-118">V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).</span><span class="sxs-lookup"><span data-stu-id="c5dea-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="c5dea-119">Aby bylo možné podporovat kolekce a vnořené kolekce, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provede všechny výrazy.</span><span class="sxs-lookup"><span data-stu-id="c5dea-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-120">je mnohem sestavitelný než Transact-SQL – každý výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="c5dea-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="c5dea-121">Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5dea-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="c5dea-122">Informace o výrazech jazyka Transact-SQL, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)], naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c5dea-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c5dea-123">Níže jsou uvedené všechny platné dotazy [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c5dea-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="c5dea-124">Jednotné zpracování poddotazů</span><span class="sxs-lookup"><span data-stu-id="c5dea-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="c5dea-125">V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů.</span><span class="sxs-lookup"><span data-stu-id="c5dea-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="c5dea-126">Například poddotaz v klauzuli `from` se považuje za multiset (tabulka).</span><span class="sxs-lookup"><span data-stu-id="c5dea-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="c5dea-127">Ale stejný poddotaz použitý v klauzuli `select` je považován za skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="c5dea-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="c5dea-128">Podobně by byl poddotaz použitý na levé straně operátoru `in` považován za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.</span><span class="sxs-lookup"><span data-stu-id="c5dea-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-129">eliminuje tyto rozdíly.</span><span class="sxs-lookup"><span data-stu-id="c5dea-129">eliminates these differences.</span></span> <span data-ttu-id="c5dea-130">Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit.</span><span class="sxs-lookup"><span data-stu-id="c5dea-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-131">předpokládá, že všechny poddotazy budou multiset poddotazy.</span><span class="sxs-lookup"><span data-stu-id="c5dea-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="c5dea-132">Pokud je v poddotazu požadováno skalární hodnota, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje operátor `anyelement`, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5dea-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="c5dea-133">Zamezení implicitních vynucení pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="c5dea-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="c5dea-134">Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c5dea-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="c5dea-135">Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.</span><span class="sxs-lookup"><span data-stu-id="c5dea-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-136">nepodporuje tuto implicitní vynucení.</span><span class="sxs-lookup"><span data-stu-id="c5dea-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-137">poskytuje operátor ANYELEMENT k extrakci hodnoty singleton z kolekce a klauzule `select value`, aby nedošlo k vytvoření řádku-obálky během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="c5dea-138">Vyberte hodnotu: vyloučí se obálku implicitního řádku.</span><span class="sxs-lookup"><span data-stu-id="c5dea-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="c5dea-139">Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c5dea-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="c5dea-140">To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="c5dea-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="c5dea-141">Transact-SQL umožňuje implicitní vynucení mezi RowType a jedním polem a hodnotou singleton stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-142">poskytuje klauzuli `select value` pro přeskočení vytváření implicitních řádků.</span><span class="sxs-lookup"><span data-stu-id="c5dea-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="c5dea-143">V klauzuli `select value` lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="c5dea-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="c5dea-144">Je-li použita taková klauzule, není vytvořena obálka řádku kolem položek v klauzuli `select` a může být vytvořena kolekce požadovaného tvaru, například: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-145">poskytuje také konstruktor Row pro vytvoření libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="c5dea-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="c5dea-146">`select` přebírá jeden nebo více prvků v projekci a vede datový záznam s poli, a to takto:</span><span class="sxs-lookup"><span data-stu-id="c5dea-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="c5dea-147">Levá korelace a aliasy</span><span class="sxs-lookup"><span data-stu-id="c5dea-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="c5dea-148">V jazyce Transact-SQL výrazy v daném oboru (jediná klauzule, jako je například `select` nebo `from`), nemohou odkazovat na výrazy definované dříve ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="c5dea-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="c5dea-149">Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto hodnot v klauzuli `from`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-150">generalizuje levá korelace v klauzuli `from` a považuje je jednotně.</span><span class="sxs-lookup"><span data-stu-id="c5dea-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="c5dea-151">Výrazy v klauzuli `from` mohou odkazovat na předchozí definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c5dea-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-152">také zavádí další omezení dotazů týkajících se klauzulí `group by`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="c5dea-153">Výrazy v klauzuli `select` a klauzule `having` takových dotazů mohou odkazovat pouze na klíče `group by` prostřednictvím jejich aliasů.</span><span class="sxs-lookup"><span data-stu-id="c5dea-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="c5dea-154">Následující konstrukce je platná v jazyce Transact-SQL, ale není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c5dea-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="c5dea-155">K tomu je potřeba [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c5dea-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="c5dea-156">Odkazy na sloupce (vlastnosti) tabulek (kolekcí)</span><span class="sxs-lookup"><span data-stu-id="c5dea-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="c5dea-157">Všechny odkazy na sloupce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být kvalifikovány pomocí aliasu tabulky.</span><span class="sxs-lookup"><span data-stu-id="c5dea-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="c5dea-158">Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T`) je platný v jazyce Transact-SQL, ale ne v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5dea-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="c5dea-159">Formulář [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je</span><span class="sxs-lookup"><span data-stu-id="c5dea-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="c5dea-160">Aliasy tabulky jsou v klauzuli `from` volitelné.</span><span class="sxs-lookup"><span data-stu-id="c5dea-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="c5dea-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="c5dea-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-162">umožňuje také následující formulář:</span><span class="sxs-lookup"><span data-stu-id="c5dea-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="c5dea-163">Navigace prostřednictvím objektů</span><span class="sxs-lookup"><span data-stu-id="c5dea-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="c5dea-164">Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky.</span><span class="sxs-lookup"><span data-stu-id="c5dea-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-165">rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="c5dea-166">Například pokud je `p` výraz typu person, následuje následující syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pro odkazování města adresy této osoby.</span><span class="sxs-lookup"><span data-stu-id="c5dea-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="c5dea-167">Žádná podpora pro \*</span><span class="sxs-lookup"><span data-stu-id="c5dea-167">No Support for \*</span></span>  
 <span data-ttu-id="c5dea-168">Transact-SQL podporuje nekvalifikované \* syntaxi jako alias pro celý řádek a kvalifikovanou syntaxi \* (t. \*) jako zástupce pro pole této tabulky.</span><span class="sxs-lookup"><span data-stu-id="c5dea-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="c5dea-169">Kromě toho Transact-SQL umožňuje pro agregaci se speciálním počtem (\*), který zahrnuje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c5dea-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-170">nepodporuje konstrukci \*.</span><span class="sxs-lookup"><span data-stu-id="c5dea-170">does not support the \* construct.</span></span> <span data-ttu-id="c5dea-171">Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze vyjádřit v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c5dea-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="c5dea-172">Kromě toho tyto konstrukce zpracovávají dědičnost (nahraditelnosti hodnoty), zatímco varianty `select *` jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-173">nepodporuje agregaci `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="c5dea-174">Místo nich se používá `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="c5dea-175">Změny pro seskupení podle</span><span class="sxs-lookup"><span data-stu-id="c5dea-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-176">podporuje aliasy klíčů `group by`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="c5dea-177">Výrazy v klauzuli `select` a klauzule `having` musí odkazovat na klíče `group by` prostřednictvím těchto aliasů.</span><span class="sxs-lookup"><span data-stu-id="c5dea-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="c5dea-178">Například tato syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c5dea-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="c5dea-179">... je ekvivalentní následujícímu jazyku Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="c5dea-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="c5dea-180">Agregace založené na kolekcích</span><span class="sxs-lookup"><span data-stu-id="c5dea-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-181">podporuje dva druhy agregací.</span><span class="sxs-lookup"><span data-stu-id="c5dea-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="c5dea-182">Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek.</span><span class="sxs-lookup"><span data-stu-id="c5dea-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="c5dea-183">Ty se můžou objevit kdekoli v dotazu a nevyžadují klauzuli `group by`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="c5dea-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5dea-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-185">také podporuje agregace ve stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="c5dea-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="c5dea-186">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5dea-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="c5dea-187">Použití klauzule ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c5dea-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="c5dea-188">Transact-SQL povoluje zadání `ORDER BY` klauzulí pouze v horním bloku `SELECT .. FROM .. WHERE`.</span><span class="sxs-lookup"><span data-stu-id="c5dea-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="c5dea-189">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz `ORDER BY` a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="c5dea-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="c5dea-190">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="c5dea-190">Identifiers</span></span>  
 <span data-ttu-id="c5dea-191">V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze.</span><span class="sxs-lookup"><span data-stu-id="c5dea-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="c5dea-192">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mají identifikátory vždycky nerozlišovat velikost písmen a musí rozlišovat diakritiku (tj. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozlišuje mezi znaky s diakritikou a neakcenty, například ' a ' se nerovná ' ấ ').</span><span class="sxs-lookup"><span data-stu-id="c5dea-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-193">zpracovává verze písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="c5dea-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="c5dea-194">Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c5dea-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="c5dea-195">Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c5dea-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="c5dea-196">Následující funkce jazyka Transact-SQL nejsou k dispozici v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5dea-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="c5dea-197">OPERACÍ</span><span class="sxs-lookup"><span data-stu-id="c5dea-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-198">v současné době neposkytuje podporu pro příkazy DML (INSERT, Update, DELETE).</span><span class="sxs-lookup"><span data-stu-id="c5dea-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="c5dea-199">SKRIPT</span><span class="sxs-lookup"><span data-stu-id="c5dea-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-200">neposkytuje podporu pro DDL v aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="c5dea-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="c5dea-201">imperativní programování</span><span class="sxs-lookup"><span data-stu-id="c5dea-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-202">neposkytuje podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c5dea-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="c5dea-203">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="c5dea-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="c5dea-204">Seskupení funkcí</span><span class="sxs-lookup"><span data-stu-id="c5dea-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-205">zatím neposkytuje podporu pro seskupování funkcí (například KRYCHLe, souhrn a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="c5dea-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="c5dea-206">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="c5dea-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-207">(zatím) neposkytuje podporu pro analytické funkce.</span><span class="sxs-lookup"><span data-stu-id="c5dea-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="c5dea-208">Předdefinované funkce, operátory</span><span class="sxs-lookup"><span data-stu-id="c5dea-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-209">podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c5dea-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="c5dea-210">Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště.</span><span class="sxs-lookup"><span data-stu-id="c5dea-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-211">používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c5dea-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="c5dea-212">Kromě toho Entity Framework umožňuje deklarovat předdefinované a uživatelsky definované funkce úložiště, pro které [!INCLUDE[esql](../../../../../../includes/esql-md.md)] použít.</span><span class="sxs-lookup"><span data-stu-id="c5dea-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="c5dea-213">Pomocné parametry</span><span class="sxs-lookup"><span data-stu-id="c5dea-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-214">neposkytuje mechanismy pro pomocný parametr dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="c5dea-215">Dávkování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="c5dea-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-216">nepodporuje dávkování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5dea-216">does not support batching query results.</span></span> <span data-ttu-id="c5dea-217">Například následuje platný příkaz Transact-SQL (odeslání jako dávky):</span><span class="sxs-lookup"><span data-stu-id="c5dea-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="c5dea-218">Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:</span><span class="sxs-lookup"><span data-stu-id="c5dea-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5dea-219">podporuje pouze jeden příkaz dotazu produkující výsledek na příkaz.</span><span class="sxs-lookup"><span data-stu-id="c5dea-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dea-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5dea-220">See also</span></span>

- [<span data-ttu-id="c5dea-221">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c5dea-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="c5dea-222">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="c5dea-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
