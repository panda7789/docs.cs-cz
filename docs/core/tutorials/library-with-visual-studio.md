---
title: Sestavení C# knihovny .NET Standard sady Visual Studio 2017
description: Zjistěte, jak vytvořit knihovnu tříd .NET Standard napsané v jazyce C# pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 6228cd93b275a059da63a8b8e3408032d78c5e39
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362012"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="08e66-103">Sestavení knihovny .NET Standard s C# a .NET Core SDK v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="08e66-103">Build a .NET Standard library with C# and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="08e66-104">A *knihovny tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="08e66-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="08e66-105">Knihovna tříd, který cílí na .NET Standard 2.0 umožňuje knihovny, které jsou volány žádné implementace .NET, která podporuje danou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="08e66-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="08e66-106">Po dokončení knihovnu tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo určuje, zda chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.</span><span class="sxs-lookup"><span data-stu-id="08e66-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="08e66-107">Seznam verzí rozhraní .NET Standard a platformy, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="08e66-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="08e66-108">V tomto tématu vytvoříte knihovnu jednoduchý nástroj, který obsahuje jedinou metodu zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="08e66-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="08e66-109">Budete implementovat jako [– metoda rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, že můžete volat, jakoby byly členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="08e66-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="08e66-110">Vytvoření řešení knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="08e66-110">Creating a class library solution</span></span>

<span data-ttu-id="08e66-111">Začněte vytvořením řešení pro váš projekt knihovny tříd a její související projekty.</span><span class="sxs-lookup"><span data-stu-id="08e66-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="08e66-112">Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="08e66-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="08e66-113">Vytvoření řešení:</span><span class="sxs-lookup"><span data-stu-id="08e66-113">To create the solution:</span></span>

1. <span data-ttu-id="08e66-114">Na řádku nabídek sady Visual Studio, zvolte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="08e66-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="08e66-115">V **nový projekt** dialogového okna, rozbalte **ostatní typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="08e66-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="08e66-116">Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="08e66-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Dialogové okno Nový projekt se zvýrazněným nové prázdné řešení](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="08e66-118">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="08e66-118">Creating the class library project</span></span>

<span data-ttu-id="08e66-119">Vytvoření projektu knihovny třídy:</span><span class="sxs-lookup"><span data-stu-id="08e66-119">Create your class library project:</span></span>

1. <span data-ttu-id="08e66-120">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení a v místní nabídce vyberte možnost **přidat** > **nový Projekt**.</span><span class="sxs-lookup"><span data-stu-id="08e66-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="08e66-121">V **přidat nový projekt** dialogového okna, rozbalte **Visual C#** uzlu, vyberte **.NET Standard** uzel, za nímž následuje **knihovna tříd (.NET Standard)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="08e66-121">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="08e66-122">V **název** textové pole, zadejte "StringLibrary" jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="08e66-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="08e66-123">Vyberte **OK** vytvořte projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="08e66-123">Select **OK** to create the class library project.</span></span>

   ![Přidat dialogové okno Nový projekt knihovny](./media/library-with-visual-studio/add-new-library-project.png)

   <span data-ttu-id="08e66-125">Potom otevře se okno kódu ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08e66-125">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio okno aplikace zobrazuje kód výchozí knihovny třídy šablony](./media/library-with-visual-studio/string-library-project.png)

1. <span data-ttu-id="08e66-127">Zkontrolujte, že naše knihovny, zaměřuje správná verze modulu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="08e66-127">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="08e66-128">Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníka řešení** windows, vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="08e66-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="08e66-129">**Cílová architektura** textovém poli se zobrazí, že jsme cílíte .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="08e66-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="08e66-131">Nahraďte kód v okně kód následujícím kódem a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="08e66-131">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="08e66-132">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, který vrátí hodnotu <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="08e66-132">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="08e66-133">Unicode standard rozlišuje velká písmena z malých písmen.</span><span class="sxs-lookup"><span data-stu-id="08e66-133">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="08e66-134"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Vrátí metoda `true` Pokud znak je velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="08e66-134">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="08e66-135">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="08e66-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="08e66-136">Projekt by měl zkompiluje bez chyb.</span><span class="sxs-lookup"><span data-stu-id="08e66-136">The project should compile without error.</span></span>

   ![Podokno výstup zobrazuje, že sestavení bylo úspěšné](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="08e66-138">Další krok</span><span class="sxs-lookup"><span data-stu-id="08e66-138">Next step</span></span>

<span data-ttu-id="08e66-139">Úspěšně jste vytvořili knihovnu.</span><span class="sxs-lookup"><span data-stu-id="08e66-139">You've successfully built the library.</span></span> <span data-ttu-id="08e66-140">Protože nejsou volány kterékoliv z jeho metod, zatím nevíte, jestli funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="08e66-140">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="08e66-141">Dalším krokem při vývoji vaší knihovny je testovat pomocí [projekt testů jednotek](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="08e66-141">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>