---
title: Vztahy typů v operacích dotazu
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 8c201abef924766d52b1adb084970a24ebea2b50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350569"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="2bc31-102">Vztahy typů v operacích dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bc31-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="2bc31-103">Proměnné používané v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] operacích dotazů jsou silného typu a musí být vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="2bc31-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="2bc31-104">Silné zadání se používá ve zdroji dat, v samotném dotazu a v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="2bc31-105">Následující ilustrace identifikuje výrazy používané k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ho dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="2bc31-106">Další informace o částech dotazu najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2bc31-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>

![Snímek obrazovky znázorňující dotaz pseudokódu s zvýrazněnými prvky](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="2bc31-108">Typ proměnné rozsahu v dotazu musí být kompatibilní s typem prvků ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="2bc31-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="2bc31-109">Typ proměnné dotazu musí být kompatibilní s elementem Sequence definovaným v klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="2bc31-110">Nakonec musí být typ elementů sekvence také kompatibilní s typem řídicí proměnné smyčky, která je použita v příkazu `For Each`, který spouští dotaz.</span><span class="sxs-lookup"><span data-stu-id="2bc31-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="2bc31-111">Toto silné zadání usnadňuje identifikaci chyb typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2bc31-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="2bc31-112">Visual Basic usnadňuje silné psaní implementací místního typu, označovaného také jako *implicitní psaní*.</span><span class="sxs-lookup"><span data-stu-id="2bc31-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="2bc31-113">Tato funkce se používá v předchozím příkladu a zobrazí se v ní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentace.</span><span class="sxs-lookup"><span data-stu-id="2bc31-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="2bc31-114">V Visual Basic je odvození místního typu provedeno jednoduše pomocí příkazu `Dim` bez klauzule `As`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="2bc31-115">V následujícím příkladu je `city` silně typované jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="2bc31-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="2bc31-116">Odvození místního typu funguje pouze v případě, že je `Option Infer` nastaveno na `On`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="2bc31-117">Další informace naleznete v tématu [příkaz Option include](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2bc31-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="2bc31-118">Nicméně i v případě, že použijete místní odvození typu v dotazu, jsou přítomny stejné vztahy typů mezi proměnné ve zdroji dat, proměnnou dotazu a smyčkou provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="2bc31-119">Při psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů nebo při práci s ukázkami a příklady kódu v dokumentaci je vhodné mít základní znalosti těchto vztahů s těmito typy.</span><span class="sxs-lookup"><span data-stu-id="2bc31-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="2bc31-120">Možná budete muset zadat explicitní typ pro proměnnou rozsahu, která se neshoduje s typem vráceným ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2bc31-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="2bc31-121">Typ proměnné rozsahu lze zadat pomocí klauzule `As`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="2bc31-122">Výsledkem je ale chyba, pokud je převod [zužujícího převodu](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastavené na `On`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="2bc31-123">Proto doporučujeme, abyste provedli převod na hodnoty načtené ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2bc31-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="2bc31-124">Hodnoty z datového zdroje můžete převést na typ proměnné explicitní rozsah pomocí metody <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="2bc31-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="2bc31-125">Hodnoty vybrané v klauzuli `Select` lze také přetypovat na explicitní typ, který se liší od typu proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="2bc31-126">Tyto body jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="2bc31-127">Dotazy, které vracejí celé prvky zdrojových dat</span><span class="sxs-lookup"><span data-stu-id="2bc31-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="2bc31-128">Následující příklad ukazuje operaci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, která vrací sekvenci prvků vybraných ze zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="2bc31-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="2bc31-129">Zdroj, `names`obsahuje pole řetězců a výstup dotazu je sekvence obsahující řetězce, které začínají písmenem M.</span><span class="sxs-lookup"><span data-stu-id="2bc31-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="2bc31-130">To je ekvivalentní následujícímu kódu, ale je mnohem kratší a snazší psát.</span><span class="sxs-lookup"><span data-stu-id="2bc31-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="2bc31-131">Spoléhání na odvození místního typu v dotazech je preferovaným stylem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2bc31-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="2bc31-132">Následující vztahy existují v obou předchozích příkladech kódu, ať už jsou typy určeny implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="2bc31-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="2bc31-133">Typ prvků ve zdroji dat, `names`, je typ proměnné rozsahu `name`v dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="2bc31-134">Typ objektu, který je vybrán, `name`, určuje typ proměnné dotazu `mNames`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="2bc31-135">Zde `name` je řetězec, takže proměnná dotazu je IEnumerable (Of String) v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2bc31-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="2bc31-136">Dotaz definovaný v `mNames` je proveden ve `For Each` smyčce.</span><span class="sxs-lookup"><span data-stu-id="2bc31-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="2bc31-137">Smyčka prochází výsledek provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="2bc31-138">Vzhledem k tomu, že při spuštění `mNames`dojde k vrácení posloupnosti řetězců, proměnná iterace smyčky, `nm`, je také řetězec.</span><span class="sxs-lookup"><span data-stu-id="2bc31-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="2bc31-139">Dotazy, které vracejí jedno pole z vybraných elementů</span><span class="sxs-lookup"><span data-stu-id="2bc31-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="2bc31-140">Následující příklad ukazuje operaci [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotazu, která vrací sekvenci obsahující pouze jednu část každého prvku vybranou ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2bc31-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="2bc31-141">Dotaz převezme kolekci objektů `Customer` jako zdroj dat a projekty ve výsledku vytvoří pouze vlastnost `Name`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="2bc31-142">Vzhledem k tomu, že název zákazníka je řetězec, dotaz vytvoří sekvenci řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="2bc31-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="2bc31-143">Vztahy mezi proměnnými jsou podobně jako v jednodušším příkladu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="2bc31-144">Typ prvků ve zdroji dat, `customers`, je typ proměnné rozsahu `cust`v dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="2bc31-145">V tomto příkladu je tento typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="2bc31-146">Příkaz `Select` vrátí vlastnost `Name` každého objektu `Customer` namísto celého objektu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="2bc31-147">Vzhledem k tomu, že `Name` je řetězec, proměnná dotazu `custNames`, bude znovu typu IEnumerable (Of String), nikoli `Customer`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="2bc31-148">Vzhledem k tomu, že `custNames` představuje sekvenci řetězců, iterační proměnná `For Each` smyčky, `custName`, musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="2bc31-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="2bc31-149">Bez odvození místního typu by byl předchozí příklad nenáročný na zápis a pochopení, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2bc31-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="2bc31-150">Dotazy, které vyžadují anonymní typy</span><span class="sxs-lookup"><span data-stu-id="2bc31-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="2bc31-151">Následující příklad ukazuje složitější situaci.</span><span class="sxs-lookup"><span data-stu-id="2bc31-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="2bc31-152">V předchozím příkladu bylo nepohodlné určit typy pro všechny proměnné explicitně.</span><span class="sxs-lookup"><span data-stu-id="2bc31-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="2bc31-153">V tomto příkladu není možné.</span><span class="sxs-lookup"><span data-stu-id="2bc31-153">In this example, it is impossible.</span></span> <span data-ttu-id="2bc31-154">Místo výběru celých prvků `Customer` ze zdroje dat nebo jednoho pole z každého prvku vrátí klauzule `Select` v tomto dotazu dvě vlastnosti původního objektu `Customer`: `Name` a `City`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="2bc31-155">V reakci na klauzuli `Select` definuje kompilátor anonymní typ, který obsahuje tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2bc31-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="2bc31-156">Výsledek spuštění `nameCityQuery` ve smyčce `For Each` je kolekce instancí nového anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="2bc31-157">Vzhledem k tomu, že anonymní typ nemá žádný použitelný název, nelze zadat typ `nameCityQuery` ani `custInfo` explicitně.</span><span class="sxs-lookup"><span data-stu-id="2bc31-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="2bc31-158">To znamená, že u anonymního typu není název typu, který by se měl použít místo `String` v `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="2bc31-159">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2bc31-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="2bc31-160">I když není možné určit typy pro všechny proměnné v předchozím příkladu, relace zůstanou stejné.</span><span class="sxs-lookup"><span data-stu-id="2bc31-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="2bc31-161">Typ prvků ve zdroji dat je znovu typem proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="2bc31-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="2bc31-162">V tomto příkladu je `cust` instancí `Customer`.</span><span class="sxs-lookup"><span data-stu-id="2bc31-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="2bc31-163">Vzhledem k tomu, že příkaz `Select` vytváří anonymní typ, musí být proměnná dotazu `nameCityQuery`, implicitně zadána jako anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="2bc31-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="2bc31-164">Anonymní typ nemá žádný použitelný název, a proto jej nelze zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="2bc31-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="2bc31-165">Typ iterační proměnné ve smyčce `For Each` je anonymní typ vytvořený v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="2bc31-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="2bc31-166">Vzhledem k tomu, že typ nemá žádný použitelný název, je nutné určit typ proměnné iterace smyčky implicitně.</span><span class="sxs-lookup"><span data-stu-id="2bc31-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bc31-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bc31-167">See also</span></span>

- [<span data-ttu-id="2bc31-168">Začínáme pomocí LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bc31-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="2bc31-169">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="2bc31-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="2bc31-170">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="2bc31-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2bc31-171">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bc31-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="2bc31-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="2bc31-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="2bc31-173">Dotazy</span><span class="sxs-lookup"><span data-stu-id="2bc31-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
