---
title: "Návod: Zápis dotazů v C# (LINQ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0885c3cc989260cf67608bec0ff512c9f4835f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="bcca9-102">Návod: Zápis dotazů v C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bcca9-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="bcca9-103">Tento návod ukazuje funkce jazyka C#, které se používají k zápisu LINQ – výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="bcca9-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="bcca9-104">Vytvoření projektu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bcca9-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcca9-105">Následující pokyny jsou pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcca9-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="bcca9-106">Pokud používáte jiné vývojové prostředí, vytvořte projekt konzolové s odkazem na System.Core.dll a `using` direktivy pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bcca9-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="bcca9-107">Vytvoření projektu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bcca9-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="bcca9-108">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcca9-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="bcca9-109">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="bcca9-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="bcca9-110">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="bcca9-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bcca9-111">Rozbalte položku **nainstalovaná**, rozbalte položku **šablony**, rozbalte položku **Visual C#**a potom zvolte **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="bcca9-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="bcca9-112">V **název** textového pole zadejte jiný název nebo přijměte výchozí název a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bcca9-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="bcca9-113">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="bcca9-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="bcca9-114">Všimněte si, že váš projekt odkazuje na System.Core.dll a `using` direktivy pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bcca9-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="bcca9-115">Vytvoření zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="bcca9-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="bcca9-116">Zdroj dat pro dotazy je jednoduchý seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="bcca9-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="bcca9-117">Každý `Student` záznam obsahuje křestní jméno, příjmení a pole celých čísel, které představuje jejich výsledků testu v třídě.</span><span class="sxs-lookup"><span data-stu-id="bcca9-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="bcca9-118">Zkopírujte tento kód do projektu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-118">Copy this code into your project.</span></span> <span data-ttu-id="bcca9-119">Vezměte na vědomí následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bcca9-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="bcca9-120">`Student` Třídy se skládá z automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bcca9-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="bcca9-121">Každý student v seznamu se inicializuje inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="bcca9-122">Samotný seznam se inicializuje pomocí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="bcca9-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="bcca9-123">Celou datovou strukturu bude inicializovat a vytvoření instance bez explicitního volání k žádnému konstruktor nebo explicitního člena přístup.</span><span class="sxs-lookup"><span data-stu-id="bcca9-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="bcca9-124">Další informace o těchto nových funkcích najdete v tématu [Auto-Implemented vlastnosti](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="bcca9-125">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="bcca9-125">To add the data source</span></span>  
  
-   <span data-ttu-id="bcca9-126">Přidat `Student` třídy a inicializovaného seznam studentů `Program` třídy ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="bcca9-127">Přidání nového objektu Student do seznamu Students</span><span class="sxs-lookup"><span data-stu-id="bcca9-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="bcca9-128">Přidejte nový `Student` k `Students` seznamu, použijte název a testování skóre podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="bcca9-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="bcca9-129">Zkuste zadat všechny nové informace studenty, aby bylo možné lépe další syntaxe pro inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="bcca9-130">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="bcca9-131">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="bcca9-132">Do aplikace `Main` metody vytvoření jednoduchého dotazu, který při spuštění, vygeneruje seznam všech studentů, jejichž skóre na první test byl větší než 90.</span><span class="sxs-lookup"><span data-stu-id="bcca9-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="bcca9-133">Všimněte si, že protože celek `Student` je objekt vybrán, je typ dotazu `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="bcca9-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="bcca9-134">Kód použít taky implicitní zadáte pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo, explicitní zadáním se používá ke jasně znázornění výsledků.</span><span class="sxs-lookup"><span data-stu-id="bcca9-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="bcca9-135">(Další informace o `var`, najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="bcca9-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="bcca9-136">Poznámka: dotaz na proměnnou rozsahu `student`, slouží jako odkaz na každý `Student` ve zdroji, poskytuje přístup ke členu pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="bcca9-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="bcca9-137">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="bcca9-138">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="bcca9-139">Nyní zápisu `foreach` smyčky, která způsobí, že dotaz provést.</span><span class="sxs-lookup"><span data-stu-id="bcca9-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="bcca9-140">Vezměte na vědomí následující skutečnosti související kód:</span><span class="sxs-lookup"><span data-stu-id="bcca9-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="bcca9-141">Každý prvek v pořadí vrácených přistupuje prostřednictvím proměnné iterace ve `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="bcca9-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="bcca9-142">Typ této proměnné je `Student`, a typ proměnné v dotazu je kompatibilní, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="bcca9-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="bcca9-143">Po přidání tohoto kódu sestavení a spuštění aplikace a zobrazte výsledky v **konzoly** okno.</span><span class="sxs-lookup"><span data-stu-id="bcca9-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="bcca9-144">Přidání další podmínky filtru</span><span class="sxs-lookup"><span data-stu-id="bcca9-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="bcca9-145">Můžete kombinovat více Boolean podmínek v `where` klauzule za účelem další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="bcca9-146">Následující kód přidá podmínku tak, že dotaz vrátí ty studenty, jejichž první skóre bylo víc než 90 a jejichž poslední skóre nižší než 80.</span><span class="sxs-lookup"><span data-stu-id="bcca9-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="bcca9-147">`where` Klauzule by měla vypadat přibližně následující kód.</span><span class="sxs-lookup"><span data-stu-id="bcca9-147">The `where` clause should resemble the following code.</span></span>  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="bcca9-148">Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="bcca9-149">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="bcca9-150">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="bcca9-150">To order the results</span></span>  
  
