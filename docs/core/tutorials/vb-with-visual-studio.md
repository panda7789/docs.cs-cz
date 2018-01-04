---
title: "Vytvoření aplikace Hello World s .NET Core a Visual Basic v Visual Studio 2017"
description: "Naučte se vytvářet jednoduché konzolové aplikace .NET Core pomocí jazyka Visual Basic pomocí Visual Studio 2017."
keywords: .NET core, aplikace konzoly .NET Core, Visual Studio 2017
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs: vb
ms.workload: dotnetcore
ms.openlocfilehash: 058e8740ed523d606da0ad46e052f91f31b3b2d9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="0c91d-104">Vytvoření aplikace Visual Basic Hello World s .NET Core v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0c91d-104">Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="0c91d-105">Toto téma obsahuje podrobné Úvod do vytváření, ladění a publikování pomocí jazyka Visual Basic ve Visual Studio 2017 jednoduché aplikace konzoly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c91d-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="0c91d-106">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vytváření aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c91d-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="0c91d-107">Tak dlouho, dokud aplikace nemá závislosti specifické pro platformu, aplikace můžete spustit na jakékoli platformě s cílem .NET Core a systému, který má nainstalovaný .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c91d-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c91d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c91d-108">Prerequisites</span></span>

<span data-ttu-id="0c91d-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.</span><span class="sxs-lookup"><span data-stu-id="0c91d-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="0c91d-110">Můžete vyvíjet aplikace pomocí rozhraní .NET 2.0 jádra.</span><span class="sxs-lookup"><span data-stu-id="0c91d-110">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="0c91d-111">Další informace najdete v tématu [požadavky pro .NET Core v systému Windows](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="0c91d-111">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="0c91d-112">Jednoduché aplikace Hello World</span><span class="sxs-lookup"><span data-stu-id="0c91d-112">A simple Hello World application</span></span>

<span data-ttu-id="0c91d-113">Začněte tím, že vytvoření jednoduché aplikace konzoly "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0c91d-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="0c91d-114">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0c91d-114">Follow these steps:</span></span>

1. <span data-ttu-id="0c91d-115">Spusťte Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0c91d-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="0c91d-116">Vyberte **soubor** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="0c91d-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0c91d-117">V *nový projekt** dialogovém okně, vyberte **jazyka Visual Basic** následuje uzlu **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="0c91d-117">In the *New Project** dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0c91d-118">Vyberte **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="0c91d-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0c91d-119">V **název** textové pole, zadejte "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0c91d-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="0c91d-120">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0c91d-120">Select the **OK** button.</span></span>

   ![Dialogové okno Nový projekt s vybrané konzolové aplikace](./media/vb-with-visual-studio/new-project.png)
   
1. <span data-ttu-id="0c91d-122">Visual Studio používá šablonu pro vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="0c91d-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="0c91d-123">Šablona konzolové aplikace jazyka Visual Basic pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu `Main`, která má <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="0c91d-123">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="0c91d-124">`Main`je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při jeho spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c91d-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="0c91d-125">Jsou k dispozici v žádných argumentů příkazového řádku zadán při spuštění aplikace *argumentů* pole.</span><span class="sxs-lookup"><span data-stu-id="0c91d-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio a nový projekt HelloWorld](./media/vb-with-visual-studio/devenv.png)

   <span data-ttu-id="0c91d-127">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0c91d-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="0c91d-128">Zavolá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="0c91d-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="0c91d-129">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0c91d-129">in the console window.</span></span> <span data-ttu-id="0c91d-130">Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="0c91d-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="0c91d-131">Pokud tak učiníte, v okně konzoly je viditelná pouze stručný časový interval před toto okno zavře.</span><span class="sxs-lookup"><span data-stu-id="0c91d-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="0c91d-132">K tomu dochází, protože `Main` metoda ukončí a co nejdříve jeden příkaz v ukončení aplikace `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="0c91d-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="0c91d-133">Aby aplikace pozastavit předtím, než toto okno zavře okno konzoly, přidejte následující kód ihned po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda:</span><span class="sxs-lookup"><span data-stu-id="0c91d-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="0c91d-134">Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud není stisknuta klíč.</span><span class="sxs-lookup"><span data-stu-id="0c91d-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="0c91d-135">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="0c91d-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="0c91d-136">To zkompiluje vaším programem do převodní jazyk (IL), který je převést na binární kód kompilátorem v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="0c91d-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="0c91d-137">Spusťte program výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0c91d-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Okno konzoly zobrazující Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="0c91d-139">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="0c91d-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="0c91d-140">Rozšíření aplikace Hello World</span><span class="sxs-lookup"><span data-stu-id="0c91d-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="0c91d-141">Vylepšení aplikace požádat uživatele o své jméno a zobrazení spolu s datum a čas.</span><span class="sxs-lookup"><span data-stu-id="0c91d-141">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="0c91d-142">Upravit a otestujte aplikaci, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0c91d-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="0c91d-143">Zadejte následující kód jazyka Visual Basic v okně kód ihned po levá hranatá závorka, která následuje `Sub Main(args As String())` řádku a před první pravá závorka:</span><span class="sxs-lookup"><span data-stu-id="0c91d-143">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="0c91d-144">Tento kód nahradí existující <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.</span><span class="sxs-lookup"><span data-stu-id="0c91d-144">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio programový soubor s aktualizované Main – metoda](./media/vb-with-visual-studio/codewindow.png)

   <span data-ttu-id="0c91d-146">Tento kód zobrazí "Jaký je název vaší?"</span><span class="sxs-lookup"><span data-stu-id="0c91d-146">This code displays "What is your name?"</span></span> <span data-ttu-id="0c91d-147">v okně konzoly a počká, dokud nebude uživatel zadá řetězec následuje klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="0c91d-147">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="0c91d-148">Ukládají se tento řetězec do proměnné s názvem `name`.</span><span class="sxs-lookup"><span data-stu-id="0c91d-148">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="0c91d-149">Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="0c91d-149">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="0c91d-150">Nakonec se používá [interpolované řetězce](../../csharp/language-reference/keywords/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0c91d-150">Finally, it uses an [interpolated string](../../csharp/language-reference/keywords/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="0c91d-151">Kompilace programu výběrem **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="0c91d-151">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="0c91d-152">Spusťte program v režimu ladění v sadě Visual Studio vyberete zelenou šipku na panelu nástrojů, Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="0c91d-152">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="0c91d-153">Odpověď na výzvu zadáním názvu a stisknutím klávesy Enter.</span><span class="sxs-lookup"><span data-stu-id="0c91d-153">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Okno konzoly výstup je upravený program](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="0c91d-155">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="0c91d-155">Press any key to close the console window.</span></span>

<span data-ttu-id="0c91d-156">Po vytvoření a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c91d-156">You've created and run your application.</span></span> <span data-ttu-id="0c91d-157">K vývoji professional aplikace, proveďte některé další kroky, aby vaše aplikace připravené pro verze:</span><span class="sxs-lookup"><span data-stu-id="0c91d-157">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="0c91d-158">Informace o ladění aplikace najdete v tématu [ladění aplikace C# Hello, World s Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0c91d-158">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="0c91d-159">Informace o vývoji a publikování distribuovatelného verzi vaší aplikace, najdete v části [publikování aplikace C# Hello, World s Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0c91d-159">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
