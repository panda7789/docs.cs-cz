---
title: 'Návod: Zápis dotazů v jazyce C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: d17d1d456752095dcc895eba291cd53745f9467d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968150"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="7d364-102">Návod: Zápis dotazů v jazyce C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7d364-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="7d364-103">Tento návod ukazuje funkce jazyka C#, které se používá k zápisu LINQ – výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="7d364-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="7d364-104">Vytvoření projektu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7d364-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d364-105">Následující pokyny jsou určené pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d364-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="7d364-106">Pokud používáte různé vývojové prostředí, vytvořte projekt konzoly s odkazem na knihovnu System.Core.dll a `using` směrnice pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d364-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="7d364-107">Vytvoření projektu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d364-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="7d364-108">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d364-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7d364-109">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7d364-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="7d364-110">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7d364-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7d364-111">Rozbalte **nainstalováno**, rozbalte **šablony**, rozbalte **Visual C#** a klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="7d364-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="7d364-112">V **název** textového pole zadejte jiný název nebo přijměte výchozí název a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7d364-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="7d364-113">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7d364-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="7d364-114">Všimněte si, že váš projekt obsahuje odkaz na System.Core.dll a `using` směrnice pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d364-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="7d364-115">Vytvoření zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="7d364-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="7d364-116">Zdroj dat pro dotazy je jednoduchý seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="7d364-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="7d364-117">Každý `Student` záznam obsahuje jméno, příjmení a pole celých čísel, která představuje jejich výsledky testu ve třídě.</span><span class="sxs-lookup"><span data-stu-id="7d364-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="7d364-118">Zkopírujte tento kód do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="7d364-118">Copy this code into your project.</span></span> <span data-ttu-id="7d364-119">Mějte na paměti následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7d364-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="7d364-120">`Student` Třídy se skládá z automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d364-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="7d364-121">Každý student v seznamu je inicializovat pomocí inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="7d364-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="7d364-122">Samotný seznam je inicializovat pomocí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="7d364-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="7d364-123">Tato struktura celé datové bude inicializována a bez explicitní volání konstruktoru nebo přístup ke členu explicitní vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="7d364-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="7d364-124">Další informace o těchto nových funkcích najdete v tématu [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="7d364-125">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="7d364-125">To add the data source</span></span>  
  
-   <span data-ttu-id="7d364-126">Přidat `Student` třídy a inicializovaný seznam studenty, aby `Program` třídu ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7d364-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="7d364-127">Přidání nového objektu Student do seznamu Students</span><span class="sxs-lookup"><span data-stu-id="7d364-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="7d364-128">Přidat nový `Student` k `Students` seznamu a pomocí názvu a otestovat skóre, které se podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="7d364-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="7d364-129">Zadejte všechny nové studentské informace, abychom tak získali lepší Seznamte se se syntaxí pro inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="7d364-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="7d364-130">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="7d364-131">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="7d364-132">V aplikaci prvku `Main` metody vytvoření jednoduchého dotazu, který, pokud je spuštěn, bude vytvoření seznamu Všichni studenti, jehož skóre na první test byl větší než 90.</span><span class="sxs-lookup"><span data-stu-id="7d364-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="7d364-133">Upozorňujeme, že celý `Student` vybrán objekt, je typ dotazu `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="7d364-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="7d364-134">I když kód může také použití implicitního zápisu pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo, explicitní zadání slouží k jasně ukazuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="7d364-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="7d364-135">(Další informace o `var`, naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="7d364-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="7d364-136">Všimněte si také, že v dotazu proměnná rozsahu `student`, slouží jako odkaz na každé `Student` ve zdroji, poskytují přístup ke členu pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="7d364-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="7d364-137">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="7d364-138">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="7d364-139">Teď zapisovat `foreach` smyčku, která způsobí, že ke spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="7d364-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="7d364-140">Mějte na paměti následující skutečnosti související kód:</span><span class="sxs-lookup"><span data-stu-id="7d364-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="7d364-141">Každý prvek ve vrácené posloupnosti je přístupné prostřednictvím proměnné iterace ve `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="7d364-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="7d364-142">Typ této proměnné je `Student`, a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="7d364-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="7d364-143">Po přidání tohoto kódu sestavte a spusťte aplikaci a ověřte výsledky v **konzoly** okna.</span><span class="sxs-lookup"><span data-stu-id="7d364-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="7d364-144">Přidání další podmínky filtru</span><span class="sxs-lookup"><span data-stu-id="7d364-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="7d364-145">Můžete zkombinovat více logických podmínek v `where` klauzuli pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="7d364-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="7d364-146">Následující kód přidává podmínku tak, že dotaz vrací ty studenty, jehož první skóre bylo víc než 90 a jejichž poslední skóre nižší než 80.</span><span class="sxs-lookup"><span data-stu-id="7d364-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="7d364-147">`where` Klauzule by měla vypadat podobně jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="7d364-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="7d364-148">Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="7d364-149">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="7d364-150">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="7d364-150">To order the results</span></span>  
  
