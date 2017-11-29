---
title: "Generování příkazu SQL ze stromy příkazů – doporučené postupy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06d2711d9dac203645c127fa86581a9888db3cb1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="71c23-102">Generování příkazu SQL ze stromy příkazů – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="71c23-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="71c23-103">Stromy příkazů dotazu výstup úzce model dotazů v SQL vyjádřit kombinací.</span><span class="sxs-lookup"><span data-stu-id="71c23-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="71c23-104">Existují však určité běžné problémy pro zprostředkovatele zapisovače při generování SQL ze stromu příkazů výstupu.</span><span class="sxs-lookup"><span data-stu-id="71c23-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="71c23-105">Toto téma popisuje tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="71c23-105">This topic discusses these challenges.</span></span> <span data-ttu-id="71c23-106">V dalším tématu ukázkového zprostředkovatele ukazuje, jak vyřešit tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="71c23-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="71c23-107">Uzly od objektu DbExpression skupiny v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="71c23-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="71c23-108">Typické příkazu jazyka SQL má vnořené struktura následující tvar:</span><span class="sxs-lookup"><span data-stu-id="71c23-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="71c23-109">Jeden nebo více klauzulích může být prázdná.</span><span class="sxs-lookup"><span data-stu-id="71c23-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="71c23-110">Vnořené příkazu SELECT mohlo dojít v některém z řádků.</span><span class="sxs-lookup"><span data-stu-id="71c23-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="71c23-111">Možné překlad dotazu stromu příkazů do příkazu SQL SELECT vytvoří pro každou relační operátor jeden poddotazu.</span><span class="sxs-lookup"><span data-stu-id="71c23-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="71c23-112">Ale povede k nepotřebné vnořené poddotazy, které by bylo obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="71c23-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="71c23-113">V některých úložišť dat dotazu může být špatná.</span><span class="sxs-lookup"><span data-stu-id="71c23-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="71c23-114">Jako příklad zvažte následující strom příkazů dotazu</span><span class="sxs-lookup"><span data-stu-id="71c23-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="71c23-115">Neefektivní překlad byste mohli vytvořit:</span><span class="sxs-lookup"><span data-stu-id="71c23-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="71c23-116">Všimněte si, že každý uzel relační výraz se nové příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="71c23-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="71c23-117">Proto je důležité k agregaci tolik uzly výrazu nejdříve do jednoho příkazu SQL SELECT při zachování správnosti.</span><span class="sxs-lookup"><span data-stu-id="71c23-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="71c23-118">Výsledek takové agregace pro tento příklad popsané výše by byl:</span><span class="sxs-lookup"><span data-stu-id="71c23-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="71c23-119">Vyrovnání spojení v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="71c23-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="71c23-120">Jeden malá agregování více uzlů do jednoho příkazu SQL SELECT je agregování více výrazů spojení do jednoho příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="71c23-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="71c23-121">DbJoinExpression představuje jeden spojení mezi dvěma vstupy.</span><span class="sxs-lookup"><span data-stu-id="71c23-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="71c23-122">Ale v rámci jednoho příkazu SQL SELECT, je možné zadat více než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="71c23-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="71c23-123">V takovém případě spojení v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="71c23-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="71c23-124">Levé spojení spine, můžete snadno průmětu (spojení, které se zobrazují jako levé podřízenou jiné připojení) do jednoho příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="71c23-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="71c23-125">Zvažte například následující příkaz stromu dotazu:</span><span class="sxs-lookup"><span data-stu-id="71c23-125">For example, consider the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="71c23-126">To může být správně přeložit na:</span><span class="sxs-lookup"><span data-stu-id="71c23-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="71c23-127">Ale spine levé straně spojení nelze snadno vyrovnány a by se neměl pokoušet vyrovnání je.</span><span class="sxs-lookup"><span data-stu-id="71c23-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="71c23-128">Například spojení v následujícím dotazu příkaz stromové struktury:</span><span class="sxs-lookup"><span data-stu-id="71c23-128">For example, the joins in the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="71c23-129">By byl přeložen do příkazu SQL SELECT s poddotazu.</span><span class="sxs-lookup"><span data-stu-id="71c23-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="71c23-130">Vstupní Alias přesměrování</span><span class="sxs-lookup"><span data-stu-id="71c23-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="71c23-131">Chcete-li popisují vstupní alias přesměrování, zvažte strukturu relační výrazy, například DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, a DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="71c23-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="71c23-132">Každý z těchto typů má jednu nebo více vlastností vstup, které popisují vstupní kolekce a odpovídající každé vstupní proměnné vazby se používá k reprezentování každý prvek tento vstup při průchodu kolekce.</span><span class="sxs-lookup"><span data-stu-id="71c23-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="71c23-133">Tato proměnná vazbu se použije k odkazování na elementu vstupu, například v predikátu vlastnost DbFilterExpression nebo vlastnost projekce DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="71c23-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="71c23-134">Když může agregování další uzly relační výrazu do jednoho příkazu SQL SELECT a vyhodnocení vazby proměnné, která používá výraz, který je součástí relační výraz (například součást vlastnost projekce DbProjectExpression) není být stejný jako alias vstupu, jako by bylo víc vazeb výraz přesměrováni do jedné míry.</span><span class="sxs-lookup"><span data-stu-id="71c23-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="71c23-135">Tento problém se nazývá přejmenování alias.</span><span class="sxs-lookup"><span data-stu-id="71c23-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="71c23-136">Zvažte v prvním příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="71c23-136">Consider the first example in this topic.</span></span> <span data-ttu-id="71c23-137">Pokud to překlad naïve a překladu projekce a.x (DbPropertyExpression (a, x)), je správné přeloží ji do `a.x` protože máme alias vstupu jako "a" tak, aby odpovídaly vazba proměnné.</span><span class="sxs-lookup"><span data-stu-id="71c23-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="71c23-138">Ale při agregování oba uzly do jednoho příkazu SQL SELECT, budete muset překládat stejnou DbPropertyExpression do `b.x`, jako vstup byl alias s "b".</span><span class="sxs-lookup"><span data-stu-id="71c23-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="71c23-139">Připojení k vyrovnání Alias</span><span class="sxs-lookup"><span data-stu-id="71c23-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="71c23-140">Na rozdíl od libovolný jiný relační výraz ve stromu příkazů výstupu DbJoinExpression výstupy typem výsledku, který je řádek skládající se z dva sloupce, z nichž každý představuje jednu ze vstupních údajů.</span><span class="sxs-lookup"><span data-stu-id="71c23-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="71c23-141">Když DbPropertyExpresssion je sestavena pro přístup k skalární vlastnost pocházející z spojení, je nad jiné DbPropertyExpresssion.</span><span class="sxs-lookup"><span data-stu-id="71c23-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="71c23-142">Mezi příklady patří "a.b.y" v příkladu 2 a "b.c.y" v příkladu 3.</span><span class="sxs-lookup"><span data-stu-id="71c23-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="71c23-143">Ale v odpovídajících příkazů SQL tyto se označují jako "b.y".</span><span class="sxs-lookup"><span data-stu-id="71c23-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="71c23-144">Opětovná aliasy se nazývá vyrovnání alias spojení.</span><span class="sxs-lookup"><span data-stu-id="71c23-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="71c23-145">Název sloupce a míry Alias přejmenování</span><span class="sxs-lookup"><span data-stu-id="71c23-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="71c23-146">Pokud dotaz SQL SELECT, který má spojení má provést s projekci, při vytváření výčtu všech zúčastněných sloupců ze vstupních hodnot, může dojít, kolize názvů, jako více než jeden vstup může mít stejný název sloupce.</span><span class="sxs-lookup"><span data-stu-id="71c23-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="71c23-147">Použijte jiný název pro sloupec, aby se zabránilo kolizí.</span><span class="sxs-lookup"><span data-stu-id="71c23-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="71c23-148">Kromě toho po vyrovnání spojení, zúčastněných tabulky (nebo poddotazy) může být kolize aliasy ve kterém případ tyto potřeba přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="71c23-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="71c23-149">Vyhněte se vyberte *</span><span class="sxs-lookup"><span data-stu-id="71c23-149">Avoid SELECT *</span></span>  
 <span data-ttu-id="71c23-150">Nepoužívejte `SELECT *` k výběru ze základních tabulek.</span><span class="sxs-lookup"><span data-stu-id="71c23-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="71c23-151">V modelu úložiště [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace může obsahovat pouze podmnožinu sloupců, které jsou v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="71c23-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="71c23-152">V takovém případě `SELECT *` mohou poskytnout nesprávný výsledek.</span><span class="sxs-lookup"><span data-stu-id="71c23-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="71c23-153">Místo toho musíte zadat všechny sloupce zúčastněných s využitím názvy sloupců z výsledný typ zúčastněných výrazy.</span><span class="sxs-lookup"><span data-stu-id="71c23-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="71c23-154">Opakované použití výrazů</span><span class="sxs-lookup"><span data-stu-id="71c23-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="71c23-155">Výrazy mohou být znovu použity ve stromu příkaz dotazu předaná [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71c23-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="71c23-156">Nepředpokládejte, že každý výraz zobrazí pouze jednou v dotazu strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="71c23-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="71c23-157">Mapování primitivní typy</span><span class="sxs-lookup"><span data-stu-id="71c23-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="71c23-158">Při mapování typů koncepční (EDM) na typy zprostředkovatele, by měl namapujte nejširší typ (Int32) tak, aby vyhovovaly všech možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="71c23-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="71c23-159">Vyhněte se také, mapování na typy, které nelze použít u mnoha operací, jako jsou typy objektů BLOB (například `ntext` v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="71c23-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c23-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="71c23-160">See Also</span></span>  
 [<span data-ttu-id="71c23-161">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="71c23-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
