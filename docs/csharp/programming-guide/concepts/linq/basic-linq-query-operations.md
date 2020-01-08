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
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635935"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="96ee2-102">Základní operace dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="96ee2-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="96ee2-103">Toto téma poskytuje stručný úvod do výrazů LINQ Query a některé z typických typů operací, které v dotazu provedete.</span><span class="sxs-lookup"><span data-stu-id="96ee2-103">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="96ee2-104">Podrobnější informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="96ee2-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="96ee2-105">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="96ee2-105">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="96ee2-106">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="96ee2-106">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="96ee2-107">Návod: zápis dotazů vC#</span><span class="sxs-lookup"><span data-stu-id="96ee2-107">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="96ee2-108">Pokud už jste obeznámeni s dotazovacím jazykem, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit.</span><span class="sxs-lookup"><span data-stu-id="96ee2-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="96ee2-109">Přečtěte si o klauzuli`from` v další části, kde se dozvíte o pořadí klauzulí ve výrazech dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="96ee2-109">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="96ee2-110">Získání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="96ee2-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="96ee2-111">V dotazu LINQ je prvním krokem určení zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="96ee2-111">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="96ee2-112">V C# nástroji as ve většině programovacích jazyků musí být před použitím deklarována proměnná.</span><span class="sxs-lookup"><span data-stu-id="96ee2-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="96ee2-113">V dotazu LINQ je klauzule `from` první, aby se zavedl zdroj dat (`customers`) a *Proměnná rozsahu* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="96ee2-113">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="96ee2-114">Proměnná rozsahu je stejná jako proměnná iterace ve smyčce `foreach`, s tím rozdílem, že ve výrazu dotazu nedochází k žádným skutečným iteracím.</span><span class="sxs-lookup"><span data-stu-id="96ee2-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="96ee2-115">Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz na každý následný prvek v `customers`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="96ee2-116">Protože kompilátor může odvodit typ `cust`, nemusíte ho explicitně určovat.</span><span class="sxs-lookup"><span data-stu-id="96ee2-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="96ee2-117">Další proměnné rozsahu mohou být zavedeny klauzulí `let`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="96ee2-118">Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-118">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96ee2-119">U neobecných zdrojů dat, jako je například <xref:System.Collections.ArrayList>, musí být proměnná rozsahu explicitně typu.</span><span class="sxs-lookup"><span data-stu-id="96ee2-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="96ee2-120">Další informace najdete v tématu [Postup dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) a [klauzule FROM](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-120">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="96ee2-121">Filtrování</span><span class="sxs-lookup"><span data-stu-id="96ee2-121">Filtering</span></span>  
 <span data-ttu-id="96ee2-122">Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="96ee2-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="96ee2-123">Filtr způsobí, že dotaz vrátí pouze prvky, pro které je výraz pravdivý.</span><span class="sxs-lookup"><span data-stu-id="96ee2-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="96ee2-124">Výsledek je vytvořen pomocí klauzule `where`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="96ee2-125">Filtr v důsledku určuje, které prvky mají být vyloučeny ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="96ee2-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="96ee2-126">V následujícím příkladu jsou vráceny pouze `customers`, kteří mají adresu v Londýně.</span><span class="sxs-lookup"><span data-stu-id="96ee2-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="96ee2-127">Pomocí známých C# logických `AND` a operátorů `OR` můžete použít libovolný počet výrazů filtru podle potřeby v klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="96ee2-128">Pokud například chcete vracet pouze zákazníky z "Londýn" `AND` jejichž název je "Devon", měli byste napsat následující kód:</span><span class="sxs-lookup"><span data-stu-id="96ee2-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="96ee2-129">Pokud chcete vracet zákazníky z Brna nebo Paříž, napište následující kód:</span><span class="sxs-lookup"><span data-stu-id="96ee2-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="96ee2-130">Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-130">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="96ee2-131">Řazení</span><span class="sxs-lookup"><span data-stu-id="96ee2-131">Ordering</span></span>  
 <span data-ttu-id="96ee2-132">Často je vhodné řazení vrácených dat.</span><span class="sxs-lookup"><span data-stu-id="96ee2-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="96ee2-133">Klauzule `orderby` způsobí, že prvky v vrácené sekvenci budou seřazeny podle výchozí porovnávací metody pro typ, který se seřadí.</span><span class="sxs-lookup"><span data-stu-id="96ee2-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="96ee2-134">Například následující dotaz lze rozšířit pro řazení výsledků na základě vlastnosti `Name`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="96ee2-135">Vzhledem k tomu, že `Name` je řetězec, výchozí porovnávání provede abecední řazení z A do Z.</span><span class="sxs-lookup"><span data-stu-id="96ee2-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="96ee2-136">Pro seřazení výsledků v opačném pořadí z Z na a použijte klauzuli `orderby…descending`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="96ee2-137">Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-137">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="96ee2-138">Seskupování</span><span class="sxs-lookup"><span data-stu-id="96ee2-138">Grouping</span></span>  
 <span data-ttu-id="96ee2-139">Klauzule `group` umožňuje seskupit výsledky podle zadaného klíče.</span><span class="sxs-lookup"><span data-stu-id="96ee2-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="96ee2-140">Můžete například určit, že by měly být výsledky seskupené podle `City` tak, že všichni zákazníci z Londýna nebo Paříž jsou v jednotlivých skupinách.</span><span class="sxs-lookup"><span data-stu-id="96ee2-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="96ee2-141">V tomto případě je `cust.City` klíč.</span><span class="sxs-lookup"><span data-stu-id="96ee2-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="96ee2-142">Když ukončíte dotaz s klauzulí `group`, vaše výsledky budou mít formu seznamu seznamů.</span><span class="sxs-lookup"><span data-stu-id="96ee2-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="96ee2-143">Každý prvek v seznamu je objekt, který má `Key` člen a seznam elementů, které jsou seskupeny pod tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="96ee2-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="96ee2-144">Při iteraci na dotaz, který vytváří sekvenci skupin, je nutné použít vnořenou smyčku `foreach`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="96ee2-145">Vnější smyčka projde každou skupinu a vnitřní smyčka projde členy každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="96ee2-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="96ee2-146">Pokud musíte odkazovat na výsledky operace skupiny, můžete pomocí klíčového slova `into` vytvořit identifikátor, který lze dotazovat dále.</span><span class="sxs-lookup"><span data-stu-id="96ee2-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="96ee2-147">Následující dotaz vrátí pouze skupiny, které obsahují více než dva zákazníky:</span><span class="sxs-lookup"><span data-stu-id="96ee2-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="96ee2-148">Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="96ee2-148">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="96ee2-149">Spojování</span><span class="sxs-lookup"><span data-stu-id="96ee2-149">Joining</span></span>  
 <span data-ttu-id="96ee2-150">Operace join vytvořte přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat.</span><span class="sxs-lookup"><span data-stu-id="96ee2-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="96ee2-151">Můžete například provést připojení a vyhledat všechny zákazníky a distributory, kteří mají stejné umístění.</span><span class="sxs-lookup"><span data-stu-id="96ee2-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="96ee2-152">V jazyce LINQ klauzule `join` vždy funguje na kolekcích objektů namísto přímo v databázových tabulkách.</span><span class="sxs-lookup"><span data-stu-id="96ee2-152">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="96ee2-153">V LINQ není nutné používat `join` tak často jako v jazyce SQL, protože cizí klíče v technologii LINQ jsou reprezentovány v objektovém modelu jako vlastnosti, které obsahují kolekci položek.</span><span class="sxs-lookup"><span data-stu-id="96ee2-153">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="96ee2-154">Například objekt `Customer` obsahuje kolekci objektů `Order`.</span><span class="sxs-lookup"><span data-stu-id="96ee2-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="96ee2-155">Místo toho, abyste mohli provádět spojení, získáte přístup k objednávkám pomocí zápisu teček:</span><span class="sxs-lookup"><span data-stu-id="96ee2-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="96ee2-156">Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-156">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="96ee2-157">Výběr (projekce)</span><span class="sxs-lookup"><span data-stu-id="96ee2-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="96ee2-158">Klauzule `select` generuje výsledky dotazu a určuje "tvar" nebo typ každého vráceného elementu.</span><span class="sxs-lookup"><span data-stu-id="96ee2-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="96ee2-159">Můžete například určit, jestli se výsledky budou skládat z kompletních `Customer` objektů, jenom jednoho člena, podmnožiny členů nebo nějakého jiného typu výsledku založeného na výpočtu nebo vytvoření nového objektu.</span><span class="sxs-lookup"><span data-stu-id="96ee2-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="96ee2-160">Když klauzule `select` vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="96ee2-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="96ee2-161">Použití projekce k transformaci dat je výkonná schopnost výrazů dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="96ee2-161">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="96ee2-162">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](./data-transformations-with-linq.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="96ee2-162">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ee2-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96ee2-163">See also</span></span>

- [<span data-ttu-id="96ee2-164">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="96ee2-164">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="96ee2-165">Návod: zápis dotazů vC#</span><span class="sxs-lookup"><span data-stu-id="96ee2-165">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="96ee2-166">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="96ee2-166">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="96ee2-167">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="96ee2-167">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
