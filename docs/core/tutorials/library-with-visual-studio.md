---
title: Vytvoření knihovny tříd .NET Standard v sadě Visual Studio
description: Zjistěte, jak vytvořit knihovnu tříd .NET Standard napsanou v jazyce C# nebo Visual Basic pomocí sady Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714009"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="2a22d-103">Vytvoření knihovny .NET Standard v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a22d-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="2a22d-104">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="2a22d-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2a22d-105">Knihovna tříd, která cílí na rozhraní .NET Standard 2.0, umožňuje, aby byla vaše knihovna volána libovolnou implementací rozhraní .NET, která tuto verzi rozhraní .NET Standard podporuje.</span><span class="sxs-lookup"><span data-stu-id="2a22d-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="2a22d-106">Po dokončení knihovny tříd se můžete rozhodnout, zda ji chcete distribuovat jako komponentu jiného výrobce nebo zda ji chcete zahrnout jako sdruženou komponentu s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="2a22d-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2a22d-107">Seznam verzí rozhraní .NET Standard a platforem, které podporují, naleznete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2a22d-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2a22d-108">V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jednu metodu zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="2a22d-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2a22d-109">Budete implementovat jako [metodu rozšíření,](../../csharp/programming-guide/classes-and-structs/extension-methods.md) takže můžete volat, jako kdyby <xref:System.String> byl členem třídy.</span><span class="sxs-lookup"><span data-stu-id="2a22d-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="2a22d-110">Vytvoření řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a22d-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="2a22d-111">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="2a22d-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2a22d-112">Řešení visual studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="2a22d-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2a22d-113">Přidáte další související projekty do stejného řešení, pokud budete pokračovat v sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="2a22d-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="2a22d-114">Chcete-li vytvořit prázdné řešení:</span><span class="sxs-lookup"><span data-stu-id="2a22d-114">To create the blank solution:</span></span>

1. <span data-ttu-id="2a22d-115">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a22d-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="2a22d-116">V počátečním okně zvolte **Vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="2a22d-117">Na stránce **Vytvořit nový projekt** zadejte **řešení** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="2a22d-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="2a22d-118">Zvolte šablonu **Prázdné řešení** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Prázdná šablona řešení v sadě Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="2a22d-120">Na stránce **Konfigurovat nový projekt** zadejte do pole Název **projektu** **projektprojektprojekt.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="2a22d-121">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="2a22d-122">Tento krok můžete také přeskočit a nechat Visual Studio vytvořit řešení pro vás při vytváření projektu v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="2a22d-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="2a22d-123">Na stránce **Konfigurace nového projektu vyhledejte** možnosti řešení.</span><span class="sxs-lookup"><span data-stu-id="2a22d-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="2a22d-124">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="2a22d-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="2a22d-125">C #</span><span class="sxs-lookup"><span data-stu-id="2a22d-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="2a22d-126">Přidejte do řešení nový projekt knihovny tříd C#.</span><span class="sxs-lookup"><span data-stu-id="2a22d-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2a22d-127">Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2a22d-128">Na stránce **Přidat nový projekt** zadejte **knihovnu** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="2a22d-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2a22d-129">Ze seznamu Jazyk zvolte **C#** a pak ze seznamu Platforma zvolte **Všechny platformy.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2a22d-130">Zvolte **šablonu Knihovna tříd (.NET Standard)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2a22d-131">Na stránce **Konfigurovat nový projekt** zadejte **StringLibrary** do pole **Název projektu.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2a22d-132">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2a22d-133">Zkontrolujte, zda knihovna cílí na správnou verzi standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="2a22d-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2a22d-134">Klepněte pravým tlačítkem myši na projekt knihovny v **Průzkumníku řešení**a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2a22d-135">Textové pole **Cílová architektura** ukazuje, že projekt cílí na standard .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a22d-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="2a22d-137">Nahraďte kód v okně kódu následujícím kódem a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="2a22d-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="2a22d-138">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje `StartsWithUpper`metodu s názvem .</span><span class="sxs-lookup"><span data-stu-id="2a22d-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2a22d-139">Tato metoda <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="2a22d-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2a22d-140">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="2a22d-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2a22d-141">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí, `true` pokud znak je velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2a22d-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2a22d-142">Na řádku nabídek vyberte **Build** > **Build Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="2a22d-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a22d-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="2a22d-144">Přidejte do řešení nový projekt knihovny tříd visual basic .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="2a22d-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2a22d-145">Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2a22d-146">Na stránce **Přidat nový projekt** zadejte **knihovnu** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="2a22d-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2a22d-147">V seznamu Jazyk **zvolte Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2a22d-148">Zvolte **šablonu Knihovna tříd (.NET Standard)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2a22d-149">Na stránce **Konfigurovat nový projekt** zadejte **StringLibrary** do pole **Název projektu.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2a22d-150">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2a22d-151">Zkontrolujte, zda knihovna cílí na správnou verzi standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="2a22d-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2a22d-152">Klepněte pravým tlačítkem myši na projekt knihovny v **Průzkumníku řešení**a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2a22d-153">Textové pole **Cílová architektura** ukazuje, že projekt cílí na standard .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a22d-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="2a22d-155">V dialogovém okně **Vlastnosti** vymažte text v textovém poli **Kořenový jmenovcí obor.**</span><span class="sxs-lookup"><span data-stu-id="2a22d-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="2a22d-156">Pro každý projekt visual basic automaticky vytvoří obor názvů, který odpovídá názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="2a22d-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="2a22d-157">V tomto kurzu definujete obor názvů nejvyšší [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) úrovně pomocí klíčového slova v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="2a22d-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="2a22d-158">Nahraďte kód v okně kódu následujícím kódem a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="2a22d-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="2a22d-159">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje `StartsWithUpper`metodu s názvem .</span><span class="sxs-lookup"><span data-stu-id="2a22d-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2a22d-160">Tato metoda <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="2a22d-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2a22d-161">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="2a22d-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2a22d-162">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí, `true` pokud znak je velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2a22d-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2a22d-163">Na řádku nabídek vyberte **Build** > **Build Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="2a22d-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="2a22d-164">Projekt by měl zkompilovat bez chyby.</span><span class="sxs-lookup"><span data-stu-id="2a22d-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2a22d-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2a22d-165">Next steps</span></span>

<span data-ttu-id="2a22d-166">Úspěšně jste vytvořili knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2a22d-166">You've successfully built the library.</span></span> <span data-ttu-id="2a22d-167">Protože jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2a22d-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="2a22d-168">Dalším krokem při vývoji knihovny je otestovat.</span><span class="sxs-lookup"><span data-stu-id="2a22d-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a22d-169">Vytvoření projektu pro testování částí</span><span class="sxs-lookup"><span data-stu-id="2a22d-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
