---
title: Použití rozhraní .NET standardní knihovny v Visual Studio 2017
description: Zjistěte, jak volat členy v knihovny tříd s Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1e71001ee8595741119293304190fd9ef4251148
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827310"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="2de78-103">Použití rozhraní .NET standardní knihovny v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2de78-103">Consuming a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="2de78-104">Po vytvoření knihovny tříd rozhraní .NET standardní podle kroků v [vytvoření knihovny tříd jazyka C# s .NET Core ve Visual Studio 2017](./library-with-visual-studio.md) nebo [vytvoření knihovny tříd jazyka Visual Basic s .NET Core v Visual Studio 2017 ](vb-library-with-visual-studio.md), otestovat ji v [testování knihovny tříd s .NET Core ve Visual Studio 2017](testing-library-with-visual-studio.md), a vytvořili verzi knihovny, je dalším krokem a zpřístupněte ji volající.</span><span class="sxs-lookup"><span data-stu-id="2de78-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="2de78-105">Můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="2de78-105">You can do this in two ways:</span></span>

* <span data-ttu-id="2de78-106">Pokud knihovny použije jedno řešení (například pokud je součástí jedné velké aplikace), můžete ho jako projekt zahrnout ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="2de78-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="2de78-107">Pokud knihovny bude obvykle přístupné, můžete ho distribuovat jako balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2de78-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="2de78-108">Včetně knihovny jako na projekt v řešení</span><span class="sxs-lookup"><span data-stu-id="2de78-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="2de78-109">Stejně jako jste zahrnuli testy jednotek ve stejném řešení jako knihovny tříd, můžete zahrnout aplikace v rámci tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="2de78-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="2de78-110">Například můžete použít knihovny tříd v konzolovou aplikaci, která zobrazí výzvu k zadání řetězec a sestavy, zda jeho první znak je velká písmena:</span><span class="sxs-lookup"><span data-stu-id="2de78-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="2de78-111">C#</span><span class="sxs-lookup"><span data-stu-id="2de78-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="2de78-112">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v [vytvoření knihovny tříd jazyka C# s .NET Core ve Visual Studio 2017](./library-with-visual-studio.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2de78-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="2de78-113">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2de78-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="2de78-114">V **přidat nový projekt** dialogové okno, rozbalte **Visual C#** uzel a vyberte možnost **.NET Core** následuje uzlu **konzolové aplikace (.NET Core)** Šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="2de78-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2de78-115">V **název** textového pole zadejte "Představením" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Přidat dialogové okno Nový projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="2de78-117">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **představením** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2de78-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Představením kontextové nabídky](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="2de78-119">Na začátku projektu nemá přístup do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="2de78-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="2de78-120">Tak, aby ji volat metody ve knihovny tříd, vytvořit odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="2de78-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="2de78-121">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="2de78-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Představením závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="2de78-123">V **správce odkazů** dialogovém okně, vyberte **StringLibrary**, vašeho projektu knihovny tříd a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="2de78-125">V okně kód pro *Program.cs* souboru, všechny kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2de78-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="2de78-126">Kód používá `row` proměnná udržovat počet řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="2de78-127">Vždy, když je větší než nebo roven 25, kód vymaže v okně konzoly a zobrazí zprávu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="2de78-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="2de78-128">Program zobrazí výzvu k zadání řetězec.</span><span class="sxs-lookup"><span data-stu-id="2de78-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="2de78-129">Označuje, zda text začíná velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="2de78-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="2de78-130">Pokud uživatel stiskne klávesu Enter bez zadávání řetězec, ukončí aplikaci a zavření okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="2de78-131">V případě potřeby změňte panelu nástrojů zkompilovat **ladění** vydání `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="2de78-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="2de78-132">Zkompilování a spuštění programu výběrem zelenou šipku na **představením** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="2de78-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2de78-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="2de78-135">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření třídy knihovny jazyka Visual Basic a .NET Core ve Visual Studio 2017](vb-library-with-visual-studio.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2de78-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="2de78-136">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2de78-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="2de78-137">V **přidat nový projekt** dialogové okno, rozbalte **jazyka Visual Basic** uzel a vyberte možnost **.NET Core** následuje uzlu **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="2de78-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2de78-138">V **název** textového pole zadejte "Představením" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Přidat dialogové okno Nový projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="2de78-140">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **představením** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2de78-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Představením kontextové nabídky](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="2de78-142">Na začátku projektu nemá přístup do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="2de78-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="2de78-143">Tak, aby ji volat metody ve knihovny tříd, vytvořit odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="2de78-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="2de78-144">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="2de78-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Představením závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="2de78-146">V **správce odkazů** dialogovém okně, vyberte **StringLibrary**, vašeho projektu knihovny tříd a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="2de78-148">V okně kód pro *soubor Program.vb* souboru, všechny kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2de78-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="2de78-149">Kód používá `row` proměnná udržovat počet řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="2de78-150">Vždy, když je větší než nebo roven 25, kód vymaže v okně konzoly a zobrazí zprávu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="2de78-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="2de78-151">Program zobrazí výzvu k zadání řetězec.</span><span class="sxs-lookup"><span data-stu-id="2de78-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="2de78-152">Označuje, zda text začíná velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="2de78-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="2de78-153">Pokud uživatel stiskne klávesu Enter bez zadávání řetězec, ukončí aplikaci a zavření okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="2de78-154">V případě potřeby změňte panelu nástrojů zkompilovat **ladění** vydání `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="2de78-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="2de78-155">Zkompilování a spuštění programu výběrem zelenou šipku na **představením** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2de78-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="2de78-157">Můžete ladit a publikovat aplikace, která tuto knihovnu používá podle kroků v [ladění aplikace Hello World s Visual Studio 2017](debugging-with-visual-studio.md) a [publikování aplikace Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2de78-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="2de78-158">Distribuce knihoven v balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="2de78-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="2de78-159">Dobrá dostupnost knihovny tříd můžete nastavit tak, že publikujete ji jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="2de78-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="2de78-160">Visual Studio nepodporuje vytváření balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="2de78-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="2de78-161">Chcete-li vytvořit, je použít [ `dotnet` nástroj příkazového řádku](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="2de78-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="2de78-162">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-162">Open a console window.</span></span> <span data-ttu-id="2de78-163">Například v **dotaz na nic** textové pole na hlavním panelu systému Windows, zadejte `Command Prompt` (nebo `cmd` pro zkrácení) a otevřete okno konzoly můžete buď **příkazového řádku** aplikace na ploše nebo pokud je vybrána ve výsledcích hledání z nich stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="2de78-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="2de78-164">Přejděte do adresáře projektu své knihovny.</span><span class="sxs-lookup"><span data-stu-id="2de78-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="2de78-165">Pokud jste změnili konfiguraci umístění typické souboru, je v *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* adresáře.</span><span class="sxs-lookup"><span data-stu-id="2de78-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="2de78-166">Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="2de78-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="2de78-167">Vydejte příkaz `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="2de78-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="2de78-168">`dotnet` Nástroj generuje balíček s *.nupkg* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2de78-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="2de78-169">Pokud adresář, který obsahuje *dotnet.exe* není v CESTĚ, můžete najít její umístění zadáním `where dotnet.exe` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="2de78-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="2de78-170">Další informace o vytváření balíčků NuGet najdete v tématu [vytvoření balíčku NuGet se mezi nástroje platformy](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="2de78-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
