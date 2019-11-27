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
ms.openlocfilehash: e9a646d60bb22507f4c6bcbcdf9222fd0ed18f02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345753"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="2f978-102">Základní operace dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f978-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="2f978-103">Toto téma poskytuje stručný úvod do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazů v Visual Basic a některé z typických druhů operací, které v dotazu provedete.</span><span class="sxs-lookup"><span data-stu-id="2f978-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="2f978-104">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="2f978-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="2f978-105">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f978-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="2f978-106">Dotazy</span><span class="sxs-lookup"><span data-stu-id="2f978-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="2f978-107">Návod: zápis dotazů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f978-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="2f978-108">Určení zdroje dat (From)</span><span class="sxs-lookup"><span data-stu-id="2f978-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="2f978-109">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu je prvním krokem určení zdroje dat, který chcete dotazovat.</span><span class="sxs-lookup"><span data-stu-id="2f978-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="2f978-110">Proto je klauzule `From` v dotazu vždy první.</span><span class="sxs-lookup"><span data-stu-id="2f978-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="2f978-111">Operátory dotazu vyberou a tvarují výsledek na základě typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="2f978-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2f978-112">Klauzule `From` Určuje zdroj dat, `customers`a *proměnnou rozsahu*`cust`.</span><span class="sxs-lookup"><span data-stu-id="2f978-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="2f978-113">Proměnná rozsahu je jako proměnná iterace smyčky, s výjimkou toho, že ve výrazu dotazu není k dispozici žádná skutečná iterace.</span><span class="sxs-lookup"><span data-stu-id="2f978-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="2f978-114">Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz na každý po sobě jdoucí prvek v `customers`.</span><span class="sxs-lookup"><span data-stu-id="2f978-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="2f978-115">Protože kompilátor může odvodit typ `cust`, nemusíte ho explicitně určovat.</span><span class="sxs-lookup"><span data-stu-id="2f978-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="2f978-116">Příklady dotazů napsaných pomocí a bez explicitního zadávání najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="2f978-117">Další informace o použití klauzule `From` v Visual Basic naleznete v části [from klauzule](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="2f978-118">Filtrování dat (Where)</span><span class="sxs-lookup"><span data-stu-id="2f978-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="2f978-119">Pravděpodobně nejběžnější operace dotazu používá filtr ve formě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="2f978-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="2f978-120">Dotaz pak vrátí pouze prvky, pro které je výraz pravdivý.</span><span class="sxs-lookup"><span data-stu-id="2f978-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="2f978-121">K provedení filtrování se používá klauzule `Where`.</span><span class="sxs-lookup"><span data-stu-id="2f978-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="2f978-122">Filtr určuje, které prvky ve zdroji dat mají být zahrnuty ve výsledné sekvenci.</span><span class="sxs-lookup"><span data-stu-id="2f978-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="2f978-123">V následujícím příkladu jsou zahrnuti pouze zákazníci, kteří mají adresu v Londýně.</span><span class="sxs-lookup"><span data-stu-id="2f978-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2f978-124">Pomocí logických operátorů, jako je například `And` a `Or`, lze kombinovat výrazy filtru v klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="2f978-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="2f978-125">Pokud například chcete vracet pouze ty zákazníky, kteří jsou z Londýna a jejichž název je Devon, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2f978-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="2f978-126">Chcete-li vracet zákazníky z Brna nebo Paříž, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2f978-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="2f978-127">Další informace o použití klauzule `Where` v Visual Basic naleznete v tématu [Where klauzule](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="2f978-128">Řazení dat (Order By)</span><span class="sxs-lookup"><span data-stu-id="2f978-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="2f978-129">Často je vhodné řadit vracená data do konkrétního pořadí.</span><span class="sxs-lookup"><span data-stu-id="2f978-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="2f978-130">Klauzule `Order By` způsobí, že prvky v vrácené sekvenci budou seřazeny podle zadaného pole nebo polí.</span><span class="sxs-lookup"><span data-stu-id="2f978-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="2f978-131">Například následující dotaz seřadí výsledky na základě vlastnosti `Name`.</span><span class="sxs-lookup"><span data-stu-id="2f978-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="2f978-132">Vzhledem k tomu, že `Name` je řetězec, vrácená data budou řazena abecedně, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="2f978-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="2f978-133">Pro seřazení výsledků v opačném pořadí z Z na a použijte klauzuli `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="2f978-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="2f978-134">Výchozí hodnota je `Ascending`, pokud není zadána žádná `Ascending` ani `Descending`.</span><span class="sxs-lookup"><span data-stu-id="2f978-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="2f978-135">Další informace o použití klauzule `Order By` v Visual Basic naleznete v tématu [ORDER by klauzule](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="2f978-136">Výběr dat (Select)</span><span class="sxs-lookup"><span data-stu-id="2f978-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="2f978-137">Klauzule `Select` určuje formulář a obsah vrácených elementů.</span><span class="sxs-lookup"><span data-stu-id="2f978-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="2f978-138">Například můžete určit, zda budou výsledky tvořit kompletní `Customer` objekty, jenom jednu `Customer` vlastnost, podmnožinu vlastností, kombinaci vlastností z různých zdrojů dat nebo některý nový typ výsledku na základě výpočtu.</span><span class="sxs-lookup"><span data-stu-id="2f978-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="2f978-139">Když klauzule `Select` vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*.</span><span class="sxs-lookup"><span data-stu-id="2f978-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="2f978-140">Chcete-li načíst kolekci, která se skládá z kompletních objektů `Customer`, vyberte proměnnou rozsahu:</span><span class="sxs-lookup"><span data-stu-id="2f978-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2f978-141">Pokud je instance `Customer` velký objekt, který má mnoho polí a všechny, které chcete načíst, je název, můžete vybrat `cust.Name`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2f978-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="2f978-142">Odvození místního typu rozpoznává, že se změní výsledný typ z kolekce `Customer` objektů na kolekci řetězců.</span><span class="sxs-lookup"><span data-stu-id="2f978-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2f978-143">Chcete-li vybrat více polí ze zdroje dat, máte dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="2f978-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="2f978-144">V klauzuli `Select` zadejte pole, která chcete zahrnout do výsledku.</span><span class="sxs-lookup"><span data-stu-id="2f978-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="2f978-145">Kompilátor definuje anonymní typ, který bude mít tato pole jako své vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2f978-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="2f978-146">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="2f978-147">Vzhledem k tomu, že vrácené elementy v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu jinde v kódu.</span><span class="sxs-lookup"><span data-stu-id="2f978-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="2f978-148">Název určený pro kompilátor pro typ obsahuje znaky, které nejsou platné v normálním Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="2f978-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="2f978-149">V následujícím příkladu jsou elementy v kolekci, které jsou vráceny dotazem v `londonCusts4` instance anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="2f978-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="2f978-150">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2f978-150">-or-</span></span>  
  
- <span data-ttu-id="2f978-151">Definujte pojmenovaný typ, který obsahuje konkrétní pole, která chcete zahrnout do výsledku, a vytvořte a inicializujte instance typu v klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="2f978-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="2f978-152">Tuto možnost použijte pouze v případě, že je nutné použít jednotlivé výsledky mimo kolekci, ve které jsou vráceny, nebo pokud je třeba je předat jako parametry v volání metody.</span><span class="sxs-lookup"><span data-stu-id="2f978-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="2f978-153">Typ `londonCusts5` v následujícím příkladu je IEnumerable (of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="2f978-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2f978-154">Další informace o použití klauzule `Select` v Visual Basic naleznete v tématu [Select klauzule](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="2f978-155">Spojování dat (Join a Group Join)</span><span class="sxs-lookup"><span data-stu-id="2f978-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="2f978-156">V několika způsobech můžete zkombinovat více než jeden zdroj dat v klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="2f978-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="2f978-157">Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="2f978-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="2f978-158">Dotaz vybírá studenty, jejichž příjmení začínají znakem samohlásky.</span><span class="sxs-lookup"><span data-stu-id="2f978-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="2f978-159">Tento kód můžete spustit se seznamem studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="2f978-160">Klíčové slovo `Join` je ekvivalentní `INNER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="2f978-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="2f978-161">Kombinuje dvě kolekce na základě shodných klíčových hodnot mezi prvky ve dvou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="2f978-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="2f978-162">Dotaz vrátí všechny prvky kolekce nebo jejich část, které mají odpovídající hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="2f978-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="2f978-163">Například následující kód duplikuje akci předchozího implicitního spojení.</span><span class="sxs-lookup"><span data-stu-id="2f978-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="2f978-164">`Group Join` kombinuje kolekce do jedné hierarchické kolekce, stejně jako `LEFT JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="2f978-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="2f978-165">Další informace najdete v tématu [klauzule JOIN](../../../../visual-basic/language-reference/queries/join-clause.md) a [klauzule Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="2f978-166">Seskupování dat (Group By)</span><span class="sxs-lookup"><span data-stu-id="2f978-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="2f978-167">Můžete přidat klauzuli `Group By` pro seskupení prvků ve výsledku dotazu podle jednoho nebo více polí prvků.</span><span class="sxs-lookup"><span data-stu-id="2f978-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="2f978-168">Například následující kód seskupuje studenty podle třídy year.</span><span class="sxs-lookup"><span data-stu-id="2f978-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="2f978-169">Pokud spustíte tento kód pomocí seznamu studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup z příkazu `For Each` je:</span><span class="sxs-lookup"><span data-stu-id="2f978-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="2f978-170">Rok: méně</span><span class="sxs-lookup"><span data-stu-id="2f978-170">Year: Junior</span></span>  
  
 <span data-ttu-id="2f978-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="2f978-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="2f978-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="2f978-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="2f978-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="2f978-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="2f978-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="2f978-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="2f978-175">Rok: vedoucí</span><span class="sxs-lookup"><span data-stu-id="2f978-175">Year: Senior</span></span>  
  
 <span data-ttu-id="2f978-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="2f978-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="2f978-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="2f978-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="2f978-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="2f978-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="2f978-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="2f978-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="2f978-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="2f978-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="2f978-181">Rok: čerstvá</span><span class="sxs-lookup"><span data-stu-id="2f978-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="2f978-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="2f978-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="2f978-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="2f978-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="2f978-184">Variace znázorněné v následujícím kódu řadí roky třídy a potom jednotlivé studenty vyřadí do každého roku podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="2f978-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="2f978-185">Další informace o `Group By`naleznete v tématu [Group by klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f978-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f978-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="2f978-187">Začínáme pomocí LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f978-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="2f978-188">Dotazy</span><span class="sxs-lookup"><span data-stu-id="2f978-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="2f978-189">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f978-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2f978-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="2f978-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
