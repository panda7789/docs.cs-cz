---
title: Základní operace dotazů (Visual Basic)
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
ms.openlocfilehash: 5ca92324dec1d4fa8885a610a6e246640f4a5752
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973025"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="0d129-102">Základní operace dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d129-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="0d129-103">Toto téma nabízí stručný úvod do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy v jazyce Visual Basic a některé typické druhy operací, které provedete v dotazu.</span><span class="sxs-lookup"><span data-stu-id="0d129-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="0d129-104">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="0d129-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="0d129-105">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d129-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="0d129-106">Dotazy</span><span class="sxs-lookup"><span data-stu-id="0d129-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="0d129-107">Návod: Zápis dotazů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d129-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="0d129-108">Určení zdroje dat (From)</span><span class="sxs-lookup"><span data-stu-id="0d129-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="0d129-109">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, prvním krokem je určení zdroje dat, který chcete zadat dotaz.</span><span class="sxs-lookup"><span data-stu-id="0d129-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="0d129-110">Proto `From` klauzule v dotazu vždy nastane dřív.</span><span class="sxs-lookup"><span data-stu-id="0d129-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="0d129-111">Operátory dotazu vyberte a tvar výsledku založená na typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="0d129-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="0d129-112">`From` Klauzule určuje zdroje dat, `customers`a *proměnnou rozsahu*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="0d129-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="0d129-113">Proměnná rozsahu je jako proměnné iterace smyčky, s tím rozdílem, že ve výrazu dotazu, dojde k žádné skutečné iterace.</span><span class="sxs-lookup"><span data-stu-id="0d129-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="0d129-114">Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz na každý prvek po sobě jdoucích `customers`.</span><span class="sxs-lookup"><span data-stu-id="0d129-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="0d129-115">Protože kompilátor může odvodit typ `cust`, není potřeba explicitně zadat.</span><span class="sxs-lookup"><span data-stu-id="0d129-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="0d129-116">Příklady dotazů zapisovat a nemusíte explicitní zadání, najdete v článku [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="0d129-117">Další informace o tom, jak používat `From` klauzule v jazyce Visual Basic naleznete v tématu [klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="0d129-118">Filtrování dat (Where)</span><span class="sxs-lookup"><span data-stu-id="0d129-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="0d129-119">Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logický výraz.</span><span class="sxs-lookup"><span data-stu-id="0d129-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="0d129-120">Dotaz vrátí pouze prvky, pro které má výraz hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="0d129-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="0d129-121">A `Where` klauzule se používá k provedení filtrování.</span><span class="sxs-lookup"><span data-stu-id="0d129-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="0d129-122">Filtr určuje prvky, které ve zdroji dat chcete zahrnout do výsledné pořadí.</span><span class="sxs-lookup"><span data-stu-id="0d129-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="0d129-123">V následujícím příkladu jsou zahrnuty pouze zákazníci, kteří mají adresu v Londýně.</span><span class="sxs-lookup"><span data-stu-id="0d129-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="0d129-124">Můžete například použít logické operátory `And` a `Or` kombinování výrazů filtru v `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0d129-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="0d129-125">Například pokud chcete vrátit pouze tito zákazníci, kteří jsou z Londýna a jejíž název je Devon, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0d129-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="0d129-126">Chcete-li vrátit zákazníci z Londýna nebo Paříž, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0d129-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="0d129-127">Další informace o tom, jak používat `Where` klauzule v jazyce Visual Basic naleznete v tématu [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="0d129-128">Řazení dat (Order By)</span><span class="sxs-lookup"><span data-stu-id="0d129-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="0d129-129">Často je vhodné seřaďte vrácená data do určitého pořadí.</span><span class="sxs-lookup"><span data-stu-id="0d129-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="0d129-130">`Order By` Klauzule způsobí prvky ve vrácené posloupnosti, která má být seřazená podle určitého pole nebo pole.</span><span class="sxs-lookup"><span data-stu-id="0d129-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="0d129-131">Například následující dotaz řadí výsledky podle `Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0d129-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="0d129-132">Protože `Name` je řetězec, vrácená data se budou řadit abecedně, z A do Z.</span><span class="sxs-lookup"><span data-stu-id="0d129-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="0d129-133">Chcete-li v obráceném pořadí řazení výsledků od Z do A, použijte `Order By...Descending` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0d129-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="0d129-134">Výchozí hodnota je `Ascending` při ani `Ascending` ani `Descending` je zadán.</span><span class="sxs-lookup"><span data-stu-id="0d129-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="0d129-135">Další informace o tom, jak používat `Order By` klauzule v jazyce Visual Basic naleznete v tématu [klauzuli ORDER by](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="0d129-136">Výběr dat (Select)</span><span class="sxs-lookup"><span data-stu-id="0d129-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="0d129-137">`Select` Klauzule určuje formulář opravdu zavřít a obsah vrácených prvků.</span><span class="sxs-lookup"><span data-stu-id="0d129-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="0d129-138">Například můžete určit, zda vaše výsledky se skládají z kompletní `Customer` objekty jen jeden `Customer` vlastnosti, podmnožinu vlastností, kombinací vlastností z různých zdrojů dat, nebo nový typ výsledku na základě výpočtu.</span><span class="sxs-lookup"><span data-stu-id="0d129-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="0d129-139">Když `Select` klauzule vytváří něco jiného než kopii zdrojového elementu, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="0d129-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="0d129-140">K načtení kolekce, která se skládá z kompletní `Customer` objektů, vyberte vlastní proměnnou rozsahu:</span><span class="sxs-lookup"><span data-stu-id="0d129-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="0d129-141">Pokud `Customer` instance je velký objekt, který má velký počet polí, a vše, co chcete načíst je název, můžete vybrat `cust.Name`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0d129-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="0d129-142">Odvození místního typu rozpozná, že změní typ výsledku z kolekce `Customer` objekty kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="0d129-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="0d129-143">Pokud chcete vybrat více polí ze zdroje dat, máte dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="0d129-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="0d129-144">V `Select` klauzule, určete pole, které chcete zahrnout do výsledku.</span><span class="sxs-lookup"><span data-stu-id="0d129-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="0d129-145">Kompilátor bude definovat anonymní typ, který má tato pole jako její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d129-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="0d129-146">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="0d129-147">Protože vrácených prvků v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu jinde ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="0d129-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="0d129-148">Název typu určen kompilátor obsahuje znaky, které nejsou platné v normální kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0d129-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="0d129-149">V následujícím příkladu elementů v kolekci, která je vrácena dotazem v `londonCusts4` jsou instancemi anonymního typu</span><span class="sxs-lookup"><span data-stu-id="0d129-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     <span data-ttu-id="0d129-150">-nebo-</span><span class="sxs-lookup"><span data-stu-id="0d129-150">-or-</span></span>  
  
-   <span data-ttu-id="0d129-151">Definování typu s názvem, který obsahuje konkrétní pole, které chcete zahrnout do výsledku a vytváření a inicializace instancí typu `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0d129-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="0d129-152">Tuto možnost použijte jenom v případě, že budete muset použít jednotlivé výsledky mimo kolekce, ve kterém jsou vráceny, nebo pokud musíte předat jako parametry volání metody.</span><span class="sxs-lookup"><span data-stu-id="0d129-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="0d129-153">Typ `londonCusts5` v následujícím příkladu je IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="0d129-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="0d129-154">Další informace o tom, jak používat `Select` klauzule v jazyce Visual Basic naleznete v tématu [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="0d129-155">Spojování dat (Join a Group Join)</span><span class="sxs-lookup"><span data-stu-id="0d129-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="0d129-156">Můžete zkombinovat více než jeden zdroj dat v `From` klauzule několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="0d129-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="0d129-157">Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="0d129-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="0d129-158">Dotaz vybere studenty, jejichž příjmení začínají samohláskou.</span><span class="sxs-lookup"><span data-stu-id="0d129-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  <span data-ttu-id="0d129-159">Můžete spustit tento kód se seznamem studenti vytvořili v [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="0d129-160">`Join` – Klíčové slovo je ekvivalentní `INNER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="0d129-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="0d129-161">Kombinuje dvě kolekce založené na odpovídající hodnoty klíče mezi prvky ve dvou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="0d129-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="0d129-162">Dotaz vrátí všechny nebo část elementů kolekce, které mají odpovídající hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="0d129-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="0d129-163">Například následující kód duplikuje akce předchozí implicitní spojení.</span><span class="sxs-lookup"><span data-stu-id="0d129-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="0d129-164">`Group Join` kombinuje kolekce do jedné hierarchické kolekce, stejně jako `LEFT JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="0d129-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="0d129-165">Další informace najdete v tématu [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md) a [Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="0d129-166">Seskupování dat (Group By)</span><span class="sxs-lookup"><span data-stu-id="0d129-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="0d129-167">Můžete přidat `Group By` klauzule seskupit elementy ve výsledku dotazu podle polí jednoho nebo více prvků.</span><span class="sxs-lookup"><span data-stu-id="0d129-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="0d129-168">Následující kód například skupiny studentů podle roku třídy.</span><span class="sxs-lookup"><span data-stu-id="0d129-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="0d129-169">Pokud jste spuštění tohoto kódu pomocí seznamu studentů vytvořené v [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup `For Each` příkaz je:</span><span class="sxs-lookup"><span data-stu-id="0d129-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="0d129-170">Rok: Nižší</span><span class="sxs-lookup"><span data-stu-id="0d129-170">Year: Junior</span></span>  
  
 <span data-ttu-id="0d129-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="0d129-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="0d129-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="0d129-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="0d129-173">Garcia Debra</span><span class="sxs-lookup"><span data-stu-id="0d129-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="0d129-174">Tucker Lance</span><span class="sxs-lookup"><span data-stu-id="0d129-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="0d129-175">Rok: Senior</span><span class="sxs-lookup"><span data-stu-id="0d129-175">Year: Senior</span></span>  
  
 <span data-ttu-id="0d129-176">Omelchenko Svetlana</span><span class="sxs-lookup"><span data-stu-id="0d129-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="0d129-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="0d129-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="0d129-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="0d129-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="0d129-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="0d129-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="0d129-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="0d129-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="0d129-181">Rok: Freshman</span><span class="sxs-lookup"><span data-stu-id="0d129-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="0d129-182">Mortensen Sven</span><span class="sxs-lookup"><span data-stu-id="0d129-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="0d129-183">Garcia Cesarovi</span><span class="sxs-lookup"><span data-stu-id="0d129-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="0d129-184">Varianta je znázorněno v následujícím kódu orders let třídy a pak podle příjmení orders studenty v rámci každý rok.</span><span class="sxs-lookup"><span data-stu-id="0d129-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="0d129-185">Další informace o `Group By`, naleznete v tématu [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d129-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d129-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d129-186">See also</span></span>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="0d129-187">Začínáme s dotazy LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d129-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="0d129-188">Dotazy</span><span class="sxs-lookup"><span data-stu-id="0d129-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0d129-189">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d129-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0d129-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="0d129-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
