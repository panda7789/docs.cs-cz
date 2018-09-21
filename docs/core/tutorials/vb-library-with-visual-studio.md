---
title: Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017
description: Další informace o vytváření knihovny tříd napsané v jazyce Visual Basic pomocí sady Visual Studio 2017
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52bbae330afe4a9ea376c6388a06941f74f6606a
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508194"
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="2951b-103">Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2951b-103">Building a class library with Visual Basic and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="2951b-104">A *knihovny tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="2951b-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2951b-105">Knihovna tříd, který cílí na .NET Standard 2.0 umožňuje knihovny, které jsou volány žádné implementace .NET, která podporuje danou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2951b-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="2951b-106">Po dokončení knihovnu tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo určuje, zda chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.</span><span class="sxs-lookup"><span data-stu-id="2951b-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2951b-107">Seznam verzí rozhraní .NET Standard a platformy, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2951b-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2951b-108">V tomto tématu vytvoříte knihovnu jednoduchý nástroj, který obsahuje jedinou metodu zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="2951b-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2951b-109">Budete implementovat jako [– metoda rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) tak, že můžete volat, jakoby byly členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="2951b-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="2951b-110">Vytvoření řešení knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="2951b-110">Creating a class library solution</span></span>

<span data-ttu-id="2951b-111">Začněte vytvořením řešení pro váš projekt knihovny tříd a její související projekty.</span><span class="sxs-lookup"><span data-stu-id="2951b-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="2951b-112">Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="2951b-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="2951b-113">Vytvoření řešení:</span><span class="sxs-lookup"><span data-stu-id="2951b-113">To create the solution:</span></span>

1. <span data-ttu-id="2951b-114">Na řádku nabídek sady Visual Studio, zvolte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2951b-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="2951b-115">V **nový projekt** dialogového okna, rozbalte **ostatní typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2951b-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="2951b-116">Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2951b-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Dialogové okno nového projektu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="2951b-118">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="2951b-118">Creating the class library project</span></span>

<span data-ttu-id="2951b-119">Vytvoření projektu knihovny třídy:</span><span class="sxs-lookup"><span data-stu-id="2951b-119">Create your class library project:</span></span>

1. <span data-ttu-id="2951b-120">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení a v místní nabídce vyberte možnost **přidat** > **nový Projekt**.</span><span class="sxs-lookup"><span data-stu-id="2951b-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="2951b-121">V **přidat nový projekt** dialogového okna, rozbalte **jazyka Visual Basic** uzlu, vyberte **.NET Standard** uzel, za nímž následuje **knihovna tříd (.NET Standard)**  šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="2951b-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="2951b-122">V **název** textové pole, zadejte "StringLibrary" jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="2951b-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="2951b-123">Vyberte **OK** vytvořte projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="2951b-123">Select **OK** to create the class library project.</span></span>

   ![Přidání dialogového okna Nový projekt](./media/vb-library-with-visual-studio/libproject.png)

   <span data-ttu-id="2951b-125">Potom otevře se okno kódu ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2951b-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Visual Studio okno aplikace zobrazuje kód výchozí knihovny třídy šablony](./media/vb-library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="2951b-127">Zkontrolujte, že knihovny, zaměřuje na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2951b-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="2951b-128">Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníka řešení** windows, vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2951b-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="2951b-129">**Cílová architektura** textovém poli se zobrazí, že jsme cílíte .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2951b-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="2951b-131">Také v **vlastnosti** dialogového okna, odstraňte text v **kořenový obor názvů** textového pole.</span><span class="sxs-lookup"><span data-stu-id="2951b-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="2951b-132">Pro každý projekt jazyka Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu a jsou nadřazené položky tohoto oboru názvů všech oborů názvů definovaných v souborech zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="2951b-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="2951b-133">Chceme, aby k definování oboru nejvyšší úrovně s použitím [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2951b-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="2951b-134">Nahraďte kód v okně kód následujícím kódem a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="2951b-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="2951b-135">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, který vrátí hodnotu <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="2951b-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2951b-136">Unicode standard rozlišuje velká písmena z malých písmen.</span><span class="sxs-lookup"><span data-stu-id="2951b-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2951b-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Vrátí metoda `true` Pokud znak je velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="2951b-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2951b-138">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="2951b-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="2951b-139">Projekt by měl zkompiluje bez chyb.</span><span class="sxs-lookup"><span data-stu-id="2951b-139">The project should compile without error.</span></span>

   ![Podokno výstup zobrazuje, že sestavení bylo úspěšné](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a><span data-ttu-id="2951b-141">Další krok</span><span class="sxs-lookup"><span data-stu-id="2951b-141">Next step</span></span>

<span data-ttu-id="2951b-142">Úspěšně jste vytvořili knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2951b-142">You've successfully built the library.</span></span> <span data-ttu-id="2951b-143">Protože nejsou volány kterékoliv z jeho metod, zatím nevíte, jestli funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2951b-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="2951b-144">Dalším krokem při vývoji vaší knihovny je testovat pomocí [projekt testů jednotek](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2951b-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
