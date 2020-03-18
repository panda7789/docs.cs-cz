---
title: Základní operace dotazů LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635935"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="d8b23-102">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d8b23-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="d8b23-103">Toto téma poskytuje stručný úvod do výrazy dotazu LINQ a některé typické druhy operací, které provádíte v dotazu.</span><span class="sxs-lookup"><span data-stu-id="d8b23-103">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="d8b23-104">Podrobnější informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="d8b23-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="d8b23-105">Výrazy dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="d8b23-105">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="d8b23-106">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="d8b23-106">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="d8b23-107">Návod: Psaní dotazů v C #</span><span class="sxs-lookup"><span data-stu-id="d8b23-107">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="d8b23-108">Pokud již znáte dotazovací jazyk, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit.</span><span class="sxs-lookup"><span data-stu-id="d8b23-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="d8b23-109">Přečtěte si`from` o "klauzuli" v další části se dozvíte o pořadí klauzulí ve výrazech dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="d8b23-109">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="d8b23-110">Získání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="d8b23-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="d8b23-111">V dotazu LINQ je prvním krokem určení zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d8b23-111">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="d8b23-112">V jazyce C# jako ve většině programovacích jazyků musí být proměnná deklarována před použitím.</span><span class="sxs-lookup"><span data-stu-id="d8b23-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="d8b23-113">V dotazu LINQ `from` je klauzule na prvním místě, aby bylo možné zavést zdroj dat (`customers`) a *proměnnou rozsahu* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="d8b23-113">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="d8b23-114">Proměnná rozsahu je jako iterace proměnné ve smyčce s tím rozdílem, `foreach` že žádná skutečná iterace dochází ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d8b23-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="d8b23-115">Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz `customers`na každý následující prvek v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="d8b23-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="d8b23-116">Vzhledem k tomu, že `cust`kompilátor můžete odvodit typ , není nutné zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="d8b23-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="d8b23-117">Další proměnné rozsahu mohou být `let` zavedeny klauzulí.</span><span class="sxs-lookup"><span data-stu-id="d8b23-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="d8b23-118">Další informace naleznete v tématu [let klauzule](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-118">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8b23-119">Pro neobecné zdroje dat, jako <xref:System.Collections.ArrayList>je například proměnná rozsahu, musí být explicitně zadána.</span><span class="sxs-lookup"><span data-stu-id="d8b23-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="d8b23-120">Další informace naleznete v [tématu Jak dotaz ArrayList s LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) a [z klauzule](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-120">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="d8b23-121">Filtrování</span><span class="sxs-lookup"><span data-stu-id="d8b23-121">Filtering</span></span>  
 <span data-ttu-id="d8b23-122">Pravděpodobně nejběžnější operace dotazu je použít filtr ve formě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="d8b23-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="d8b23-123">Filtr způsobí, že dotaz vrátí pouze ty prvky, pro které je výraz pravdivý.</span><span class="sxs-lookup"><span data-stu-id="d8b23-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="d8b23-124">Výsledek je vytvořen pomocí `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d8b23-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="d8b23-125">Filtr v platnost určuje, které prvky vyloučit ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="d8b23-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="d8b23-126">V následujícím příkladu `customers` jsou vráceny pouze ty, kteří mají adresu v Londýně.</span><span class="sxs-lookup"><span data-stu-id="d8b23-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="d8b23-127">Můžete použít známé C# `AND` `OR` logické a operátory použít tolik výrazy filtru podle potřeby v klauzuli. `where`</span><span class="sxs-lookup"><span data-stu-id="d8b23-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="d8b23-128">Chcete-li například vrátit pouze `AND` zákazníky z "Londýna", jehož název je "Devon", napíšete následující kód:</span><span class="sxs-lookup"><span data-stu-id="d8b23-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="d8b23-129">Chcete-li vrátit zákazníkům z Londýna nebo Paříže, napište následující kód:</span><span class="sxs-lookup"><span data-stu-id="d8b23-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="d8b23-130">Další informace naleznete v tématu [where clause](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-130">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="d8b23-131">Řazení</span><span class="sxs-lookup"><span data-stu-id="d8b23-131">Ordering</span></span>  
 <span data-ttu-id="d8b23-132">Často je vhodné seřadit vrácená data.</span><span class="sxs-lookup"><span data-stu-id="d8b23-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="d8b23-133">Klauzule `orderby` způsobí, že prvky ve vrácené sekvenci budou seřazeny podle výchozího porovnávání pro typ, který je seřazen.</span><span class="sxs-lookup"><span data-stu-id="d8b23-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="d8b23-134">Například následující dotaz lze rozšířit seřadit výsledky `Name` na základě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d8b23-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="d8b23-135">Protože `Name` je řetězec, výchozí porovnávání provádí abecední řazení od A do Z.</span><span class="sxs-lookup"><span data-stu-id="d8b23-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="d8b23-136">Chcete-li výsledky seřadit v opačném pořadí `orderby…descending` od Z do A, použijte klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d8b23-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="d8b23-137">Další informace naleznete v [tématu orderby klauzule](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-137">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="d8b23-138">Seskupování</span><span class="sxs-lookup"><span data-stu-id="d8b23-138">Grouping</span></span>  
 <span data-ttu-id="d8b23-139">Klauzule `group` umožňuje seskupit výsledky na základě zadaného klíče.</span><span class="sxs-lookup"><span data-stu-id="d8b23-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="d8b23-140">Můžete například určit, že výsledky by `City` měly být seskupeny tak, aby všichni zákazníci z Londýna nebo Paříže byli v jednotlivých skupinách.</span><span class="sxs-lookup"><span data-stu-id="d8b23-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="d8b23-141">V tomto `cust.City` případě je klíč.</span><span class="sxs-lookup"><span data-stu-id="d8b23-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="d8b23-142">Když dotaz ukončíte `group` klauzulí, budou mít výsledky podobu seznamu seznamů.</span><span class="sxs-lookup"><span data-stu-id="d8b23-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="d8b23-143">Každý prvek v seznamu je objekt, který má `Key` člen a seznam prvků, které jsou seskupeny pod tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="d8b23-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="d8b23-144">Při itetu přes dotaz, který vytváří posloupnost skupin, `foreach` je nutné použít vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="d8b23-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="d8b23-145">Vnější smyčka iterát přes každou skupinu a vnitřní smyčka iterates nad členy každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="d8b23-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="d8b23-146">Pokud je nutné odkazovat na výsledky operace skupiny, můžete použít `into` klíčové slovo k vytvoření identifikátoru, který lze dále dotazovat.</span><span class="sxs-lookup"><span data-stu-id="d8b23-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="d8b23-147">Následující dotaz vrátí pouze ty skupiny, které obsahují více než dva zákazníky:</span><span class="sxs-lookup"><span data-stu-id="d8b23-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="d8b23-148">Další informace naleznete v tématu [group clause](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-148">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="d8b23-149">Připojení</span><span class="sxs-lookup"><span data-stu-id="d8b23-149">Joining</span></span>  
 <span data-ttu-id="d8b23-150">Operace spojení vytvářejí přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat.</span><span class="sxs-lookup"><span data-stu-id="d8b23-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="d8b23-151">Můžete například provést spojení a najít všechny zákazníky a distributory, kteří mají stejné umístění.</span><span class="sxs-lookup"><span data-stu-id="d8b23-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="d8b23-152">V LINQ `join` klauzule vždy pracuje proti kolekce objektů namísto tabulky databáze přímo.</span><span class="sxs-lookup"><span data-stu-id="d8b23-152">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="d8b23-153">V LINQ není třeba používat `join` tak často jako v SQL, protože cizí klíče v LINQ jsou reprezentovány v objektovém modelu jako vlastnosti, které drží kolekci položek.</span><span class="sxs-lookup"><span data-stu-id="d8b23-153">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="d8b23-154">Například `Customer` objekt obsahuje kolekci `Order` objektů.</span><span class="sxs-lookup"><span data-stu-id="d8b23-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="d8b23-155">Místo provedení spojení přistupujete k příkazům pomocí tečkového zápisu:</span><span class="sxs-lookup"><span data-stu-id="d8b23-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="d8b23-156">Další informace naleznete v tématu [join clause](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-156">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="d8b23-157">Výběr (projekce)</span><span class="sxs-lookup"><span data-stu-id="d8b23-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="d8b23-158">Klauzule `select` vytváří výsledky dotazu a určuje "tvar" nebo typ každého vráceného prvku.</span><span class="sxs-lookup"><span data-stu-id="d8b23-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="d8b23-159">Můžete například určit, zda se výsledky `Customer` budou skládat z úplných objektů, pouze jednoho člena, podmnožiny členů nebo zcela jiného typu výsledku na základě výpočtu nebo vytvoření nového objektu.</span><span class="sxs-lookup"><span data-stu-id="d8b23-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="d8b23-160">Když `select` klauzule vytvoří něco jiného než kopii zdrojového prvku, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="d8b23-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="d8b23-161">Použití projekce k transformaci dat je výkonné schopnosti výrazů dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="d8b23-161">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="d8b23-162">Další informace naleznete [v tématu transformace dat s LINQ (C#)](./data-transformations-with-linq.md) a [select klauzule](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d8b23-162">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b23-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8b23-163">See also</span></span>

- [<span data-ttu-id="d8b23-164">Výrazy dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="d8b23-164">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="d8b23-165">Návod: Psaní dotazů v C #</span><span class="sxs-lookup"><span data-stu-id="d8b23-165">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="d8b23-166">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d8b23-166">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="d8b23-167">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d8b23-167">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
