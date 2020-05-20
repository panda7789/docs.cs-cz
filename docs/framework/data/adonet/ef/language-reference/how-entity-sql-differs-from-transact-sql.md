---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615628"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="ccbce-102">Způsob, jakým se Entity SQL liší od jazyka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccbce-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="ccbce-103">Tento článek popisuje rozdíly mezi Entity SQL a Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="ccbce-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="ccbce-104">Podpora dědičnosti a vztahů</span><span class="sxs-lookup"><span data-stu-id="ccbce-104">Inheritance and Relationships Support</span></span>  
 <span data-ttu-id="ccbce-105">Entity SQL pracuje přímo s koncepčními schématy entit a podporuje koncepční modelové funkce, jako je například dědičnost a vztahy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="ccbce-106">Při práci s děděním je často vhodné vybrat instance podtypu z kolekce instancí typu nadtyp.</span><span class="sxs-lookup"><span data-stu-id="ccbce-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="ccbce-107">Tato funkce poskytuje operátor [OfType](oftype-entity-sql.md) v Entity SQL (podobně jako `oftype` v sekvencích C#).</span><span class="sxs-lookup"><span data-stu-id="ccbce-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="ccbce-108">Podpora pro kolekce</span><span class="sxs-lookup"><span data-stu-id="ccbce-108">Support for Collections</span></span>  
 <span data-ttu-id="ccbce-109">Entity SQL považuje kolekce za entity první třídy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="ccbce-110">Například:</span><span class="sxs-lookup"><span data-stu-id="ccbce-110">For example:</span></span>  
  
