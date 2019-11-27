---
title: Zápis dotazů
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 6a9f229697ce3d6328c6fb09d18d4cc2627eab10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351018"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="bfb26-102">Návod: Zápis dotazů ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfb26-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="bfb26-103">Tento návod ukazuje, jak lze pomocí Visual Basicch funkcí jazyka napsat [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="bfb26-104">Návod ukazuje, jak vytvořit dotazy na seznam objektů studenta, jak spustit dotazy a jak je upravit.</span><span class="sxs-lookup"><span data-stu-id="bfb26-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="bfb26-105">Dotazy obsahují několik funkcí, včetně inicializátorů objektů, místního typu odvození a anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="bfb26-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="bfb26-106">Po dokončení tohoto Názorného postupu budete připraveni přejít k ukázkám a dokumentaci pro konkrétního poskytovatele [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], kterého vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="bfb26-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> <span data-ttu-id="bfb26-107">mezi poskytovatele [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] patří [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfb26-107">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="bfb26-108">Vytvořit projekt</span><span class="sxs-lookup"><span data-stu-id="bfb26-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="bfb26-109">Vytvoření projektu konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="bfb26-109">To create a console application project</span></span>

1. <span data-ttu-id="bfb26-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bfb26-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="bfb26-111">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bfb26-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="bfb26-112">V seznamu **Nainstalované šablony** klikněte na **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="bfb26-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="bfb26-113">V seznamu typů projektů klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="bfb26-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="bfb26-114">Do pole **název** zadejte název projektu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfb26-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="bfb26-115">Vytvoří se projekt.</span><span class="sxs-lookup"><span data-stu-id="bfb26-115">A project is created.</span></span> <span data-ttu-id="bfb26-116">Ve výchozím nastavení obsahuje odkaz na System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="bfb26-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="bfb26-117">Také seznam **importovaných oborů názvů** na [stránce odkazy, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) obsahuje obor názvů <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfb26-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="bfb26-118">Na [stránce kompilovat Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)zajistěte, aby byla **možnost odvoditelné** na hodnotu **zapnuto**.</span><span class="sxs-lookup"><span data-stu-id="bfb26-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="bfb26-119">Přidání zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="bfb26-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="bfb26-120">Zdroj dat pro dotazy v tomto návodu je seznam `Student`ch objektů.</span><span class="sxs-lookup"><span data-stu-id="bfb26-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="bfb26-121">Každý objekt `Student` obsahuje křestní jméno, příjmení, rok třídy a akademickou hodnost v těle studenta.</span><span class="sxs-lookup"><span data-stu-id="bfb26-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="bfb26-122">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="bfb26-122">To add the data source</span></span>

- <span data-ttu-id="bfb26-123">Definujte třídu `Student` a vytvořte seznam instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="bfb26-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="bfb26-124">Kód potřebný k definování třídy `Student` a vytvoření seznamu, který se používá v příkladech návodu, je uveden v tématu [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="bfb26-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="bfb26-125">Můžete z něj zkopírovat a vložit ho do projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="bfb26-126">Nový kód nahradí kód, který se zobrazil při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="bfb26-127">Přidání nového studenta do seznamu studentů</span><span class="sxs-lookup"><span data-stu-id="bfb26-127">To add a new student to the students list</span></span>

- <span data-ttu-id="bfb26-128">Podle vzoru v metodě `getStudents` přidejte další instanci `Student` třídy do seznamu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="bfb26-129">Přidáním studenta se seznámíte s Inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="bfb26-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="bfb26-130">Další informace naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfb26-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="bfb26-131">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="bfb26-131">Create a Query</span></span>

<span data-ttu-id="bfb26-132">Po spuštění se dotaz přidaný v této části vytvoří seznam studentů, jejichž školní řazení je v prvních deseti.</span><span class="sxs-lookup"><span data-stu-id="bfb26-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="bfb26-133">Vzhledem k tomu, že dotaz vybírá úplný `Student` objekt pokaždé, je typ výsledku dotazu `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="bfb26-134">Nicméně typ dotazu obvykle není zadán v definicích dotazů.</span><span class="sxs-lookup"><span data-stu-id="bfb26-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="bfb26-135">Místo toho kompilátor používá odvození místního typu k určení typu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="bfb26-136">Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="bfb26-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="bfb26-137">Proměnná rozsahu dotazu `currentStudent`, slouží jako odkaz na každou instanci `Student` ve zdroji `students`a poskytuje přístup k vlastnostem každého objektu v `students`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="bfb26-138">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="bfb26-138">To create a simple query</span></span>

1. <span data-ttu-id="bfb26-139">Vyhledejte místo v metodě `Main` projektu, který je označen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bfb26-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="bfb26-140">Zkopírujte následující kód a vložte ho do.</span><span class="sxs-lookup"><span data-stu-id="bfb26-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="bfb26-141">Umístěte ukazatel myši na `studentQuery` ve vašem kódu, abyste ověřili, že typ přiřazený kompilátorem je `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="bfb26-142">Spuštění dotazu</span><span class="sxs-lookup"><span data-stu-id="bfb26-142">Run the Query</span></span>

<span data-ttu-id="bfb26-143">Proměnná `studentQuery` obsahuje definici dotazu, nikoli výsledky spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="bfb26-144">Typickým mechanismem pro spuštění dotazu je `For Each` smyčka.</span><span class="sxs-lookup"><span data-stu-id="bfb26-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="bfb26-145">Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="bfb26-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="bfb26-146">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="bfb26-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="bfb26-147">Spuštění dotazu</span><span class="sxs-lookup"><span data-stu-id="bfb26-147">To run the query</span></span>

1. <span data-ttu-id="bfb26-148">Přidejte následující `For Each` cyklus pod dotaz v projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="bfb26-149">Po přesunutí ukazatele myši na ovládací prvek smyčky `studentRecord` zobrazíte jeho datový typ.</span><span class="sxs-lookup"><span data-stu-id="bfb26-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="bfb26-150">Typ `studentRecord` je odvozen jako `Student`, protože `studentQuery` vrátí kolekci instancí `Student`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="bfb26-151">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bfb26-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="bfb26-152">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bfb26-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="bfb26-153">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="bfb26-153">Modify the Query</span></span>

<span data-ttu-id="bfb26-154">Vyhledávání výsledků dotazu je snazší, pokud jsou v zadaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bfb26-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="bfb26-155">Vrácenou sekvenci můžete seřadit na základě libovolného dostupného pole.</span><span class="sxs-lookup"><span data-stu-id="bfb26-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="bfb26-156">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="bfb26-156">To order the results</span></span>

1. <span data-ttu-id="bfb26-157">Do příkazu `Where` a příkazu `Select` dotazu přidejte následující klauzuli `Order By`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="bfb26-158">Klauzule `Order By` seřadí výsledky abecedně od A do Z v závislosti na posledním jménu každého studenta.</span><span class="sxs-lookup"><span data-stu-id="bfb26-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="bfb26-159">Chcete-li seřadit podle příjmení a pak jako křestní jméno, přidejte do dotazu obě pole:</span><span class="sxs-lookup"><span data-stu-id="bfb26-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="bfb26-160">Můžete také zadat `Descending` pro řazení z Z do A.</span><span class="sxs-lookup"><span data-stu-id="bfb26-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="bfb26-161">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bfb26-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="bfb26-162">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bfb26-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="bfb26-163">Zavedení lokálního identifikátoru</span><span class="sxs-lookup"><span data-stu-id="bfb26-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="bfb26-164">Přidejte kód v této části, chcete-li do výrazu dotazu zavést místní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="bfb26-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="bfb26-165">Místní identifikátor bude obsahovat mezilehlé výsledky.</span><span class="sxs-lookup"><span data-stu-id="bfb26-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="bfb26-166">V následujícím příkladu je `name` identifikátor, který obsahuje zřetězení křestní jméno a příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="bfb26-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="bfb26-167">Místní identifikátor lze použít pro pohodlí nebo může zvýšit výkon tím, že ukládá výsledky výrazu, který by jinak vypočítal vícekrát.</span><span class="sxs-lookup"><span data-stu-id="bfb26-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="bfb26-168">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bfb26-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="bfb26-169">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bfb26-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="bfb26-170">Projekce jednoho pole v klauzuli Select</span><span class="sxs-lookup"><span data-stu-id="bfb26-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="bfb26-171">Přidejte dotaz a smyčku `For Each` z této části, chcete-li vytvořit dotaz, který vytvoří sekvenci, jejíž prvky se liší od prvků ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="bfb26-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="bfb26-172">V následujícím příkladu je zdrojem kolekce objektů `Student`, ale je vrácen pouze jeden člen každého objektu: křestní jméno studentů, jejichž příjmení je Garcia.</span><span class="sxs-lookup"><span data-stu-id="bfb26-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="bfb26-173">Vzhledem k tomu, že `currentStudent.First` je řetězec, datový typ sekvence vrácený `studentQuery3` je `IEnumerable(Of String)`, sekvence řetězců.</span><span class="sxs-lookup"><span data-stu-id="bfb26-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="bfb26-174">Stejně jako v předchozích příkladech je přiřazení datového typu pro `studentQuery3` ponecháno pro kompilátor pro určení pomocí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="bfb26-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="bfb26-175">Umístěte ukazatel myši na `studentQuery3` ve vašem kódu, abyste ověřili, že je přiřazený typ `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="bfb26-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="bfb26-176">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bfb26-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="bfb26-177">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bfb26-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="bfb26-178">Vytvoření anonymního typu v klauzuli Select</span><span class="sxs-lookup"><span data-stu-id="bfb26-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="bfb26-179">Přidejte kód z této části, abyste viděli, jak se v dotazech používají anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="bfb26-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="bfb26-180">Můžete je použít v dotazech, pokud chcete vrátit několik polí ze zdroje dat, nikoli úplné záznamy (`currentStudent` záznamů v předchozích příkladech) nebo v jednom poli (`First` v předchozí části).</span><span class="sxs-lookup"><span data-stu-id="bfb26-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="bfb26-181">Namísto definování nového pojmenovaného typu obsahujícího pole, která chcete zahrnout do výsledku, zadáte pole v klauzuli `Select` a kompilátor vytvoří anonymní typ s těmito poli jako jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bfb26-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="bfb26-182">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfb26-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="bfb26-183">Následující příklad vytvoří dotaz, který vrátí název a pořadí vyšších, jejichž školní řazení je v pořadí podle akademického řádu v rozmezí od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="bfb26-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="bfb26-184">V tomto příkladu musí být typ `studentQuery4` odvozený, protože klauzule `Select` vrací instanci anonymního typu a anonymní typ nemá použitelný název.</span><span class="sxs-lookup"><span data-stu-id="bfb26-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="bfb26-185">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bfb26-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="bfb26-186">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bfb26-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="bfb26-187">Další příklady</span><span class="sxs-lookup"><span data-stu-id="bfb26-187">Additional Examples</span></span>

<span data-ttu-id="bfb26-188">Teď, když rozumíte základům, najdete v následujícím seznamu Další příklady, které znázorňují flexibilitu a výkon [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů.</span><span class="sxs-lookup"><span data-stu-id="bfb26-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="bfb26-189">Každý příklad předchází stručný popis toho, co dělá.</span><span class="sxs-lookup"><span data-stu-id="bfb26-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="bfb26-190">Umístěte ukazatel myši na výslednou proměnnou dotazu pro každý dotaz, aby se zobrazil odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="bfb26-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="bfb26-191">Výsledky můžete vytvořit pomocí `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="bfb26-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="bfb26-192">Další informace</span><span class="sxs-lookup"><span data-stu-id="bfb26-192">Additional Information</span></span>

<span data-ttu-id="bfb26-193">Jakmile se seznámíte se základními koncepty práce s dotazy, můžete si přečíst dokumentaci a ukázky pro konkrétní typ poskytovatele [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], který vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="bfb26-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>

- [<span data-ttu-id="bfb26-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="bfb26-194">LINQ to Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [<span data-ttu-id="bfb26-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bfb26-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="bfb26-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="bfb26-196">LINQ to XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [<span data-ttu-id="bfb26-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bfb26-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="bfb26-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfb26-198">See also</span></span>

- [<span data-ttu-id="bfb26-199">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfb26-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="bfb26-200">Začínáme pomocí LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfb26-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="bfb26-201">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="bfb26-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="bfb26-202">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="bfb26-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="bfb26-203">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="bfb26-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="bfb26-204">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfb26-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="bfb26-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="bfb26-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="bfb26-206">Dotazy</span><span class="sxs-lookup"><span data-stu-id="bfb26-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
