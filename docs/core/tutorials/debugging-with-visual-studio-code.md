---
title: Ladění konzolové aplikace .NET Core pomocí Visual Studio Code
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: 40e9b114df1bd12fb05bfb773781d6009d087a06
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702124"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="faf3e-103">Kurz: ladění konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="faf3e-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="faf3e-104">Tento kurz zavádí ladicí nástroje, které jsou k dispozici v Visual Studio Code pro práci s aplikacemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faf3e-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="faf3e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="faf3e-105">Prerequisites</span></span>

- <span data-ttu-id="faf3e-106">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="faf3e-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="faf3e-107">Použít konfiguraci sestavení pro ladění</span><span class="sxs-lookup"><span data-stu-id="faf3e-107">Use Debug build configuration</span></span>

<span data-ttu-id="faf3e-108">*Ladění* a vydaných *verzí* jsou integrované konfigurace sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faf3e-108">*Debug* and *Release* are .NET Core's built-in build configurations.</span></span> <span data-ttu-id="faf3e-109">Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="faf3e-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="faf3e-110">V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="faf3e-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="faf3e-111">Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.</span><span class="sxs-lookup"><span data-stu-id="faf3e-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="faf3e-112">Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.</span><span class="sxs-lookup"><span data-stu-id="faf3e-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="faf3e-113">Ve výchozím nastavení Visual Studio Code spuštění nastavení používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.</span><span class="sxs-lookup"><span data-stu-id="faf3e-113">By default, Visual Studio Code launch settings use the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="faf3e-114">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="faf3e-114">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="faf3e-115">Otevřete složku projektu, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="faf3e-115">Open the folder of the project that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="faf3e-116">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="faf3e-116">Set a breakpoint</span></span>

<span data-ttu-id="faf3e-117">*Zarážka* dočasně přerušuje provádění aplikace před provedením řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="faf3e-117">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="faf3e-118">Otevřete soubor *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="faf3e-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="faf3e-119">Nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="faf3e-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="faf3e-120">Levý okraj je nalevo od čísel řádků.</span><span class="sxs-lookup"><span data-stu-id="faf3e-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="faf3e-121">Další způsoby, jak nastavit zarážku, jsou stisknuté klávesou <kbd>F9</kbd> nebo výběrem možnosti **Spustit**  >  **přepínací zarážku** z nabídky, když je vybraná řádka kódu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-121">Other ways to set a breakpoint are by pressing <kbd>F9</kbd> or selecting **Run** > **Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

   <span data-ttu-id="faf3e-122">Visual Studio Code určuje čáru, na které je zarážka nastavena, zobrazením červené tečky na levém okraji.</span><span class="sxs-lookup"><span data-stu-id="faf3e-122">Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Sada zarážek":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="faf3e-124">Nastavení pro terminálový vstup</span><span class="sxs-lookup"><span data-stu-id="faf3e-124">Set up for terminal input</span></span>

<span data-ttu-id="faf3e-125">Zarážka je umístěna po `Console.ReadLine` volání metody.</span><span class="sxs-lookup"><span data-stu-id="faf3e-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="faf3e-126">**Konzola ladění** nepřijímá vstup terminálu pro spuštěný program.</span><span class="sxs-lookup"><span data-stu-id="faf3e-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="faf3e-127">Pro zpracování vstupu terminálu během ladění můžete použít integrovaný terminál (jeden z Visual Studio Code Windows) nebo externí terminál.</span><span class="sxs-lookup"><span data-stu-id="faf3e-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="faf3e-128">V tomto kurzu použijete integrovaný terminál.</span><span class="sxs-lookup"><span data-stu-id="faf3e-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="faf3e-129">Otevřete *. VSCode/launch.jsna*.</span><span class="sxs-lookup"><span data-stu-id="faf3e-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="faf3e-130">Změňte `console` nastavení na `integratedTerminal` .</span><span class="sxs-lookup"><span data-stu-id="faf3e-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="faf3e-131">Z:</span><span class="sxs-lookup"><span data-stu-id="faf3e-131">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="faf3e-132">Do:</span><span class="sxs-lookup"><span data-stu-id="faf3e-132">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="faf3e-133">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="faf3e-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="faf3e-134">Spustit ladění</span><span class="sxs-lookup"><span data-stu-id="faf3e-134">Start debugging</span></span>

1. <span data-ttu-id="faf3e-135">Otevřete zobrazení ladění výběrem ikony ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="faf3e-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Otevřete kartu ladění v Visual Studio Code":::

1. <span data-ttu-id="faf3e-137">V horní části podokna vyberte zelenou šipku a vedle položku **.NET Core Launch (konzola)**.</span><span class="sxs-lookup"><span data-stu-id="faf3e-137">Select the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span> <span data-ttu-id="faf3e-138">Jiný způsob, jak spustit program v režimu ladění, je výběrem možnosti **Spustit**  >  **ladění** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="faf3e-138">Another way to start the program in debugging mode is by choosing **Run** > **Start Debugging** from the menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Spustit ladění":::

