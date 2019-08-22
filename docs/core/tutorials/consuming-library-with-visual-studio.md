---
title: Využití knihovny .NET Standard v sadě Visual Studio 2017
description: Sestavte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 7a7ab9e8f148eaab8250a7cb10c7d38d2f70e4cd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660570"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="39446-103">Využití knihovny .NET Standard v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="39446-103">Consume a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="39446-104">Po vytvoření knihovny tříd .NET Standard pomocí postupu v části [Vytvoření knihovny C# tříd pomocí .NET Core v aplikaci Visual Studio 2017](./library-with-visual-studio.md) nebo [Vytvoření knihovny tříd Visual Basic pomocí .NET core v aplikaci Visual Studio 2017](vb-library-with-visual-studio.md)je testováno v [ Testování knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017](testing-library-with-visual-studio.md)a sestavení vydané verze knihovny, je dalším krokem zpřístupnění volajícím.</span><span class="sxs-lookup"><span data-stu-id="39446-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="39446-105">Můžete to provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="39446-105">You can do this in two ways:</span></span>

* <span data-ttu-id="39446-106">Pokud bude knihovna použita v jednom řešení (například v případě, že se jedná o komponentu v jedné velké aplikaci), můžete ji zahrnout jako projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="39446-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="39446-107">Pokud bude knihovna všeobecně dostupná, můžete ji distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="39446-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="39446-108">Zahrnutí knihovny jako projektu do řešení</span><span class="sxs-lookup"><span data-stu-id="39446-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="39446-109">Stejně jako v případě, že jste zahrnuli jednotkové testy do stejného řešení jako vaše knihovna tříd, můžete zahrnout aplikaci jako součást tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="39446-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="39446-110">Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznamuje, zda je jeho první znak velkými písmeny:</span><span class="sxs-lookup"><span data-stu-id="39446-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="39446-111">C#</span><span class="sxs-lookup"><span data-stu-id="39446-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="39446-112">Otevřete řešení, které jste vytvořili v tématu [sestavení C# knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017.](./library-with-visual-studio.md) `ClassLibraryProjects`</span><span class="sxs-lookup"><span data-stu-id="39446-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="39446-113">V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **ClassLibraryProjects** a v místní nabídce vyberte **Přidat** > **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="39446-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="39446-114">V dialogovém okně **Přidat nový projekt** rozbalte uzel **vizuál C#**  a vyberte uzel **.NET Core** následovaný šablonou projektu konzolová **aplikace (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="39446-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="39446-115">Do textového pole **název** zadejte "prezentuje" a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="39446-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dialogová okna pro přidání nového projektu sady Visual Studio –C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="39446-117">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="39446-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu –C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="39446-119">Zpočátku váš projekt nemá přístup k vaší knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="39446-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="39446-120">Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="39446-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="39446-121">V **Průzkumník řešení**klikněte pravým tlačítkem myši `ShowCase` na uzel **závislosti** projektu a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="39446-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Místní nabídka pro přidání odkazu na projekt sady Visual Studio –C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="39446-123">V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="39446-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Dialogové okno Správa odkazů v aplikaci Visual Studio –C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="39446-125">V okně kódu pro soubor *program.cs* nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="39446-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="39446-126">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="39446-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="39446-127">Vždy, když je číslo větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="39446-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="39446-128">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="39446-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="39446-129">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="39446-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="39446-130">Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="39446-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="39446-131">V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="39446-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="39446-132">Zkompilujte a spusťte program tak, že vyberete zelenou šipku na tlačítku pro sestavování.</span><span class="sxs-lookup"><span data-stu-id="39446-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění –C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
# <a name="visual-basictabvb"></a>[<span data-ttu-id="39446-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39446-134">Visual Basic</span></span>](#tab/vb)
1. <span data-ttu-id="39446-135">Otevřete řešení, které jste vytvořili v tématu [sestavení knihovny tříd pomocí Visual Basic a .NET Core v aplikaci Visual Studio 2017.](vb-library-with-visual-studio.md) `ClassLibraryProjects`</span><span class="sxs-lookup"><span data-stu-id="39446-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="39446-136">V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **ClassLibraryProjects** a v místní nabídce vyberte **Přidat** > **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="39446-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="39446-137">V dialogovém okně **Přidat nový projekt** rozbalte uzel **Visual Basic** a vyberte uzel **.NET Core** následovaný šablonou projektu konzolová **aplikace (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="39446-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="39446-138">Do textového pole **název** zadejte "prezentuje" a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="39446-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dialogová okna pro přidání nového projektu sady Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="39446-140">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="39446-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu-Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="39446-142">Zpočátku váš projekt nemá přístup k vaší knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="39446-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="39446-143">Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="39446-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="39446-144">V **Průzkumník řešení**klikněte pravým tlačítkem myši `ShowCase` na uzel **závislosti** projektu a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="39446-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Místní nabídka pro přidání odkazu na projekt sady Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="39446-146">V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="39446-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Dialogové okno Správa odkazů v aplikaci Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="39446-148">V okně kód pro soubor *program. vb* nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="39446-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="39446-149">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="39446-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="39446-150">Vždy, když je číslo větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="39446-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="39446-151">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="39446-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="39446-152">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="39446-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="39446-153">Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="39446-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="39446-154">V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="39446-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="39446-155">Zkompilujte a spusťte program tak, že vyberete zelenou šipku na tlačítku pro sestavování.</span><span class="sxs-lookup"><span data-stu-id="39446-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Ladění na panelu nástrojů – Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
---

<span data-ttu-id="39446-157">Můžete ladit a publikovat aplikaci, která používá tuto knihovnu, podle kroků v části [ladění aplikace Hello World pomocí sady Visual studio 2017](debugging-with-visual-studio.md) a [publikování Hello World aplikace pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="39446-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="39446-158">Distribuce knihovny do balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="39446-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="39446-159">Vaše knihovna tříd může být široce dostupná, když ji publikujete jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="39446-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="39446-160">Visual Studio nepodporuje vytváření balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="39446-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="39446-161">Pokud ho chcete vytvořit, použijte [ `dotnet` nástroj příkazového řádku](../tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="39446-161">To create one, you use the [`dotnet` command line utility](../tools/dotnet.md):</span></span>

1. <span data-ttu-id="39446-162">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="39446-162">Open a console window.</span></span> <span data-ttu-id="39446-163">Například v textovém poli **Zobrazit vše** v hlavním panelu systému Windows zadejte `Command Prompt` (nebo `cmd` pro krátkou hodnotu) a otevřete okno konzoly, a to tak, že vyberete aplikaci pro stolní počítače nebo stisknete klávesu ENTER, pokud je vybraná ve vyhledávání. důsledk.</span><span class="sxs-lookup"><span data-stu-id="39446-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="39446-164">Přejděte do adresáře projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="39446-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="39446-165">Pokud jste nenakonfigurovali typické umístění souboru, je to v adresáři *Documents\Visual Studio 2017 \ Projects\ClassLibraryProjects\StringLibrary* .</span><span class="sxs-lookup"><span data-stu-id="39446-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="39446-166">Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="39446-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="39446-167">Vydejte příkaz `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="39446-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="39446-168">Nástroj vygeneruje balíček s příponou *. nupkg.* `dotnet`</span><span class="sxs-lookup"><span data-stu-id="39446-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="39446-169">Pokud adresář, který obsahuje *dotnet. exe* , není ve vaší cestě, můžete najít jeho umístění zadáním `where dotnet.exe` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="39446-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="39446-170">Další informace o vytváření balíčků NuGet najdete v tématu [Postup vytvoření balíčku NuGet s nástroji pro různé platformy](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="39446-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
