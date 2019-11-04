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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418058"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="f571c-102">Návod: Zápis dotazů v C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f571c-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="f571c-103">Tento návod ukazuje funkce C# jazyka, které se používají k zápisu výrazů dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="f571c-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="f571c-104">Vytvoření projektu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f571c-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f571c-105">Následující pokyny jsou pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f571c-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="f571c-106">Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem na System. Core. dll a direktivu `using` pro obor názvů <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f571c-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="f571c-107">Vytvoření projektu v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f571c-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="f571c-108">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f571c-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="f571c-109">Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f571c-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="f571c-110">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="f571c-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="f571c-111">Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **vizuál C#** a pak zvolte možnost **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f571c-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="f571c-112">Do textového pole **název** zadejte jiný název nebo přijměte výchozí název a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="f571c-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="f571c-113">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f571c-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="f571c-114">Všimněte si, že váš projekt má odkaz na System. Core. dll a direktivu `using` pro obor názvů <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f571c-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="f571c-115">Vytvoření zdroje dat v paměti</span><span class="sxs-lookup"><span data-stu-id="f571c-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="f571c-116">Zdrojem dat pro dotazy je jednoduchý seznam `Student` objektů.</span><span class="sxs-lookup"><span data-stu-id="f571c-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="f571c-117">Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, která představují jejich skóre testů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="f571c-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="f571c-118">Zkopírujte tento kód do projektu.</span><span class="sxs-lookup"><span data-stu-id="f571c-118">Copy this code into your project.</span></span> <span data-ttu-id="f571c-119">Všimněte si následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="f571c-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="f571c-120">Třída `Student` se skládá z automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="f571c-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="f571c-121">Každý student v seznamu se inicializuje s inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="f571c-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="f571c-122">Samotný seznam je inicializován s inicializátorem kolekce.</span><span class="sxs-lookup"><span data-stu-id="f571c-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="f571c-123">Tato Celá datová struktura bude inicializována a vytvořena bez explicitního volání jakéhokoliv konstruktoru nebo explicitního přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="f571c-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="f571c-124">Další informace o těchto nových funkcích naleznete v tématu [automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="f571c-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="f571c-125">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="f571c-125">To add the data source</span></span>  
  
- <span data-ttu-id="f571c-126">Přidejte třídu `Student` a inicializovaný seznam studentů do třídy `Program` ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="f571c-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="f571c-127">Přidání nového objektu Student do seznamu Students</span><span class="sxs-lookup"><span data-stu-id="f571c-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="f571c-128">Přidejte nový `Student` do seznamu `Students` a použijte název a hodnocení podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="f571c-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="f571c-129">Zkuste zadat všechny informace o novém studentovi, aby se lépe dozvěděla syntaxe inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="f571c-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="f571c-130">Vytvoření dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="f571c-131">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-131">To create a simple query</span></span>  
  
- <span data-ttu-id="f571c-132">V metodě `Main` aplikace vytvořte jednoduchý dotaz, který při spuštění vytvoří seznam všech studentů, jejichž skóre prvního testu bylo větší než 90.</span><span class="sxs-lookup"><span data-stu-id="f571c-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="f571c-133">Všimněte si, že vzhledem k tomu, že je vybrán celý objekt `Student`, je typ dotazu `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="f571c-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="f571c-134">I když kód může také použít implicitní zadání pomocí klíčového slova [var](../../../language-reference/keywords/var.md) , explicitní psaní se používá k jasné ilustraci výsledků.</span><span class="sxs-lookup"><span data-stu-id="f571c-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="f571c-135">(Další informace o `var`naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="f571c-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="f571c-136">Všimněte si také, že proměnná rozsahu dotazu `student`, slouží jako odkaz na každý `Student` ve zdroji a poskytuje pro každý objekt přístup pro členy.</span><span class="sxs-lookup"><span data-stu-id="f571c-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="f571c-137">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="f571c-138">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-138">To execute the query</span></span>  
  