1. <span data-ttu-id="faf3e-140">Vyberte kartu **terminál** , pokud chcete zobrazit "Co je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="faf3e-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="faf3e-141">před čekáním na odpověď se zobrazí výzva k zadání programu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Výběr karty terminálu":::

1. <span data-ttu-id="faf3e-143">V okně **terminálu** zadejte řetězec jako odpověď na výzvu pro název a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="faf3e-144">Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="faf3e-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="faf3e-145">Oddíl **místních** hodnot v okně **proměnné** zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="faf3e-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Pozice zarážky, zobrazení lokálních hodnot":::

## <a name="use-the-debug-console"></a><span data-ttu-id="faf3e-147">Použití konzoly ladění</span><span class="sxs-lookup"><span data-stu-id="faf3e-147">Use the Debug Console</span></span>

<span data-ttu-id="faf3e-148">Okno **konzoly ladění** vám umožní pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="faf3e-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="faf3e-149">Můžete změnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.</span><span class="sxs-lookup"><span data-stu-id="faf3e-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="faf3e-150">Vyberte kartu **Konzola ladění** .</span><span class="sxs-lookup"><span data-stu-id="faf3e-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="faf3e-151">Zadejte `name = "Gracie"` na příkazovém řádku v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="faf3e-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Změnit hodnoty proměnných":::

1. <span data-ttu-id="faf3e-153">Zadejte `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="faf3e-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="faf3e-154">V okně **proměnné** se zobrazí nové hodnoty `name` `date` proměnných a.</span><span class="sxs-lookup"><span data-stu-id="faf3e-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="faf3e-155">Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** .</span><span class="sxs-lookup"><span data-stu-id="faf3e-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="faf3e-156">Dalším způsobem, jak pokračovat, je stisknout klávesu <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Pokračovat v ladění":::

1. <span data-ttu-id="faf3e-158">Znovu vyberte kartu **terminálu** .</span><span class="sxs-lookup"><span data-stu-id="faf3e-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="faf3e-159">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **konzole ladění**.</span><span class="sxs-lookup"><span data-stu-id="faf3e-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminál znázorňující zadané hodnoty":::

1. <span data-ttu-id="faf3e-161">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="faf3e-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="faf3e-162">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="faf3e-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="faf3e-163">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="faf3e-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="faf3e-164">Co se stane, když uživatel nezadá něco?</span><span class="sxs-lookup"><span data-stu-id="faf3e-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="faf3e-165">Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.</span><span class="sxs-lookup"><span data-stu-id="faf3e-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="faf3e-166">Klikněte pravým tlačítkem myši (<kbd>CTRL +</kbd>kliknutí na MacOS) na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="faf3e-166">Right-click (<kbd>Ctrl</kbd>-click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="faf3e-167">V místní nabídce vyberte **Upravit zarážku** , aby se otevřelo dialogové okno, které vám umožní zadat podmíněný výraz.</span><span class="sxs-lookup"><span data-stu-id="faf3e-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Místní nabídka zarážky":::

1. <span data-ttu-id="faf3e-169">`Expression`V rozevíracím seznamu vyberte, zadejte následující podmíněný výraz a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Zadejte podmíněný výraz.":::

   <span data-ttu-id="faf3e-171">Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="faf3e-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="faf3e-172">Místo podmíněného výrazu můžete zadat *počet*průchodů, který přerušuje spuštění programu před provedením příkazu určeného počtu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="faf3e-173">Další možností je určit *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="faf3e-173">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="faf3e-174">Spusťte program s laděním stisknutím klávesy <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-174">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="faf3e-175">Na kartě **terminál** po zobrazení výzvy k zadání názvu stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="faf3e-175">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="faf3e-176">Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ) je splněná, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="faf3e-176">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="faf3e-177">Okno **proměnné** ukazuje, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="faf3e-177">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="faf3e-178">Zadáním následujícího příkazu na příkazovém řádku **konzoly ladění** a stisknutím klávesy <kbd>ENTER</kbd>potvrďte, že hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="faf3e-178">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="faf3e-179">Výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="faf3e-179">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Ladit konzolu vracející hodnotu true po provedení příkazu":::

1. <span data-ttu-id="faf3e-181">Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-181">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="faf3e-182">Vyberte kartu **terminál** a stisknutím libovolné klávesy ukončete program a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="faf3e-182">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="faf3e-183">Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="faf3e-183">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="faf3e-184">Další způsoby, jak zarážku vymazat, je stisknutí klávesy <kbd>F9</kbd> nebo zvolením možnosti **Spustit > v nabídce Přepnout zarážku** , zatímco je vybraný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-184">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run > Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

1. <span data-ttu-id="faf3e-185">Pokud se zobrazí upozornění, že bude ztracena Podmínka zarážky, vyberte možnost **odebrat zarážku**.</span><span class="sxs-lookup"><span data-stu-id="faf3e-185">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="faf3e-186">Krokovat program</span><span class="sxs-lookup"><span data-stu-id="faf3e-186">Step through a program</span></span>

<span data-ttu-id="faf3e-187">Visual Studio Code také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="faf3e-187">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="faf3e-188">Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-188">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="faf3e-189">Vzhledem k tomu, že je tento program malý, můžete projít celým programem.</span><span class="sxs-lookup"><span data-stu-id="faf3e-189">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="faf3e-190">Nastavte zarážku na levou složenou závorku `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="faf3e-190">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="faf3e-191">Stisknutím klávesy <kbd>F5</kbd> spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="faf3e-191">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="faf3e-192">Visual Studio Code zvýrazní řádek zarážky.</span><span class="sxs-lookup"><span data-stu-id="faf3e-192">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="faf3e-193">V tomto okamžiku okno **proměnné** ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="faf3e-193">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="faf3e-194">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-194">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Tlačítko Krokovat s vnořením":::

   <span data-ttu-id="faf3e-196">Visual Studio Code zvýrazní další řádek.</span><span class="sxs-lookup"><span data-stu-id="faf3e-196">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="faf3e-197">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-197">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="faf3e-198">Visual Studio Code spustí `Console.WriteLine` pro příkazový řádek název a zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="faf3e-198">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="faf3e-199">Další řádek je `Console.ReadLine` pro `name` .</span><span class="sxs-lookup"><span data-stu-id="faf3e-199">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="faf3e-200">Okno **proměnné** se nezměnilo a karta **terminálu** zobrazuje "Co je vaše jméno?"</span><span class="sxs-lookup"><span data-stu-id="faf3e-200">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="faf3e-201">výzv.</span><span class="sxs-lookup"><span data-stu-id="faf3e-201">prompt.</span></span>