1.  <span data-ttu-id="bcca9-151">Bude snazší výsledky kontroly, pokud jsou v nějakém pořadí.</span><span class="sxs-lookup"><span data-stu-id="bcca9-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="bcca9-152">Můžete uspořádat vrácený pořadí pomocí libovolné dostupné pole ve zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="bcca9-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="bcca9-153">Například následující `orderby` klauzule řadí výsledky v abecedním pořadí od A do Z podle poslední název každé student.</span><span class="sxs-lookup"><span data-stu-id="bcca9-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="bcca9-154">Přidejte následující `orderby` klauzule do dotazu, hned po `where` prohlášení a před `select` příkaz:</span><span class="sxs-lookup"><span data-stu-id="bcca9-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="bcca9-155">Nyní změnit `orderby` klauzule, které se v obráceném pořadí řadí výsledky podle skóre na první testu z nejvyšší skóre skóre.</span><span class="sxs-lookup"><span data-stu-id="bcca9-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="bcca9-156">Změna `WriteLine` řetězec formátu, takže uvidíte skóre:</span><span class="sxs-lookup"><span data-stu-id="bcca9-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="bcca9-157">Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="bcca9-158">Seskupení výsledků</span><span class="sxs-lookup"><span data-stu-id="bcca9-158">To group the results</span></span>  
  
