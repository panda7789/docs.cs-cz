---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 1a4bf8267ee5f036effc5f7bc91c28d1485b7612
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250861"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="239f7-102">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="239f7-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="239f7-103">Toto téma popisuje rozdíly mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="239f7-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="239f7-104">Podpora dědičnosti a vztahů</span><span class="sxs-lookup"><span data-stu-id="239f7-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-105">pracuje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.</span><span class="sxs-lookup"><span data-stu-id="239f7-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="239f7-106">Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp.</span><span class="sxs-lookup"><span data-stu-id="239f7-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="239f7-107">Tato [](oftype-entity-sql.md) funkce poskytuje operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] OfType v ( `oftype` podobně C# jako v sekvencích).</span><span class="sxs-lookup"><span data-stu-id="239f7-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="239f7-108">Podpora pro kolekce</span><span class="sxs-lookup"><span data-stu-id="239f7-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-109">zpracovává kolekce jako entity první třídy.</span><span class="sxs-lookup"><span data-stu-id="239f7-109">treats collections as first-class entities.</span></span> <span data-ttu-id="239f7-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="239f7-110">For example:</span></span>  
  
- <span data-ttu-id="239f7-111">Výrazy kolekce jsou platné v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="239f7-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="239f7-112">`in`a `exists` poddotazy byly zobecněny, aby umožňovaly všechny kolekce.</span><span class="sxs-lookup"><span data-stu-id="239f7-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="239f7-113">Poddotaz je jeden druh kolekce.</span><span class="sxs-lookup"><span data-stu-id="239f7-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="239f7-114">`e1 in e2``exists(e)` a[!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou konstrukcemi k provedení těchto operací.</span><span class="sxs-lookup"><span data-stu-id="239f7-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="239f7-115">Nastavení operací, `union`jako jsou, `intersect`a `except`, teď fungují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="239f7-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="239f7-116">Spojení se spouštějí na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="239f7-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="239f7-117">Podpora pro výrazy</span><span class="sxs-lookup"><span data-stu-id="239f7-117">Support for Expressions</span></span>  
 <span data-ttu-id="239f7-118">V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).</span><span class="sxs-lookup"><span data-stu-id="239f7-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="239f7-119">Aby bylo možné podporovat kolekce a vnořené [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce, provede vše výraz.</span><span class="sxs-lookup"><span data-stu-id="239f7-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-120">je více sestavitelný než Transact-SQL – každý výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="239f7-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="239f7-121">Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce.</span><span class="sxs-lookup"><span data-stu-id="239f7-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="239f7-122">Informace o výrazech jazyka Transact-SQL, které nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji podporovány, naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="239f7-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="239f7-123">Níže jsou uvedené všechny platné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy:</span><span class="sxs-lookup"><span data-stu-id="239f7-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="239f7-124">Jednotné zpracování poddotazů</span><span class="sxs-lookup"><span data-stu-id="239f7-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="239f7-125">V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů.</span><span class="sxs-lookup"><span data-stu-id="239f7-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="239f7-126">Například poddotaz v `from` klauzuli se považuje za multiset (Table).</span><span class="sxs-lookup"><span data-stu-id="239f7-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="239f7-127">Ale stejný poddotaz použitý v `select` klauzuli je považován za skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="239f7-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="239f7-128">Podobně, poddotaz použitý na levé straně `in` operátoru se považuje za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.</span><span class="sxs-lookup"><span data-stu-id="239f7-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-129">eliminuje tyto rozdíly.</span><span class="sxs-lookup"><span data-stu-id="239f7-129">eliminates these differences.</span></span> <span data-ttu-id="239f7-130">Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit.</span><span class="sxs-lookup"><span data-stu-id="239f7-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-131">posuzuje všechny poddotazy, které mají být multiset poddotazy.</span><span class="sxs-lookup"><span data-stu-id="239f7-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="239f7-132">Pokud je v poddotazu požadováno skalární hodnota, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `anyelement` poskytuje operátor, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="239f7-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="239f7-133">Zamezení implicitních vynucení pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="239f7-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="239f7-134">Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="239f7-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="239f7-135">Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.</span><span class="sxs-lookup"><span data-stu-id="239f7-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-136">nepodporuje tuto implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="239f7-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-137">poskytuje operátor AnyElement k extrakci hodnoty singleton z kolekce a `select value` klauzule, která vyloučí řádkovou obálku během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="239f7-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="239f7-138">Vyberte hodnotu: Zamezení obálky implicitního řádku</span><span class="sxs-lookup"><span data-stu-id="239f7-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="239f7-139">Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="239f7-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="239f7-140">To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="239f7-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="239f7-141">Transact-SQL umožňuje implicitní vynucení mezi RowType a jedním polem a hodnotou singleton stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="239f7-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-142">`select value` poskytuje klauzuli pro přeskočení vytváření implicitních řádků.</span><span class="sxs-lookup"><span data-stu-id="239f7-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="239f7-143">V `select value` klauzuli lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="239f7-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="239f7-144">Je-li použita taková klauzule, není kolem položek v `select` klauzuli vytvořena obálka řádku a může být vytvořena kolekce požadovaného tvaru, například:. `select value a`</span><span class="sxs-lookup"><span data-stu-id="239f7-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-145">také poskytuje konstruktor Row pro vytvoření libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="239f7-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="239f7-146">`select`přebírá jeden nebo více prvků v projekci a vede datový záznam s poli, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="239f7-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="239f7-147">Levá korelace a aliasy</span><span class="sxs-lookup"><span data-stu-id="239f7-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="239f7-148">V jazyce Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from`) nemohou odkazovat na výrazy definované dříve ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="239f7-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="239f7-149">Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="239f7-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-150">generalizuje levé korelační `from` klauzule v klauzuli a považuje je jednotně.</span><span class="sxs-lookup"><span data-stu-id="239f7-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="239f7-151">Výrazy v `from` klauzuli mohou odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.</span><span class="sxs-lookup"><span data-stu-id="239f7-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-152">také zavádí další omezení dotazů týkajících `group by` se klauzulí.</span><span class="sxs-lookup"><span data-stu-id="239f7-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="239f7-153">Výrazy v `select` klauzuli a `having` klauzuli těchto dotazů `group by` mohou odkazovat pouze na klíče přes jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="239f7-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="239f7-154">Následující konstrukce je platná v jazyce Transact-SQL, ale není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="239f7-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="239f7-155">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Postup:</span><span class="sxs-lookup"><span data-stu-id="239f7-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="239f7-156">Odkazy na sloupce (vlastnosti) tabulek (kolekcí)</span><span class="sxs-lookup"><span data-stu-id="239f7-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="239f7-157">Všechny odkazy na sloupce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v nástroji musí být kvalifikovány pomocí aliasu tabulky.</span><span class="sxs-lookup"><span data-stu-id="239f7-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="239f7-158">Následující konstrukce (za předpokladu `a` , že je platný sloupec tabulky `T`) je platná v jazyce Transact-SQL, ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ne v.</span><span class="sxs-lookup"><span data-stu-id="239f7-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="239f7-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formulář je</span><span class="sxs-lookup"><span data-stu-id="239f7-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="239f7-160">Aliasy tabulky jsou v `from` klauzuli volitelné.</span><span class="sxs-lookup"><span data-stu-id="239f7-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="239f7-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="239f7-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-162">umožňuje také následující formulář:</span><span class="sxs-lookup"><span data-stu-id="239f7-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="239f7-163">Navigace prostřednictvím objektů</span><span class="sxs-lookup"><span data-stu-id="239f7-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="239f7-164">Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky.</span><span class="sxs-lookup"><span data-stu-id="239f7-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-165">rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="239f7-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="239f7-166">Například pokud `p` je výraz typu person, následuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe pro odkazování města adresy této osoby.</span><span class="sxs-lookup"><span data-stu-id="239f7-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="239f7-167">Žádná podpora pro \*</span><span class="sxs-lookup"><span data-stu-id="239f7-167">No Support for \*</span></span>  
 <span data-ttu-id="239f7-168">Transact-SQL podporuje nekvalifikované \* syntaxi jako alias pro celý řádek a kvalifikovanou \* syntaxi (t.\*) jako zástupce pro pole této tabulky.</span><span class="sxs-lookup"><span data-stu-id="239f7-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="239f7-169">Kromě toho jazyk Transact-SQL umožňuje použití speciální agregace Count (\*), která zahrnuje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="239f7-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-170">nepodporuje konstrukci \*.</span><span class="sxs-lookup"><span data-stu-id="239f7-170">does not support the \* construct.</span></span> <span data-ttu-id="239f7-171">Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze je vyjádřit v podobě jako [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="239f7-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="239f7-172">Kromě toho tyto konstrukce zpracovávají dědičnost (hodnotu nahraditelnosti), zatímco `select *` varianty jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="239f7-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-173">`count(*)` nepodporuje agregaci.</span><span class="sxs-lookup"><span data-stu-id="239f7-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="239f7-174">Místo nich se používá `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="239f7-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="239f7-175">Změny pro seskupení podle</span><span class="sxs-lookup"><span data-stu-id="239f7-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-176">podporuje aliasy `group by` klíčů.</span><span class="sxs-lookup"><span data-stu-id="239f7-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="239f7-177">Výrazy v `select` klauzuli a `having` klauzule musí odkazovat na klíčepřestytoaliasy.`group by`</span><span class="sxs-lookup"><span data-stu-id="239f7-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="239f7-178">Například tato [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:</span><span class="sxs-lookup"><span data-stu-id="239f7-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="239f7-179">... je ekvivalentní následujícímu jazyku Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="239f7-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="239f7-180">Agregace založené na kolekcích</span><span class="sxs-lookup"><span data-stu-id="239f7-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-181">podporuje dva druhy agregací.</span><span class="sxs-lookup"><span data-stu-id="239f7-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="239f7-182">Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek.</span><span class="sxs-lookup"><span data-stu-id="239f7-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="239f7-183">Ty se můžou objevit kdekoli v dotazu a nevyžadují `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="239f7-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="239f7-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="239f7-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-185">podporuje také agregace ve stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="239f7-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="239f7-186">Příklad:</span><span class="sxs-lookup"><span data-stu-id="239f7-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="239f7-187">Použití klauzule ORDER BY</span><span class="sxs-lookup"><span data-stu-id="239f7-187">ORDER BY Clause Usage</span></span>  
 <span data-ttu-id="239f7-188">Příkaz Transact-SQL umožňuje zadat klauzule ORDER BY pouze v horním výběru.</span><span class="sxs-lookup"><span data-stu-id="239f7-188">Transact-SQL allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="239f7-189">Z..</span><span class="sxs-lookup"><span data-stu-id="239f7-189">FROM ..</span></span> <span data-ttu-id="239f7-190">Blok WHERE.</span><span class="sxs-lookup"><span data-stu-id="239f7-190">WHERE block.</span></span> <span data-ttu-id="239f7-191">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený výraz ORDER by a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="239f7-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="239f7-192">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="239f7-192">Identifiers</span></span>  
 <span data-ttu-id="239f7-193">V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze.</span><span class="sxs-lookup"><span data-stu-id="239f7-193">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="239f7-194">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jsou identifikátory vždy bez rozlišení velkých a malých písmen a s diakritikou ( [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to znamená rozlišení mezi znaky s diakritikou a neakcenty, například ' a ' se nerovná ' ấ ').</span><span class="sxs-lookup"><span data-stu-id="239f7-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-195">zpracovává verze písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="239f7-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="239f7-196">Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="239f7-196">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="239f7-197">Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.</span><span class="sxs-lookup"><span data-stu-id="239f7-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="239f7-198">Následující funkce jazyka Transact-SQL nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji k dispozici.</span><span class="sxs-lookup"><span data-stu-id="239f7-198">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="239f7-199">DML</span><span class="sxs-lookup"><span data-stu-id="239f7-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-200">v současné době není k dispozici žádná podpora pro příkazy DML (vložení, aktualizace, odstranění).</span><span class="sxs-lookup"><span data-stu-id="239f7-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="239f7-201">DDL</span><span class="sxs-lookup"><span data-stu-id="239f7-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-202">v aktuální verzi neposkytuje žádnou podporu pro DDL.</span><span class="sxs-lookup"><span data-stu-id="239f7-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="239f7-203">imperativní programování</span><span class="sxs-lookup"><span data-stu-id="239f7-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-204">neposkytuje žádnou podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="239f7-204">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="239f7-205">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="239f7-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="239f7-206">Seskupení funkcí</span><span class="sxs-lookup"><span data-stu-id="239f7-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-207">ještě neposkytuje podporu pro seskupování funkcí (například KRYCHLe, souhrn a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="239f7-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="239f7-208">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="239f7-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-209">ještě neposkytuje podporu pro analytické funkce.</span><span class="sxs-lookup"><span data-stu-id="239f7-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="239f7-210">Předdefinované funkce, operátory</span><span class="sxs-lookup"><span data-stu-id="239f7-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-211">podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="239f7-211">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="239f7-212">Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště.</span><span class="sxs-lookup"><span data-stu-id="239f7-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-213">používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="239f7-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="239f7-214">Kromě toho [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje deklarovat předdefinované a uživatelem definované funkce úložiště [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , které se mají použít.</span><span class="sxs-lookup"><span data-stu-id="239f7-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="239f7-215">Pomocné parametry</span><span class="sxs-lookup"><span data-stu-id="239f7-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-216">neposkytuje mechanismy pro pomocný parametr dotazu.</span><span class="sxs-lookup"><span data-stu-id="239f7-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="239f7-217">Dávkování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="239f7-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-218">nepodporuje dávkování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="239f7-218">does not support batching query results.</span></span> <span data-ttu-id="239f7-219">Například následuje platný příkaz Transact-SQL (odeslání jako dávky):</span><span class="sxs-lookup"><span data-stu-id="239f7-219">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="239f7-220">Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:</span><span class="sxs-lookup"><span data-stu-id="239f7-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="239f7-221">pro každý příkaz podporuje pouze jeden příkaz dotazu vytvářející výsledek.</span><span class="sxs-lookup"><span data-stu-id="239f7-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239f7-222">Viz také:</span><span class="sxs-lookup"><span data-stu-id="239f7-222">See also</span></span>

- [<span data-ttu-id="239f7-223">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="239f7-223">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="239f7-224">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="239f7-224">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
