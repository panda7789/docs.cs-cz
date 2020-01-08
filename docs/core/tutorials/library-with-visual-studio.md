---
title: Sestavení knihovny tříd .NET Standard v aplikaci Visual Studio
description: Naučte se vytvářet .NET Standard knihovny tříd napsané v C# nebo Visual Basic pomocí sady Visual Studio.
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343118"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="3fe68-103">Sestavení knihovny .NET Standard v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fe68-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="3fe68-104">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="3fe68-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="3fe68-105">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3fe68-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="3fe68-106">Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako součást třetí strany, nebo zda ji chcete zahrnout jako součást sady s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="3fe68-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3fe68-107">Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="3fe68-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="3fe68-108">V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="3fe68-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="3fe68-109">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem třídy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3fe68-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="3fe68-110">Vytvoření řešení pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fe68-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="3fe68-111">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="3fe68-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="3fe68-112">Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="3fe68-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="3fe68-113">Další související projekty přidáte do stejného řešení, pokud budete pokračovat s řadou kurzů.</span><span class="sxs-lookup"><span data-stu-id="3fe68-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="3fe68-114">Vytvoření prázdného řešení:</span><span class="sxs-lookup"><span data-stu-id="3fe68-114">To create the blank solution:</span></span>

1. <span data-ttu-id="3fe68-115">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3fe68-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="3fe68-116">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="3fe68-117">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="3fe68-118">Zvolte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Šablonu prázdného řešení v sadě Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="3fe68-120">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **ClassLibraryProjects** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="3fe68-121">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="3fe68-122">Tento krok můžete také přeskočit a nechat si Visual Studio vytvořit řešení při vytváření projektu v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="3fe68-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="3fe68-123">Vyhledejte možnosti řešení na stránce **Konfigurovat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="3fe68-124">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="3fe68-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="3fe68-125">C#</span><span class="sxs-lookup"><span data-stu-id="3fe68-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="3fe68-126">Přidejte do řešení C# nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="3fe68-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="3fe68-127">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="3fe68-128">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="3fe68-129">Vyberte **C#** ze seznamu jazyk a v seznamu platforma zvolte možnost **všechny platformy** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="3fe68-130">Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="3fe68-131">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="3fe68-132">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="3fe68-133">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3fe68-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="3fe68-134">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="3fe68-135">Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="3fe68-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="3fe68-137">Kód v okně kód nahraďte následujícím kódem a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="3fe68-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="3fe68-138">Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="3fe68-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="3fe68-139">Tato metoda vrací hodnotu <xref:System.Boolean>, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="3fe68-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="3fe68-140">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="3fe68-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="3fe68-141">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="3fe68-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="3fe68-142">Na panelu nabídek vyberte **sestavení** **řešení**Build > .</span><span class="sxs-lookup"><span data-stu-id="3fe68-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="3fe68-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fe68-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="3fe68-144">Přidejte do řešení nový projekt knihovny tříd Visual Basic .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="3fe68-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="3fe68-145">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="3fe68-146">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="3fe68-147">V seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **všechny platformy** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="3fe68-148">Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="3fe68-149">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="3fe68-150">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="3fe68-151">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3fe68-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="3fe68-152">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3fe68-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="3fe68-153">Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="3fe68-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="3fe68-155">V dialogovém okně **vlastnosti** vymažte text v textovém poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="3fe68-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="3fe68-156">Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="3fe68-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="3fe68-157">V tomto kurzu definujete obor názvů nejvyšší úrovně pomocí klíčového slova [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="3fe68-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="3fe68-158">Kód v okně kód nahraďte následujícím kódem a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="3fe68-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="3fe68-159">Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="3fe68-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="3fe68-160">Tato metoda vrací hodnotu <xref:System.Boolean>, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="3fe68-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="3fe68-161">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="3fe68-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="3fe68-162">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="3fe68-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="3fe68-163">Na panelu nabídek vyberte **sestavení** **řešení**Build > .</span><span class="sxs-lookup"><span data-stu-id="3fe68-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="3fe68-164">Projekt by měl být zkompilován bez chyby.</span><span class="sxs-lookup"><span data-stu-id="3fe68-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3fe68-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3fe68-165">Next steps</span></span>

<span data-ttu-id="3fe68-166">Úspěšně jste vytvořili knihovnu.</span><span class="sxs-lookup"><span data-stu-id="3fe68-166">You've successfully built the library.</span></span> <span data-ttu-id="3fe68-167">Vzhledem k tomu, že jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="3fe68-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="3fe68-168">Dalším krokem při vývoji knihovny je testování.</span><span class="sxs-lookup"><span data-stu-id="3fe68-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3fe68-169">Vytvoření projektu pro testování částí</span><span class="sxs-lookup"><span data-stu-id="3fe68-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
