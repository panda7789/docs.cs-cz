---
title: Přehled standardních operátorů dotazu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841469"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="3d803-102">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="3d803-103">*Standardních operátorů pro dotazování* jsou metody, které tvoří LINQ vzoru.</span><span class="sxs-lookup"><span data-stu-id="3d803-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="3d803-104">Většina z těchto metod pracovat v pořadí, ve kterém sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3d803-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="3d803-105">Operátory standardního dotazu zadejte možnosti dotazu, jako je filtrování, projekce, agregace, řazení a další.</span><span class="sxs-lookup"><span data-stu-id="3d803-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="3d803-106">Existují dvě sady operátory standardního dotazu LINQ, ten, který funguje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který funguje na objektech typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3d803-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3d803-107">Statické členy třídy jsou metody, které tvoří každou sadu <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3d803-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="3d803-108">Jsou definovány jako *rozšiřující metody* typu, který funguje na.</span><span class="sxs-lookup"><span data-stu-id="3d803-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="3d803-109">To znamená, že lze volat pomocí syntaxe statickou metodu nebo pomocí syntaxe metody instance.</span><span class="sxs-lookup"><span data-stu-id="3d803-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="3d803-110">Kromě toho několik standardní metody operátoru dotazu pracovat s typy než ty, které na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3d803-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3d803-111"><xref:System.Linq.Enumerable> Typ definuje tyto dvě metody jak pracovat s objekty typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="3d803-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="3d803-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci neparametrizované nebo neobecnou, aby se dalo dotazovat v LINQ vzoru.</span><span class="sxs-lookup"><span data-stu-id="3d803-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="3d803-113">Je to tak, že vytvoříte kolekci silně typovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="3d803-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="3d803-114"><xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objektech typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="3d803-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="3d803-115">Operátory standardního dotazu se liší v časování jejich spuštění, v závislosti na tom, zda vrátit hodnotu singleton nebo posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="3d803-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="3d803-116">Tyto metody, které vracejí hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="3d803-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="3d803-117">Metody, které vracejí sekvenci odloží provedení dotazu a vrátí vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="3d803-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="3d803-118">V případě metody, které pracují na kolekce v paměti, to znamená, že tyto metody, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zachycuje argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="3d803-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="3d803-119">Když tento objekt je vypočten, použijí logiky – operátor dotazu a jsou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="3d803-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="3d803-120">Naproti tomu jsou metody, které rozšiřují <xref:System.Linq.IQueryable%601> neimplementují všechna dotazování chování, ale sestavení strom výrazu, který představuje dotaz, který má být provedena.</span><span class="sxs-lookup"><span data-stu-id="3d803-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="3d803-121">Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="3d803-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="3d803-122">Volání metody dotazu je možné zřetězit v jednom dotazu, který umožňuje dotazům stát libovolně složité.</span><span class="sxs-lookup"><span data-stu-id="3d803-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="3d803-123">Následující příklad kódu ukazuje, jak lze získat informace o posloupnosti standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="3d803-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="3d803-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="3d803-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="3d803-125">Některé častěji používané operátory standardního dotazu mít vyhrazené syntaxi jazyka – klíčové slovo jazyka C# a Visual Basic, která je volána v rámci umožňuje *dotazu* *výraz*.</span><span class="sxs-lookup"><span data-stu-id="3d803-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="3d803-126">Další informace o standardních operátorů dotazu, které mají vyhrazená klíčová slova a jejich odpovídající syntaxe, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3d803-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="3d803-127">Rozšíření standardních operátorů pro dotazování</span><span class="sxs-lookup"><span data-stu-id="3d803-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="3d803-128">Metodami vytváření specifického pro doménu, které jsou vhodné pro cílovou doménu nebo technologii lze rozšířit sadu standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="3d803-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="3d803-129">Operátory standardního dotazu můžete také nahradit vlastní implementace, které poskytují další služby, jako je vzdálené testování, překladu dotazu a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3d803-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="3d803-130">Zobrazit <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.</span><span class="sxs-lookup"><span data-stu-id="3d803-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d803-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3d803-131">Related Sections</span></span>  
 <span data-ttu-id="3d803-132">Pomocí následujících odkazů můžete na témata, která poskytují další informace o různých standardních operátorů pro dotazování závislosti na funkcích.</span><span class="sxs-lookup"><span data-stu-id="3d803-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="3d803-133">Řazení dat</span><span class="sxs-lookup"><span data-stu-id="3d803-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="3d803-134">Množinové operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="3d803-135">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="3d803-136">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="3d803-137">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="3d803-138">Dělení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="3d803-139">Připojte se k operací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="3d803-140">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="3d803-141">Generování operací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="3d803-142">Operace rovnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="3d803-143">Operace s elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="3d803-144">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="3d803-145">Operace sřetězení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="3d803-146">Aggregation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d803-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d803-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="3d803-148">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="3d803-149">Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="3d803-150">Klasifikace standardních operátorů dotazu podle metody provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d803-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="3d803-151">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="3d803-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