1.  <span data-ttu-id="7d364-151">Ji bude snazší výsledky kontroly, pokud se nějaký druh pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d364-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="7d364-152">Můžete si objednat vrácená sekvence podle jakékoli přístupné pole ve zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="7d364-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="7d364-153">Například následující `orderby` klauzule řadí výsledky v abecedním pořadí od A až Z podle poslední název každého studenta.</span><span class="sxs-lookup"><span data-stu-id="7d364-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="7d364-154">Přidejte následující `orderby` klauzule dotazu, hned po `where` příkazu a před `select` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="7d364-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="7d364-155">Teď změňte `orderby` klauzule tak, že v obráceném pořadí řadí výsledky podle skóre v prvním testu z nejvyšším skóre skóre.</span><span class="sxs-lookup"><span data-stu-id="7d364-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="7d364-156">Změnit `WriteLine` řetězec formátu, kde lze zobrazit skóre:</span><span class="sxs-lookup"><span data-stu-id="7d364-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="7d364-157">Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="7d364-158">Seskupení výsledků</span><span class="sxs-lookup"><span data-stu-id="7d364-158">To group the results</span></span>  
  
1.  <span data-ttu-id="7d364-159">Seskupení je výkonná funkce ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="7d364-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="7d364-160">Dotazy s klauzulí skupiny vytvoří posloupnost skupin a obsahuje samotnou skupinu `Key` a sekvenci, která se skládá ze všech členů této skupiny.</span><span class="sxs-lookup"><span data-stu-id="7d364-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="7d364-161">Následující nový dotaz seskupí studenty s použitím první písmeno jeho příjmení jako klíč.</span><span class="sxs-lookup"><span data-stu-id="7d364-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2.  <span data-ttu-id="7d364-162">Všimněte si, že je typ dotazu se změnilo.</span><span class="sxs-lookup"><span data-stu-id="7d364-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="7d364-163">Nyní generuje sekvenci skupiny, které mají `char` typ jako klíč a sekvencí `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="7d364-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="7d364-164">Protože došlo ke změně typu dotazu, následující změny kódu `foreach` provádění smyčky také:</span><span class="sxs-lookup"><span data-stu-id="7d364-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3.  <span data-ttu-id="7d364-165">Spusťte aplikaci a zobrazit výsledky v **konzoly** okna.</span><span class="sxs-lookup"><span data-stu-id="7d364-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="7d364-166">Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="7d364-167">Převedení proměnných na implicitně typované proměnné</span><span class="sxs-lookup"><span data-stu-id="7d364-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="7d364-168">Explicitně kódování `IEnumerables` z `IGroupings` může být zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="7d364-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="7d364-169">Můžete napsat stejný dotaz a `foreach` smyčky mnohem snadněji pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="7d364-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="7d364-170">`var` – Klíčové slovo nezmění typy objektů; právě instruuje kompilátor k odvození typů.</span><span class="sxs-lookup"><span data-stu-id="7d364-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="7d364-171">Změna typu `studentQuery` a iterační proměnné `group` k `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="7d364-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="7d364-172">Všimněte si, že v vnitřní `foreach` smyčky, iterační proměnná je stále zadán jako `Student`, a dotaz funguje stejně jako v minulosti.</span><span class="sxs-lookup"><span data-stu-id="7d364-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="7d364-173">Změnit `s` iterační proměnné a `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="7d364-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="7d364-174">Uvidíte, že dostanete přesně stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="7d364-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="7d364-175">Další informace o [var](../../../../csharp/language-reference/keywords/var.md), naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="7d364-176">Seřazení skupin podle hodnoty jejich klíče</span><span class="sxs-lookup"><span data-stu-id="7d364-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="7d364-177">Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d364-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="7d364-178">Chcete-li toto nastavení změnit, je nutné zadat `orderby` klauzule po `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7d364-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="7d364-179">Ale pro použití `orderby` klauzule, musíte nejprve identifikátor, který slouží jako odkaz na skupinách vytvořených skriptem `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7d364-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="7d364-180">Zadejte identifikátor pomocí `into` – klíčové slovo, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7d364-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="7d364-181">Při spuštění tohoto dotazu, zobrazí se, že tyto skupiny jsou nyní seřadit v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d364-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="7d364-182">Zavedení identifikátoru s použitím klíčového slova let</span><span class="sxs-lookup"><span data-stu-id="7d364-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="7d364-183">Můžete použít `let` – klíčové slovo zavedení identifikátoru pro libovolný výsledek výrazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="7d364-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="7d364-184">Tento identifikátor může být pro přehlednost jako v následujícím příkladu, nebo ho můžete zvýšit výkon ukládáním výsledky výrazu tak, aby nemá vypočítávat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="7d364-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="7d364-185">Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7d364-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="7d364-186">Použití syntaxe využívající metody ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="7d364-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="7d364-187">Jak je popsáno v [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), nějakých operací dotazů lze vyjádřit pouze pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="7d364-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="7d364-188">Následující kód vypočítá celkové skóre pro každou `Student` ve zdrojové sekvence a poté zavolá `Average()` metodu na výsledky dotazu pro výpočet průměrné skóre třídy.</span><span class="sxs-lookup"><span data-stu-id="7d364-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="7d364-189">Transformace nebo projekce v klauzuli select</span><span class="sxs-lookup"><span data-stu-id="7d364-189">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="7d364-190">Je velmi běžné, že dotaz, který vytvoří posloupnost, jehož prvky se liší od elementy ve zdrojových posloupností.</span><span class="sxs-lookup"><span data-stu-id="7d364-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="7d364-191">Odstranit nebo okomentovat předchozí dotaz a provádění smyčky a nahraďte ho následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7d364-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="7d364-192">Všimněte si, že dotaz vrací posloupnost řetězců (není `Students`), a tuto skutečnost se projeví v `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="7d364-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2.  <span data-ttu-id="7d364-193">Kód výše v tomto názorném postupu uvedeno, že třída průměrné skóre je přibližně 334.</span><span class="sxs-lookup"><span data-stu-id="7d364-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="7d364-194">K vytvoření sekvence `Students` jehož celkovým skóre je větší než průměr třídy společně s jejich `Student ID`, můžete použít anonymní typ v `select` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="7d364-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="7d364-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7d364-195">Next Steps</span></span>  
 <span data-ttu-id="7d364-196">Jakmile se seznámíte s základní aspektů práce s dotazy v jazyce C#, jste připravení číst dokumentaci a ukázky pro konkrétní typ zprostředkovatele LINQ, které vás zajímají:</span><span class="sxs-lookup"><span data-stu-id="7d364-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="7d364-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7d364-197">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="7d364-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7d364-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="7d364-199">Technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7d364-199">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="7d364-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7d364-200">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d364-201">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d364-201">See also</span></span>

- [<span data-ttu-id="7d364-202">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7d364-202">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="7d364-203">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7d364-203">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="7d364-204">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="7d364-204">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