1.  <span data-ttu-id="bcca9-159">Seskupení je účinné ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="bcca9-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="bcca9-160">Dotaz s klauzuli group vytváří pořadí skupin a obsahuje každou skupinu jako celek `Key` a sekvenci, která se skládá ze všech členů této skupiny.</span><span class="sxs-lookup"><span data-stu-id="bcca9-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="bcca9-161">Následující dotaz nové skupiny studenty pomocí první písmeno jeho příjmení jako klíč.</span><span class="sxs-lookup"><span data-stu-id="bcca9-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="bcca9-162">Všimněte si, že typ dotazu se změnilo.</span><span class="sxs-lookup"><span data-stu-id="bcca9-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="bcca9-163">Nyní vyvolá posloupnost skupiny, které mají `char` typ jako klíč a posloupnost `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="bcca9-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="bcca9-164">Protože se změnil typ dotazu, následující kód změny `foreach` provádění cykly také:</span><span class="sxs-lookup"><span data-stu-id="bcca9-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="bcca9-165">Spusťte aplikaci a zobrazit výsledky v **konzoly** okno.</span><span class="sxs-lookup"><span data-stu-id="bcca9-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="bcca9-166">Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="bcca9-167">Převedení proměnných na implicitně typované proměnné</span><span class="sxs-lookup"><span data-stu-id="bcca9-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="bcca9-168">Explicitně kódování `IEnumerables` z `IGroupings` může být zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="bcca9-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="bcca9-169">Můžete napsat stejný dotaz a `foreach` cykly mnohem snadněji pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="bcca9-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="bcca9-170">`var` – Klíčové slovo nezmění typy objektů vašeho; je právě dává pokyn kompilátoru odvodit typy.</span><span class="sxs-lookup"><span data-stu-id="bcca9-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="bcca9-171">Změnit typ `studentQuery` a proměnné iterace `group` k `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="bcca9-172">Všimněte si, že v vnitřní `foreach` smyčky, proměnné iterace je stále zadán jako `Student`, a dotaz funguje stejně jako předtím.</span><span class="sxs-lookup"><span data-stu-id="bcca9-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="bcca9-173">Změna `s` proměnné iterace k `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="bcca9-174">Uvidíte, že dostanete přesně stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="bcca9-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="bcca9-175">Další informace o [var](../../../../csharp/language-reference/keywords/var.md), najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="bcca9-176">Seřazení skupin podle hodnoty jejich klíče</span><span class="sxs-lookup"><span data-stu-id="bcca9-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="bcca9-177">Při spuštění předchozího dotazu, si všimnete, že skupiny nejsou v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="bcca9-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="bcca9-178">Chcete-li toto nastavení změnit, je nutné zadat `orderby` klauzule po `group` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bcca9-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="bcca9-179">Ale pro použití `orderby` klauzule, musíte nejprve identifikátor, který slouží jako odkaz na skupiny vytvořené `group` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bcca9-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="bcca9-180">Zadejte identifikátor pomocí `into` – klíčové slovo, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bcca9-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="bcca9-181">Při spuštění tohoto dotazu, zobrazí se, že skupiny jsou nyní seřazené podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="bcca9-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="bcca9-182">Zavedení identifikátoru s použitím klíčového slova let</span><span class="sxs-lookup"><span data-stu-id="bcca9-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="bcca9-183">Můžete použít `let` – klíčové slovo zavádět identifikátor pro žádný výsledek výraz ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="bcca9-184">Tento identifikátor může být pro vaše pohodlí, jako v následujícím příkladu, nebo ji můžete zvýšit výkon uložením výsledky výrazu tak, aby nemá vypočítávat vícekrát.</span><span class="sxs-lookup"><span data-stu-id="bcca9-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="bcca9-185">Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bcca9-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="bcca9-186">Použití syntaxe využívající metody ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="bcca9-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="bcca9-187">Jak je popsáno v [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), některé operace dotazů lze vyjádřit pouze pomocí syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="bcca9-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="bcca9-188">Následující kód vypočítá celkové skóre pro každou `Student` zdrojové sekvence a potom volání `Average()` metodu na výsledky tohoto dotazu pro výpočet průměrné skóre třídy.</span><span class="sxs-lookup"><span data-stu-id="bcca9-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span> <span data-ttu-id="bcca9-189">Poznamenejte si umístění v závorkách výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="bcca9-189">Note the placement of parentheses around the query expression.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="bcca9-190">Transformace nebo projekce v klauzuli select</span><span class="sxs-lookup"><span data-stu-id="bcca9-190">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="bcca9-191">Je velmi běžné pro dotaz k vytvoření pořadí, jehož elementy liší z elementů ve zdrojovém pořadí.</span><span class="sxs-lookup"><span data-stu-id="bcca9-191">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="bcca9-192">Odstranit nebo komentář předchozího dotazu a provádění smyčky a nahraďte ji následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="bcca9-192">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="bcca9-193">Všimněte si, že dotaz vrátí posloupnosti řetězců (ne `Students`), a tento fakt se odrazí v `foreach` smyčky.</span><span class="sxs-lookup"><span data-stu-id="bcca9-193">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="bcca9-194">Kód dříve v tomto návodu ukázalo, že průměrná třída skóre je přibližně 334.</span><span class="sxs-lookup"><span data-stu-id="bcca9-194">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="bcca9-195">K vytvoření posloupnost `Students` jejichž celkové skóre je větší než třída průměr, společně s jejich `Student ID`, můžete použít anonymní typ v `select` příkaz:</span><span class="sxs-lookup"><span data-stu-id="bcca9-195">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="bcca9-196">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bcca9-196">Next Steps</span></span>  
 <span data-ttu-id="bcca9-197">Jakmile se seznámíte s základní aspektů práce s dotazy v jazyce C#, jste připravení číst dokumentace a ukázky pro konkrétní typ LINQ zprostředkovatele, které vás zajímají:</span><span class="sxs-lookup"><span data-stu-id="bcca9-197">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="bcca9-198">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bcca9-198">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
  
 [<span data-ttu-id="bcca9-199">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="bcca9-199">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="bcca9-200">Technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bcca9-200">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="bcca9-201">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="bcca9-201">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="bcca9-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcca9-202">See Also</span></span>  
 [<span data-ttu-id="bcca9-203">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bcca9-203">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="bcca9-204">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="bcca9-204">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="bcca9-205">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="bcca9-205">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
