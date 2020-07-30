---
title: 'Návod: Zápis dotazů v C# (LINQ)'
description: Tento návod ukazuje, jak se ve výrazech dotazů LINQ používají funkce jazyka C#. Tento článek používá Visual Studio jako vývojové prostředí.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: d49cb725c9ce9a417f78f638795e98a75a086893
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302214"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="e6e95-104">Návod: Zápis dotazů v C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e6e95-104">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="e6e95-105">Tento návod ukazuje funkce jazyka C#, které slouží k zápisu výrazů dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="e6e95-105">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="e6e95-106">Vytvoření projektu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e6e95-106">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6e95-107">Následující pokyny jsou pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6e95-107">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="e6e95-108">Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem na System.Core.dll a `using` direktivou pro <xref:System.Linq?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e6e95-108">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="e6e95-109">Vytvoření projektu v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e95-109">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="e6e95-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6e95-110">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="e6e95-111">Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6e95-111">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="e6e95-112">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="e6e95-112">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="e6e95-113">Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **Visual C#** a pak zvolte možnost **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="e6e95-113">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="e6e95-114">Do textového pole **název** zadejte jiný název nebo přijměte výchozí název a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="e6e95-114">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="e6e95-115">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="e6e95-115">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="e6e95-116">Všimněte si, že váš projekt má odkaz na System.Core.dll a `using` direktivu pro <xref:System.Linq?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e6e95-116">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="e6e95-117">Vytvoření zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="e6e95-117">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="e6e95-118">Zdroj dat pro dotazy je jednoduchý seznam `Student` objektů.</span><span class="sxs-lookup"><span data-stu-id="e6e95-118">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="e6e95-119">Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, která představují jejich skóre testů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="e6e95-119">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="e6e95-120">Zkopírujte tento kód do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-120">Copy this code into your project.</span></span> <span data-ttu-id="e6e95-121">Všimněte si následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="e6e95-121">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="e6e95-122">`Student`Třída se skládá z automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="e6e95-122">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="e6e95-123">Každý student v seznamu se inicializuje s inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-123">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="e6e95-124">Samotný seznam je inicializován s inicializátorem kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6e95-124">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="e6e95-125">Tato Celá datová struktura bude inicializována a vytvořena bez explicitního volání jakéhokoliv konstruktoru nebo explicitního přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-125">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="e6e95-126">Další informace o těchto nových funkcích naleznete v tématu [automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="e6e95-126">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="e6e95-127">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="e6e95-127">To add the data source</span></span>  
  
- <span data-ttu-id="e6e95-128">Přidejte `Student` třídu a inicializovaný seznam studentů do `Program` třídy v projektu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-128">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="e6e95-129">Přidání nového objektu Student do seznamu Students</span><span class="sxs-lookup"><span data-stu-id="e6e95-129">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="e6e95-130">Přidejte nový `Student` do `Students` seznamu a použijte název a hodnocení podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="e6e95-130">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="e6e95-131">Zkuste zadat všechny informace o novém studentovi, aby se lépe dozvěděla syntaxe inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-131">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="e6e95-132">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-132">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="e6e95-133">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-133">To create a simple query</span></span>  
  
