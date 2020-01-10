---
title: Využití knihovny .NET Standard v sadě Visual Studio
description: Sestavte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí sady Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ec9c6f992bcd4a76e2f70018f3facca42b7b660c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714069"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="4c0a8-103">Využití knihovny .NET Standard v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c0a8-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="4c0a8-104">Jakmile vytvoříte knihovnu tříd .NET Standard, otestujete ji a sestavíte si prodejní verzi knihovny, je dalším krokem zpřístupnění volajícím.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="4c0a8-105">To můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="4c0a8-105">You can do this in two ways:</span></span>

- <span data-ttu-id="4c0a8-106">Pokud bude knihovna použita v jednom řešení (například v případě, že se jedná o komponentu v jedné velké aplikaci), můžete ji zahrnout jako projekt ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="4c0a8-107">Pokud bude knihovna veřejně dostupná, můžete ji distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="4c0a8-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4c0a8-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4c0a8-109">Přidejte konzolovou aplikaci do řešení, které odkazuje na projekt knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="4c0a8-110">Vytvořte balíček NuGet, který obsahuje projekt knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="4c0a8-111">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="4c0a8-111">Add a console app to your solution</span></span>

<span data-ttu-id="4c0a8-112">Stejně jako v případě, že jste zahrnuli jednotkové testy do stejného řešení jako knihovnu tříd v rámci [testu knihovny .NET Standard v aplikaci Visual Studio](testing-library-with-visual-studio.md), můžete zahrnout aplikaci jako součást tohoto řešení.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="4c0a8-113">Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznamuje, zda je jeho první znak velkými písmeny:</span><span class="sxs-lookup"><span data-stu-id="4c0a8-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="4c0a8-114">Otevřete řešení `ClassLibraryProjects`, které jste vytvořili v článku [Vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="4c0a8-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="4c0a8-115">Do řešení přidejte novou konzolovou aplikaci .NET Core s názvem prezentující.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="4c0a8-116">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="4c0a8-117">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="4c0a8-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="4c0a8-118">V **C#** seznamu jazyků vyberte nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="4c0a8-119">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="4c0a8-120">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **prezentující** .</span><span class="sxs-lookup"><span data-stu-id="4c0a8-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="4c0a8-121">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="4c0a8-122">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="4c0a8-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="4c0a8-124">Zpočátku váš projekt nemá přístup k vaší knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="4c0a8-125">Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="4c0a8-126">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu `ShowCase` a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Přidat kontextovou nabídku odkazu v aplikaci Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="4c0a8-128">V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="4c0a8-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Dialog Správce odkazů s vybraným StringLibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="4c0a8-130">V okně kódu pro soubor *program.cs* nebo *program. vb* nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4c0a8-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="4c0a8-131">Kód používá proměnnou `row` k udržení počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="4c0a8-132">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="4c0a8-133">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="4c0a8-134">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="4c0a8-135">Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="4c0a8-136">V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="4c0a8-137">Zkompilujte a spusťte program tak, že vyberete zelenou šipku na **tlačítku pro** sestavování.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="4c0a8-139">Můžete ladit a publikovat aplikaci, která používá tuto knihovnu, pomocí postupu v části [ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio](debugging-with-visual-studio.md) a [publikování aplikace .NET Core Hello World v aplikaci Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4c0a8-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="4c0a8-140">Vytvoření balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4c0a8-140">Create a NuGet package</span></span>

<span data-ttu-id="4c0a8-141">Vaše knihovna tříd může být široce dostupná, když ji publikujete jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="4c0a8-142">Visual Studio nepodporuje vytváření balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="4c0a8-143">Abyste ho mohli vytvořit, musíte použít .NET Core CLI příkazy:</span><span class="sxs-lookup"><span data-stu-id="4c0a8-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="4c0a8-144">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-144">Open a console window.</span></span>

   <span data-ttu-id="4c0a8-145">Zadejte například **příkazový řádek** do pole Hledat na panelu úloh systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="4c0a8-146">Vyberte aplikaci desktopového **řádku** nebo stiskněte klávesu **ENTER** , pokud už je ve výsledcích hledání vybraná.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="4c0a8-147">Přejděte do adresáře projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="4c0a8-148">Adresář obsahuje zdrojový kód a soubor projektu, *StringLibrary. csproj* nebo *StringLibrary. vbproj*.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="4c0a8-149">Spusťte příkaz [dotnet Pack](../tools/dotnet-pack.md) pro vygenerování balíčku s příponou *. nupkg* :</span><span class="sxs-lookup"><span data-stu-id="4c0a8-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="4c0a8-150">Pokud adresář, který obsahuje *dotnet. exe* , není ve vaší cestě, můžete najít jeho umístění zadáním `where dotnet.exe` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4c0a8-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="4c0a8-151">Další informace o vytváření balíčků NuGet najdete v tématu [Postup vytvoření balíčku NuGet s nástroji pro různé platformy](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="4c0a8-151">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
