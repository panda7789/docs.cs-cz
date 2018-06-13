---
title: Přehled standardních operátorů dotazu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 27b144ae75054dbdc535b6ad894e4a5a0b8529e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653569"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="7557a-102">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="7557a-103">*Standardní operátory dotazu* jsou metody, které tvoří vzoru LINQ.</span><span class="sxs-lookup"><span data-stu-id="7557a-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="7557a-104">Většina z nich fungovat v pořadí, kde je posloupnost objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7557a-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="7557a-105">Standardní operátory dotazu zadejte možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.</span><span class="sxs-lookup"><span data-stu-id="7557a-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="7557a-106">Existují dvě sady LINQ standardní operátory dotazu, který funguje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a dalších, který pracuje s objekty typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7557a-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7557a-107">Metody, které tvoří každá sada jsou statické členy <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7557a-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="7557a-108">Jsou definovány jako *rozšiřující metody* typu, které budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="7557a-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="7557a-109">To znamená, že nelze volat pomocí syntaxe statickou metodu nebo syntaxi metody instance.</span><span class="sxs-lookup"><span data-stu-id="7557a-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="7557a-110">Kromě toho existuje několik metod operátor standardní dotaz pracovat typy kromě těch, na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7557a-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7557a-111"><xref:System.Linq.Enumerable> Typ definuje tyto dvě metody i na objekty typu pracovat <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="7557a-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="7557a-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci-parametry nebo neobecné, chcete-li spustit dotaz ve vzoru LINQ.</span><span class="sxs-lookup"><span data-stu-id="7557a-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="7557a-113">Je to tak, že vytvoříte silného typu kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="7557a-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="7557a-114"><xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objekty typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="7557a-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="7557a-115">Standardní operátory dotazu se liší v načasování jejich spuštění, v závislosti na tom, jestli vrátit hodnotu singleton nebo pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="7557a-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="7557a-116">Tyto metody, které vrací hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="7557a-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="7557a-117">Metody, které vracejí sekvenci odložení spuštění dotazu a vrátí vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="7557a-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="7557a-118">V případě metody, které působí na kolekce v paměti, který je těchto metod, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zaznamená argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="7557a-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="7557a-119">Když tento objekt je ve výčtu uvedena, zaměstnání logiku operátor dotazu a budou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="7557a-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="7557a-120">Naproti tomu jsou metody, rozšířit <xref:System.Linq.IQueryable%601> neimplementuje žádné chování dotazování, ale sestavení strom výrazu představující dotaz provést.</span><span class="sxs-lookup"><span data-stu-id="7557a-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="7557a-121">Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="7557a-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="7557a-122">Volání metody dotazů možné zřetězit společně v jednom dotazu, který umožňuje dotazy se libovolně komplexní.</span><span class="sxs-lookup"><span data-stu-id="7557a-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="7557a-123">Následující příklad kódu ukazuje, jak standardní operátory dotazu slouží k získání informací o sekvenci.</span><span class="sxs-lookup"><span data-stu-id="7557a-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="7557a-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="7557a-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="7557a-125">Některé více často používaných standardní operátory dotazu mít vyhrazené syntaxe jazyka – klíčové slovo C# a Visual Basic umožňující volat v rámci *dotazu* *výraz*.</span><span class="sxs-lookup"><span data-stu-id="7557a-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="7557a-126">Další informace o standardních operátorů dotazu, které mají vyhrazený klíčová slova a jejich odpovídající syntaxe najdete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7557a-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="7557a-127">Rozšíření standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="7557a-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="7557a-128">Sadu standardních operátorů dotazu lze posílení metodami vytváření specifické pro doménu, které jsou vhodné pro cílovou doménu nebo technologii.</span><span class="sxs-lookup"><span data-stu-id="7557a-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="7557a-129">Můžete také standardní operátory dotazu nahraďte vlastní implementace, které poskytují další služby, jako je například vzdálené vyhodnocení, překlad dotazu a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="7557a-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="7557a-130">V tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.</span><span class="sxs-lookup"><span data-stu-id="7557a-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7557a-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7557a-131">Related Sections</span></span>  
 <span data-ttu-id="7557a-132">Pomocí následujících odkazů se dostanete na témata, která obsahují další informace o různých standardních operátorů dotazu podle funkce.</span><span class="sxs-lookup"><span data-stu-id="7557a-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="7557a-133">Řazení dat</span><span class="sxs-lookup"><span data-stu-id="7557a-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="7557a-134">Množinové operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="7557a-135">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="7557a-136">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="7557a-137">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="7557a-138">Segmentace dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="7557a-139">Připojení k operací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="7557a-140">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="7557a-141">Generování operací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="7557a-142">Operace rovnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="7557a-143">Operace s elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="7557a-144">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="7557a-145">Operace sřetězení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="7557a-146">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="7557a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="7557a-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="7557a-148">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [<span data-ttu-id="7557a-149">Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="7557a-150">Klasifikace standardních operátorů dotazu podle metody provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7557a-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="7557a-151">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="7557a-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
