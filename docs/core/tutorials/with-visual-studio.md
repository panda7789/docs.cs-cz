---
title: Vytvoření aplikace Hello World s .NET Core a C# v Visual Studio 2017
description: Naučte se vytvářet jednoduché konzolové aplikace .NET Core pomocí C# s použitím Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: 7abc0cc087553e2cac10c8cc1da560a048b8e323
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="49e50-103">Sestavení C# Hello, World aplikace s .NET Core v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="49e50-103">Build a C# Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="49e50-104">Toto téma obsahuje podrobné Úvod do vytváření, ladění a publikování pomocí jazyka C# v aplikaci Visual Studio 2017 jednoduché aplikace konzoly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49e50-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="49e50-105">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vytváření aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49e50-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="49e50-106">Tak dlouho, dokud aplikace nemá závislosti specifické pro platformu, aplikace můžete spustit na jakékoli platformě s cílem .NET Core a systému, který má nainstalovaný .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49e50-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49e50-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49e50-107">Prerequisites</span></span>

<span data-ttu-id="49e50-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.</span><span class="sxs-lookup"><span data-stu-id="49e50-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="49e50-109">Můžete vyvíjet aplikace s .NET Core 1.1 nebo .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="49e50-109">You can develop your app with either .NET Core 1.1 or .NET Core 2.0.</span></span>

