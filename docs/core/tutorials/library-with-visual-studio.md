---
title: "Sestavení .NET standardní knihovny tříd s C# a .NET Core v Visual Studio 2017"
description: "Naučte se vytvářet napsané v C# s použitím Visual Studio 2017 .NET standardní knihovny tříd."
keywords: ".NET core, .NET Standard knihovny tříd, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.workload: dotnetcore
ms.openlocfilehash: cc24c97e878362e91ab9d27452fd44d7df81ada7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="1cc33-104">Vytvoření knihovny tříd s C# a .NET Core v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1cc33-104">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="1cc33-105">A *knihovny tříd* definuje typy a metody, které se nazývají jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc33-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="1cc33-106">Knihovny tříd zacílený standardní rozhraní .NET 2.0 umožňuje své knihovny a volat žádnou implementaci rozhraní .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1cc33-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="1cc33-107">Po dokončení knihovny tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo jestli chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.</span><span class="sxs-lookup"><span data-stu-id="1cc33-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="1cc33-108">Seznam .NET Standard verze a platformy podporují, naleznete v části [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="1cc33-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="1cc33-109">V tomto tématu vytvoříte jednoduchého nástroje knihovny, která obsahuje jednu metodu zpracování řetězce.</span><span class="sxs-lookup"><span data-stu-id="1cc33-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="1cc33-110">Budete implementovat jej jako [metoda rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, aby můžete volat, jako by šlo členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="1cc33-110">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="1cc33-111">Vytváření řešení knihovna – třída</span><span class="sxs-lookup"><span data-stu-id="1cc33-111">Creating a class library solution</span></span>

<span data-ttu-id="1cc33-112">Začněte vytvořením řešení pro váš projekt knihovny tříd a jeho souvisejících projekty.</span><span class="sxs-lookup"><span data-stu-id="1cc33-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="1cc33-113">Řešení sady Visual Studio právě slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="1cc33-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="1cc33-114">Pokud chcete vytvořit řešení:</span><span class="sxs-lookup"><span data-stu-id="1cc33-114">To create the solution:</span></span>

1. <span data-ttu-id="1cc33-115">Na panelu nabídek Visual Studio zvolte **soubor** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1cc33-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="1cc33-116">V **nový projekt** dialogové okno, rozbalte **jiné typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1cc33-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="1cc33-117">Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1cc33-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Dialogové okno Nový projekt](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="1cc33-119">Vytvoření projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="1cc33-119">Creating the class library project</span></span>

<span data-ttu-id="1cc33-120">Vytvoření projektu knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="1cc33-120">Create your class library project:</span></span>

1. <span data-ttu-id="1cc33-121">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení souboru a v místní nabídce vyberte **přidat** > **nový Projekt**.</span><span class="sxs-lookup"><span data-stu-id="1cc33-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="1cc33-122">V **přidat nový projekt** dialogové okno, rozbalte **Visual C#** uzlu, pak vyberte **.NET Standard** následuje uzlu **(.NET Standard)–Knihovnatříd** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="1cc33-122">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="1cc33-123">V **název** textové pole, jako název projektu zadejte "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="1cc33-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="1cc33-124">Vyberte **OK** k vytvoření projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="1cc33-124">Select **OK** to create the class library project.</span></span>

   ![Přidat dialogové okno Nový projekt](./media/library-with-visual-studio/libproject.png)

   <span data-ttu-id="1cc33-126">V okně Kód pak otevře ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1cc33-126">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio okna aplikace zobrazuje kód výchozí třídy knihovny šablony](./media/library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="1cc33-128">Zkontrolujte, že naše knihovna cílem správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1cc33-128">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="1cc33-129">Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníku řešení** windows, potom vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1cc33-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="1cc33-130">**Cílové rozhraní** textového pole ukazuje, že jsme se cílení na rozhraní .NET 2.0 standardní.</span><span class="sxs-lookup"><span data-stu-id="1cc33-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="1cc33-132">Nahraďte kód v okně kód následující kód a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="1cc33-132">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="1cc33-133">Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, která vrátí <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="1cc33-133">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="1cc33-134">Standardu Unicode rozlišuje velká písmena z malých písmen.</span><span class="sxs-lookup"><span data-stu-id="1cc33-134">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="1cc33-135"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda vrátí `true` Pokud znak je velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="1cc33-135">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="1cc33-136">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="1cc33-136">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="1cc33-137">Projekt by měl kompilovat bez chyby.</span><span class="sxs-lookup"><span data-stu-id="1cc33-137">The project should compile without error.</span></span>

   ![V podokně výstupu zobrazující, že bylo úspěšně dokončeno sestavení](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a><span data-ttu-id="1cc33-139">Další krok</span><span class="sxs-lookup"><span data-stu-id="1cc33-139">Next step</span></span>

<span data-ttu-id="1cc33-140">Úspěšně jste vytvořili knihovny.</span><span class="sxs-lookup"><span data-stu-id="1cc33-140">You've successfully built the library.</span></span> <span data-ttu-id="1cc33-141">Vzhledem k tomu, že nebyly volá všechny její metody, nevíte, zda vše funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="1cc33-141">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="1cc33-142">Dalším krokem při vývoji vaše knihovna je otestovat pomocí [projektu testování částí](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1cc33-142">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>