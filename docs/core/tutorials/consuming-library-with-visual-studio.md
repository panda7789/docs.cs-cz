---
title: Využití knihovny .NET Standard v sadě Visual Studio
description: Vytvořte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí Visual Studia 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920460"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="b2dfc-103">Využití knihovny .NET Standard v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2dfc-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="b2dfc-104">Jakmile vytvoříte knihovnu tříd .NET Standard, otestujete ji a vytvoříte vyvolanou verzi knihovny, dalším krokem je zpřístupnit ji volajícím.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="b2dfc-105">To můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b2dfc-105">You can do this in two ways:</span></span>

- <span data-ttu-id="b2dfc-106">Pokud bude knihovna používána jediným řešením (například pokud se jedná o součást v jedné velké aplikaci), můžete ji zahrnout jako projekt do řešení.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="b2dfc-107">Pokud bude knihovna veřejně dostupná, můžete ji distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="b2dfc-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b2dfc-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b2dfc-109">Přidejte do svého řešení konzolovou aplikaci, která odkazuje na projekt knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="b2dfc-110">Vytvořte balíček NuGet, který obsahuje projekt knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="b2dfc-111">Přidání konzolové aplikace do vašeho řešení</span><span class="sxs-lookup"><span data-stu-id="b2dfc-111">Add a console app to your solution</span></span>

<span data-ttu-id="b2dfc-112">Stejně jako jste zahrnuli testy částí do stejného řešení jako vaše knihovna tříd v [test .NET Standard knihovny v sadě Visual Studio](testing-library-with-visual-studio.md), můžete zahrnout aplikace jako součást tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="b2dfc-113">Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznámí, zda je jeho první znak velkými písmeny:</span><span class="sxs-lookup"><span data-stu-id="b2dfc-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="b2dfc-114">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v článku [Sestavení a standardní knihovny .NET v sadě Visual Studio.](library-with-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b2dfc-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="b2dfc-115">Přidejte do řešení novou aplikaci konzoly .NET Core s názvem "ShowCase".</span><span class="sxs-lookup"><span data-stu-id="b2dfc-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="b2dfc-116">Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="b2dfc-117">Na stránce **Přidat nový projekt** zadejte **konzolu** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="b2dfc-118">V seznamu Jazyk zvolte **C#** nebo **Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="b2dfc-119">Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="b2dfc-120">Na stránce **Konfigurovat nový projekt** zadejte do pole Název **projektu** **ZobrazitPřípad.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="b2dfc-121">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="b2dfc-122">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **ShowCase** a v místní nabídce vyberte nastavit **jako projekt spuštění.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Kontextová nabídka projektu sady Visual Studio pro nastavení spouštěcího projektu](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="b2dfc-124">Zpočátku projekt nemá přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="b2dfc-125">Chcete-li povolit volání metod v knihovně tříd, vytvořte odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="b2dfc-126">V **Průzkumníku řešení**klepněte pravým tlačítkem `ShowCase` myši na uzel **Závislosti** projektu a vyberte příkaz Přidat **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Přidání kontextové nabídky odkazu v sadě Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b2dfc-128">V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Dialogové okno Správce odkazů s vybranou knihovnou stringlibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="b2dfc-130">V okně kódu pro soubor *Program.cs* nebo *Program.vb* nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b2dfc-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="b2dfc-131">Kód používá `row` proměnnou k udržení počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b2dfc-132">Vždy, když je větší než nebo rovno 25, kód vymaže okno konzoly a zobrazí zprávu uživateli.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="b2dfc-133">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b2dfc-134">Označuje, zda řetězec začíná znakem velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b2dfc-135">Pokud uživatel stiskne klávesu Enter bez zadání řetězce, aplikace se ukončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="b2dfc-136">V případě potřeby změňte panel nástrojů a `ShowCase` zkompilujte verzi **projektu ladění.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="b2dfc-137">Zkompilujte a spusťte program výběrem zelené šipky na tlačítku **ShowCase.**</span><span class="sxs-lookup"><span data-stu-id="b2dfc-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Panel nástrojů projektu sady Visual Studio s tlačítkem Ladění](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="b2dfc-139">Aplikaci, která používá tuto knihovnu, můžete ladit a publikovat podle kroků v části [Ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio](debugging-with-visual-studio.md) a publikování aplikace [.NET Core Hello World pomocí sady Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b2dfc-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="b2dfc-140">Vytvoření balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="b2dfc-140">Create a NuGet package</span></span>

<span data-ttu-id="b2dfc-141">Knihovnu tříd můžete zpřístupnit publikováním jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="b2dfc-142">Visual Studio nepodporuje vytváření balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="b2dfc-143">Chcete-li jej vytvořit, musíte použít příkazy příkazu PŘÍKAZU .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b2dfc-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="b2dfc-144">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-144">Open a console window.</span></span>

   <span data-ttu-id="b2dfc-145">Zadejte například **příkazový řádek** do vyhledávacího pole na hlavním panelu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="b2dfc-146">Vyberte aplikaci **Command Prompt** desktop nebo stiskněte **Enter,** pokud je již ve výsledcích hledání vybraná.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="b2dfc-147">Přejděte do adresáře projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="b2dfc-148">Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary.csproj* nebo *StringLibrary.vbproj*.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="b2dfc-149">Spusťte příkaz [dotnet pack](../tools/dotnet-pack.md) a vygenerujte balíček s příponou *.nupkg:*</span><span class="sxs-lookup"><span data-stu-id="b2dfc-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="b2dfc-150">Pokud adresář, který obsahuje *program dotnet.exe,* není ve vaší `where dotnet.exe` cestě, můžete jeho umístění najít zadáním do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="b2dfc-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="b2dfc-151">Další informace o vytváření balíčků NuGet naleznete v [tématu Jak vytvořit balíček NuGet s rozhraním .NET Core CLI](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="b2dfc-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
