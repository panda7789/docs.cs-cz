---
title: 'Návod: Zápis dotazů v C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73418058"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="9e054-102">Návod: Zápis dotazů v C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9e054-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="9e054-103">Tento návod ukazuje funkce jazyka C#, které se používají k zápisu výrazů dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="9e054-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="9e054-104">Vytvoření projektu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9e054-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e054-105">Následující pokyny jsou pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e054-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="9e054-106">Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem `using` na soubor <xref:System.Linq?displayProperty=nameWithType> System.Core.dll a direktivu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9e054-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="9e054-107">Vytvoření projektu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e054-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="9e054-108">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e054-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="9e054-109">Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="9e054-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="9e054-110">Otevře se dialogové okno **Nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="9e054-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="9e054-111">Rozbalte **Nainstalované**, **rozbalte položku Šablony**, rozbalte **položku Visual C#** a pak zvolte **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9e054-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="9e054-112">Do textového pole **Název** zadejte jiný název nebo přijměte výchozí název a pak zvolte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="9e054-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="9e054-113">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="9e054-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="9e054-114">Všimněte si, že váš projekt má odkaz `using` na System.Core.dll a směrnice pro obor <xref:System.Linq?displayProperty=nameWithType> názvů.</span><span class="sxs-lookup"><span data-stu-id="9e054-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="9e054-115">Vytvoření zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="9e054-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="9e054-116">Zdroj dat pro dotazy je jednoduchý `Student` seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="9e054-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="9e054-117">Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, které představuje jejich výsledky testů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="9e054-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="9e054-118">Zkopírujte tento kód do projektu.</span><span class="sxs-lookup"><span data-stu-id="9e054-118">Copy this code into your project.</span></span> <span data-ttu-id="9e054-119">Všimněte si následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="9e054-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="9e054-120">Třída `Student` se skládá z automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="9e054-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="9e054-121">Každý student v seznamu je inicializován inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="9e054-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="9e054-122">Samotný seznam je inicializován inicializátorem kolekce.</span><span class="sxs-lookup"><span data-stu-id="9e054-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="9e054-123">Celá tato datová struktura bude inicializována a vytvořena bez explicitních volání libovolného konstruktoru nebo explicitního přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="9e054-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="9e054-124">Další informace o těchto nových funkcích naleznete [v tématu Automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="9e054-125">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="9e054-125">To add the data source</span></span>  
  
- <span data-ttu-id="9e054-126">Přidejte `Student` do `Program` kurzu v projektu kurz a inicializovaný seznam studentů.</span><span class="sxs-lookup"><span data-stu-id="9e054-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="9e054-127">Přidání nového objektu Student do seznamu Students</span><span class="sxs-lookup"><span data-stu-id="9e054-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="9e054-128">Přidejte `Student` do `Students` seznamu nové a použijte název a výsledky testů podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="9e054-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="9e054-129">Zkuste zadat všechny nové informace o studentovi, abyste se lépe naučili syntaxi inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="9e054-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="9e054-130">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="9e054-131">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-131">To create a simple query</span></span>  
  
- <span data-ttu-id="9e054-132">V `Main` metodě aplikace vytvořte jednoduchý dotaz, který při spuštění vytvoří seznam všech studentů, jejichž skóre v prvním testu bylo větší než 90.</span><span class="sxs-lookup"><span data-stu-id="9e054-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="9e054-133">Všimněte si, `Student` že vzhledem k tomu, `IEnumerable<Student>`že je vybrán celý objekt, je typ dotazu .</span><span class="sxs-lookup"><span data-stu-id="9e054-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="9e054-134">Přestože kód může také použít implicitní psaní pomocí klíčového slova [var,](../../../language-reference/keywords/var.md) explicitní psaní se používá k jasnému ilustraci výsledků.</span><span class="sxs-lookup"><span data-stu-id="9e054-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="9e054-135">(Další informace `var`o , naleznete [v tématu implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="9e054-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="9e054-136">Všimněte si také, že `student`proměnná rozsahu dotazu, , slouží jako odkaz na každý `Student` ve zdroji, poskytuje přístup členů pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="9e054-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="9e054-137">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="9e054-138">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-138">To execute the query</span></span>  
  
