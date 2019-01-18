---
title: .NET core aplikace Hello World v jazyce Visual Basic v sadě Visual Studio 2017
description: Zjistěte, jak vytvořit jednoduchou konzolovou aplikaci .NET Core pomocí sady Visual Basic pomocí sady Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: de7a423bb3e9a288d17c86e9e0afc3b00f6fd80b
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362259"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="c9050-103">Vytvořit aplikaci Hello World jazyka Visual Basic pomocí .NET Core SDK v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c9050-103">Build a Visual Basic Hello World application with the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="c9050-104">Toto téma obsahuje podrobný Úvod k vytváření, ladění a publikování jednoduchou konzolovou aplikaci .NET Core pomocí jazyka Visual Basic v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c9050-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="c9050-105">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro sestavování aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9050-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="c9050-106">Za předpokladu, aplikace nemá závislosti pro konkrétní platformu, aplikaci můžete spustit na libovolné platformě, který cílí na .NET Core a na jakémkoli počítači, který má nainstalovaný .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9050-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9050-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9050-107">Prerequisites</span></span>

<span data-ttu-id="c9050-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="c9050-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="c9050-109">Můžete vyvíjet aplikace s využitím .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c9050-109">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="c9050-110">Další informace najdete v tématu [předpoklady pro .NET Core ve Windows](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="c9050-110">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="c9050-111">Jednoduchou aplikaci Hello World</span><span class="sxs-lookup"><span data-stu-id="c9050-111">A simple Hello World application</span></span>

<span data-ttu-id="c9050-112">Začněte vytvořením jednoduché konzolové aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c9050-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="c9050-113">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="c9050-113">Follow these steps:</span></span>

1. <span data-ttu-id="c9050-114">Spusťte Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c9050-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="c9050-115">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="c9050-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c9050-116">V *nový projekt*\* dialogového okna, vyberte **jazyka Visual Basic** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="c9050-116">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c9050-117">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="c9050-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c9050-118">V **název** textové pole, zadejte "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c9050-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="c9050-119">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9050-119">Select the **OK** button.</span></span>

   ![Dialogové okno nového projektu s vybraná aplikace konzoly](./media/vb-with-visual-studio/visual-studio-new-project.png)
   
1. <span data-ttu-id="c9050-121">Visual Studio používá šablony k vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c9050-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="c9050-122">Šablona konzolové aplikace jazyka Visual Basic pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu, `Main`, která přijímá <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="c9050-122">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c9050-123">`Main` je vstupní bod aplikace metodu, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9050-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c9050-124">Jsou k dispozici v jakékoli argumenty příkazového řádku při spuštění aplikace *args* pole.</span><span class="sxs-lookup"><span data-stu-id="c9050-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio a nový projekt Hello World](./media/vb-with-visual-studio/visual-studio-main-window.png)

   <span data-ttu-id="c9050-126">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c9050-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c9050-127">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcový literál "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c9050-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="c9050-128">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9050-128">in the console window.</span></span> <span data-ttu-id="c9050-129">Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="c9050-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="c9050-130">Pokud tak učiníte, v okně konzoly je viditelná pro jenom stručný časový interval předtím, než se toto okno zavře.</span><span class="sxs-lookup"><span data-stu-id="c9050-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="c9050-131">K tomu dochází, `Main` metoda se ukončí a ukončení aplikace co nejdříve jeden příkaz v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c9050-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="c9050-132">Aby v aplikaci k pozastavení před zavřením okna konzoly, přidejte následující kód bezprostředně po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="c9050-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="c9050-133">Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud se stiskne klávesa.</span><span class="sxs-lookup"><span data-stu-id="c9050-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="c9050-134">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="c9050-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="c9050-135">Tento program zkompiluje do intermediate language (IL), která se převádí do binárního kódu, kompilátor just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c9050-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="c9050-136">Spusťte program tak, že vyberete **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c9050-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Okna konzoly zobrazuje Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c9050-138">Stisknutím jakékoli klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9050-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="c9050-139">Vylepšení aplikace Hello World</span><span class="sxs-lookup"><span data-stu-id="c9050-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="c9050-140">Vylepšete vaše aplikace vyzve uživatele k jeho název a zobrazit společně s datum a čas.</span><span class="sxs-lookup"><span data-stu-id="c9050-140">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="c9050-141">Upravit a otestujte aplikaci, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="c9050-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="c9050-142">Zadejte následující kód jazyka Visual Basic v okně kódu ihned po levá hranatá závorka, která následuje `Sub Main(args As String())` řádku a před první uzavírací závorku:</span><span class="sxs-lookup"><span data-stu-id="c9050-142">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="c9050-143">Tento kód nahradí stávající <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.</span><span class="sxs-lookup"><span data-stu-id="c9050-143">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio programový soubor s aktualizovanou metodu Main](./media/vb-with-visual-studio/visual-basic-code-window.png)

   <span data-ttu-id="c9050-145">Tento kód zobrazí "Jaký je název vašeho?"</span><span class="sxs-lookup"><span data-stu-id="c9050-145">This code displays "What is your name?"</span></span> <span data-ttu-id="c9050-146">v okně konzoly a počká, dokud uživatel zadá řetězec, za nímž následuje klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="c9050-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c9050-147">Ukládají se tento řetězec do proměnné s názvem `name`.</span><span class="sxs-lookup"><span data-stu-id="c9050-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c9050-148">Také načte hodnota <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="c9050-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="c9050-149">Nakonec se používá [interpolovaný řetězec](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení tyto hodnoty v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9050-149">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c9050-150">Kompilovat program výběrem **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="c9050-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c9050-151">Spusťte program v režimu ladění v sadě Visual Studio vyberte zelenou šipku na panelu nástrojů, stisknutím klávesy F5 nebo výběrem položky **ladění** > **spustit ladění** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="c9050-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="c9050-152">Na výzvy odpovíte zadáním názvu a stisknutím klávesy Enter.</span><span class="sxs-lookup"><span data-stu-id="c9050-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Okno konzoly s výstupem upravené programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c9050-154">Stisknutím jakékoli klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9050-154">Press any key to close the console window.</span></span>

<span data-ttu-id="c9050-155">Jste vytvořili a spustili aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9050-155">You've created and run your application.</span></span> <span data-ttu-id="c9050-156">K vývoji profesionální aplikace, proveďte některé další kroky pro zajištění připraven k vydání aplikace:</span><span class="sxs-lookup"><span data-stu-id="c9050-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="c9050-157">Chcete-li ladit aplikaci, najdete v článku [ladit aplikaci .NET Core Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c9050-157">To debug your application, see [Debug your .NET Core Hello World application using Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="c9050-158">K publikování distribuovatelná verze aplikace, najdete v článku [publikování aplikace .NET Core Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c9050-158">To publish a distributable version of your application, see [Publish your .NET Core Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
