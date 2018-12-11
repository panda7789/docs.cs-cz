---
title: Použití knihovny .NET Standard v sadě Visual Studio 2017
description: Sestavte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ccf8d33b1017c3def137de7daec4373bfeec6305
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168884"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="4c3a1-103">Použití knihovny .NET Standard v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4c3a1-103">Consuming a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="4c3a1-104">Po vytvoření knihovny tříd .NET Standard podle postupu v [vytváření knihovny tříd jazyka C# pomocí .NET Core v sadě Visual Studio 2017](./library-with-visual-studio.md) nebo [vytváření knihovny tříd jazyka Visual Basic pomocí .NET Core v sadě Visual Studio 2017 ](vb-library-with-visual-studio.md), otestovat ji v [testování knihovny tříd pomocí platformy .NET Core v sadě Visual Studio 2017](testing-library-with-visual-studio.md), a integrované verzi knihovny, dalším krokem je zpřístupnit volající.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="4c3a1-105">Můžete to provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="4c3a1-105">You can do this in two ways:</span></span>

* <span data-ttu-id="4c3a1-106">Pokud knihovny použije jediného řešení (například, pokud je součástí jedné velké aplikace), můžete ho zahrnout jako projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="4c3a1-107">Pokud knihovny bude obecně dostupná, můžete ho distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="4c3a1-108">Včetně knihovnu jako projekt v řešení</span><span class="sxs-lookup"><span data-stu-id="4c3a1-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="4c3a1-109">Stejně jako jste zahrnuli testy jednotek ve stejném řešení jako knihovnu tříd, může obsahovat aplikaci jako součást tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="4c3a1-110">Například můžete použít knihovnu tříd v konzolové aplikaci, která se zobrazí výzva k zadání řetězec a sestavy, zda je jeho prvního znaku velké písmeno:</span><span class="sxs-lookup"><span data-stu-id="4c3a1-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="4c3a1-111">C#</span><span class="sxs-lookup"><span data-stu-id="4c3a1-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="4c3a1-112">Otevřít `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření knihovny tříd jazyka C# pomocí .NET Core v sadě Visual Studio 2017](./library-with-visual-studio.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="4c3a1-113">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="4c3a1-114">V **přidat nový projekt** dialogového okna, rozbalte **Visual C#** uzel a vyberte **.NET Core** uzel, za nímž následuje **Konzolová aplikace (.NET Core)** Šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="4c3a1-115">V **název** textového pole zadejte "Prezentaci" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dialogové okno Visual Studio přidat nový projekt-C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="4c3a1-117">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prezentaci** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio projekt kontextové nabídky nastavení při spuštění projektu –C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="4c3a1-119">Na začátku projektu nemá přístup do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="4c3a1-120">Aby mohla volat metody v knihovně tříd, vytvořit odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="4c3a1-121">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Projekt sady Visual Studio přidejte odkaz na místní nabídka-C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="4c3a1-123">V **správce odkazů** dialogového okna, vyberte **StringLibrary**, váš projekt knihovny tříd a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Visual Studio spravovat odkazy na dialogové okno –C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="4c3a1-125">V okně kódu *Program.cs* souboru, nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4c3a1-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="4c3a1-126">Tento kód použije `row` proměnné udržovat přehled o počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="4c3a1-127">Pokaždé, když je větší než nebo roven 25, kód vymaže okno konzoly a zobrazí zprávu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="4c3a1-128">Program se zobrazí výzva k zadání řetězec.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="4c3a1-129">Znamená to, jestli řetězec začíná velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="4c3a1-130">Pokud uživatel stiskne klávesu Enter bez zadání řetězce, se aplikace ukončí a zavře okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="4c3a1-131">V případě potřeby změňte nástrojů ke kompilaci **ladění** vydání `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="4c3a1-132">Zkompilujte a spusťte program výběrem na zelenou šipku na **prezentaci** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Visual Studio projekt nástrojů zobrazující tlačítko ladění –C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
# <a name="visual-basictabvb"></a>[<span data-ttu-id="4c3a1-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c3a1-134">Visual Basic</span></span>](#tab/vb)
1. <span data-ttu-id="4c3a1-135">Otevřít `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření třídy knihovny jazyka Visual Basic a .NET Core v sadě Visual Studio 2017](vb-library-with-visual-studio.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="4c3a1-136">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="4c3a1-137">V **přidat nový projekt** dialogového okna, rozbalte **jazyka Visual Basic** uzel a vyberte **.NET Core** uzel, za nímž následuje **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="4c3a1-138">V **název** textového pole zadejte "Prezentaci" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Visual Studio přidat nový projekt dialog - jazyka Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="4c3a1-140">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prezentaci** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Visual Studio projekt kontextové nabídky projekt po spuštění – nastavení jazyka Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="4c3a1-142">Na začátku projektu nemá přístup do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="4c3a1-143">Aby mohla volat metody v knihovně tříd, vytvořit odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="4c3a1-144">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Projekt sady Visual Studio přidejte odkaz na místní nabídka - jazyka Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="4c3a1-146">V **správce odkazů** dialogového okna, vyberte **StringLibrary**, váš projekt knihovny tříd a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Spravovat Visual Studio odkazuje na dialogové okno – Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="4c3a1-148">V okně kódu *soubor Program.vb* souboru, nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4c3a1-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="4c3a1-149">Tento kód použije `row` proměnné udržovat přehled o počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="4c3a1-150">Pokaždé, když je větší než nebo roven 25, kód vymaže okno konzoly a zobrazí zprávu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="4c3a1-151">Program se zobrazí výzva k zadání řetězec.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="4c3a1-152">Znamená to, jestli řetězec začíná velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="4c3a1-153">Pokud uživatel stiskne klávesu Enter bez zadání řetězce, se aplikace ukončí a zavře okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="4c3a1-154">V případě potřeby změňte nástrojů ke kompilaci **ladění** vydání `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="4c3a1-155">Zkompilujte a spusťte program výběrem na zelenou šipku na **prezentaci** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Ladění na panelu nástrojů – Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
---

<span data-ttu-id="4c3a1-157">Můžete ladit a publikovat aplikaci, která používá tuto knihovnu podle postupu v [ladění aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md) a [publikování aplikace Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4c3a1-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="4c3a1-158">Distribuce knihoven v balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4c3a1-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="4c3a1-159">Můžete provést knihovnu tříd široce dostupné a publikujte ho jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="4c3a1-160">Visual Studio nepodporuje vytváření balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="4c3a1-161">Chcete-li jeden vytvořit, je použít [ `dotnet` nástroj příkazového řádku](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="4c3a1-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="4c3a1-162">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-162">Open a console window.</span></span> <span data-ttu-id="4c3a1-163">Například v **zeptejte se mě, nic** textové pole na hlavním panelu Windows, zadejte `Command Prompt` (nebo `cmd` zkráceně) a otevřete okno konzoly tak, že vyberete **příkazového řádku** desktopové aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="4c3a1-164">Přejděte do adresáře projektu své knihovny.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="4c3a1-165">Pokud jste změnili konfiguraci umístění typické souboru, se *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* adresáře.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="4c3a1-166">Adresář obsahuje váš zdrojový kód a soubor projektu *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="4c3a1-167">Příkaz `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="4c3a1-168">`dotnet` Nástroj vygeneruje balíček se *.nupkg* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="4c3a1-169">Pokud adresář, který obsahuje *dotnet.exe* není v CESTĚ, můžete najít tak, že zadáte jeho umístění `where dotnet.exe` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c3a1-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="4c3a1-170">Další informace o vytváření balíčků NuGet, naleznete v tématu [vytvoření balíčku NuGet pomocí nástrojů pro různé platformy](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="4c3a1-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
