---
title: Vytvoření knihovny tříd jazyka Visual Basic a .NET Core v Visual Studio 2017
description: Naučte se vytvářet napsané v jazyce Visual Basic, Visual Studio 2017 pomocí knihovny tříd
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 149be4788d924afee8affc816eede075cbe4e3a1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="ca8be-103">Vytvoření knihovny tříd jazyka Visual Basic a .NET Core v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ca8be-103">Building a class library with Visual Basic and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="ca8be-104">A *knihovny tříd* definuje typy a metody, které se nazývají jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca8be-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="ca8be-105">Knihovny tříd zacílený standardní rozhraní .NET 2.0 umožňuje své knihovny a volat žádnou implementaci rozhraní .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ca8be-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="ca8be-106">Po dokončení knihovny tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo jestli chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.</span><span class="sxs-lookup"><span data-stu-id="ca8be-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ca8be-107">Seznam .NET Standard verze a platformy podporují, naleznete v části [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="ca8be-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="ca8be-108">V tomto tématu vytvoříte jednoduchého nástroje knihovny, která obsahuje jednu metodu zpracování řetězce.</span><span class="sxs-lookup"><span data-stu-id="ca8be-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="ca8be-109">Budete implementovat jej jako [metoda rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) tak, aby můžete volat, jako by šlo členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="ca8be-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="ca8be-110">Vytváření řešení knihovna – třída</span><span class="sxs-lookup"><span data-stu-id="ca8be-110">Creating a class library solution</span></span>

<span data-ttu-id="ca8be-111">Začněte vytvořením řešení pro váš projekt knihovny tříd a jeho souvisejících projekty.</span><span class="sxs-lookup"><span data-stu-id="ca8be-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="ca8be-112">Řešení sady Visual Studio právě slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="ca8be-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="ca8be-113">Pokud chcete vytvořit řešení:</span><span class="sxs-lookup"><span data-stu-id="ca8be-113">To create the solution:</span></span>

1. <span data-ttu-id="ca8be-114">Na panelu nabídek Visual Studio zvolte **soubor** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ca8be-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="ca8be-115">V **nový projekt** dialogové okno, rozbalte **jiné typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca8be-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="ca8be-116">Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ca8be-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Dialogové okno Nový projekt](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="ca8be-118">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="ca8be-118">Creating the class library project</span></span>

<span data-ttu-id="ca8be-119">Vytvoření projektu knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="ca8be-119">Create your class library project:</span></span>

1. <span data-ttu-id="ca8be-120">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení souboru a v místní nabídce vyberte **přidat** > **nový Projekt**.</span><span class="sxs-lookup"><span data-stu-id="ca8be-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="ca8be-121">V **přidat nový projekt** dialogové okno, rozbalte **jazyka Visual Basic** uzlu, pak vyberte **.NET Standard** následuje uzlu **knihovny tříd (.NET Standard)**  šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="ca8be-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="ca8be-122">V **název** textové pole, jako název projektu zadejte "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="ca8be-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="ca8be-123">Vyberte **OK** k vytvoření projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="ca8be-123">Select **OK** to create the class library project.</span></span>

   ![Přidat dialogové okno Nový projekt](./media/vb-library-with-visual-studio/libproject.png)

   <span data-ttu-id="ca8be-125">V okně Kód pak otevře ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca8be-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Visual Studio okna aplikace zobrazuje kód výchozí třídy knihovny šablony](./media/vb-library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="ca8be-127">Zkontrolujte, že cílem knihovny správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ca8be-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="ca8be-128">Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníku řešení** windows, potom vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ca8be-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="ca8be-129">**Cílové rozhraní** textového pole ukazuje, že jsme se cílení na rozhraní .NET 2.0 standardní.</span><span class="sxs-lookup"><span data-stu-id="ca8be-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="ca8be-131">Také v **vlastnosti** dialogové okno, odstraňte text v **kořenový obor názvů** textové pole.</span><span class="sxs-lookup"><span data-stu-id="ca8be-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="ca8be-132">Pro každý projekt automaticky vytvoří obor názvů, který odpovídá názvu projektu jazyka Visual Basic a všech oborů názvů definovaných v soubory zdrojového kódu jsou rodičů tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ca8be-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="ca8be-133">Chceme definovat nejvyšší úrovně oboru názvů pomocí [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ca8be-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="ca8be-134">Nahraďte kód v okně kód následující kód a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="ca8be-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="ca8be-135">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, která vrátí <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="ca8be-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="ca8be-136">Standardu Unicode rozlišuje velká písmena z malých písmen.</span><span class="sxs-lookup"><span data-stu-id="ca8be-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="ca8be-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda vrátí `true` Pokud znak je velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="ca8be-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="ca8be-138">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="ca8be-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="ca8be-139">Projekt by měl kompilovat bez chyby.</span><span class="sxs-lookup"><span data-stu-id="ca8be-139">The project should compile without error.</span></span>

   ![V podokně výstupu zobrazující, že bylo úspěšně dokončeno sestavení](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a><span data-ttu-id="ca8be-141">Další krok</span><span class="sxs-lookup"><span data-stu-id="ca8be-141">Next step</span></span>

<span data-ttu-id="ca8be-142">Úspěšně jste vytvořili knihovny.</span><span class="sxs-lookup"><span data-stu-id="ca8be-142">You've successfully built the library.</span></span> <span data-ttu-id="ca8be-143">Vzhledem k tomu, že nebyly volá všechny její metody, nevíte, zda vše funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ca8be-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="ca8be-144">Dalším krokem při vývoji vaše knihovna je otestovat pomocí [projektu testování částí](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ca8be-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
