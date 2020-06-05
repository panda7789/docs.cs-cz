---
title: Přehled standardních operátorů dotazu
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406778"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="629d9-102">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="629d9-103">*Standardní operátory dotazu* jsou metody, které tvoří vzor LINQ.</span><span class="sxs-lookup"><span data-stu-id="629d9-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="629d9-104">Většina těchto metod pracuje na sekvencích, kde sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="629d9-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="629d9-105">Standardní operátory dotazu poskytují možnosti dotazování, včetně filtrování, projekce, agregace, řazení a dalších.</span><span class="sxs-lookup"><span data-stu-id="629d9-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="629d9-106">Existují dvě sady standardních operátorů dotazů LINQ, jeden, který pracuje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který pracuje s objekty typu <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="629d9-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="629d9-107">Metody, které tvoří každou sadu, jsou statické členy <xref:System.Linq.Enumerable> tříd a v <xref:System.Linq.Queryable> uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="629d9-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="629d9-108">Jsou definovány jako *metody rozšíření* typu, na kterém pracují.</span><span class="sxs-lookup"><span data-stu-id="629d9-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="629d9-109">To znamená, že mohou být volány buď pomocí syntaxe statické metody, nebo syntaxe metody instance.</span><span class="sxs-lookup"><span data-stu-id="629d9-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="629d9-110">Kromě toho několik metod standardních operátorů dotazů pracuje na jiných typech než těch, které jsou založeny na <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="629d9-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="629d9-111"><xref:System.Linq.Enumerable>Typ definuje dvě takové metody, které pracují s objekty typu <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="629d9-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="629d9-112">Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umožňují povolit dotazování na kolekci, která není Parametrizovaná, nebo neobecná, aby bylo možné dotazovat ve vzorci LINQ.</span><span class="sxs-lookup"><span data-stu-id="629d9-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="629d9-113">To dělají vytvořením silně typované kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="629d9-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="629d9-114"><xref:System.Linq.Queryable>Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> , které pracují s objekty typu <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="629d9-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="629d9-115">Standardní operátory dotazu se liší v časování jejich spuštění v závislosti na tom, zda vracejí hodnotu typu Singleton nebo sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="629d9-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="629d9-116">Tyto metody, které vracejí hodnotu typu Singleton (například <xref:System.Linq.Enumerable.Average%2A> a), se <xref:System.Linq.Enumerable.Sum%2A> spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="629d9-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="629d9-117">Metody, které vracejí sekvenci, odloží provedení dotazu a vrátí vyčíslitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="629d9-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="629d9-118">V případě metod, které pracují s kolekcemi v paměti, což znamená, že tyto metody, které rozšíření <xref:System.Collections.Generic.IEnumerable%601> , vrátí vyčíslitelné objekty argumenty, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="629d9-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="629d9-119">Při vytváření výčtu tohoto objektu je vytvořena logika operátoru dotazu a jsou vráceny výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="629d9-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="629d9-120">Naproti tomu metody, které rozšiřuje, <xref:System.Linq.IQueryable%601> neimplementují žádné dotazy, ale sestaví strom výrazu, který představuje dotaz, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="629d9-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="629d9-121">Zpracování dotazu je zpracováváno zdrojovým <xref:System.Linq.IQueryable%601> objektem.</span><span class="sxs-lookup"><span data-stu-id="629d9-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="629d9-122">Volání metod dotazů lze zřetězit společně v jednom dotazu, který umožňuje, aby se dotazy staly libovolně složité.</span><span class="sxs-lookup"><span data-stu-id="629d9-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="629d9-123">Následující příklad kódu ukazuje, jak lze použít standardní operátory dotazu k získání informací o sekvenci.</span><span class="sxs-lookup"><span data-stu-id="629d9-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

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

## <a name="query-expression-syntax"></a><span data-ttu-id="629d9-124">Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="629d9-124">Query Expression Syntax</span></span>

<span data-ttu-id="629d9-125">Některé z často používaných standardních operátorů dotazů mají vyhrazená syntaxe klíčového slova jazyka C# a Visual Basic, která umožňuje jejich volání jako součást výrazu *dotazu* *expression*.</span><span class="sxs-lookup"><span data-stu-id="629d9-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="629d9-126">Další informace o standardních operátorech dotazu, které mají vyhrazená klíčová slova a jejich odpovídajících syntaxech, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="629d9-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="629d9-127">Rozšíření standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="629d9-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="629d9-128">Můžete rozšířit sadu standardních operátorů dotazů vytvořením metod specifických pro doménu, které jsou vhodné pro vaši cílovou doménu nebo technologii.</span><span class="sxs-lookup"><span data-stu-id="629d9-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="629d9-129">Standardní operátory dotazu můžete také nahradit vlastními implementacemi, které poskytují další služby, jako je vzdálené vyhodnocení, překlad dotazů a optimalizace.</span><span class="sxs-lookup"><span data-stu-id="629d9-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="629d9-130">Příklad najdete v tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> .</span><span class="sxs-lookup"><span data-stu-id="629d9-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="629d9-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="629d9-131">Related Sections</span></span>

<span data-ttu-id="629d9-132">Následující odkazy odkazují na témata, která poskytují další informace o různých standardních dotazovacích operátorech na základě funkcí.</span><span class="sxs-lookup"><span data-stu-id="629d9-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="629d9-133">Řazení dat</span><span class="sxs-lookup"><span data-stu-id="629d9-133">Sorting Data</span></span>](sorting-data.md)

- [<span data-ttu-id="629d9-134">Operace set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-134">Set Operations (Visual Basic)</span></span>](set-operations.md)

- [<span data-ttu-id="629d9-135">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-135">Filtering Data (Visual Basic)</span></span>](filtering-data.md)

- [<span data-ttu-id="629d9-136">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-136">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)

- [<span data-ttu-id="629d9-137">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-137">Projection Operations (Visual Basic)</span></span>](projection-operations.md)

- [<span data-ttu-id="629d9-138">Dělení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-138">Partitioning Data (Visual Basic)</span></span>](partitioning-data.md)

- [<span data-ttu-id="629d9-139">Operace join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-139">Join Operations (Visual Basic)</span></span>](join-operations.md)

- [<span data-ttu-id="629d9-140">Seskupování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-140">Grouping Data (Visual Basic)</span></span>](grouping-data.md)

- [<span data-ttu-id="629d9-141">Operace generování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-141">Generation Operations (Visual Basic)</span></span>](generation-operations.md)

- [<span data-ttu-id="629d9-142">Operace rovnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-142">Equality Operations (Visual Basic)</span></span>](equality-operations.md)

- [<span data-ttu-id="629d9-143">Operace elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-143">Element Operations (Visual Basic)</span></span>](element-operations.md)

- [<span data-ttu-id="629d9-144">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-144">Converting Data Types (Visual Basic)</span></span>](converting-data-types.md)

- [<span data-ttu-id="629d9-145">Operace zřetězení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-145">Concatenation Operations (Visual Basic)</span></span>](concatenation-operations.md)

- [<span data-ttu-id="629d9-146">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-146">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="629d9-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="629d9-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="629d9-148">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-148">Introduction to LINQ (Visual Basic)</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="629d9-149">Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="629d9-150">Klasifikace standardních operátorů dotazu podle způsobu provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629d9-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="629d9-151">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="629d9-151">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
