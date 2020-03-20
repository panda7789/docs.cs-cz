---
title: Jak se Entity SQL liší od Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150228"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="390a6-102">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="390a6-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="390a6-103">Toto téma popisuje rozdíly [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mezi a Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="390a6-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="390a6-104">Podpora dědičnosti a vztahů</span><span class="sxs-lookup"><span data-stu-id="390a6-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-105">pracuje přímo se schématy koncepčních entit a podporuje funkce konceptuálního modelu, jako je dědičnost a vztahy.</span><span class="sxs-lookup"><span data-stu-id="390a6-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="390a6-106">Při práci s dědičností je často užitečné vybrat instance podtypu z kolekce instancí nadtypu.</span><span class="sxs-lookup"><span data-stu-id="390a6-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="390a6-107">[Oftype](oftype-entity-sql.md) operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v (podobně jako `oftype` v C# Sekvence) poskytuje tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="390a6-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="390a6-108">Podpora kolekcí</span><span class="sxs-lookup"><span data-stu-id="390a6-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-109">zachází s kolekcemi jako s entitami první třídy.</span><span class="sxs-lookup"><span data-stu-id="390a6-109">treats collections as first-class entities.</span></span> <span data-ttu-id="390a6-110">Například:</span><span class="sxs-lookup"><span data-stu-id="390a6-110">For example:</span></span>  
  
- <span data-ttu-id="390a6-111">Kolekce výrazy jsou `from` platné v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="390a6-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="390a6-112">`in`a `exists` poddotazy byly zobecněny tak, aby umožňovaly všechny kolekce.</span><span class="sxs-lookup"><span data-stu-id="390a6-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="390a6-113">Poddotaz je jeden druh kolekce.</span><span class="sxs-lookup"><span data-stu-id="390a6-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="390a6-114">`e1 in e2`a `exists(e)` jsou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukce k provedení těchto operací.</span><span class="sxs-lookup"><span data-stu-id="390a6-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="390a6-115">Nastavte operace, `union`například `intersect` `except`, a , nyní pracují na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="390a6-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="390a6-116">Spojení pracovat na kolekce.</span><span class="sxs-lookup"><span data-stu-id="390a6-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="390a6-117">Podpora výrazů</span><span class="sxs-lookup"><span data-stu-id="390a6-117">Support for Expressions</span></span>  
 <span data-ttu-id="390a6-118">Transact-SQL má poddotazy (tabulky) a výrazy (řádky a sloupce).</span><span class="sxs-lookup"><span data-stu-id="390a6-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="390a6-119">Pro podporu kolekcí a vnořených kolekcí, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dělá vše výraz.</span><span class="sxs-lookup"><span data-stu-id="390a6-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-120">je kompozitnější než Transact-SQL – každý výraz lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="390a6-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="390a6-121">Výrazy dotazu vždy za následek kolekce promítnuté typy a lze použít kdekoli výraz kolekce je povoleno.</span><span class="sxs-lookup"><span data-stu-id="390a6-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="390a6-122">Informace o výrazech Transact-SQL, které [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nejsou podporovány v aplikaci , naleznete v [tématu Nepodporované výrazy](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="390a6-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="390a6-123">Níže jsou všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] platné dotazy:</span><span class="sxs-lookup"><span data-stu-id="390a6-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="390a6-124">Jednotné zacházení s poddotazy</span><span class="sxs-lookup"><span data-stu-id="390a6-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="390a6-125">Vzhledem k jeho důraz na tabulky, Transact-SQL provádí kontextovou interpretaci poddotazů.</span><span class="sxs-lookup"><span data-stu-id="390a6-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="390a6-126">Například poddotaz v `from` klauzuli je považován za multiset (tabulka).</span><span class="sxs-lookup"><span data-stu-id="390a6-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="390a6-127">Ale stejný poddotaz použitý `select` v klauzuli je považován za skalární poddotaz.</span><span class="sxs-lookup"><span data-stu-id="390a6-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="390a6-128">Podobně poddotaz použitý na levé straně `in` operátoru je považován za skalární poddotaz, zatímco pravá strana se očekává, že vícemnožinový poddotaz.</span><span class="sxs-lookup"><span data-stu-id="390a6-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-129">tyto rozdíly eliminuje.</span><span class="sxs-lookup"><span data-stu-id="390a6-129">eliminates these differences.</span></span> <span data-ttu-id="390a6-130">Výraz má jednotný výklad, který nezávisí na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="390a6-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-131">považuje všechny poddotazy za vícemnožinové poddotazy.</span><span class="sxs-lookup"><span data-stu-id="390a6-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="390a6-132">Pokud skalární hodnota je žádoucí z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poddotazu, poskytuje `anyelement` operátor, který pracuje na kolekci (v tomto případě poddotaz) a extrahuje hodnotu singleton z kolekce.</span><span class="sxs-lookup"><span data-stu-id="390a6-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="390a6-133">Jak se vyhnout implicitním nátlakům pro poddotazy</span><span class="sxs-lookup"><span data-stu-id="390a6-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="390a6-134">Související vedlejší účinek jednotného zpracování poddotazů je implicitní převod poddotazů na skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="390a6-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="390a6-135">Konkrétně v Transact-SQL je vícenásobná sada řádků (s jedním polem) implicitně převedena na skalární hodnotu, jejíž datový typ je datový masív pole.</span><span class="sxs-lookup"><span data-stu-id="390a6-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-136">nepodporuje toto implicitní nátlak.</span><span class="sxs-lookup"><span data-stu-id="390a6-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-137">poskytuje operátor ANYELEMENT extrahovat hodnotu singleton `select value` z kolekce a klauzule, aby se zabránilo vytvoření obálky řádku během výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="390a6-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="390a6-138">Vybrat hodnotu: Vyhnout se implicitnímu obálkovi řádku</span><span class="sxs-lookup"><span data-stu-id="390a6-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="390a6-139">Select klauzule v poddotazu Transact-SQL implicitně vytvoří obálku řádku kolem položky v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="390a6-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="390a6-140">To znamená, že nemůžeme vytvářet kolekce skalárů nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="390a6-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="390a6-141">Transact-SQL umožňuje implicitní nátlaku mezi typem řádku s jedním polem a singletonovým hodnotou stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="390a6-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-142">poskytuje `select value` klauzuli přeskočit implicitní konstrukce řádku.</span><span class="sxs-lookup"><span data-stu-id="390a6-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="390a6-143">V klauzuli může být `select value` zadána pouze jedna položka.</span><span class="sxs-lookup"><span data-stu-id="390a6-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="390a6-144">Při použití takové klauzule, žádné obálky řádku je `select` vytvořen kolem položky v klauzuli a kolekce `select value a`požadovaný tvar může být vytvořena, například: .</span><span class="sxs-lookup"><span data-stu-id="390a6-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-145">také poskytuje konstruktor řádku pro vytvoření libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="390a6-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="390a6-146">`select`trvá jeden nebo více prvků v projekci a výsledkem je datový záznam s poli takto:</span><span class="sxs-lookup"><span data-stu-id="390a6-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="390a6-147">Levá korelace a aliasing</span><span class="sxs-lookup"><span data-stu-id="390a6-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="390a6-148">V Transact-SQL výrazy v daném oboru (jedna klauzule jako `select` nebo `from`) nemůže odkazovat na výrazy definované dříve ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="390a6-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="390a6-149">Některé dialekty SQL (včetně Transact-SQL) podporují omezené formy `from` těchto v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="390a6-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-150">zobecňuje levé `from` korelace v klauzuli a zachází s nimi jednotně.</span><span class="sxs-lookup"><span data-stu-id="390a6-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="390a6-151">Výrazy v `from` klauzuli můžete odkazovat na dřívější definice (definice vlevo) ve stejné klauzuli bez nutnosti další syntaxe.</span><span class="sxs-lookup"><span data-stu-id="390a6-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-152">rovněž ukládá další omezení na `group by` dotazy týkající se doložek.</span><span class="sxs-lookup"><span data-stu-id="390a6-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="390a6-153">Výrazy v `select` klauzuli a `having` klauzule těchto dotazů může odkazovat pouze na `group by` klíče prostřednictvím svých aliasů.</span><span class="sxs-lookup"><span data-stu-id="390a6-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="390a6-154">Následující konstrukce je platná v Transact-SQL, ale nejsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="390a6-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="390a6-155">Chcete-li [!INCLUDE[esql](../../../../../../includes/esql-md.md)]to provést v :</span><span class="sxs-lookup"><span data-stu-id="390a6-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="390a6-156">Odkazování na sloupce (vlastnosti) tabulek (kolekce)</span><span class="sxs-lookup"><span data-stu-id="390a6-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="390a6-157">Všechny odkazy na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sloupce v písmenu musí být kvalifikovány aliasem tabulky.</span><span class="sxs-lookup"><span data-stu-id="390a6-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="390a6-158">Následující konstrukce (za `a` předpokladu, že `T`je platný sloupec tabulky ) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]je platný v Transact-SQL, ale není v .</span><span class="sxs-lookup"><span data-stu-id="390a6-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="390a6-159">Formulář [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je</span><span class="sxs-lookup"><span data-stu-id="390a6-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="390a6-160">Aliasy tabulky jsou volitelné `from` v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="390a6-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="390a6-161">Název tabulky se používá jako implicitní alias.</span><span class="sxs-lookup"><span data-stu-id="390a6-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-162">umožňuje také následující formu:</span><span class="sxs-lookup"><span data-stu-id="390a6-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="390a6-163">Navigace přes objekty</span><span class="sxs-lookup"><span data-stu-id="390a6-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="390a6-164">Transact-SQL používá notaci "." pro odkazování na sloupce (řádek) tabulky.</span><span class="sxs-lookup"><span data-stu-id="390a6-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-165">rozšiřuje tento zápis (vypůjčený z programovacích jazyků) pro podporu navigace přes vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="390a6-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="390a6-166">Například pokud `p` je výraz typu Osoba, následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je syntaxe pro odkazování na město adresy této osoby.</span><span class="sxs-lookup"><span data-stu-id="390a6-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="390a6-167">Žádná podpora pro \*</span><span class="sxs-lookup"><span data-stu-id="390a6-167">No Support for \*</span></span>  
 <span data-ttu-id="390a6-168">Transact-SQL podporuje nekvalifikovanou \* syntaxi jako alias pro \* celý řádek\*a kvalifikovanou syntaxi (t. ) jako zástupce pro pole této tabulky.</span><span class="sxs-lookup"><span data-stu-id="390a6-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="390a6-169">Kromě toho Transact-SQL umožňuje speciální\*počet( ) agregace, která obsahuje nulls.</span><span class="sxs-lookup"><span data-stu-id="390a6-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-170">nepodporuje \* konstrukci.</span><span class="sxs-lookup"><span data-stu-id="390a6-170">does not support the \* construct.</span></span> <span data-ttu-id="390a6-171">Transact-SQL dotazy `select * from T` formuláře a `select T1.* from T1, T2...` mohou být [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vyjádřeny v jako `select value t from T as t` a `select value t1 from T1 as t1, T2 as t2...`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="390a6-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="390a6-172">Kromě toho tyto konstrukce zpracovávat dědičnost (hodnota substitutability), zatímco `select *` varianty jsou omezeny na nejvyšší úrovni vlastnosti deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="390a6-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-173">nepodporuje agregát. `count(*)`</span><span class="sxs-lookup"><span data-stu-id="390a6-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="390a6-174">Místo toho použijte `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="390a6-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="390a6-175">Změny v seskupení podle</span><span class="sxs-lookup"><span data-stu-id="390a6-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-176">podporuje aliasing `group by` klíčů.</span><span class="sxs-lookup"><span data-stu-id="390a6-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="390a6-177">Výrazy v `select` klauzuli a `having` klauzuli musí odkazovat na `group by` klíče prostřednictvím těchto aliasů.</span><span class="sxs-lookup"><span data-stu-id="390a6-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="390a6-178">Například tato [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntaxe:</span><span class="sxs-lookup"><span data-stu-id="390a6-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="390a6-179">... je ekvivalentní následujícímu Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="390a6-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="390a6-180">Agregáty založené na kolekci</span><span class="sxs-lookup"><span data-stu-id="390a6-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-181">podporuje dva druhy agregátů.</span><span class="sxs-lookup"><span data-stu-id="390a6-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="390a6-182">Agregace založené na kolekcích pracují na kolekcích a vytvářejí agregovaný výsledek.</span><span class="sxs-lookup"><span data-stu-id="390a6-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="390a6-183">Ty se mohou objevit kdekoli v dotazu a nevyžadují klauzuli. `group by`</span><span class="sxs-lookup"><span data-stu-id="390a6-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="390a6-184">Například:</span><span class="sxs-lookup"><span data-stu-id="390a6-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-185">podporuje také agregace ve stylu SQL.</span><span class="sxs-lookup"><span data-stu-id="390a6-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="390a6-186">Například:</span><span class="sxs-lookup"><span data-stu-id="390a6-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="390a6-187">POUŽITÍ KLAUZULE OBJEDNÁNÍ Podle</span><span class="sxs-lookup"><span data-stu-id="390a6-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="390a6-188">Transact-SQL `ORDER BY` umožňuje klauzule, které mají `SELECT .. FROM .. WHERE` být zadány pouze v nejvyšším bloku.</span><span class="sxs-lookup"><span data-stu-id="390a6-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="390a6-189">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] můžete použít vnořený `ORDER BY` výraz a může být umístěn kdekoli v dotazu, ale řazení v vnořený dotaz není zachována.</span><span class="sxs-lookup"><span data-stu-id="390a6-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="390a6-190">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="390a6-190">Identifiers</span></span>  
 <span data-ttu-id="390a6-191">V Transact-SQL porovnání identifikátorů je založena na řazení aktuální databáze.</span><span class="sxs-lookup"><span data-stu-id="390a6-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="390a6-192">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)]znaku jsou identifikátory vždy rozlišovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)] malá a velká písmena (to znamená rozlišování mezi znaky s diakritikou a znaky bez diakritiky; například "a" se nerovná znaku "a").</span><span class="sxs-lookup"><span data-stu-id="390a6-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-193">zachází s verzemi písmen, která vypadají stejně, ale jsou z různých znakových stránek jako různé znaky.</span><span class="sxs-lookup"><span data-stu-id="390a6-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="390a6-194">Další informace naleznete [v tématu Input Character Set](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="390a6-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="390a6-195">Funkce Transact-SQL nejsou v entitě SQL k dispozici</span><span class="sxs-lookup"><span data-stu-id="390a6-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="390a6-196">Následující funkce Transact-SQL není k [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dispozici v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="390a6-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="390a6-197">Dml</span><span class="sxs-lookup"><span data-stu-id="390a6-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-198">v současné době neposkytuje žádnou podporu pro příkazy DML (vložit, aktualizovat, odstranit).</span><span class="sxs-lookup"><span data-stu-id="390a6-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="390a6-199">Ddl</span><span class="sxs-lookup"><span data-stu-id="390a6-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-200">neposkytuje žádnou podporu pro DDL v aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="390a6-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="390a6-201">imperativní programování</span><span class="sxs-lookup"><span data-stu-id="390a6-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-202">neposkytuje žádnou podporu pro imperativní programování, na rozdíl od Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="390a6-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="390a6-203">Místo toho použijte programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="390a6-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="390a6-204">Seskupování funkcí</span><span class="sxs-lookup"><span data-stu-id="390a6-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-205">dosud neposkytuje podporu pro seskupování funkcí (například CUBE, ROLLUP a GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="390a6-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="390a6-206">Analytické funkce</span><span class="sxs-lookup"><span data-stu-id="390a6-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-207">(zatím) neposkytuje podporu analytických funkcí.</span><span class="sxs-lookup"><span data-stu-id="390a6-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="390a6-208">Vestavěné funkce, operátoři</span><span class="sxs-lookup"><span data-stu-id="390a6-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-209">podporuje podmnožinu vestavěných funkcí a operátorů Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="390a6-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="390a6-210">Tyto operátory a funkce budou pravděpodobně podporovány hlavními poskytovateli obchodů.</span><span class="sxs-lookup"><span data-stu-id="390a6-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-211">používá funkce specifické pro úložiště deklarované v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="390a6-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="390a6-212">Kromě toho entity framework umožňuje deklarovat integrované a uživatelem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] definované existující funkce úložiště pro použití.</span><span class="sxs-lookup"><span data-stu-id="390a6-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="390a6-213">Tipy</span><span class="sxs-lookup"><span data-stu-id="390a6-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-214">neposkytuje mechanismy pro rady při psaní dotazu.</span><span class="sxs-lookup"><span data-stu-id="390a6-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="390a6-215">Dávkování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="390a6-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-216">nepodporuje dávkování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="390a6-216">does not support batching query results.</span></span> <span data-ttu-id="390a6-217">Například následující je platný Transact-SQL (odesílání jako dávka):</span><span class="sxs-lookup"><span data-stu-id="390a6-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="390a6-218">Ekvivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] však není podporován:</span><span class="sxs-lookup"><span data-stu-id="390a6-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="390a6-219">podporuje pouze jeden příkaz dotazu vytvářející výsledky na příkaz.</span><span class="sxs-lookup"><span data-stu-id="390a6-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390a6-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="390a6-220">See also</span></span>

- [<span data-ttu-id="390a6-221">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="390a6-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="390a6-222">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="390a6-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
