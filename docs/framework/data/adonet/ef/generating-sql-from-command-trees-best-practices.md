---
title: Generování SQL ze stromů příkazů – osvědčené postupy
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 9859c7df941ae6681c991001e0d1e5a50c7ffc60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855013"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="c55b1-102">Generování SQL ze stromů příkazů – osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="c55b1-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="c55b1-103">Ve stromových strukturách příkazů pro výstup dotazu jsou dotazy vyhodnotit v SQL.</span><span class="sxs-lookup"><span data-stu-id="c55b1-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="c55b1-104">Existují však některé běžné výzvy pro zapisovače poskytovatele při generování SQL z výstupního stromu příkazů.</span><span class="sxs-lookup"><span data-stu-id="c55b1-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="c55b1-105">Toto téma popisuje tyto výzvy.</span><span class="sxs-lookup"><span data-stu-id="c55b1-105">This topic discusses these challenges.</span></span> <span data-ttu-id="c55b1-106">V dalším tématu poskytovatel ukázkových řešení ukazuje, jak tyto výzvy vyřešit.</span><span class="sxs-lookup"><span data-stu-id="c55b1-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="c55b1-107">Seskupení uzlů DbExpression v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="c55b1-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="c55b1-108">Typický příkaz SQL má vnořenou strukturu následujícího tvaru:</span><span class="sxs-lookup"><span data-stu-id="c55b1-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="c55b1-109">Jedna nebo více klauzulí může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="c55b1-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="c55b1-110">Vnořený příkaz SELECT může nastat v některém z řádků.</span><span class="sxs-lookup"><span data-stu-id="c55b1-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="c55b1-111">Možný převod stromu příkazů dotazu na příkaz SQL SELECT by vytvořil jeden poddotaz pro každý relační operátor.</span><span class="sxs-lookup"><span data-stu-id="c55b1-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="c55b1-112">To by ale vedlo k zbytečným vnořeným poddotazům, které by bylo obtížné přečíst.</span><span class="sxs-lookup"><span data-stu-id="c55b1-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="c55b1-113">V některých úložištích dat může dotaz fungovat špatně.</span><span class="sxs-lookup"><span data-stu-id="c55b1-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="c55b1-114">Podívejte se například na následující strom příkazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="c55b1-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="c55b1-115">Neefektivní překlad by vytvořil:</span><span class="sxs-lookup"><span data-stu-id="c55b1-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="c55b1-116">Všimněte si, že každý uzel relačních výrazů se stal novým příkazem SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="c55b1-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="c55b1-117">Proto je důležité agregovat co nejvíce uzlů výrazů do jednoho příkazu SELECT jazyka SQL a přitom zachovat správnost.</span><span class="sxs-lookup"><span data-stu-id="c55b1-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="c55b1-118">Výsledek takové agregace pro příklad uvedený výše by byl:</span><span class="sxs-lookup"><span data-stu-id="c55b1-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="c55b1-119">Sloučit spojení v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="c55b1-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="c55b1-120">Jeden případ agregace více uzlů do jednoho příkazu SELECT SQL sestaví více výrazů JOIN do jednoho příkazu SELECT jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c55b1-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="c55b1-121">DbJoinExpression představuje jedno spojení mezi dvěma vstupy.</span><span class="sxs-lookup"><span data-stu-id="c55b1-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="c55b1-122">V rámci jednoho příkazu SELECT jazyka SQL je však možné zadat více než jedno spojení.</span><span class="sxs-lookup"><span data-stu-id="c55b1-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="c55b1-123">V takovém případě se spojení provádějí v zadaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c55b1-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="c55b1-124">Spojení s levou hřbetou, (spojení, která se zobrazují jako levý podřízený objekt jiného spojení), lze snadněji sloučit do jednoho příkazu SELECT jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c55b1-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="c55b1-125">Zvažte například následující strom příkazů dotazu:</span><span class="sxs-lookup"><span data-stu-id="c55b1-125">For example, consider the following query command tree:</span></span>

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="c55b1-126">To se dá správně přeložit na:</span><span class="sxs-lookup"><span data-stu-id="c55b1-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="c55b1-127">Spojení páteře bez levého hřbetu ale nejdou snadno sloučit a neměli byste je slučovat.</span><span class="sxs-lookup"><span data-stu-id="c55b1-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="c55b1-128">Například spojení v následujícím stromu příkazů dotazu:</span><span class="sxs-lookup"><span data-stu-id="c55b1-128">For example, the joins in the following query command tree:</span></span>

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="c55b1-129">By byl přeložen na příkaz jazyka SQL SELECT s poddotazem.</span><span class="sxs-lookup"><span data-stu-id="c55b1-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="c55b1-130">Přesměrování vstupního aliasu</span><span class="sxs-lookup"><span data-stu-id="c55b1-130">Input Alias Redirecting</span></span>

