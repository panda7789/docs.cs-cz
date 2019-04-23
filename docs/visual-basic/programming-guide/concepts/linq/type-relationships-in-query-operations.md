---
title: Vztahy typů v operacích dotazu (Visual Basic)
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
ms.openlocfilehash: 14f17e89e2a4143580b4a2ca7f9d30013ded58f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327630"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="4eb16-102">Vztahy typů v operacích dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eb16-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="4eb16-103">Proměnné použité v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotazu operace jsou silného typu a musí být navzájem kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4eb16-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="4eb16-104">Silné typování se používá ve zdroji dat, v samotném dotazu a ve spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="4eb16-105">Následující obrázek označuje termíny používané k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="4eb16-106">Další informace o části dotazu, naleznete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4eb16-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 ![Snímek obrazovky zobrazující pseudokódu dotazu se zvýrazněnými elementy.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 <span data-ttu-id="4eb16-108">Musí být kompatibilní s typem prvků ve zdroji dat typu proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="4eb16-109">Typ proměnné dotazu musí být kompatibilní s pořadí element definovaný v `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4eb16-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="4eb16-110">Nakonec typu pořadí elementů také musí být kompatibilní s typem řídicí proměnná smyčky for, který se používá v `For Each` příkaz, který provede daný dotaz.</span><span class="sxs-lookup"><span data-stu-id="4eb16-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="4eb16-111">Silné typování usnadňuje identifikaci chyby typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4eb16-111">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="4eb16-112">Visual Basic umožňuje silného typování pohodlný implementací odvození místního typu, označované také jako *implicitního zápisu*.</span><span class="sxs-lookup"><span data-stu-id="4eb16-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="4eb16-113">Že v předchozím příkladu se používá funkce, a zobrazí se používá v rámci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4eb16-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="4eb16-114">V jazyce Visual Basic, se jednoduše tak, že pomocí provádí odvození místního typu `Dim` příkaz bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4eb16-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="4eb16-115">V následujícím příkladu `city` je silně typováno jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="4eb16-115">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="4eb16-116">Odvození místního typu funguje pouze tehdy, když `Option Infer` je nastavena na `On`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="4eb16-117">Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4eb16-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="4eb16-118">Ale i v případě použití odvození místního typu v dotazu, stejný typ relace jsou k dispozici mezi proměnné ve zdroji dat, proměnná dotazu a smyčka provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="4eb16-119">Je užitečné mít základní znalosti o těchto vztahů typů, když vytváříte [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy nebo práce s ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4eb16-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="4eb16-120">Budete muset zadat explicitní typ pro proměnnou rozsahu, který typ vrácený ze zdroje dat se neshoduje.</span><span class="sxs-lookup"><span data-stu-id="4eb16-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="4eb16-121">Druh proměnné rozsahu můžete zadat pomocí `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4eb16-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="4eb16-122">Nicméně to způsobí chybu při převodu [zužující převod](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastavena na `On`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="4eb16-123">Proto doporučujeme provést převod na hodnoty získané ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4eb16-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="4eb16-124">Hodnoty lze převést ze zdroje dat na typ proměnné explicitního rozsahu pomocí <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4eb16-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="4eb16-125">Můžete také přetypování hodnoty vybrané v `Select` klauzule explicitního typu, který se liší od typu proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="4eb16-126">Tyto body jsou znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-126">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="4eb16-127">Dotazy vracející celé prvky zdroje dat</span><span class="sxs-lookup"><span data-stu-id="4eb16-127">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="4eb16-128">Následující příklad ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operaci, která vrátí sekvenci prvků vybrané ze zdroje dat dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="4eb16-129">Zdroj, `names`, obsahuje pole řetězců a výstup dotazu je sekvence obsahující řetězce, které začínají písmenem M.</span><span class="sxs-lookup"><span data-stu-id="4eb16-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 <span data-ttu-id="4eb16-130">To je ekvivalentní následujícímu kódu, ale je mnohem kratší a jednodušší pro zápis.</span><span class="sxs-lookup"><span data-stu-id="4eb16-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="4eb16-131">Závislost na odvození místního typu v dotazech je upřednostňovaný stylu v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4eb16-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4eb16-132">V obou předchozí příklady kódu, existují následující relace, zda typy jsou určeny implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="4eb16-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1. <span data-ttu-id="4eb16-133">Typ prvků ve zdroji dat `names`, je druh proměnné rozsahu `name`, v dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2. <span data-ttu-id="4eb16-134">Typ objektu, který je vybrán, `name`, určuje typ proměnné dotazu `mNames`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="4eb16-135">Tady `name` je řetězec, proměnná dotazu je IEnumerable (Of String) v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4eb16-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3. <span data-ttu-id="4eb16-136">Dotaz definovaný v `mNames` se provádí `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="4eb16-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="4eb16-137">Smyčky Iteruje přes výsledek provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="4eb16-138">Protože `mNames`, pokud je spuštěn, vrátí sekvencí řetězců, iterační proměnná smyčky `nm`, je také řetězec.</span><span class="sxs-lookup"><span data-stu-id="4eb16-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="4eb16-139">Dotazy, které vracejí jedno pole z vybraných elementů</span><span class="sxs-lookup"><span data-stu-id="4eb16-139">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="4eb16-140">Následující příklad ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci, která vrátí sekvenci, který obsahuje pouze jednu část každý prvek vybrané ze zdroje dat dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="4eb16-141">Dotaz vezme kolekci `Customer` objektů jako svůj zdroj dat a pouze pro projekty `Name` vlastnosti ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="4eb16-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="4eb16-142">Protože název zákazníka je řetězec, dotaz vyprodukuje sekvenci řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="4eb16-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="4eb16-143">Vztahy mezi proměnné jsou podobné těm v příkladu jednodušší.</span><span class="sxs-lookup"><span data-stu-id="4eb16-143">The relationships between variables are like those in the simpler example.</span></span>  
  
1. <span data-ttu-id="4eb16-144">Typ prvků ve zdroji dat `customers`, je druh proměnné rozsahu `cust`, v dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="4eb16-145">V tomto příkladu, který je typu `Customer`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-145">In this example, that type is `Customer`.</span></span>  
  
2. <span data-ttu-id="4eb16-146">`Select` Příkaz vrátí `Name` vlastnosti každého `Customer` objektu, nikoli celý objekt.</span><span class="sxs-lookup"><span data-stu-id="4eb16-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="4eb16-147">Protože `Name` řetězce, proměnná dotazu je `custNames`, bude znovu nebyl IEnumerable (Of String) o `Customer`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3. <span data-ttu-id="4eb16-148">Protože `custNames` představuje posloupnost řetězců, `For Each` iterační proměnná smyčky `custName`, musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="4eb16-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="4eb16-149">Bez odvození místního typu v předchozím příkladu by těžkopádnější k zápisu a informace o tom, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4eb16-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="4eb16-150">Dotazy, které vyžadují anonymní typy</span><span class="sxs-lookup"><span data-stu-id="4eb16-150">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="4eb16-151">Následující příklad ukazuje mnohem složitější situace.</span><span class="sxs-lookup"><span data-stu-id="4eb16-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="4eb16-152">V předchozím příkladu bylo nepraktické explicitně určit typy všech proměnných.</span><span class="sxs-lookup"><span data-stu-id="4eb16-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="4eb16-153">V tomto příkladu je nemožné.</span><span class="sxs-lookup"><span data-stu-id="4eb16-153">In this example, it is impossible.</span></span> <span data-ttu-id="4eb16-154">Místo výběru celé `Customer` elementy ze zdroje dat, nebo jedno pole z každého prvku `Select` klauzule v tomto dotazu vrátí dvě vlastnosti původní `Customer` objektu: `Name` a `City`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="4eb16-155">V reakci `Select` klauzule, kompilátor definuje anonymního typu, který obsahuje tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4eb16-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="4eb16-156">Výsledek provedení `nameCityQuery` v `For Each` smyčky je kolekci instancí novém anonymním typu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="4eb16-157">Protože anonymního typu nemá žádný použitelný název, nelze zadat typ `nameCityQuery` nebo `custInfo` explicitně.</span><span class="sxs-lookup"><span data-stu-id="4eb16-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="4eb16-158">To znamená, pomocí anonymního typu, máte název bez typu použít místo `String` v `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="4eb16-159">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4eb16-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="4eb16-160">Ačkoli to není možné určit typy pro všechny proměnné v předchozím příkladu, vztahy zůstávají stejné.</span><span class="sxs-lookup"><span data-stu-id="4eb16-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1. <span data-ttu-id="4eb16-161">Typ prvků ve zdroji dat je znovu typu proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="4eb16-162">V tomto příkladu `cust` je instance `Customer`.</span><span class="sxs-lookup"><span data-stu-id="4eb16-162">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2. <span data-ttu-id="4eb16-163">Protože `Select` příkaz produkuje anonymní typ, proměnná dotazu `nameCityQuery`, musí být implicitně typované jako anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="4eb16-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="4eb16-164">Anonymní typ nemá žádný použitelný název a proto nelze zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="4eb16-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3. <span data-ttu-id="4eb16-165">Typ proměnné iterace ve `For Each` smyčky je anonymní typ vytvořili v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="4eb16-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="4eb16-166">Vzhledem k tomu, že typ nemá žádný použitelný název, třeba implicitně určit typ proměnné iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="4eb16-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb16-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4eb16-167">See also</span></span>

- [<span data-ttu-id="4eb16-168">Začínáme s dotazy LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4eb16-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="4eb16-169">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="4eb16-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="4eb16-170">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="4eb16-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="4eb16-171">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4eb16-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4eb16-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="4eb16-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="4eb16-173">Dotazy</span><span class="sxs-lookup"><span data-stu-id="4eb16-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