<span data-ttu-id="49e50-110">Další informace najdete v tématu [požadavky pro .NET Core v systému Windows](../../core/windows-prerequisites.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="49e50-110">For more information, see the [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md) topic.</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="49e50-111">Jednoduché aplikace Hello World</span><span class="sxs-lookup"><span data-stu-id="49e50-111">A simple Hello World application</span></span>

<span data-ttu-id="49e50-112">Začněte tím, že vytvoření jednoduché aplikace konzoly "Hello World".</span><span class="sxs-lookup"><span data-stu-id="49e50-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="49e50-113">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="49e50-113">Follow these steps:</span></span>

1. <span data-ttu-id="49e50-114">Spusťte Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="49e50-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="49e50-115">Vyberte **soubor** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="49e50-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="49e50-116">V *nový projekt*\* dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="49e50-116">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="49e50-117">Vyberte **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="49e50-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="49e50-118">V **název** textové pole, zadejte "Hello World".</span><span class="sxs-lookup"><span data-stu-id="49e50-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="49e50-119">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="49e50-119">Select the **OK** button.</span></span>

   ![Dialogové okno Nový projekt s vybrané konzolové aplikace](./media/with-visual-studio/newproject.png)
   
1. <span data-ttu-id="49e50-121">Visual Studio používá šablonu pro vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="49e50-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="49e50-122">Šablona konzolovou aplikaci C# pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu `Main`, které nepřijímá <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="49e50-122">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="49e50-123">`Main` je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při jeho spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="49e50-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="49e50-124">Jsou k dispozici v žádných argumentů příkazového řádku zadán při spuštění aplikace *argumentů* pole.</span><span class="sxs-lookup"><span data-stu-id="49e50-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/devenv.png)

   <span data-ttu-id="49e50-126">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="49e50-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="49e50-127">Zavolá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="49e50-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="49e50-128">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="49e50-128">in the console window.</span></span> <span data-ttu-id="49e50-129">Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="49e50-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="49e50-130">Pokud tak učiníte, v okně konzoly je viditelná pouze stručný časový interval před toto okno zavře.</span><span class="sxs-lookup"><span data-stu-id="49e50-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="49e50-131">K tomu dochází, protože `Main` metoda ukončí a co nejdříve jeden příkaz v ukončení aplikace `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="49e50-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="49e50-132">Aby aplikace pozastavit předtím, než toto okno zavře okno konzoly, přidejte následující kód ihned po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda:</span><span class="sxs-lookup"><span data-stu-id="49e50-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   <span data-ttu-id="49e50-133">Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud není stisknuta klíč.</span><span class="sxs-lookup"><span data-stu-id="49e50-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="49e50-134">Na panelu nabídek vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="49e50-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="49e50-135">To zkompiluje vaším programem do převodní jazyk (IL), který je převést na binární kód kompilátorem v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="49e50-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="49e50-136">Spusťte program výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="49e50-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Okno konzoly zobrazující Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="49e50-138">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="49e50-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="49e50-139">Rozšíření aplikace Hello World</span><span class="sxs-lookup"><span data-stu-id="49e50-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="49e50-140">Vylepšení aplikace vyzve uživatele k zadání názvu a zobrazit ji společně s datum a čas.</span><span class="sxs-lookup"><span data-stu-id="49e50-140">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="49e50-141">Upravit a otestujte aplikaci, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="49e50-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="49e50-142">Zadejte následující kód C# v okně kód ihned po levá hranatá závorka, která následuje `static void Main(string[] args)` řádku a před první pravá závorka:</span><span class="sxs-lookup"><span data-stu-id="49e50-142">Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing bracket:</span></span>

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="49e50-143">Tento kód nahradí existující <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.</span><span class="sxs-lookup"><span data-stu-id="49e50-143">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio programu c ostré soubor s aktualizované Main – metoda](./media/with-visual-studio/codewindow.png)

   <span data-ttu-id="49e50-145">Tento kód zobrazí "Jaký je název vaší?"</span><span class="sxs-lookup"><span data-stu-id="49e50-145">This code displays "What is your name?"</span></span> <span data-ttu-id="49e50-146">v okně konzoly a počká, dokud nebude uživatel zadá řetězec následuje klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="49e50-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="49e50-147">Ukládají se tento řetězec do proměnné s názvem `name`.</span><span class="sxs-lookup"><span data-stu-id="49e50-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="49e50-148">Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `date`.</span><span class="sxs-lookup"><span data-stu-id="49e50-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="49e50-149">Nakonec se používá [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="49e50-149">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="49e50-150">Kompilace programu výběrem **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="49e50-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="49e50-151">Spusťte program v režimu ladění v sadě Visual Studio vyberete zelenou šipku na panelu nástrojů, Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="49e50-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="49e50-152">Odpověď na výzvu zadáním názvu a stisknutím klávesy Enter.</span><span class="sxs-lookup"><span data-stu-id="49e50-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Okno konzoly výstup je upravený program](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="49e50-154">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="49e50-154">Press any key to close the console window.</span></span>

<span data-ttu-id="49e50-155">Po vytvoření a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="49e50-155">You've created and run your application.</span></span> <span data-ttu-id="49e50-156">K vývoji professional aplikace, proveďte některé další kroky, aby vaše aplikace připravené pro verze:</span><span class="sxs-lookup"><span data-stu-id="49e50-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="49e50-157">Informace o ladění aplikace najdete v tématu [ladění aplikace C# Hello, World s Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="49e50-157">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="49e50-158">Informace o vývoji a publikování distribuovatelného verzi vaší aplikace, najdete v části [publikování aplikace C# Hello, World s Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="49e50-158">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="49e50-159">Související témata</span><span class="sxs-lookup"><span data-stu-id="49e50-159">Related topics</span></span>

<span data-ttu-id="49e50-160">Místo konzolovou aplikaci můžete také vytvořit knihovny tříd s .NET Core a Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="49e50-160">Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017.</span></span> <span data-ttu-id="49e50-161">Krok za krokem úvod naleznete v tématu [vytvoření knihovny tříd s C# a .NET Core ve Visual Studio 2017](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="49e50-161">For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).</span></span>

<span data-ttu-id="49e50-162">Také můžete vyvíjet aplikace konzoly .NET Core na Mac, Linux a Windows pomocí [Visual Studio Code](https://code.visualstudio.com/), editor ke stažení kódu.</span><span class="sxs-lookup"><span data-stu-id="49e50-162">You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor.</span></span> <span data-ttu-id="49e50-163">Podrobný kurz, najdete v části [Začínáme s Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="49e50-163">For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md).</span></span>
