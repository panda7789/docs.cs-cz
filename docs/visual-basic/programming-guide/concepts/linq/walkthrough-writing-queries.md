---
title: Zápis dotazů v Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 256075ad5de5b88595dd4be7f199a74b5912c082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046551"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="711de-102">Návod: Zápis dotazů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="711de-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="711de-103">Tento návod ukazuje, jak lze pomocí funkcí jazyka Visual Basic zapsat [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="711de-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="711de-104">Návod ukazuje, jak vytvořit dotazy na seznam objektů studenta, jak spustit dotazy a jak je upravit.</span><span class="sxs-lookup"><span data-stu-id="711de-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="711de-105">Dotazy obsahují několik funkcí, včetně inicializátorů objektů, místního typu odvození a anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="711de-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="711de-106">Po dokončení tohoto Názorného postupu budete připraveni přejít k ukázkám a dokumentaci pro konkrétního [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele, kterého vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="711de-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="711de-107">poskytovatelé [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnují, LINQ to DataSet a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="711de-107">providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="711de-108">Vytvořit projekt</span><span class="sxs-lookup"><span data-stu-id="711de-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="711de-109">Vytvoření projektu konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="711de-109">To create a console application project</span></span>

1. <span data-ttu-id="711de-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="711de-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="711de-111">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="711de-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="711de-112">V seznamu **Nainstalované šablony** klikněte na **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="711de-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="711de-113">V seznamu typů projektů klikněte na konzolová **aplikace**.</span><span class="sxs-lookup"><span data-stu-id="711de-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="711de-114">Do pole **název** zadejte název projektu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="711de-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="711de-115">Vytvoří se projekt.</span><span class="sxs-lookup"><span data-stu-id="711de-115">A project is created.</span></span> <span data-ttu-id="711de-116">Ve výchozím nastavení obsahuje odkaz na System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="711de-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="711de-117">Také seznam **importovaných oborů názvů** na [stránce s odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) obsahuje <xref:System.Linq?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="711de-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="711de-118">Na [stránce kompilovat Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)zajistěte, aby byla **možnost** odvoditelné na hodnotu **zapnuto**.</span><span class="sxs-lookup"><span data-stu-id="711de-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="711de-119">Přidání zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="711de-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="711de-120">Zdroj dat pro dotazy v tomto návodu je seznam `Student` objektů.</span><span class="sxs-lookup"><span data-stu-id="711de-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="711de-121">Každý `Student` objekt obsahuje křestní jméno, příjmení, rok třídy a akademickou hodnost v těle studenta.</span><span class="sxs-lookup"><span data-stu-id="711de-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="711de-122">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="711de-122">To add the data source</span></span>

- <span data-ttu-id="711de-123">`Student` Definujte třídu a vytvořte seznam instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="711de-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="711de-124">Kód potřebný k definování `Student` třídy a vytvoření seznamu, který se používá v příkladech návodu, je uveden v [tématu How to: Vytvoří seznam položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="711de-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="711de-125">Můžete z něj zkopírovat a vložit ho do projektu.</span><span class="sxs-lookup"><span data-stu-id="711de-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="711de-126">Nový kód nahradí kód, který se zobrazil při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="711de-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="711de-127">Přidání nového studenta do seznamu studentů</span><span class="sxs-lookup"><span data-stu-id="711de-127">To add a new student to the students list</span></span>

- <span data-ttu-id="711de-128">Postupujte podle vzoru v `getStudents` metodě pro přidání další instance `Student` třídy do seznamu.</span><span class="sxs-lookup"><span data-stu-id="711de-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="711de-129">Přidáním studenta se seznámíte s Inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="711de-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="711de-130">Další informace najdete v tématu [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="711de-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="711de-131">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="711de-131">Create a Query</span></span>

<span data-ttu-id="711de-132">Po spuštění se dotaz přidaný v této části vytvoří seznam studentů, jejichž školní řazení je v prvních deseti.</span><span class="sxs-lookup"><span data-stu-id="711de-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="711de-133">Vzhledem k tomu, že dotaz `Student` vybírá úplný objekt pokaždé, typ výsledku dotazu je `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="711de-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="711de-134">Nicméně typ dotazu obvykle není zadán v definicích dotazů.</span><span class="sxs-lookup"><span data-stu-id="711de-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="711de-135">Místo toho kompilátor používá odvození místního typu k určení typu.</span><span class="sxs-lookup"><span data-stu-id="711de-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="711de-136">Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="711de-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="711de-137">Proměnná `currentStudent`rozsahu dotazu slouží jako odkaz na každou `Student` `students`instanci ve zdroji, a poskytuje přístup k vlastnostem každého objektu v `students`.</span><span class="sxs-lookup"><span data-stu-id="711de-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="711de-138">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="711de-138">To create a simple query</span></span>

1. <span data-ttu-id="711de-139">Vyhledejte místo v `Main` metodě projektu, který je označen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="711de-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="711de-140">Zkopírujte následující kód a vložte ho do.</span><span class="sxs-lookup"><span data-stu-id="711de-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="711de-141">Umístěte ukazatel myši nad `studentQuery` v kódu a ověřte, zda je `IEnumerable(Of Student)`typ přiřazený kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="711de-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="711de-142">Spuštění dotazu</span><span class="sxs-lookup"><span data-stu-id="711de-142">Run the Query</span></span>

<span data-ttu-id="711de-143">Proměnná `studentQuery` obsahuje definici dotazu, nikoli výsledky spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="711de-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="711de-144">Typickým mechanismem pro spuštění dotazu je `For Each` smyčka.</span><span class="sxs-lookup"><span data-stu-id="711de-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="711de-145">Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="711de-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="711de-146">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="711de-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="711de-147">Spuštění dotazu</span><span class="sxs-lookup"><span data-stu-id="711de-147">To run the query</span></span>

1. <span data-ttu-id="711de-148">Přidejte následující `For Each` smyčku pod dotaz v projektu.</span><span class="sxs-lookup"><span data-stu-id="711de-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="711de-149">Umístěte ukazatel myši na proměnnou `studentRecord` ovládacího prvku smyčky, aby se zobrazil jeho datový typ.</span><span class="sxs-lookup"><span data-stu-id="711de-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="711de-150">Typ `studentRecord` je odvozený `Student` `studentQuery` ,`Student` protože vrací kolekci instancí.</span><span class="sxs-lookup"><span data-stu-id="711de-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="711de-151">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="711de-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="711de-152">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="711de-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="711de-153">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="711de-153">Modify the Query</span></span>

<span data-ttu-id="711de-154">Vyhledávání výsledků dotazu je snazší, pokud jsou v zadaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="711de-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="711de-155">Vrácenou sekvenci můžete seřadit na základě libovolného dostupného pole.</span><span class="sxs-lookup"><span data-stu-id="711de-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="711de-156">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="711de-156">To order the results</span></span>

1. <span data-ttu-id="711de-157">Přidejte následující `Order By` klauzuli `Where` mezi příkaz a `Select` příkaz dotazu.</span><span class="sxs-lookup"><span data-stu-id="711de-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="711de-158">`Order By` Klauzule seřadí výsledky abecedně od a do Z v závislosti na posledním jménu každého studenta.</span><span class="sxs-lookup"><span data-stu-id="711de-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="711de-159">Chcete-li seřadit podle příjmení a pak jako křestní jméno, přidejte do dotazu obě pole:</span><span class="sxs-lookup"><span data-stu-id="711de-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="711de-160">Můžete také určit `Descending` , že se má seřadit z z do a.</span><span class="sxs-lookup"><span data-stu-id="711de-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="711de-161">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="711de-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="711de-162">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="711de-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="711de-163">Zavedení lokálního identifikátoru</span><span class="sxs-lookup"><span data-stu-id="711de-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="711de-164">Přidejte kód v této části, chcete-li do výrazu dotazu zavést místní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="711de-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="711de-165">Místní identifikátor bude obsahovat mezilehlé výsledky.</span><span class="sxs-lookup"><span data-stu-id="711de-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="711de-166">V následujícím příkladu `name` je identifikátor, který obsahuje zřetězení křestní jméno a příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="711de-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="711de-167">Místní identifikátor lze použít pro pohodlí nebo může zvýšit výkon tím, že ukládá výsledky výrazu, který by jinak vypočítal vícekrát.</span><span class="sxs-lookup"><span data-stu-id="711de-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="711de-168">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="711de-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="711de-169">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="711de-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="711de-170">Projekce jednoho pole v klauzuli Select</span><span class="sxs-lookup"><span data-stu-id="711de-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="711de-171">Přidejte dotaz a `For Each` smyčku z této části, chcete-li vytvořit dotaz, který vytvoří sekvenci, jejíž prvky se liší od prvků ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="711de-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="711de-172">V následujícím příkladu je zdrojem kolekce `Student` objektů, ale je vrácen pouze jeden člen každého objektu: křestní jméno studentů, jejichž příjmení je Garcia.</span><span class="sxs-lookup"><span data-stu-id="711de-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="711de-173">Vzhledem `currentStudent.First` k tomu, že je řetězec, datový typ sekvence, kterou `studentQuery3` vrátí `IEnumerable(Of String)`, je sekvence řetězců.</span><span class="sxs-lookup"><span data-stu-id="711de-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="711de-174">Jak je uvedeno v předchozích příkladech, přiřazení datového typu pro `studentQuery3` je ponecháno pro kompilátor pro určení pomocí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="711de-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="711de-175">Umístěte ukazatel myši nad `studentQuery3` v kódu a ověřte, zda je `IEnumerable(Of String)`přiřazený typ.</span><span class="sxs-lookup"><span data-stu-id="711de-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="711de-176">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="711de-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="711de-177">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="711de-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="711de-178">Vytvoření anonymního typu v klauzuli Select</span><span class="sxs-lookup"><span data-stu-id="711de-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="711de-179">Přidejte kód z této části, abyste viděli, jak se v dotazech používají anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="711de-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="711de-180">Je možné je použít v dotazech, pokud chcete vrátit několik polí ze zdroje dat namísto úplných záznamů (`currentStudent` záznamy v předchozích příkladech) nebo v jednom`First` poli (v předchozí části).</span><span class="sxs-lookup"><span data-stu-id="711de-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="711de-181">Namísto definování nového pojmenovaného typu, který obsahuje pole, která chcete zahrnout do výsledku, zadáte pole v `Select` klauzuli a kompilátor vytvoří anonymní typ s těmito poli jako jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="711de-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="711de-182">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="711de-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="711de-183">Následující příklad vytvoří dotaz, který vrátí název a pořadí vyšších, jejichž školní řazení je v pořadí podle akademického řádu v rozmezí od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="711de-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="711de-184">V tomto příkladu `studentQuery4` musí být typ odvozen, `Select` protože klauzule vrací instanci anonymního typu a anonymní typ nemá použitelný název.</span><span class="sxs-lookup"><span data-stu-id="711de-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="711de-185">Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="711de-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="711de-186">Všimněte si výsledků v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="711de-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="711de-187">Další příklady</span><span class="sxs-lookup"><span data-stu-id="711de-187">Additional Examples</span></span>

<span data-ttu-id="711de-188">Teď, když rozumíte základům, následuje seznam dalších příkladů, které znázorňují flexibilitu a sílu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů.</span><span class="sxs-lookup"><span data-stu-id="711de-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="711de-189">Každý příklad předchází stručný popis toho, co dělá.</span><span class="sxs-lookup"><span data-stu-id="711de-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="711de-190">Umístěte ukazatel myši na výslednou proměnnou dotazu pro každý dotaz, aby se zobrazil odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="711de-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="711de-191">K vytvoření výsledků použijte smyčku.`For Each`</span><span class="sxs-lookup"><span data-stu-id="711de-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="711de-192">Další informace</span><span class="sxs-lookup"><span data-stu-id="711de-192">Additional Information</span></span>

<span data-ttu-id="711de-193">Jakmile se seznámíte se základními koncepty práce s dotazy, můžete si přečíst dokumentaci a ukázky pro konkrétní typ [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele, kterého vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="711de-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>

- [<span data-ttu-id="711de-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="711de-194">LINQ to Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [<span data-ttu-id="711de-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="711de-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="711de-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="711de-196">LINQ to XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [<span data-ttu-id="711de-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="711de-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="711de-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="711de-198">See also</span></span>

- [<span data-ttu-id="711de-199">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="711de-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="711de-200">Začínáme pomocí LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="711de-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="711de-201">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="711de-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="711de-202">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="711de-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="711de-203">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="711de-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="711de-204">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="711de-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="711de-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="711de-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="711de-206">Dotazy</span><span class="sxs-lookup"><span data-stu-id="711de-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
