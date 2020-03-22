---
title: Základní operace dotazů
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266375"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="a7783-102">Základní operace dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7783-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="a7783-103">Toto téma obsahuje stručný úvod do jazykintegrované ho dotazu (LINQ) výrazy v jazyce Visual Basic a některé typické druhy operací, které provádíte v dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7783-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="a7783-104">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="a7783-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="a7783-105">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7783-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="a7783-106">Dotazy</span><span class="sxs-lookup"><span data-stu-id="a7783-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="a7783-107">Návod: Zápis dotazů ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7783-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="a7783-108">Určení zdroje dat (From)</span><span class="sxs-lookup"><span data-stu-id="a7783-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="a7783-109">V dotazu LINQ je prvním krokem určení zdroje dat, na který chcete dotazovat.</span><span class="sxs-lookup"><span data-stu-id="a7783-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="a7783-110">Proto klauzule `From` v dotazu vždy na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="a7783-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="a7783-111">Operátory dotazů vyberou a vytupují výsledek na základě typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="a7783-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="a7783-112">Klauzule `From` určuje zdroj `customers`dat a *proměnnou rozsahu*. `cust`</span><span class="sxs-lookup"><span data-stu-id="a7783-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="a7783-113">Proměnná rozsahu je jako proměnná iterace smyčky, s tím rozdílem, že ve výrazu dotazu nedojde k žádné skutečné iteraci.</span><span class="sxs-lookup"><span data-stu-id="a7783-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="a7783-114">Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz `customers`na každý následující prvek v .</span><span class="sxs-lookup"><span data-stu-id="a7783-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="a7783-115">Vzhledem k tomu, že `cust`kompilátor můžete odvodit typ , není nutné zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="a7783-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="a7783-116">Příklady dotazů napsaných s explicitním psaním a bez něj naleznete [v tématu Type Relationships in Query Operations (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)</span><span class="sxs-lookup"><span data-stu-id="a7783-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="a7783-117">Další informace o použití `From` klauzule v jazyce Visual Basic naleznete v tématu [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="a7783-118">Filtrování dat (Where)</span><span class="sxs-lookup"><span data-stu-id="a7783-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="a7783-119">Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="a7783-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="a7783-120">Dotaz pak vrátí pouze ty prvky, pro které je výraz true.</span><span class="sxs-lookup"><span data-stu-id="a7783-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="a7783-121">Klauzule `Where` se používá k provedení filtrování.</span><span class="sxs-lookup"><span data-stu-id="a7783-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="a7783-122">Filtr určuje, které prvky ve zdroji dat mají být zahrnuty do výsledné sekvence.</span><span class="sxs-lookup"><span data-stu-id="a7783-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="a7783-123">V následujícím příkladu jsou zahrnuty pouze zákazníci, kteří mají adresu v Londýně.</span><span class="sxs-lookup"><span data-stu-id="a7783-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="a7783-124">Můžete použít logické operátory, jako `And` jsou a `Where` `Or` kombinovat výrazy filtru v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a7783-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="a7783-125">Chcete-li například vrátit pouze zákazníky, kteří jsou z Londýna a jejichž jméno je Devon, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="a7783-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="a7783-126">Chcete-li vrátit zákazníkům z Londýna nebo Paříže, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="a7783-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="a7783-127">Další informace o použití `Where` klauzule v jazyce Visual Basic naleznete v tématu [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="a7783-128">Řazení dat (Order By)</span><span class="sxs-lookup"><span data-stu-id="a7783-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="a7783-129">Často je vhodné seřadit vrácená data do určitého pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7783-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="a7783-130">Klauzule `Order By` způsobí, že prvky ve vrácené sekvenci budou seřazeny podle zadaného pole nebo polí.</span><span class="sxs-lookup"><span data-stu-id="a7783-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="a7783-131">Například následující dotaz seřadí výsledky `Name` na základě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a7783-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="a7783-132">Protože `Name` je řetězec, vrácená data budou seřazena abecedně, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="a7783-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="a7783-133">Chcete-li výsledky seřadit v opačném pořadí `Order By...Descending` od Z do A, použijte klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a7783-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="a7783-134">Výchozí hodnota `Ascending` je, `Ascending` `Descending` když ani není zadán.</span><span class="sxs-lookup"><span data-stu-id="a7783-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="a7783-135">Další informace o použití `Order By` klauzule v jazyce Visual Basic naleznete v [tématu Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="a7783-136">Výběr dat (Select)</span><span class="sxs-lookup"><span data-stu-id="a7783-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="a7783-137">Klauzule `Select` určuje formu a obsah vrácených prvků.</span><span class="sxs-lookup"><span data-stu-id="a7783-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="a7783-138">Můžete například určit, zda se výsledky `Customer` budou skládat z úplných objektů, pouze z jedné `Customer` vlastnosti, podmnožiny vlastností, kombinace vlastností z různých zdrojů dat nebo z nějakého nového typu výsledku založeného na výpočtu.</span><span class="sxs-lookup"><span data-stu-id="a7783-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="a7783-139">Když `Select` klauzule vytvoří něco jiného než kopii zdrojového prvku, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="a7783-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="a7783-140">Chcete-li načíst kolekci, která se skládá z úplných `Customer` objektů, vyberte samotnou proměnnou rozsahu:</span><span class="sxs-lookup"><span data-stu-id="a7783-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a7783-141">Pokud `Customer` je instance velký objekt, který má mnoho polí a vše, co `cust.Name`chcete načíst, je název, můžete vybrat , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a7783-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="a7783-142">Odvození místního typu rozpozná, že to změní `Customer` typ výsledku z kolekce objektů na kolekci řetězců.</span><span class="sxs-lookup"><span data-stu-id="a7783-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a7783-143">Chcete-li vybrat více polí ze zdroje dat, máte dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="a7783-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="a7783-144">V `Select` klauzuli zadejte pole, která chcete zahrnout do výsledku.</span><span class="sxs-lookup"><span data-stu-id="a7783-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="a7783-145">Kompilátor definuje anonymní typ, který má tato pole jako jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a7783-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="a7783-146">Další informace naleznete [v tématu Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="a7783-147">Vzhledem k tomu, že vrácené prvky v následujícím příkladu jsou instance anonymního typu, nelze odkazovat na typ podle názvu jinde v kódu.</span><span class="sxs-lookup"><span data-stu-id="a7783-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="a7783-148">Název typu určený kompilátorem obsahuje znaky, které nejsou platné v normálním kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7783-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="a7783-149">V následujícím příkladu jsou prvky v kolekci, `londonCusts4` které jsou vráceny dotazem v instancí anonymního typu</span><span class="sxs-lookup"><span data-stu-id="a7783-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="a7783-150">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a7783-150">-or-</span></span>  
  
- <span data-ttu-id="a7783-151">Definujte pojmenovaný typ, který obsahuje konkrétní pole, která chcete zahrnout do výsledku, a `Select` vytvořte a inicializujte instance typu v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a7783-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="a7783-152">Tuto možnost použijte pouze v případě, že máte použít jednotlivé výsledky mimo kolekci, ve které jsou vráceny, nebo pokud je musíte předat jako parametry ve volání metod.</span><span class="sxs-lookup"><span data-stu-id="a7783-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="a7783-153">Typ `londonCusts5` v následujícím příkladu je IEnumerable(Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="a7783-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="a7783-154">Další informace o použití `Select` klauzule v jazyce Visual Basic naleznete v [tématu Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="a7783-155">Spojování dat (Join a Group Join)</span><span class="sxs-lookup"><span data-stu-id="a7783-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="a7783-156">V klauzuli `From` můžete zkombinovat více než jeden zdroj dat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="a7783-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="a7783-157">Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="a7783-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="a7783-158">Dotaz vybere studenty, jejichž příjmení začíná samohláská.</span><span class="sxs-lookup"><span data-stu-id="a7783-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="a7783-159">Tento kód můžete spustit se seznamem studentů vytvořeným v [části Postup: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="a7783-160">Klíčové `Join` slovo je `INNER JOIN` ekvivalentní v SQL.</span><span class="sxs-lookup"><span data-stu-id="a7783-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="a7783-161">Kombinuje dvě kolekce založené na odpovídající hodnoty klíče mezi prvky v obou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="a7783-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="a7783-162">Dotaz vrátí všechny nebo část kolekce prvků, které mají odpovídající hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="a7783-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="a7783-163">Například následující kód duplikuje akci předchozího implicitního spojení.</span><span class="sxs-lookup"><span data-stu-id="a7783-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="a7783-164">`Group Join`kombinuje kolekce do jedné hierarchické kolekce, `LEFT JOIN` stejně jako v SQL.</span><span class="sxs-lookup"><span data-stu-id="a7783-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="a7783-165">Další informace naleznete v [tématu Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) a [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="a7783-166">Seskupování dat (Group By)</span><span class="sxs-lookup"><span data-stu-id="a7783-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="a7783-167">Můžete přidat `Group By` klauzuli seskupit prvky ve výsledku dotazu podle jednoho nebo více polí prvků.</span><span class="sxs-lookup"><span data-stu-id="a7783-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="a7783-168">Například následující kód seskupuje studenty podle roku třídy.</span><span class="sxs-lookup"><span data-stu-id="a7783-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="a7783-169">Pokud spustíte tento kód pomocí seznamu studentů vytvořených v [části Postup: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup z příkazu `For Each` je:</span><span class="sxs-lookup"><span data-stu-id="a7783-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="a7783-170">Rok: Junior</span><span class="sxs-lookup"><span data-stu-id="a7783-170">Year: Junior</span></span>  
  
 <span data-ttu-id="a7783-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="a7783-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="a7783-172">Garciová, Hugo</span><span class="sxs-lookup"><span data-stu-id="a7783-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="a7783-173">Garciová, Debra</span><span class="sxs-lookup"><span data-stu-id="a7783-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="a7783-174">Tucker, Kopí</span><span class="sxs-lookup"><span data-stu-id="a7783-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="a7783-175">Rok: Senior</span><span class="sxs-lookup"><span data-stu-id="a7783-175">Year: Senior</span></span>  
  
 <span data-ttu-id="a7783-176">Omelčenko, Světlana</span><span class="sxs-lookup"><span data-stu-id="a7783-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="a7783-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="a7783-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="a7783-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="a7783-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="a7783-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="a7783-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="a7783-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="a7783-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="a7783-181">Rok: Prvák</span><span class="sxs-lookup"><span data-stu-id="a7783-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="a7783-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="a7783-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="a7783-183">Garciová, Cesar</span><span class="sxs-lookup"><span data-stu-id="a7783-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="a7783-184">Odchylka uvedená v následujícím kódu objednává ročníky a poté objednává studenty v rámci každého roku podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="a7783-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a7783-185">Další informace `Group By`naleznete v [tématu Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7783-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7783-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7783-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="a7783-187">Začínáme s dotazy LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7783-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="a7783-188">Dotazy</span><span class="sxs-lookup"><span data-stu-id="a7783-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a7783-189">Standardní operátory dotazů – přehled (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7783-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a7783-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="a7783-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