1. <span data-ttu-id="f571c-139">Nyní zapište smyčku `foreach`, která způsobí, že se dotaz spustí.</span><span class="sxs-lookup"><span data-stu-id="f571c-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="f571c-140">Všimněte si následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f571c-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="f571c-141">Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace ve smyčce `foreach`.</span><span class="sxs-lookup"><span data-stu-id="f571c-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="f571c-142">Typ této proměnné je `Student`a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="f571c-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="f571c-143">Po přidání tohoto kódu Sestavte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="f571c-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="f571c-144">Přidání další podmínky filtru</span><span class="sxs-lookup"><span data-stu-id="f571c-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="f571c-145">Můžete zkombinovat více logických podmínek v klauzuli `where`, aby bylo možné dále upřesnit dotaz.</span><span class="sxs-lookup"><span data-stu-id="f571c-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="f571c-146">Následující kód přidá podmínku, takže dotaz vrátí takové studenty, jejichž první skóre bylo nad 90 a jejichž poslední skóre bylo menší než 80.</span><span class="sxs-lookup"><span data-stu-id="f571c-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="f571c-147">Klauzule `where` by se měla podobat následujícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="f571c-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="f571c-148">Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f571c-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="f571c-149">Úprava dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="f571c-150">Řazení výsledků</span><span class="sxs-lookup"><span data-stu-id="f571c-150">To order the results</span></span>  
  
1. <span data-ttu-id="f571c-151">Vyhledávání výsledků bude snazší, pokud jsou v nějakém typu pořadí.</span><span class="sxs-lookup"><span data-stu-id="f571c-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="f571c-152">Vrácenou sekvenci můžete seřadit podle libovolného dostupného pole ve zdrojových prvcích.</span><span class="sxs-lookup"><span data-stu-id="f571c-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="f571c-153">Například následující klauzule `orderby` seřadí výsledky v abecedním pořadí od A do Z v závislosti na posledním názvu každého studenta.</span><span class="sxs-lookup"><span data-stu-id="f571c-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="f571c-154">Přidejte následující klauzuli `orderby` do dotazu, hned za příkaz `where` a před příkaz `select`:</span><span class="sxs-lookup"><span data-stu-id="f571c-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="f571c-155">Nyní změňte klauzuli `orderby` tak, aby odpovídala výsledkům v obráceném pořadí podle skóre prvního testu, od nejvyššího skóre až po nejnižší skóre.</span><span class="sxs-lookup"><span data-stu-id="f571c-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="f571c-156">Změňte řetězec formátu `WriteLine`, abyste viděli skóre:</span><span class="sxs-lookup"><span data-stu-id="f571c-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="f571c-157">Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f571c-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="f571c-158">Seskupení výsledků</span><span class="sxs-lookup"><span data-stu-id="f571c-158">To group the results</span></span>  
  
