---
title: Generování SQL ze stromů příkazů – osvědčené postupy
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 476a2b9d6d3a8efb6094afce0143abed765bdb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659092"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="709d2-102">Generování SQL ze stromů příkazů – osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="709d2-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="709d2-103">Stromy příkazů výstup dotazu věrně modelovala dotazů v SQL anyAttribute.</span><span class="sxs-lookup"><span data-stu-id="709d2-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="709d2-104">Existují však některé běžné problémy pro zprostředkovatele modulů pro zápis při generování SQL ze strom výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="709d2-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="709d2-105">Toto téma popisuje tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="709d2-105">This topic discusses these challenges.</span></span> <span data-ttu-id="709d2-106">V dalším tématu se zprostředkovateli ukázek ukazuje, jak tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="709d2-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="709d2-107">Seskupování uzlů DbExpression v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="709d2-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="709d2-108">Typické příkaz jazyka SQL má vnořené struktury následujícím tvaru:</span><span class="sxs-lookup"><span data-stu-id="709d2-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="709d2-109">Jednu či více klauzulí může být prázdný.</span><span class="sxs-lookup"><span data-stu-id="709d2-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="709d2-110">Vnořený příkaz SELECT může dojít v žádném z řádků.</span><span class="sxs-lookup"><span data-stu-id="709d2-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="709d2-111">Je to možné překlad dotazu stromu příkazů do příkazu SQL SELECT byste mohli vytvořit jeden poddotaz pro každý relační operátor.</span><span class="sxs-lookup"><span data-stu-id="709d2-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="709d2-112">Nicméně, které by mohlo dojít k zbytečné vnořené poddotazy, které by bylo obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="709d2-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="709d2-113">Na některá úložiště dat může provést dotaz špatně.</span><span class="sxs-lookup"><span data-stu-id="709d2-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="709d2-114">Jako příklad zvažte následující stromu příkazů dotazů</span><span class="sxs-lookup"><span data-stu-id="709d2-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="709d2-115">Neefektivní překlad byste mohli vytvořit:</span><span class="sxs-lookup"><span data-stu-id="709d2-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="709d2-116">Všimněte si, že každý uzel relační výraz stane nový příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="709d2-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="709d2-117">Proto je potřeba agregovat tolik uzly výrazu nejdříve do jednoho příkazu SQL SELECT při zachování správnosti.</span><span class="sxs-lookup"><span data-stu-id="709d2-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="709d2-118">Výsledkem těchto agregace pro příklad uvedený výše by byl:</span><span class="sxs-lookup"><span data-stu-id="709d2-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="709d2-119">Sloučit spojení v příkazu SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="709d2-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="709d2-120">Jeden případ agregaci více uzlů do jednoho příkazu SQL SELECT je agregovat více spojení výrazů do jednoho příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="709d2-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="709d2-121">DbJoinExpression představuje jeden spojení mezi dvěma vstupy.</span><span class="sxs-lookup"><span data-stu-id="709d2-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="709d2-122">Ale v rámci jednoho příkazu SQL SELECT, je možné zadat více než jedno spojení.</span><span class="sxs-lookup"><span data-stu-id="709d2-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="709d2-123">V takovém případě spojení jsou prováděny v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="709d2-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="709d2-124">Spine spojení LEFT, můžete snadněji sloučí (spojení, které se zobrazují jako levého potomka jiného spojení) do jednoho příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="709d2-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="709d2-125">Představte si třeba následující příkaz stromu dotazu:</span><span class="sxs-lookup"><span data-stu-id="709d2-125">For example, consider the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="709d2-126">To může být správně přeloženy do:</span><span class="sxs-lookup"><span data-stu-id="709d2-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="709d2-127">Však-levé straně spine spojení nelze snadno sloučí a by se neměl pokoušet linearizace.</span><span class="sxs-lookup"><span data-stu-id="709d2-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="709d2-128">Například příkaz spojení do ní následující dotaz stromu:</span><span class="sxs-lookup"><span data-stu-id="709d2-128">For example, the joins in the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="709d2-129">By byl přeložen na příkazu SQL SELECT s poddotazu.</span><span class="sxs-lookup"><span data-stu-id="709d2-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="709d2-130">Vstupní Alias přesměrování</span><span class="sxs-lookup"><span data-stu-id="709d2-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="709d2-131">Abychom vysvětlili, přesměrování vstupní alias, vezměte v úvahu struktura relační výrazy, jako je například DbFilterExpression DbProjectExpression, objekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, Dbgroupaggregate, objektu DbApplyExpression, a DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="709d2-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="709d2-132">Každý z těchto typů má jednu nebo více vlastností vstup, které popisují vstupní kolekce a odpovídající pro každý vstupní vazby proměnné se používá k reprezentaci všech prvků objektu vstup během procházení kolekce.</span><span class="sxs-lookup"><span data-stu-id="709d2-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="709d2-133">Proměnné vazby se používá k odkazování na element input, například v predikátu vlastnost DbFilterExpression nebo vlastnost projekce DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="709d2-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="709d2-134">Když může agregaci více uzlů relační výraz do jednoho příkazu SQL SELECT a vyhodnocení výrazu, který je součástí výrazu relační (například část vlastnosti projekce DbProjectExpression) proměnné vazby, kterou používá nesmí být stejný jako alias vstupu, jak víc vazeb výrazu musel být přesměrováno do jedné míry.</span><span class="sxs-lookup"><span data-stu-id="709d2-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="709d2-135">Tento problém se nazývá přejmenování alias.</span><span class="sxs-lookup"><span data-stu-id="709d2-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="709d2-136">Podívejte se na první příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="709d2-136">Consider the first example in this topic.</span></span> <span data-ttu-id="709d2-137">Pokud se tím překlad naivní a překladu a.x projekce (DbPropertyExpression (a, x)), je správné a přeloží ji do `a.x` máme alias vstupu jako "a" tak, aby odpovídaly vazby proměnné.</span><span class="sxs-lookup"><span data-stu-id="709d2-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="709d2-138">Ale při agregování obou uzlů v jediném příkazu SQL SELECT, budete muset překládat stejnou DbPropertyExpression do `b.x`, jako vstup byl vytvořen alias s "b".</span><span class="sxs-lookup"><span data-stu-id="709d2-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="709d2-139">Připojte se k vyrovnání Alias</span><span class="sxs-lookup"><span data-stu-id="709d2-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="709d2-140">Na rozdíl od libovolný jiný relační výraz ve výstupu příkazu stromu DbJoinExpression Vypíše typ výsledku, který je řádek skládající se z dva sloupce, z nichž každý představuje jednu ze vstupů.</span><span class="sxs-lookup"><span data-stu-id="709d2-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="709d2-141">Při vytváření DbPropertyExpresssion pro přístup k skalární vlastnost pocházející z spojení, je prostřednictvím jiného DbPropertyExpresssion.</span><span class="sxs-lookup"><span data-stu-id="709d2-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="709d2-142">Mezi příklady patří "a.b.y" v příkladu 2 a "b.c.y" v příkladu 3.</span><span class="sxs-lookup"><span data-stu-id="709d2-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="709d2-143">Ale v odpovídajících příkazů SQL tyto jsou označovány jako "b.y".</span><span class="sxs-lookup"><span data-stu-id="709d2-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="709d2-144">Re aliasy se nazývá spojení sloučení alias.</span><span class="sxs-lookup"><span data-stu-id="709d2-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="709d2-145">Název sloupce a míry Alias přejmenování</span><span class="sxs-lookup"><span data-stu-id="709d2-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="709d2-146">Pokud je dotaz SQL SELECT, který obsahuje spojení dokončit projekce, při vytváření výčtu všech zúčastněných sloupců ze vstupů, kolize názvů může dojít, jako více než jeden vstup může mít stejný název sloupce.</span><span class="sxs-lookup"><span data-stu-id="709d2-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="709d2-147">Použijte jiný název sloupce, aby se zabránilo kolize.</span><span class="sxs-lookup"><span data-stu-id="709d2-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="709d2-148">Navíc při sloučení spojení, tabulky (nebo poddotazy) může mít kolize aliasy ve které malá a velká tyto nutné přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="709d2-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="709d2-149">Vyhněte se vybrat \*</span><span class="sxs-lookup"><span data-stu-id="709d2-149">Avoid SELECT \*</span></span>  
 <span data-ttu-id="709d2-150">Nepoužívejte `SELECT *` k výběru ze základních tabulek.</span><span class="sxs-lookup"><span data-stu-id="709d2-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="709d2-151">V modelu úložiště [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace může obsahovat pouze podmnožinu sloupců, které jsou v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="709d2-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="709d2-152">V takovém případě `SELECT *` může způsobit nesprávný výsledek.</span><span class="sxs-lookup"><span data-stu-id="709d2-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="709d2-153">Místo toho měli byste určit všechny zúčastněné sloupce s použitím názvy sloupců z typ výsledku zúčastněných výrazů.</span><span class="sxs-lookup"><span data-stu-id="709d2-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="709d2-154">Opakované použití výrazů</span><span class="sxs-lookup"><span data-stu-id="709d2-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="709d2-155">Výrazy mohou být znovu použity ve stromu příkazů dotazů předávány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="709d2-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="709d2-156">Nepředpokládejte, že každý výraz se vyskytuje jenom jednou v dotazu strom příkazů.</span><span class="sxs-lookup"><span data-stu-id="709d2-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="709d2-157">Mapování primitivní typy</span><span class="sxs-lookup"><span data-stu-id="709d2-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="709d2-158">Při mapování typů koncepční (EDM) na poskytovatele typů, byste měli namapovat na nejširší typ (Int32) tak, aby se vešly všechny možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="709d2-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="709d2-159">Navíc neměla být mapování pro typy, které nelze použít pro mnoho operací, jako jsou typy objektů BLOB (například `ntext` v systému SQL Server).</span><span class="sxs-lookup"><span data-stu-id="709d2-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709d2-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="709d2-160">See also</span></span>
- [<span data-ttu-id="709d2-161">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="709d2-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