<span data-ttu-id="c55b1-131">Chcete-li vysvětlovat přesměrování vstupu aliasu, zvažte strukturu relačních výrazů, například DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupAggregate, argumenty DbApplyExpression pro a DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="c55b1-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="c55b1-132">Každý z těchto typů má jednu nebo více vstupních vlastností popisujících vstupní kolekci a proměnná vazby odpovídající jednotlivým vstupům slouží k reprezentaci každého prvku daného vstupu během průchodu kolekcí.</span><span class="sxs-lookup"><span data-stu-id="c55b1-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="c55b1-133">Proměnná vazby se používá při odkazování na element input, například ve vlastnosti predikátu DbFilterExpression nebo vlastnosti projekce třídy DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="c55b1-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="c55b1-134">Při agregaci dalších uzlů relačních výrazů do jednoho příkazu SELECT jazyka SQL a vyhodnocení výrazu, který je součástí relačního výrazu (například část vlastnosti projekce DbProjectExpression), kterou proměnnou vazby může používat. nesmí být stejný jako alias vstupu, protože vícenásobné vazby výrazů by musely být přesměrovány do jednoho rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c55b1-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="c55b1-135">Tento problém se nazývá přejmenování aliasu.</span><span class="sxs-lookup"><span data-stu-id="c55b1-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="c55b1-136">Vezměte v úvahu první příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c55b1-136">Consider the first example in this topic.</span></span> <span data-ttu-id="c55b1-137">Pokud se provádí překlad Naive a překlad projekce a. x (DbPropertyExpression (a, x)), je správné ho přeložit do `a.x` , protože máme alias vstupu jako "a", aby se shodoval s proměnnou vazby.</span><span class="sxs-lookup"><span data-stu-id="c55b1-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="c55b1-138">Při agregaci uzlů do jednoho příkazu SELECT SQL je však nutné přeložit stejný DbPropertyExpression do `b.x`, protože vstup byl aliasem "b".</span><span class="sxs-lookup"><span data-stu-id="c55b1-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="c55b1-139">Spojit sloučení aliasů</span><span class="sxs-lookup"><span data-stu-id="c55b1-139">Join Alias Flattening</span></span>

<span data-ttu-id="c55b1-140">Na rozdíl od jakéhokoli jiného relačního výrazu ve stromové struktuře příkazu OUTPUT DbJoinExpression vypíše výsledný typ, který je řádek sestávající ze dvou sloupců, z nichž každý odpovídá jednomu ze vstupů.</span><span class="sxs-lookup"><span data-stu-id="c55b1-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="c55b1-141">Když je DbPropertyExpression sestaven pro přístup k skalární vlastnosti pocházející z JOIN, je nad jinou DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="c55b1-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="c55b1-142">Mezi příklady patří "a. b. y" v příkladu 2 a "b. c. y" v příkladu 3.</span><span class="sxs-lookup"><span data-stu-id="c55b1-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="c55b1-143">V odpovídajících příkazech SQL se však říká "b. y".</span><span class="sxs-lookup"><span data-stu-id="c55b1-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="c55b1-144">Tento opakovaný alias se nazývá sloučení aliasů spojování.</span><span class="sxs-lookup"><span data-stu-id="c55b1-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="c55b1-145">Název sloupce a přejmenování aliasu rozsahu</span><span class="sxs-lookup"><span data-stu-id="c55b1-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="c55b1-146">Pokud je dotaz SELECT SQL, který má spojení, dokončen s projekcí, při vytváření výčtu všech zúčastněných sloupců ze vstupů může dojít ke kolizi názvů, protože více než jeden vstup může mít stejný název sloupce.</span><span class="sxs-lookup"><span data-stu-id="c55b1-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="c55b1-147">Chcete-li se vyhnout kolizi, použijte jiný název sloupce.</span><span class="sxs-lookup"><span data-stu-id="c55b1-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="c55b1-148">Také při sloučení spojení mohou mít zúčastněné tabulky (nebo poddotazy) kolizi s aliasy, v takovém případě je třeba je přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="c55b1-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="c55b1-149">Vyhněte se výběru \*</span><span class="sxs-lookup"><span data-stu-id="c55b1-149">Avoid SELECT \*</span></span>

<span data-ttu-id="c55b1-150">Nepoužívejte `SELECT *` k výběru ze základních tabulek.</span><span class="sxs-lookup"><span data-stu-id="c55b1-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="c55b1-151">Model úložiště v aplikaci Entity Framework může obsahovat jenom podmnožinu sloupců, které se nacházejí v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="c55b1-151">The storage model in an Entity Framework application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="c55b1-152">V takovém případě `SELECT *` může způsobit nesprávný výsledek.</span><span class="sxs-lookup"><span data-stu-id="c55b1-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="c55b1-153">Místo toho byste měli zadat všechny účastnící se sloupce pomocí názvů sloupců z výsledného typu výrazů, které se účastní.</span><span class="sxs-lookup"><span data-stu-id="c55b1-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="c55b1-154">Opakované použití výrazů</span><span class="sxs-lookup"><span data-stu-id="c55b1-154">Reuse of Expressions</span></span>

<span data-ttu-id="c55b1-155">Výrazy se můžou znovu použít ve stromu příkazů dotazu, který předává Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c55b1-155">Expressions may be reused in the query command tree passed by the Entity Framework.</span></span> <span data-ttu-id="c55b1-156">Nepředpokládáme, že se každý výraz ve stromu příkazů dotazu vyskytuje jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="c55b1-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="c55b1-157">Mapování primitivních typů</span><span class="sxs-lookup"><span data-stu-id="c55b1-157">Mapping Primitive Types</span></span>

<span data-ttu-id="c55b1-158">Při mapování koncepčních typů (EDM) na typy poskytovatelů byste měli mapovat na nejširší typ (Int32) tak, aby se všechny možné hodnoty vešly.</span><span class="sxs-lookup"><span data-stu-id="c55b1-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="c55b1-159">Nepoužívejte také mapování na typy, které nelze použít pro mnoho operací, jako jsou typy objektů BLOB (například `ntext` v SQL Server).</span><span class="sxs-lookup"><span data-stu-id="c55b1-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="c55b1-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c55b1-160">See also</span></span>

- [<span data-ttu-id="c55b1-161">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="c55b1-161">SQL Generation</span></span>](sql-generation.md)