1. <span data-ttu-id="f571c-159">Seskupení je výkonná funkce ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="f571c-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="f571c-160">Dotaz s klauzulí GROUP vytvoří posloupnost skupin a každá skupina obsahuje `Key` a sekvenci, která se skládá ze všech členů této skupiny.</span><span class="sxs-lookup"><span data-stu-id="f571c-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="f571c-161">Následující nové dotazy seskupují studenty pomocí prvního písmene jejich příjmení jako klíče.</span><span class="sxs-lookup"><span data-stu-id="f571c-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="f571c-162">Všimněte si, že typ dotazu byl nyní změněn.</span><span class="sxs-lookup"><span data-stu-id="f571c-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="f571c-163">Nyní vytváří sekvenci skupin, které mají typ `char` jako klíč, a sekvenci objektů `Student`.</span><span class="sxs-lookup"><span data-stu-id="f571c-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="f571c-164">Vzhledem k tomu, že se typ dotazu změnil, následující kód změní také smyčku spuštění `foreach`:</span><span class="sxs-lookup"><span data-stu-id="f571c-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="f571c-165">Spusťte aplikaci a zobrazte výsledky v okně **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="f571c-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="f571c-166">Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="f571c-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="f571c-167">Převedení proměnných na implicitně typované proměnné</span><span class="sxs-lookup"><span data-stu-id="f571c-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="f571c-168">Explicitní kódování `IEnumerables` `IGroupings` se může rychle stát zdlouhavě.</span><span class="sxs-lookup"><span data-stu-id="f571c-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="f571c-169">Stejný dotaz a `foreach`ovou smyčku můžete napsat mnohem pohodlně pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="f571c-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="f571c-170">Klíčové slovo `var` nemění typy vašich objektů; pouze instruuje kompilátor, aby odvodí typy.</span><span class="sxs-lookup"><span data-stu-id="f571c-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="f571c-171">Změňte typ `studentQuery` a proměnnou iterace `group` na `var` a znovu spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="f571c-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="f571c-172">Všimněte si, že ve vnitřní `foreach` smyčce je proměnná iterace zapsána jako `Student`a dotaz funguje stejně jako dřív.</span><span class="sxs-lookup"><span data-stu-id="f571c-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="f571c-173">Změňte `s` proměnnou iterace na `var` a spusťte dotaz znovu.</span><span class="sxs-lookup"><span data-stu-id="f571c-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="f571c-174">Vidíte, že se vám přesně vrátí stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="f571c-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="f571c-175">Další informace o funkci [var](../../../language-reference/keywords/var.md)naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="f571c-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="f571c-176">Seřazení skupin podle hodnoty jejich klíče</span><span class="sxs-lookup"><span data-stu-id="f571c-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="f571c-177">Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="f571c-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="f571c-178">Chcete-li toto změnit, je nutné zadat klauzuli `orderby` za klauzulí `group`.</span><span class="sxs-lookup"><span data-stu-id="f571c-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="f571c-179">Chcete-li však použít klauzuli `orderby`, nejprve potřebujete identifikátor, který slouží jako odkaz na skupiny vytvořené klauzulí `group`.</span><span class="sxs-lookup"><span data-stu-id="f571c-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="f571c-180">Identifikátor zadáte pomocí klíčového slova `into` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f571c-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="f571c-181">Když spustíte tento dotaz, uvidíte, že se skupiny teď řadí v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="f571c-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="f571c-182">Zavedení identifikátoru s použitím klíčového slova let</span><span class="sxs-lookup"><span data-stu-id="f571c-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="f571c-183">Klíčové slovo `let` lze použít k představení identifikátoru pro jakýkoli výsledek výrazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f571c-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="f571c-184">Tento identifikátor může být pohodlí, jak je uvedeno v následujícím příkladu, nebo může zvýšit výkon tím, že uloží výsledky výrazu tak, aby se nemusela vypočítat víckrát.</span><span class="sxs-lookup"><span data-stu-id="f571c-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="f571c-185">Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f571c-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="f571c-186">Použití syntaxe využívající metody ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f571c-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="f571c-187">Jak je popsáno v syntaxi [dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="f571c-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="f571c-188">Následující kód vypočítá celkové skóre pro každý `Student` ve zdrojové sekvenci a poté zavolá metodu `Average()` ve výsledcích tohoto dotazu pro výpočet průměrného skóre třídy.</span><span class="sxs-lookup"><span data-stu-id="f571c-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="f571c-189">Transformace nebo projekce v klauzuli select</span><span class="sxs-lookup"><span data-stu-id="f571c-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="f571c-190">Je velmi běžné, že dotaz vytvoří sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="f571c-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="f571c-191">Odstraňte nebo zakomentujte předchozí dotaz a smyčku spuštění a nahraďte ji následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="f571c-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="f571c-192">Všimněte si, že dotaz vrátí sekvenci řetězců (není `Students`) a tento fakt se projeví ve `foreach` smyčce.</span><span class="sxs-lookup"><span data-stu-id="f571c-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="f571c-193">Kód uvedený výše v tomto návodu uvádí, že průměrné skóre třídy je přibližně 334.</span><span class="sxs-lookup"><span data-stu-id="f571c-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="f571c-194">Chcete-li vytvořit sekvenci `Students`, jejichž celkové skóre je větší než průměr třídy, spolu s jejich `Student ID`, můžete v příkazu `select` použít anonymní typ:</span><span class="sxs-lookup"><span data-stu-id="f571c-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="f571c-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f571c-195">Next Steps</span></span>  
 <span data-ttu-id="f571c-196">Jakmile se seznámíte se základními aspekty práce s dotazy v C#nástroji, můžete si přečíst dokumentaci a ukázky pro konkrétního typu poskytovatele LINQ, kterého vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="f571c-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="f571c-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f571c-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="f571c-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f571c-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="f571c-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f571c-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="f571c-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="f571c-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="f571c-201">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f571c-201">See also</span></span>

- [<span data-ttu-id="f571c-202">Dotaz integrovaný na jazyku (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="f571c-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="f571c-203">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="f571c-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