- <span data-ttu-id="e6e95-134">V `Main` metodě aplikace vytvořte jednoduchý dotaz, který při jeho spuštění vytvoří seznam všech studentů, jejichž skóre na prvním testu bylo větší než 90.</span><span class="sxs-lookup"><span data-stu-id="e6e95-134">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="e6e95-135">Všimněte si, že vzhledem k tomu `Student` , že je vybrán celý objekt, je typ dotazu `IEnumerable<Student>` .</span><span class="sxs-lookup"><span data-stu-id="e6e95-135">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="e6e95-136">I když kód může také použít implicitní zadání pomocí klíčového slova [var](../../../language-reference/keywords/var.md) , explicitní psaní se používá k jasné ilustraci výsledků.</span><span class="sxs-lookup"><span data-stu-id="e6e95-136">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="e6e95-137">(Další informace o naleznete `var` v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="e6e95-137">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="e6e95-138">Všimněte si také, že proměnná rozsahu dotazu `student` slouží jako odkaz na každý `Student` zdroj a poskytuje pro každý objekt přístup pro členy.</span><span class="sxs-lookup"><span data-stu-id="e6e95-138">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="e6e95-139">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-139">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="e6e95-140">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-140">To execute the query</span></span>  
  
1. <span data-ttu-id="e6e95-141">Nyní zapište `foreach` smyčku, která způsobí, že se dotaz spustí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-141">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="e6e95-142">Všimněte si následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="e6e95-142">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="e6e95-143">Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace ve `foreach` smyčce.</span><span class="sxs-lookup"><span data-stu-id="e6e95-143">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="e6e95-144">Typ této proměnné je `Student` a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>` .</span><span class="sxs-lookup"><span data-stu-id="e6e95-144">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="e6e95-145">Po přidání tohoto kódu Sestavte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="e6e95-145">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="e6e95-146">Přidání další podmínky filtru</span><span class="sxs-lookup"><span data-stu-id="e6e95-146">To add another filter condition</span></span>  
  
1. <span data-ttu-id="e6e95-147">Můžete zkombinovat více logických podmínek v `where` klauzuli, aby bylo možné dále upřesnit dotaz.</span><span class="sxs-lookup"><span data-stu-id="e6e95-147">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="e6e95-148">Následující kód přidá podmínku, takže dotaz vrátí takové studenty, jejichž první skóre bylo nad 90 a jejichž poslední skóre bylo menší než 80.</span><span class="sxs-lookup"><span data-stu-id="e6e95-148">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="e6e95-149">`where`Klauzule by měla vypadat podobně jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="e6e95-149">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="e6e95-150">Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6e95-150">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="e6e95-151">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-151">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="e6e95-152">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="e6e95-152">To order the results</span></span>  
  
1. <span data-ttu-id="e6e95-153">Vyhledávání výsledků bude snazší, pokud jsou v nějakém typu pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-153">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="e6e95-154">Vrácenou sekvenci můžete seřadit podle libovolného dostupného pole ve zdrojových prvcích.</span><span class="sxs-lookup"><span data-stu-id="e6e95-154">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="e6e95-155">Například následující `orderby` klauzule seřadí výsledky v abecedním pořadí od A do Z podle příjmení každého studenta.</span><span class="sxs-lookup"><span data-stu-id="e6e95-155">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="e6e95-156">Přidejte `orderby` do dotazu následující klauzuli, a to hned za `where` příkazem a před `select` příkazem:</span><span class="sxs-lookup"><span data-stu-id="e6e95-156">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="e6e95-157">Nyní změňte `orderby` klauzuli tak, aby odpovídala výsledkům v obráceném pořadí podle skóre prvního testu od nejvyššího skóre po nejnižší skóre.</span><span class="sxs-lookup"><span data-stu-id="e6e95-157">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="e6e95-158">Změňte `WriteLine` řetězec formátu tak, abyste viděli skóre:</span><span class="sxs-lookup"><span data-stu-id="e6e95-158">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="e6e95-159">Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6e95-159">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="e6e95-160">Seskupení výsledků</span><span class="sxs-lookup"><span data-stu-id="e6e95-160">To group the results</span></span>  
  
1. <span data-ttu-id="e6e95-161">Seskupení je výkonná funkce ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="e6e95-161">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="e6e95-162">Dotaz s klauzulí GROUP vytvoří posloupnost skupin a každá skupina obsahuje `Key` a sekvenci, která se skládá ze všech členů této skupiny.</span><span class="sxs-lookup"><span data-stu-id="e6e95-162">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="e6e95-163">Následující nové dotazy seskupují studenty pomocí prvního písmene jejich příjmení jako klíče.</span><span class="sxs-lookup"><span data-stu-id="e6e95-163">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="e6e95-164">Všimněte si, že typ dotazu byl nyní změněn.</span><span class="sxs-lookup"><span data-stu-id="e6e95-164">Note that the type of the query has now changed.</span></span> <span data-ttu-id="e6e95-165">Nyní vytváří sekvenci skupin, které mají `char` typ jako klíč, a posloupnost `Student` objektů.</span><span class="sxs-lookup"><span data-stu-id="e6e95-165">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="e6e95-166">Vzhledem k tomu, že se typ dotazu změnil, následující kód změní `foreach` smyčku spouštění také:</span><span class="sxs-lookup"><span data-stu-id="e6e95-166">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="e6e95-167">Spusťte aplikaci a zobrazte výsledky v okně **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="e6e95-167">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="e6e95-168">Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="e6e95-168">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="e6e95-169">Převedení proměnných na implicitně typované proměnné</span><span class="sxs-lookup"><span data-stu-id="e6e95-169">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="e6e95-170">Explicitní kódování `IEnumerables` `IGroupings` se může rychle stát zdlouhavě.</span><span class="sxs-lookup"><span data-stu-id="e6e95-170">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="e6e95-171">Stejný dotaz a smyčku můžete napsat `foreach` mnohem přesněji pomocí `var` .</span><span class="sxs-lookup"><span data-stu-id="e6e95-171">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="e6e95-172">`var`Klíčové slovo nemění typy vašich objektů; pouze instruuje kompilátor, aby odvodí typy.</span><span class="sxs-lookup"><span data-stu-id="e6e95-172">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="e6e95-173">Změňte typ `studentQuery` proměnné a proměnnou iterace `group` na `var` a znovu spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="e6e95-173">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="e6e95-174">Všimněte si, že ve vnitřní `foreach` smyčce je proměnná iterace stále zadána jako `Student` a dotaz funguje stejně jako předtím.</span><span class="sxs-lookup"><span data-stu-id="e6e95-174">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="e6e95-175">Změňte `s` proměnnou iterace na `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-175">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="e6e95-176">Vidíte, že se vám přesně vrátí stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e6e95-176">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="e6e95-177">Další informace o funkci [var](../../../language-reference/keywords/var.md)naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e6e95-177">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="e6e95-178">Seřazení skupin podle hodnoty jejich klíče</span><span class="sxs-lookup"><span data-stu-id="e6e95-178">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="e6e95-179">Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-179">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="e6e95-180">Chcete-li toto změnit, je nutné zadat `orderby` klauzuli za `group` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-180">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="e6e95-181">Chcete-li však použít `orderby` klauzuli, nejprve potřebujete identifikátor, který slouží jako odkaz na skupiny vytvořené `group` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-181">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="e6e95-182">Identifikátor můžete zadat pomocí `into` klíčového slova následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e6e95-182">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="e6e95-183">Když spustíte tento dotaz, uvidíte, že se skupiny teď řadí v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6e95-183">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="e6e95-184">Zavedení identifikátoru s použitím klíčového slova let</span><span class="sxs-lookup"><span data-stu-id="e6e95-184">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="e6e95-185">Klíčové slovo lze použít `let` k zavedení identifikátoru pro jakýkoli výsledek výrazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6e95-185">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="e6e95-186">Tento identifikátor může být pohodlí, jak je uvedeno v následujícím příkladu, nebo může zvýšit výkon tím, že uloží výsledky výrazu tak, aby se nemusela vypočítat víckrát.</span><span class="sxs-lookup"><span data-stu-id="e6e95-186">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="e6e95-187">Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6e95-187">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="e6e95-188">Použití syntaxe využívající metody ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="e6e95-188">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="e6e95-189">Jak je popsáno v syntaxi [dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="e6e95-189">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="e6e95-190">Následující kód vypočítá celkové skóre pro každý `Student` ze zdrojových sekvencí a potom zavolá `Average()` metodu pro výsledky tohoto dotazu pro výpočet průměrného skóre třídy.</span><span class="sxs-lookup"><span data-stu-id="e6e95-190">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="e6e95-191">Transformace nebo projekce v klauzuli select</span><span class="sxs-lookup"><span data-stu-id="e6e95-191">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="e6e95-192">Je velmi běžné, že dotaz vytvoří sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="e6e95-192">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="e6e95-193">Odstraňte nebo zakomentujte předchozí dotaz a smyčku spuštění a nahraďte ji následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="e6e95-193">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="e6e95-194">Všimněte si, že dotaz vrátí sekvenci řetězců (ne `Students` ) a tento fakt se projeví ve `foreach` smyčce.</span><span class="sxs-lookup"><span data-stu-id="e6e95-194">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="e6e95-195">Kód uvedený výše v tomto návodu uvádí, že průměrné skóre třídy je přibližně 334.</span><span class="sxs-lookup"><span data-stu-id="e6e95-195">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="e6e95-196">Chcete-li vytvořit sekvenci `Students` , jejichž celkové skóre je větší než průměr třídy, společně s jejich pomocí `Student ID` , můžete v příkazu použít anonymní typ `select` :</span><span class="sxs-lookup"><span data-stu-id="e6e95-196">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="e6e95-197">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e6e95-197">Next Steps</span></span>  
 <span data-ttu-id="e6e95-198">Až budete obeznámeni se základními aspekty práce s dotazy v jazyce C#, jste připraveni si přečíst dokumentaci a ukázky pro konkrétního typu poskytovatele LINQ, kterého vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="e6e95-198">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="e6e95-199">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e6e95-199">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="e6e95-200">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="e6e95-200">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="e6e95-201">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e95-201">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="e6e95-202">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e95-202">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6e95-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6e95-203">See also</span></span>

- [<span data-ttu-id="e6e95-204">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e95-204">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="e6e95-205">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="e6e95-205">LINQ Query Expressions</span></span>](../../../linq/index.md)
