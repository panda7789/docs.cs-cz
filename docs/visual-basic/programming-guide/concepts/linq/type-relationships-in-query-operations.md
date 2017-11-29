---
title: "Vztahy typů v operacích dotazu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b93188475dd2bb00aea044ff178028eb87e00d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="50af1-102">Vztahy typů v operacích dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50af1-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="50af1-103">Proměnné používané v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotazu operace jsou silného typu a musí být vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="50af1-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="50af1-104">Silného typování se používá ve zdroji dat, v samotném dotazu a při provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="50af1-105">Na následujícím obrázku identifikuje termínů používaných k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="50af1-106">Další informace o části dotazu najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="50af1-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="50af1-107">![Dotaz pseudokódu se zvýrazněnými elementy. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="50af1-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="50af1-108">Části dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="50af1-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="50af1-109">Typ proměnné rozsahu v dotazu musí být kompatibilní s typem elementů ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="50af1-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="50af1-110">Typ proměnné dotazu musí být kompatibilní s element pořadí definovaný v `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="50af1-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="50af1-111">Nakonec typ pořadí elementů také musí být kompatibilní s typem řídicí proměnná smyčky, který se používá v `For Each` příkaz, který provede daný dotaz.</span><span class="sxs-lookup"><span data-stu-id="50af1-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="50af1-112">Tato silného typování usnadňuje identifikace typu chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="50af1-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="50af1-113">Díky silného typování pohodlný implementací odvození místního typu, také známé jako *implicitní zadáním*.</span><span class="sxs-lookup"><span data-stu-id="50af1-113"> makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="50af1-114">Funkce používá v předchozím příkladu, a zobrazí se jeho používaných v celém [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentace.</span><span class="sxs-lookup"><span data-stu-id="50af1-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="50af1-115">V jazyce Visual Basic odvození místního typu dosahuje jednoduše pomocí `Dim` příkaz bez `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="50af1-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="50af1-116">V následujícím příkladu `city` silného jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="50af1-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="50af1-117">Odvození místního typu funguje pouze tehdy, když `Option Infer` je nastaven na `On`.</span><span class="sxs-lookup"><span data-stu-id="50af1-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="50af1-118">Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="50af1-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="50af1-119">Ale i v případě, že používáte odvození místního typu v dotazu, stejný typ relace nejsou mezi proměnné ve zdroji dat, proměnné dotazu a cyklus zpracování dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="50af1-120">Je užitečné při psaní mají základní znalosti o tyto relace typu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy nebo práci s ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="50af1-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="50af1-121">Musíte zadat explicitní typ pro proměnnou rozsahu, která se neshoduje s typem vráceným ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="50af1-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="50af1-122">Můžete určit typ proměnné rozsahu pomocí `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="50af1-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="50af1-123">Ale to vede k chybě pokud převod [zužující převod](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastaven na `On`.</span><span class="sxs-lookup"><span data-stu-id="50af1-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="50af1-124">Proto doporučujeme provést převod na hodnoty získané z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="50af1-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="50af1-125">Hodnoty můžete převést ze zdroje dat na typ proměnné rozsahu explicitní pomocí <xref:System.Linq.Enumerable.Cast%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="50af1-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="50af1-126">Můžete také obsadit hodnot vybraných v `Select` klauzule explicitní typ, který je odlišný od typu proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="50af1-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="50af1-127">Tyto body jsou znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="50af1-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="50af1-128">Dotazy, které vracejí celý elementy zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="50af1-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="50af1-129">Následující příklad ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operace, která vrací posloupnost elementy vybrané ze zdrojových dat dotazů.</span><span class="sxs-lookup"><span data-stu-id="50af1-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="50af1-130">Zdroje, `names`, obsahuje pole řetězců, a výstupu dotazu je posloupnost obsahující řetězce, které začínají písmeno M.</span><span class="sxs-lookup"><span data-stu-id="50af1-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 <span data-ttu-id="50af1-131">To je ekvivalentní následující kód, ale je mnohem kratší a psát.</span><span class="sxs-lookup"><span data-stu-id="50af1-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="50af1-132">Závislá na odvození místního typu v dotazech je upřednostňovaný styl v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="50af1-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 <span data-ttu-id="50af1-133">V obou předchozích ukázky kódu, existují následující relace, zda typy jsou určeny implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="50af1-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="50af1-134">Typ elementů ve zdroji dat `names`, je typ proměnné rozsahu `name`, v dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="50af1-135">Typ objektu, který je vybraný `name`, určuje typ proměnné dotazu `mNames`.</span><span class="sxs-lookup"><span data-stu-id="50af1-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="50af1-136">Zde `name` je řetězec, proměnné v dotazu je rozhraní IEnumerable (Of String) v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="50af1-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="50af1-137">Dotaz definované v `mNames` se spouštějí v tom `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="50af1-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="50af1-138">Smyčky iteruje nad výsledek provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="50af1-139">Protože `mNames`, když je proveden, vrátí pořadí řetězců, proměnné iterace smyčky, `nm`, také obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="50af1-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="50af1-140">Dotazy, které vrátí jedno pole z vybrané elementy</span><span class="sxs-lookup"><span data-stu-id="50af1-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="50af1-141">Následující příklad ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operace, která vrací posloupnost obsahující pouze jednu část jednotlivých prvků vybrané ze zdroje dat dotazů.</span><span class="sxs-lookup"><span data-stu-id="50af1-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="50af1-142">Dotaz vezme kolekci `Customer` objektů jako svůj zdroj dat a projekty pouze `Name` vlastnost ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="50af1-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="50af1-143">Protože jméno zákazníka je řetězec, vytvoří dotaz posloupnost řetězce jako výstup.</span><span class="sxs-lookup"><span data-stu-id="50af1-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="50af1-144">Vztahy mezi proměnné jsou stejně jako v příkladu jednodušší.</span><span class="sxs-lookup"><span data-stu-id="50af1-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="50af1-145">Typ elementů ve zdroji dat `customers`, je typ proměnné rozsahu `cust`, v dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="50af1-146">V tomto příkladu, který je typu `Customer`.</span><span class="sxs-lookup"><span data-stu-id="50af1-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="50af1-147">`Select` Příkaz vrátí `Name` vlastnost jednotlivých `Customer` objektu, nikoli celý objekt.</span><span class="sxs-lookup"><span data-stu-id="50af1-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="50af1-148">Protože `Name` je řetězec dotazu proměnné `custNames`, bude znovu být IEnumerable (Of String), není `Customer`.</span><span class="sxs-lookup"><span data-stu-id="50af1-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="50af1-149">Protože `custNames` představuje posloupnost řetězce, `For Each` proměnné iterace smyčky, `custName`, musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="50af1-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="50af1-150">Bez odvození místního typu bude předchozí příklad těžkopádnější zápisu a pochopit, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="50af1-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="50af1-151">Dotazy, které vyžadují anonymní typy</span><span class="sxs-lookup"><span data-stu-id="50af1-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="50af1-152">Následující příklad ukazuje složitější situaci.</span><span class="sxs-lookup"><span data-stu-id="50af1-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="50af1-153">V předchozím příkladu bylo nepraktické explicitně určit typy pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="50af1-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="50af1-154">V tomto příkladu není možné.</span><span class="sxs-lookup"><span data-stu-id="50af1-154">In this example, it is impossible.</span></span> <span data-ttu-id="50af1-155">Místo výběru celé `Customer` elementy ze zdroje dat nebo jediné pole z jednotlivých prvků `Select` klauzule v tomto dotazu vrátí dvě vlastnosti původního `Customer` objekt: `Name` a `City`.</span><span class="sxs-lookup"><span data-stu-id="50af1-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="50af1-156">V reakci `Select` klauzuli kompilátor definuje anonymní typ, který obsahuje tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50af1-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="50af1-157">Výsledek provedení `nameCityQuery` v `For Each` smyčka je kolekci instancí nového anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="50af1-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="50af1-158">Protože anonymní typ nemá žádný použitelný název, nemůžete zadat typ `nameCityQuery` nebo `custInfo` explicitně.</span><span class="sxs-lookup"><span data-stu-id="50af1-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="50af1-159">To znamená, s anonymní typ, máte název typu používat místě `String` v `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="50af1-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="50af1-160">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="50af1-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="50af1-161">I když není možné určit typy pro všechny proměnné v předchozím příkladu, vztahy zůstávají stejné.</span><span class="sxs-lookup"><span data-stu-id="50af1-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="50af1-162">Typ elementů ve zdroji dat je znovu typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="50af1-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="50af1-163">V tomto příkladu `cust` je instance `Customer`.</span><span class="sxs-lookup"><span data-stu-id="50af1-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="50af1-164">Protože `Select` příkaz vytvoří instanci anonymního typu proměnnou dotazu `nameCityQuery`, musí být zadán implicitně jako anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="50af1-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="50af1-165">Anonymní typ nemá žádný použitelný název a proto nemůže být explicitně určen.</span><span class="sxs-lookup"><span data-stu-id="50af1-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="50af1-166">Typ proměnné iterace ve `For Each` smyčka je anonymní typ vytvořili v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="50af1-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="50af1-167">Vzhledem k tomu, že typ nemá žádný použitelný název, typ proměnné iterace smyčky musí určit implicitně.</span><span class="sxs-lookup"><span data-stu-id="50af1-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50af1-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="50af1-168">See Also</span></span>  
 [<span data-ttu-id="50af1-169">Začínáme s dotazy LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50af1-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="50af1-170">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="50af1-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="50af1-171">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="50af1-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="50af1-172">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50af1-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="50af1-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="50af1-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="50af1-174">Dotazy</span><span class="sxs-lookup"><span data-stu-id="50af1-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
