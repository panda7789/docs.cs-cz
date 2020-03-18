---
title: Standardní operátory dotazů – přehled (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167852"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="6ac3f-102">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="6ac3f-103">*Standardní operátory dotazu* jsou metody, které tvoří vzor LINQ.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="6ac3f-104">Většina těchto metod pracovat na sekvence, kde sekvence je <xref:System.Collections.Generic.IEnumerable%601> objekt, <xref:System.Linq.IQueryable%601> jehož typ implementuje rozhraní nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="6ac3f-105">Standardní operátory dotazů poskytují možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="6ac3f-106">Existují dvě sady linq standardní operátory dotazu, jeden, který pracuje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který pracuje na objekty typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="6ac3f-107">Metody, které tvoří každou sadu jsou <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> statické členy a třídy, resp.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="6ac3f-108">Jsou definovány jako *rozšiřující metody* typu, na kterém pracují.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="6ac3f-109">To znamená, že mohou být volány pomocí syntaxe statické metody nebo syntaxe metody instance.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="6ac3f-110">Kromě toho několik standardních metod operátoru dotazu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601>pracovat na typy než ty, které jsou založeny na nebo .</span><span class="sxs-lookup"><span data-stu-id="6ac3f-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="6ac3f-111">Typ <xref:System.Linq.Enumerable> definuje dvě takové metody, které pracují <xref:System.Collections.IEnumerable>na objekty typu .</span><span class="sxs-lookup"><span data-stu-id="6ac3f-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="6ac3f-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>a , umožňují povolit neparametrizované nebo neobecné kolekce, které mají být dotazovány ve vzoru LINQ.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="6ac3f-113">To provést vytvořením kolekce silného typu objektů.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="6ac3f-114">Třída <xref:System.Linq.Queryable> definuje dvě podobné <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> metody <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>a , které <xref:System.Linq.Queryable>pracují s objekty typu .</span><span class="sxs-lookup"><span data-stu-id="6ac3f-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="6ac3f-115">Standardní operátory dotazu se liší v časování jejich provádění, v závislosti na tom, zda vrátí hodnotu singleton nebo posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="6ac3f-116">Tyto metody, které vracejí hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="6ac3f-117">Metody, které vrátí pořadí odložit spuštění dotazu a vrátit výčtu objektu.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="6ac3f-118">V případě metod, které pracují na in-memory kolekce, to <xref:System.Collections.Generic.IEnumerable%601>znamená, že tyto metody, které rozšiřují , vrácené výčtu objektu zachycuje argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="6ac3f-119">Pokud je tento objekt výčtu, logika operátoru dotazu je zaměstnán a jsou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="6ac3f-120">Naproti tomu metody, <xref:System.Linq.IQueryable%601> které rozšiřují neimplementují žádné dotazování chování, ale vytvořit strom výraz, který představuje dotaz, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="6ac3f-121">Zpracování dotazu je zpracována zdrojový <xref:System.Linq.IQueryable%601> objekt.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="6ac3f-122">Volání metod dotazu lze zřetězit společně v jednom dotazu, který umožňuje dotazy stát libovolně složité.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="6ac3f-123">Následující příklad kódu ukazuje, jak lze standardní operátory dotazu použít k získání informací o posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="6ac3f-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="6ac3f-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="6ac3f-125">Některé z nejčastěji používaných operátorů standardní dotaz mají vyhrazené C# a Visual Basic jazyk syntaxe, která umožňuje jejich volání jako součást *výrazu* *dotazu* .</span><span class="sxs-lookup"><span data-stu-id="6ac3f-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="6ac3f-126">Další informace o standardních operátorech dotazů, které mají vyhrazená klíčová slova a odpovídající syntaxe, naleznete [v tématu Syntaxe výrazu dotazu pro operátory standardních dotazů (C#).](./query-expression-syntax-for-standard-query-operators.md)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="6ac3f-127">Rozšíření operátorů standardních dotazů</span><span class="sxs-lookup"><span data-stu-id="6ac3f-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="6ac3f-128">Sadu standardních operátorů dotazů můžete rozšířit vytvořením metod specifických pro doménu, které jsou vhodné pro cílovou doménu nebo technologii.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="6ac3f-129">Můžete také nahradit operátory standardní dotazů vlastními implementacemi, které poskytují další služby, jako je vzdálené vyhodnocení, překlad dotazů a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="6ac3f-130">Viz <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ac3f-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6ac3f-131">Related Sections</span></span>  
 <span data-ttu-id="6ac3f-132">Následující odkazy přejdete na témata, která poskytují další informace o různých operátorech standardnídotaz na základě funkce.</span><span class="sxs-lookup"><span data-stu-id="6ac3f-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="6ac3f-133">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-133">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="6ac3f-134">Nastavit operace (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-134">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="6ac3f-135">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-135">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="6ac3f-136">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-136">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="6ac3f-137">Projekční operace (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-137">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="6ac3f-138">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-138">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="6ac3f-139">Operace spojení (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-139">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="6ac3f-140">Seskupování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-140">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="6ac3f-141">Operace generování (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-141">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="6ac3f-142">Operace rovnosti (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-142">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="6ac3f-143">Operace prvku (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-143">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="6ac3f-144">Převod datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-144">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="6ac3f-145">Zřetězení (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-145">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="6ac3f-146">Operace agregace (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-146">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ac3f-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ac3f-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="6ac3f-148">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-148">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="6ac3f-149">Syntaxe výrazu dotazu pro standardní operátory dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="6ac3f-150">Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac3f-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="6ac3f-151">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="6ac3f-151">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