1. <span data-ttu-id="faf3e-202">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-202">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="faf3e-203">Visual Studio zvýrazní `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="faf3e-203">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="faf3e-204">V okně **proměnné** se zobrazí, že `name` je stále `null` .</span><span class="sxs-lookup"><span data-stu-id="faf3e-204">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="faf3e-205">Na výzvu odpovězte zadáním řetězce na kartě terminálu a stisknutím klávesy <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-205">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="faf3e-206">Karta **terminálu** nezobrazuje řetězec, který zadáte při zadávání, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda zachytí vstup.</span><span class="sxs-lookup"><span data-stu-id="faf3e-206">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="faf3e-207">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-207">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="faf3e-208">Visual Studio Code zvýrazní `date` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="faf3e-208">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="faf3e-209">Okno **proměnné** zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="faf3e-209">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="faf3e-210">Na kartě **terminál** se zobrazí řetězec, který jste zadali na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="faf3e-210">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="faf3e-211">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-211">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="faf3e-212">Okno **proměnné** zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="faf3e-212">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="faf3e-213">Vyberte možnost **Spustit**  >  **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-213">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="faf3e-214">Visual Studio Code volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="faf3e-214">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="faf3e-215">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="faf3e-215">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="faf3e-216">Vyberte možnost **Spustit**  >  **Krok ven** nebo stiskněte klávesu <kbd>SHIFT</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="faf3e-216">Select **Run** > **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Tlačítko pro krokování":::

1. <span data-ttu-id="faf3e-218">Vyberte kartu **terminál** .</span><span class="sxs-lookup"><span data-stu-id="faf3e-218">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="faf3e-219">Terminál zobrazí "při ukončení stiskněte libovolnou klávesu..."</span><span class="sxs-lookup"><span data-stu-id="faf3e-219">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="faf3e-220">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="faf3e-220">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="faf3e-221">Použít konfiguraci sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="faf3e-221">Use Release build configuration</span></span>

<span data-ttu-id="faf3e-222">Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="faf3e-222">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="faf3e-223">Verze Release zahrnuje optimalizace kompilátoru, které mohou ovlivnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="faf3e-223">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="faf3e-224">Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="faf3e-224">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="faf3e-225">Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, otevřete **terminál** a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="faf3e-225">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="faf3e-226">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="faf3e-226">Additional resources</span></span>

* [<span data-ttu-id="faf3e-227">Ladění v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="faf3e-227">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="faf3e-228">Další kroky</span><span class="sxs-lookup"><span data-stu-id="faf3e-228">Next steps</span></span>

<span data-ttu-id="faf3e-229">V tomto kurzu jste použili Visual Studio Code ladicí nástroje.</span><span class="sxs-lookup"><span data-stu-id="faf3e-229">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="faf3e-230">V dalším kurzu publikujete nasazovatelné verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="faf3e-230">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="faf3e-231">Publikování konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="faf3e-231">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