- <span data-ttu-id="ccbce-111">Výrazy kolekce jsou platné v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ccbce-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="ccbce-112">`in`a `exists` poddotazy byly zobecněny, aby umožňovaly všechny kolekce.</span><span class="sxs-lookup"><span data-stu-id="ccbce-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="ccbce-113">Poddotaz je jeden druh kolekce.</span><span class="sxs-lookup"><span data-stu-id="ccbce-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="ccbce-114">`e1 in e2`a `exists(e)` jsou Entity SQL konstrukce pro provedení těchto operací.</span><span class="sxs-lookup"><span data-stu-id="ccbce-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="ccbce-115">Nastavení operací, jako jsou `union` , `intersect` a `except` , teď fungují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="ccbce-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="ccbce-116">Spojení se spouštějí na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="ccbce-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="ccbce-117">Podpora pro výrazy</span><span class="sxs-lookup"><span data-stu-id="ccbce-117">Support for Expressions</span></span>  
 <span data-ttu-id="ccbce-118">V jazyce Transact-SQL jsou poddotazy (tabulky) a výrazy (řádky a sloupce).</span><span class="sxs-lookup"><span data-stu-id="ccbce-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="ccbce-119">Aby bylo možné podporovat kolekce a vnořené kolekce, Entity SQL provede všechny výrazy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="ccbce-120">Entity SQL je lépe sestavitelný než Transact-SQL – každý výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="ccbce-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="ccbce-121">Výrazy dotazů mají vždycky za následek kolekce projektových typů a dají se použít kdekoli je povolený výraz kolekce.</span><span class="sxs-lookup"><span data-stu-id="ccbce-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="ccbce-122">Informace o výrazech jazyka Transact-SQL, které nejsou v Entity SQL podporovány, naleznete v tématu [nepodporované výrazy](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ccbce-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ccbce-123">Níže jsou uvedené všechny platné dotazy Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="ccbce-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="ccbce-124">Jednotné zpracování poddotazů</span><span class="sxs-lookup"><span data-stu-id="ccbce-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="ccbce-125">V jazyce Transact-SQL, který má vzhledem k tabulkám zdůraznění, provádí kontextovou interpretaci poddotazů.</span><span class="sxs-lookup"><span data-stu-id="ccbce-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="ccbce-126">Například poddotaz v `from` klauzuli se považuje za multiset (Table).</span><span class="sxs-lookup"><span data-stu-id="ccbce-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="ccbce-127">Ale stejný poddotaz použitý v `select` klauzuli je považován za skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="ccbce-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="ccbce-128">Podobně, poddotaz použitý na levé straně `in` operátoru se považuje za skalární poddotaz, zatímco na pravé straně se očekává poddotaz multiset.</span><span class="sxs-lookup"><span data-stu-id="ccbce-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="ccbce-129">Entity SQL eliminují tyto rozdíly.</span><span class="sxs-lookup"><span data-stu-id="ccbce-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="ccbce-130">Výraz má jednotný výklad, který není závislý na kontextu, ve kterém je použit.</span><span class="sxs-lookup"><span data-stu-id="ccbce-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="ccbce-131">Entity SQL předpokládá, že všechny poddotazy budou multiset poddotazy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="ccbce-132">Pokud je v poddotazu požadováno skalární hodnota, Entity SQL poskytuje `anyelement` operátor, který pracuje na kolekci (v tomto případě poddotaz), a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="ccbce-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="ccbce-133">Zamezení implicitních vynucení pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="ccbce-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="ccbce-134">Související vedlejší účinky jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccbce-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="ccbce-135">Konkrétně v jazyce Transact-SQL je multiset řádků (s jedním polem) implicitně převeden na skalární hodnotu, jejíž datový typ je to pole.</span><span class="sxs-lookup"><span data-stu-id="ccbce-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="ccbce-136">Entity SQL nepodporuje tuto implicitní vynucení.</span><span class="sxs-lookup"><span data-stu-id="ccbce-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="ccbce-137">Entity SQL poskytuje `ANYELEMENT` operátor pro extrakci hodnoty typu Singleton z kolekce a `select value` klauzule, která vyloučí řádkovou obálku během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="ccbce-138">Vyberte hodnotu: vyloučí se obálku implicitního řádku.</span><span class="sxs-lookup"><span data-stu-id="ccbce-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="ccbce-139">Klauzule SELECT v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položek v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ccbce-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="ccbce-140">To znamená, že nemůžeme vytvořit kolekce skalárních objektů nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="ccbce-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="ccbce-141">Transact-SQL umožňuje implicitní vynucení mezi `rowtype` s jedním polem a hodnotou singleton stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="ccbce-142">Entity SQL poskytuje `select value` klauzuli pro přeskočení vytváření implicitních řádků.</span><span class="sxs-lookup"><span data-stu-id="ccbce-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="ccbce-143">V klauzuli lze zadat pouze jednu položku `select value` .</span><span class="sxs-lookup"><span data-stu-id="ccbce-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="ccbce-144">Je-li použita taková klauzule, není kolem položek v klauzuli vytvořena obálka řádku `select` a může být vytvořena kolekce požadovaného tvaru, například `select value a` .</span><span class="sxs-lookup"><span data-stu-id="ccbce-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="ccbce-145">Entity SQL také poskytuje konstruktor Row pro sestavování libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="ccbce-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="ccbce-146">`select`přebírá jeden nebo více prvků v projekci a vede datový záznam s poli:</span><span class="sxs-lookup"><span data-stu-id="ccbce-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="ccbce-147">Levá korelace a aliasy</span><span class="sxs-lookup"><span data-stu-id="ccbce-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="ccbce-148">V jazyce Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from` ) nemohou odkazovat na výrazy definované dříve ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="ccbce-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="ccbce-149">Některé dialekty jazyka SQL (včetně jazyka Transact-SQL) podporují omezené formy těchto v `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ccbce-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="ccbce-150">Entity SQL generalizuje levá korelace v `from` klauzuli a považuje je jednotně.</span><span class="sxs-lookup"><span data-stu-id="ccbce-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="ccbce-151">Výrazy v `from` klauzuli mohou odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ccbce-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="ccbce-152">Entity SQL také zavádí dodatečná omezení pro dotazy zahrnující `group by` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ccbce-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="ccbce-153">Výrazy v `select` klauzuli a `having` klauzuli těchto dotazů mohou odkazovat pouze na `group by` klíče přes jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="ccbce-154">Následující konstrukce je platná v jazyce Transact-SQL, ale není v Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="ccbce-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="ccbce-155">Postup v Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="ccbce-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="ccbce-156">Odkazy na sloupce (vlastnosti) tabulek (kolekcí)</span><span class="sxs-lookup"><span data-stu-id="ccbce-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="ccbce-157">Všechny odkazy na sloupce v Entity SQL musí být kvalifikovány pomocí aliasu tabulky.</span><span class="sxs-lookup"><span data-stu-id="ccbce-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="ccbce-158">Následující konstrukce (za předpokladu, že `a` je platný sloupec tabulky `T` ) je platná v jazyce Transact-SQL, ale ne v Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="ccbce-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="ccbce-159">Formulář Entity SQL je</span><span class="sxs-lookup"><span data-stu-id="ccbce-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="ccbce-160">Aliasy tabulky jsou v klauzuli volitelné `from` .</span><span class="sxs-lookup"><span data-stu-id="ccbce-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="ccbce-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="ccbce-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="ccbce-162">Entity SQL umožňuje také následující formulář:</span><span class="sxs-lookup"><span data-stu-id="ccbce-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="ccbce-163">Navigace prostřednictvím objektů</span><span class="sxs-lookup"><span data-stu-id="ccbce-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="ccbce-164">Transact-SQL používá notaci "." pro odkazující sloupce (řádek) tabulky.</span><span class="sxs-lookup"><span data-stu-id="ccbce-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="ccbce-165">Entity SQL rozšiřuje tento zápis (vypůjčil z programovacích jazyků), aby podporoval navigaci prostřednictvím vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="ccbce-166">Například pokud `p` je výraz typu person, následuje následující syntaxe Entity SQL pro odkazování města adresy této osoby.</span><span class="sxs-lookup"><span data-stu-id="ccbce-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="ccbce-167">Žádná podpora pro\*</span><span class="sxs-lookup"><span data-stu-id="ccbce-167">No Support for \*</span></span>  
 <span data-ttu-id="ccbce-168">Transact-SQL podporuje nekvalifikovanou \* syntaxi jako alias pro celý řádek a kvalifikovanou \* syntaxi (t. \* ) jako zástupce pro pole této tabulky.</span><span class="sxs-lookup"><span data-stu-id="ccbce-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="ccbce-169">Kromě toho jazyk Transact-SQL umožňuje použití speciální agregace Count ( \* ), která zahrnuje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="ccbce-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="ccbce-170">Entity SQL nepodporuje konstrukci \*.</span><span class="sxs-lookup"><span data-stu-id="ccbce-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="ccbce-171">Dotazy Transact-SQL formuláře `select * from T` a `select T1.* from T1, T2...` lze je vyjádřit v Entity SQL jako a v `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ccbce-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="ccbce-172">Kromě toho tyto konstrukce zpracovávají dědičnost (hodnotu nahraditelnosti), zatímco `select *` varianty jsou omezeny na vlastnosti nejvyšší úrovně deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="ccbce-173">Entity SQL nepodporuje `count(*)` agregaci.</span><span class="sxs-lookup"><span data-stu-id="ccbce-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="ccbce-174">Místo toho použijte `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="ccbce-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="ccbce-175">Změny pro seskupení podle</span><span class="sxs-lookup"><span data-stu-id="ccbce-175">Changes to Group By</span></span>  
 <span data-ttu-id="ccbce-176">Entity SQL podporuje aliasy `group by` klíčů.</span><span class="sxs-lookup"><span data-stu-id="ccbce-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="ccbce-177">Výrazy v `select` klauzuli a `having` klauzule musí odkazovat na `group by` klíče přes tyto aliasy.</span><span class="sxs-lookup"><span data-stu-id="ccbce-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="ccbce-178">Například tato syntaxe Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="ccbce-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="ccbce-179">... je ekvivalentní následujícímu jazyku Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="ccbce-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="ccbce-180">Agregace založené na kolekcích</span><span class="sxs-lookup"><span data-stu-id="ccbce-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="ccbce-181">Entity SQL podporuje dva druhy agregací.</span><span class="sxs-lookup"><span data-stu-id="ccbce-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="ccbce-182">Agregace založené na kolekcích pracují s kolekcemi a vytváří agregovaný výsledek.</span><span class="sxs-lookup"><span data-stu-id="ccbce-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="ccbce-183">Ty se můžou objevit kdekoli v dotazu a nevyžadují `group by` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ccbce-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="ccbce-184">Například:</span><span class="sxs-lookup"><span data-stu-id="ccbce-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="ccbce-185">Entity SQL podporuje také agregace ve stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="ccbce-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="ccbce-186">Například:</span><span class="sxs-lookup"><span data-stu-id="ccbce-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="ccbce-187">Použití klauzule ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ccbce-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="ccbce-188">Klauzule Transact-SQL umožňují `ORDER BY` zadat pouze v horním `SELECT .. FROM .. WHERE` bloku.</span><span class="sxs-lookup"><span data-stu-id="ccbce-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="ccbce-189">V Entity SQL můžete použít vnořený `ORDER BY` výraz a může být umístěn kdekoli v dotazu, ale řazení vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="ccbce-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="ccbce-190">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="ccbce-190">Identifiers</span></span>  
 <span data-ttu-id="ccbce-191">V jazyce Transact-SQL je porovnání identifikátorů založeno na kolaci aktuální databáze.</span><span class="sxs-lookup"><span data-stu-id="ccbce-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="ccbce-192">V Entity SQL identifikátory jsou vždy bez rozlišení velkých a malých písmen a s diakritikou (to znamená Entity SQL rozlišovat znaky s diakritikou a nezvýrazněnými znaky; například ' a ' se nerovná ' ấ ').</span><span class="sxs-lookup"><span data-stu-id="ccbce-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="ccbce-193">Entity SQL zachází s verzemi písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="ccbce-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="ccbce-194">Další informace najdete v tématu [vstupní znaková sada](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ccbce-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="ccbce-195">Funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ccbce-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="ccbce-196">Následující funkce jazyka Transact-SQL nejsou v Entity SQL k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ccbce-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="ccbce-197">OPERACÍ</span><span class="sxs-lookup"><span data-stu-id="ccbce-197">DML</span></span>  
 <span data-ttu-id="ccbce-198">Entity SQL v současné době neposkytuje podporu pro příkazy DML (INSERT, Update, DELETE).</span><span class="sxs-lookup"><span data-stu-id="ccbce-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="ccbce-199">SKRIPT</span><span class="sxs-lookup"><span data-stu-id="ccbce-199">DDL</span></span>  
 <span data-ttu-id="ccbce-200">Entity SQL neposkytuje žádnou podporu pro DDL v aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="ccbce-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="ccbce-201">imperativní programování</span><span class="sxs-lookup"><span data-stu-id="ccbce-201">Imperative Programming</span></span>  
 <span data-ttu-id="ccbce-202">Entity SQL neposkytuje žádnou podporu pro imperativní programování, na rozdíl od jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="ccbce-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="ccbce-203">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="ccbce-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="ccbce-204">Seskupení funkcí</span><span class="sxs-lookup"><span data-stu-id="ccbce-204">Grouping Functions</span></span>  
 <span data-ttu-id="ccbce-205">Entity SQL ještě neposkytuje podporu seskupování funkcí (například datová krychle, souhrn a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="ccbce-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="ccbce-206">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="ccbce-206">Analytic Functions</span></span>  
 <span data-ttu-id="ccbce-207">Entity SQL ještě neposkytuje podporu pro analytické funkce.</span><span class="sxs-lookup"><span data-stu-id="ccbce-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="ccbce-208">Předdefinované funkce, operátory</span><span class="sxs-lookup"><span data-stu-id="ccbce-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="ccbce-209">Entity SQL podporuje podmnožinu vestavěných funkcí a operátorů jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="ccbce-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="ccbce-210">Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli úložiště.</span><span class="sxs-lookup"><span data-stu-id="ccbce-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="ccbce-211">Entity SQL používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="ccbce-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="ccbce-212">Kromě toho Entity Framework umožňuje deklarovat předdefinované a uživatelsky definované funkce úložiště, které Entity SQL použít.</span><span class="sxs-lookup"><span data-stu-id="ccbce-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="ccbce-213">Pomocné parametry</span><span class="sxs-lookup"><span data-stu-id="ccbce-213">Hints</span></span>  
 <span data-ttu-id="ccbce-214">Entity SQL neposkytuje mechanismy pro pomocný parametr dotazu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="ccbce-215">Dávkování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="ccbce-215">Batching Query Results</span></span>  
 <span data-ttu-id="ccbce-216">Entity SQL nepodporuje dávkování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="ccbce-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="ccbce-217">Například následuje platný příkaz Transact-SQL (odeslání jako dávky):</span><span class="sxs-lookup"><span data-stu-id="ccbce-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="ccbce-218">Ekvivalentní Entity SQL však není podporován:</span><span class="sxs-lookup"><span data-stu-id="ccbce-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="ccbce-219">Entity SQL podporuje pouze jeden příkaz dotazu vytvářejícího výsledek na příkaz.</span><span class="sxs-lookup"><span data-stu-id="ccbce-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbce-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccbce-220">See also</span></span>

- [<span data-ttu-id="ccbce-221">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ccbce-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ccbce-222">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="ccbce-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
