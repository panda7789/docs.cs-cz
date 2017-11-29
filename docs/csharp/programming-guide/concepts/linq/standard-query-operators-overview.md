---
title: "Přehled standardních operátorů dotazu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bcf64b87eb7fa1cba863f809dc11ab0ccb68ea9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="2b438-102">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="2b438-103">*Standardní operátory dotazu* jsou metody, které tvoří vzoru LINQ.</span><span class="sxs-lookup"><span data-stu-id="2b438-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="2b438-104">Většina z nich fungovat v pořadí, kde je posloupnost objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b438-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="2b438-105">Standardní operátory dotazu zadejte možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.</span><span class="sxs-lookup"><span data-stu-id="2b438-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="2b438-106">Existují dvě sady LINQ standardní operátory dotazu, který funguje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a dalších, který pracuje s objekty typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2b438-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2b438-107">Metody, které tvoří každá sada jsou statické členy <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b438-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="2b438-108">Jsou definovány jako *rozšiřující metody* typu, které budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="2b438-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="2b438-109">To znamená, že nelze volat pomocí syntaxe statickou metodu nebo syntaxi metody instance.</span><span class="sxs-lookup"><span data-stu-id="2b438-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="2b438-110">Kromě toho existuje několik metod operátor standardní dotaz pracovat typy kromě těch, na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2b438-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2b438-111"><xref:System.Linq.Enumerable> Typ definuje tyto dvě metody i na objekty typu pracovat <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="2b438-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="2b438-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci-parametry nebo neobecné, chcete-li spustit dotaz ve vzoru LINQ.</span><span class="sxs-lookup"><span data-stu-id="2b438-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="2b438-113">Je to tak, že vytvoříte silného typu kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="2b438-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="2b438-114"><xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objekty typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="2b438-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="2b438-115">Standardní operátory dotazu se liší v načasování jejich spuštění, v závislosti na tom, jestli vrátit hodnotu singleton nebo pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="2b438-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="2b438-116">Tyto metody, které vrací hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="2b438-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="2b438-117">Metody, které vracejí sekvenci odložení spuštění dotazu a vrátí vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="2b438-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="2b438-118">V případě metody, které působí na kolekce v paměti, který je těchto metod, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zaznamená argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="2b438-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="2b438-119">Když tento objekt je ve výčtu uvedena, zaměstnání logiku operátor dotazu a budou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="2b438-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="2b438-120">Naproti tomu jsou metody, rozšířit <xref:System.Linq.IQueryable%601> neimplementuje žádné chování dotazování, ale sestavení strom výrazu představující dotaz provést.</span><span class="sxs-lookup"><span data-stu-id="2b438-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="2b438-121">Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="2b438-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="2b438-122">Volání metody dotazů možné zřetězit společně v jednom dotazu, který umožňuje dotazy se libovolně komplexní.</span><span class="sxs-lookup"><span data-stu-id="2b438-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="2b438-123">Následující příklad kódu ukazuje, jak standardní operátory dotazu slouží k získání informací o sekvenci.</span><span class="sxs-lookup"><span data-stu-id="2b438-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="2b438-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="2b438-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="2b438-125">Některé více často používaných standardní operátory dotazu mít vyhrazené syntaxe jazyka – klíčové slovo C# a Visual Basic umožňující volat v rámci *dotazu* *výraz*.</span><span class="sxs-lookup"><span data-stu-id="2b438-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="2b438-126">Další informace o standardních operátorů dotazu, které mají vyhrazený klíčová slova a jejich odpovídající syntaxe najdete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2b438-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="2b438-127">Rozšíření standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="2b438-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="2b438-128">Sadu standardních operátorů dotazu lze posílení metodami vytváření specifické pro doménu, které jsou vhodné pro cílovou doménu nebo technologii.</span><span class="sxs-lookup"><span data-stu-id="2b438-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="2b438-129">Můžete také standardní operátory dotazu nahraďte vlastní implementace, které poskytují další služby, jako je například vzdálené vyhodnocení, překlad dotazu a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="2b438-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="2b438-130">V tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.</span><span class="sxs-lookup"><span data-stu-id="2b438-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2b438-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2b438-131">Related Sections</span></span>  
 <span data-ttu-id="2b438-132">Pomocí následujících odkazů se dostanete na témata, která obsahují další informace o různých standardních operátorů dotazu podle funkce.</span><span class="sxs-lookup"><span data-stu-id="2b438-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="2b438-133">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="2b438-134">Množinové operace (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="2b438-135">Filtrování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="2b438-136">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="2b438-137">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="2b438-138">Segmentace dat (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="2b438-139">Připojení k operace (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="2b438-140">Seskupování dat (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="2b438-141">Generování operací (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="2b438-142">Operace rovnosti (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="2b438-143">Operace s elementy (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="2b438-144">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="2b438-145">Operace sřetězení (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="2b438-146">Agregační operace (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b438-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b438-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="2b438-148">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [<span data-ttu-id="2b438-149">Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="2b438-150">Klasifikace standardních operátorů dotazu podle metody provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="2b438-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="2b438-151">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="2b438-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