1. <span data-ttu-id="9e054-139">Nyní napište `foreach` smyčku, která způsobí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="9e054-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="9e054-140">Všimněte si následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9e054-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="9e054-141">Každý prvek ve vrácené posloupnosti je `foreach` přístupný prostřednictvím iterace proměnné ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="9e054-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="9e054-142">Typ této proměnné `Student`je a typ proměnné dotazu `IEnumerable<Student>`je kompatibilní .</span><span class="sxs-lookup"><span data-stu-id="9e054-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="9e054-143">Po přidání tohoto kódu vytvořte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly.**</span><span class="sxs-lookup"><span data-stu-id="9e054-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="9e054-144">Přidání další podmínky filtru</span><span class="sxs-lookup"><span data-stu-id="9e054-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="9e054-145">Můžete kombinovat více booleovské `where` podmínky v klauzuli za účelem dalšího upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="9e054-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="9e054-146">Následující kód přidá podmínku tak, aby dotaz vrátí ty studenty, jejichž první skóre bylo více než 90 a jehož poslední skóre bylo menší než 80.</span><span class="sxs-lookup"><span data-stu-id="9e054-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="9e054-147">Klauzule `where` by se měla podobat následující kód.</span><span class="sxs-lookup"><span data-stu-id="9e054-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="9e054-148">Další informace naleznete v tématu [where clause](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="9e054-149">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="9e054-150">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="9e054-150">To order the results</span></span>  
  
1. <span data-ttu-id="9e054-151">Bude snazší skenovat výsledky, pokud jsou v nějakém pořadí.</span><span class="sxs-lookup"><span data-stu-id="9e054-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="9e054-152">Vrácenou sekvenci můžete seřadit podle libovolného přístupného pole ve zdrojových prvcích.</span><span class="sxs-lookup"><span data-stu-id="9e054-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="9e054-153">Například následující `orderby` klauzule seřazuje výsledky v abecedním pořadí od A do Z podle příjmení každého studenta.</span><span class="sxs-lookup"><span data-stu-id="9e054-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="9e054-154">Přidejte `orderby` do dotazu následující klauzuli, hned za `where` příkaz a před `select` příkaz:</span><span class="sxs-lookup"><span data-stu-id="9e054-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="9e054-155">Nyní změňte `orderby` klauzuli tak, aby se výsledky seřadila v opačném pořadí podle skóre v prvním testu, od nejvyššího skóre k nejnižšímu skóre.</span><span class="sxs-lookup"><span data-stu-id="9e054-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="9e054-156">Změňte `WriteLine` formátovací řetězec tak, aby bylo vidět skóre:</span><span class="sxs-lookup"><span data-stu-id="9e054-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="9e054-157">Další informace naleznete v [tématu orderby klauzule](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="9e054-158">Seskupení výsledků</span><span class="sxs-lookup"><span data-stu-id="9e054-158">To group the results</span></span>  
  
1. <span data-ttu-id="9e054-159">Seskupení je výkonná funkce ve výrazech dotazu.</span><span class="sxs-lookup"><span data-stu-id="9e054-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="9e054-160">Dotaz s klauzulí group vytvoří posloupnost skupin a `Key` každá skupina sama obsahuje a a posloupnost, která se skládá ze všech členů této skupiny.</span><span class="sxs-lookup"><span data-stu-id="9e054-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="9e054-161">Následující nový dotaz seskupuje studenty pomocí prvního písmene jejich příjmení jako klíče.</span><span class="sxs-lookup"><span data-stu-id="9e054-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="9e054-162">Všimněte si, že typ dotazu se nyní změnil.</span><span class="sxs-lookup"><span data-stu-id="9e054-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="9e054-163">Nyní vytváří posloupnost skupin, `char` které mají typ jako klíč `Student` a posloupnost objektů.</span><span class="sxs-lookup"><span data-stu-id="9e054-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="9e054-164">Vzhledem k tomu, že se typ `foreach` dotazu změnil, následující kód změní také smyčku spuštění:</span><span class="sxs-lookup"><span data-stu-id="9e054-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="9e054-165">Spusťte aplikaci a zobrazte výsledky v okně **konzoly.**</span><span class="sxs-lookup"><span data-stu-id="9e054-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="9e054-166">Další informace naleznete v tématu [group clause](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="9e054-167">Převedení proměnných na implicitně typované proměnné</span><span class="sxs-lookup"><span data-stu-id="9e054-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="9e054-168">Explicitně `IEnumerables` `IGroupings` kódování může rychle stát únavné.</span><span class="sxs-lookup"><span data-stu-id="9e054-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="9e054-169">Můžete napsat stejný dotaz `foreach` a smyčky mnohem `var`pohodlněji pomocí .</span><span class="sxs-lookup"><span data-stu-id="9e054-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="9e054-170">Klíčové `var` slovo nezmění typy objektů; pouze instruuje kompilátor odvodit typy.</span><span class="sxs-lookup"><span data-stu-id="9e054-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="9e054-171">Změňte typ `studentQuery` a itetivní proměnnou `group` a `var` znovu spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="9e054-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="9e054-172">Všimněte si, `foreach` že ve vnitřní smyčce `Student`je proměnná iterace stále zadána jako a dotaz funguje stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="9e054-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="9e054-173">Změňte `s` proměnnou `var` iterace na a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="9e054-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="9e054-174">Vidíte, že dostanete přesně stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="9e054-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="9e054-175">Další informace o [var](../../../language-reference/keywords/var.md)naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="9e054-176">Seřazení skupin podle hodnoty jejich klíče</span><span class="sxs-lookup"><span data-stu-id="9e054-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="9e054-177">Při spuštění předchozího dotazu zjistíte, že skupiny nejsou v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="9e054-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="9e054-178">Chcete-li to změnit, `orderby` musíte `group` zadat klauzuli za klauzulí.</span><span class="sxs-lookup"><span data-stu-id="9e054-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="9e054-179">Ale chcete-li použít `orderby` klauzuli, nejprve potřebujete identifikátor, který `group` slouží jako odkaz na skupiny vytvořené klauzulí.</span><span class="sxs-lookup"><span data-stu-id="9e054-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="9e054-180">Identifikátor zadáte pomocí klíčového `into` slova následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9e054-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="9e054-181">Při spuštění tohoto dotazu uvidíte, že skupiny jsou nyní seřazeny v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="9e054-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="9e054-182">Zavedení identifikátoru s použitím klíčového slova let</span><span class="sxs-lookup"><span data-stu-id="9e054-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="9e054-183">Pomocí klíčového `let` slova můžete zavést identifikátor pro libovolný výraz, který má výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="9e054-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="9e054-184">Tento identifikátor může být pohodlí, jako v následujícím příkladu, nebo může zvýšit výkon uložením výsledků výrazu tak, aby není nutné vypočítat vícekrát.</span><span class="sxs-lookup"><span data-stu-id="9e054-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="9e054-185">Další informace naleznete v tématu [let klauzule](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e054-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="9e054-186">Použití syntaxe využívající metody ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9e054-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="9e054-187">Jak je popsáno v [syntaxi dotazu a syntaxi metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="9e054-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="9e054-188">Následující kód vypočítá celkové skóre `Student` pro každý ve zdrojové `Average()` sekvenci a potom volá metodu na výsledky tohoto dotazu k výpočtu průměrné skóre třídy.</span><span class="sxs-lookup"><span data-stu-id="9e054-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="9e054-189">Transformace nebo projekce v klauzuli select</span><span class="sxs-lookup"><span data-stu-id="9e054-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="9e054-190">Je velmi běžné, že dotaz vytvořit sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="9e054-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="9e054-191">Odstraňte nebo zakomentujte předchozí smyčku dotazu a spuštění a nahraďte ji následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="9e054-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="9e054-192">Všimněte si, že dotaz vrátí `Students`posloupnost řetězců (ne `foreach` ) a tato skutečnost se projeví ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="9e054-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="9e054-193">Kód dříve v tomto návodu uvedeno, že průměrné skóre třídy je přibližně 334.</span><span class="sxs-lookup"><span data-stu-id="9e054-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="9e054-194">Chcete-li vytvořit `Students` posloupnost, jejíž celkové skóre `Student ID`je větší než průměr třídy, spolu s jejich , můžete použít anonymní typ v příkazu: `select`</span><span class="sxs-lookup"><span data-stu-id="9e054-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="9e054-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e054-195">Next Steps</span></span>  
 <span data-ttu-id="9e054-196">Poté, co jste obeznámeni se základními aspekty práce s dotazy v jazyce C#, jste připraveni přečíst dokumentaci a ukázky pro konkrétní typ poskytovatele LINQ, který vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="9e054-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="9e054-197">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e054-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="9e054-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9e054-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="9e054-199">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9e054-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="9e054-200">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="9e054-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e054-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e054-201">See also</span></span>

- [<span data-ttu-id="9e054-202">Dotaz integrovaný jazykem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e054-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="9e054-203">Výrazy dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="9e054-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
