---
title: Sestavení .NET Standard knihovny tříd Visual Basic v aplikaci Visual Studio 2017
description: Naučte se vytvářet .NET Standard knihovny tříd napsané v Visual Basic pomocí sady Visual Studio 2017
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100870"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="cbeea-103">Sestavení knihovny .NET Standard s Visual Basic a .NET Core SDK v aplikaci Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="cbeea-103">Build a .NET Standard library with Visual Basic and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="cbeea-104">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="cbeea-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="cbeea-105">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cbeea-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="cbeea-106">Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako součást třetí strany, nebo zda ji chcete zahrnout jako součást sady s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="cbeea-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="cbeea-107">Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="cbeea-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="cbeea-108">V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="cbeea-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="cbeea-109">Implementujete ho jako [metodu rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem třídy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cbeea-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="cbeea-110">Vytvoření řešení knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="cbeea-110">Creating a class library solution</span></span>

<span data-ttu-id="cbeea-111">Začněte vytvořením řešení pro projekt knihovny tříd a souvisejících projektů.</span><span class="sxs-lookup"><span data-stu-id="cbeea-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="cbeea-112">Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="cbeea-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="cbeea-113">Postup vytvoření řešení:</span><span class="sxs-lookup"><span data-stu-id="cbeea-113">To create the solution:</span></span>

1. <span data-ttu-id="cbeea-114">Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="cbeea-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="cbeea-115">V dialogovém okně **Nový projekt** rozbalte uzel **ostatní typy projektů** a vyberte **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cbeea-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="cbeea-116">Pojmenujte řešení "ClassLibraryProjects" a vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="cbeea-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Dialog pro vytvoření nového testovacího projektu v aplikaci Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="cbeea-118">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="cbeea-118">Creating the class library project</span></span>

<span data-ttu-id="cbeea-119">Vytvořte projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="cbeea-119">Create your class library project:</span></span>

1. <span data-ttu-id="cbeea-120">V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor řešení **ClassLibraryProjects** a z místní nabídky vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="cbeea-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="cbeea-121">V dialogovém okně **Přidat nový projekt** rozbalte uzel **Visual Basic** a pak vyberte **.NET Standard** uzel následovaný šablonou projektu **Knihovna tříd (.NET Standard)** .</span><span class="sxs-lookup"><span data-stu-id="cbeea-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="cbeea-122">Do textového pole **název** zadejte "StringLibrary" jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="cbeea-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="cbeea-123">Vyberte **OK** a vytvořte projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="cbeea-123">Select **OK** to create the class library project.</span></span>

   ![Dialogové okno Přidat nový projekt knihovny pro Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   <span data-ttu-id="cbeea-125">Okno Code (kód) se pak otevře ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbeea-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Okno aplikace sady Visual Studio zobrazující výchozí kód šablony knihovny tříd](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. <span data-ttu-id="cbeea-127">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cbeea-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="cbeea-128">V **Průzkumník řešení** oknech klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cbeea-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="cbeea-129">Textové pole **cílové rozhraní** uvádí, že cílíme na .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="cbeea-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="cbeea-131">V dialogovém okně **vlastnosti** také vymažte text v textovém poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="cbeea-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="cbeea-132">Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu, a všechny obory názvů definované v souborech zdrojového kódu jsou rodičem tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbeea-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="cbeea-133">Chceme definovat obor názvů nejvyšší úrovně pomocí klíčového slova [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="cbeea-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="cbeea-134">Kód v okně kód nahraďte následujícím kódem a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="cbeea-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="cbeea-135">Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, která vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="cbeea-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="cbeea-136">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="cbeea-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="cbeea-137">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="cbeea-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="cbeea-138">Na panelu nabídek vyberte **sestavení** **řešení**Build > .</span><span class="sxs-lookup"><span data-stu-id="cbeea-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="cbeea-139">Projekt by měl být zkompilován bez chyby.</span><span class="sxs-lookup"><span data-stu-id="cbeea-139">The project should compile without error.</span></span>

   ![Podokno výstup ukazující, že sestavení bylo úspěšné](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="cbeea-141">Další krok</span><span class="sxs-lookup"><span data-stu-id="cbeea-141">Next step</span></span>

<span data-ttu-id="cbeea-142">Úspěšně jste vytvořili knihovnu.</span><span class="sxs-lookup"><span data-stu-id="cbeea-142">You've successfully built the library.</span></span> <span data-ttu-id="cbeea-143">Vzhledem k tomu, že jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="cbeea-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="cbeea-144">Dalším krokem při vývoji knihovny je testování pomocí [projektu testování částí](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cbeea-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
