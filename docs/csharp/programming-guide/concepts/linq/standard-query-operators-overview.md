---
title: Přehled standardních operátorů dotazu (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 397d1368a3c4e0b20a0bc9c694421ed60119d1aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502436"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="5ef17-102">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="5ef17-103">*Standardních operátorů pro dotazování* jsou metody, které tvoří LINQ vzoru.</span><span class="sxs-lookup"><span data-stu-id="5ef17-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="5ef17-104">Většina z těchto metod pracovat v pořadí, ve kterém sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5ef17-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="5ef17-105">Operátory standardního dotazu zadejte možnosti dotazu, jako je filtrování, projekce, agregace, řazení a další.</span><span class="sxs-lookup"><span data-stu-id="5ef17-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="5ef17-106">Existují dvě sady operátory standardního dotazu LINQ, ten, který funguje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který funguje na objektech typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="5ef17-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="5ef17-107">Statické členy třídy jsou metody, které tvoří každou sadu <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5ef17-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="5ef17-108">Jsou definovány jako *rozšiřující metody* typu, který funguje na.</span><span class="sxs-lookup"><span data-stu-id="5ef17-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="5ef17-109">To znamená, že lze volat pomocí syntaxe statickou metodu nebo pomocí syntaxe metody instance.</span><span class="sxs-lookup"><span data-stu-id="5ef17-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="5ef17-110">Kromě toho několik standardní metody operátoru dotazu pracovat s typy než ty, které na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="5ef17-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="5ef17-111"><xref:System.Linq.Enumerable> Typ definuje tyto dvě metody jak pracovat s objekty typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="5ef17-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="5ef17-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci neparametrizované nebo neobecnou, aby se dalo dotazovat v LINQ vzoru.</span><span class="sxs-lookup"><span data-stu-id="5ef17-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="5ef17-113">Je to tak, že vytvoříte kolekci silně typovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="5ef17-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="5ef17-114"><xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objektech typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="5ef17-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="5ef17-115">Operátory standardního dotazu se liší v časování jejich spuštění, v závislosti na tom, zda vrátit hodnotu singleton nebo posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="5ef17-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="5ef17-116">Tyto metody, které vracejí hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="5ef17-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="5ef17-117">Metody, které vracejí sekvenci odloží provedení dotazu a vrátí vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="5ef17-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="5ef17-118">V případě metody, které pracují na kolekce v paměti, to znamená, že tyto metody, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zachycuje argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="5ef17-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="5ef17-119">Když tento objekt je vypočten, použijí logiky – operátor dotazu a jsou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="5ef17-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="5ef17-120">Naproti tomu jsou metody, které rozšiřují <xref:System.Linq.IQueryable%601> neimplementují všechna dotazování chování, ale sestavení strom výrazu, který představuje dotaz, který má být provedena.</span><span class="sxs-lookup"><span data-stu-id="5ef17-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="5ef17-121">Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="5ef17-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="5ef17-122">Volání metody dotazu je možné zřetězit v jednom dotazu, který umožňuje dotazům stát libovolně složité.</span><span class="sxs-lookup"><span data-stu-id="5ef17-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="5ef17-123">Následující příklad kódu ukazuje, jak lze získat informace o posloupnosti standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="5ef17-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="5ef17-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="5ef17-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="5ef17-125">Některé častěji používané operátory standardního dotazu mít vyhrazené syntaxi jazyka – klíčové slovo jazyka C# a Visual Basic, která je volána v rámci umožňuje *dotazu* *výraz*.</span><span class="sxs-lookup"><span data-stu-id="5ef17-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="5ef17-126">Další informace o standardních operátorů dotazu, které mají vyhrazená klíčová slova a jejich odpovídající syntaxe, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5ef17-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="5ef17-127">Rozšíření standardních operátorů pro dotazování</span><span class="sxs-lookup"><span data-stu-id="5ef17-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="5ef17-128">Metodami vytváření specifického pro doménu, které jsou vhodné pro cílovou doménu nebo technologii lze rozšířit sadu standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="5ef17-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="5ef17-129">Operátory standardního dotazu můžete také nahradit vlastní implementace, které poskytují další služby, jako je vzdálené testování, překladu dotazu a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="5ef17-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="5ef17-130">Zobrazit <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.</span><span class="sxs-lookup"><span data-stu-id="5ef17-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ef17-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5ef17-131">Related Sections</span></span>  
 <span data-ttu-id="5ef17-132">Pomocí následujících odkazů můžete na témata, která poskytují další informace o různých standardních operátorů pro dotazování závislosti na funkcích.</span><span class="sxs-lookup"><span data-stu-id="5ef17-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="5ef17-133">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="5ef17-134">Množinové operace (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="5ef17-135">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="5ef17-136">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="5ef17-137">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="5ef17-138">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="5ef17-139">Připojte se k operace (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="5ef17-140">Seskupování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="5ef17-141">Generování operací (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="5ef17-142">Operace rovnosti (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="5ef17-143">Operace s elementy (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="5ef17-144">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="5ef17-145">Operace sřetězení (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="5ef17-146">Agregační operace (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="5ef17-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ef17-147">See Also</span></span>

- <xref:System.Linq.Enumerable>  
- <xref:System.Linq.Queryable>  
- [<span data-ttu-id="5ef17-148">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
- [<span data-ttu-id="5ef17-149">Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
- [<span data-ttu-id="5ef17-150">Klasifikace standardních operátorů dotazu podle metody provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="5ef17-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
- [<span data-ttu-id="5ef17-151">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="5ef17-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
