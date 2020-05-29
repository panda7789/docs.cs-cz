---
title: Ladění konzolové aplikace .NET Core pomocí Visual Studio Code
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: eaeb97f54442006d2f0e29483a68dc3de89b5778
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202587"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="b0662-103">Kurz: ladění konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b0662-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="b0662-104">Tento kurz zavádí ladicí nástroje, které jsou k dispozici v Visual Studio Code pro práci s aplikacemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0662-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0662-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0662-105">Prerequisites</span></span>

- <span data-ttu-id="b0662-106">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b0662-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="b0662-107">Použít konfiguraci sestavení pro ladění</span><span class="sxs-lookup"><span data-stu-id="b0662-107">Use Debug build configuration</span></span>

<span data-ttu-id="b0662-108">*Ladění* a *vydání* jsou dvě konfigurace sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0662-108">*Debug* and *release* are two of .NET Core's build configurations.</span></span> <span data-ttu-id="b0662-109">Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="b0662-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="b0662-110">V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="b0662-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="b0662-111">Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.</span><span class="sxs-lookup"><span data-stu-id="b0662-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="b0662-112">Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.</span><span class="sxs-lookup"><span data-stu-id="b0662-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="b0662-113">Ve výchozím nastavení Visual Studio Code používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.</span><span class="sxs-lookup"><span data-stu-id="b0662-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="b0662-114">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="b0662-114">Set a breakpoint</span></span>

<span data-ttu-id="b0662-115">Zarážka dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="b0662-115">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="b0662-116">V *program.cs*nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="b0662-116">In *Program.cs*, set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="b0662-117">Levý okraj je nalevo od čísel řádků.</span><span class="sxs-lookup"><span data-stu-id="b0662-117">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="b0662-118">Dalším způsobem, jak nastavit zarážku, je umístit kurzor do řádku kódu a stisknout <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-118">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing <kbd>F9</kbd>.</span></span>

   <span data-ttu-id="b0662-119">Jak ukazuje následující obrázek, Visual Studio Code označuje řádek, na kterém je zarážka nastavena, zobrazením červené tečky na levém okraji.</span><span class="sxs-lookup"><span data-stu-id="b0662-119">As the following image shows, Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Sada zarážek":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="b0662-121">Nastavení pro terminálový vstup</span><span class="sxs-lookup"><span data-stu-id="b0662-121">Set up for terminal input</span></span>

<span data-ttu-id="b0662-122">Zarážka je umístěna po `Console.ReadLine` volání metody.</span><span class="sxs-lookup"><span data-stu-id="b0662-122">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="b0662-123">**Konzola ladění** nepřijímá vstup terminálu pro spuštěný program.</span><span class="sxs-lookup"><span data-stu-id="b0662-123">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="b0662-124">Pro zpracování vstupu terminálu během ladění můžete použít integrovaný terminál (jeden z Visual Studio Code Windows) nebo externí terminál.</span><span class="sxs-lookup"><span data-stu-id="b0662-124">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="b0662-125">V tomto kurzu použijete integrovaný terminál.</span><span class="sxs-lookup"><span data-stu-id="b0662-125">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="b0662-126">Otevřete *. VSCode/Launch. JSON*.</span><span class="sxs-lookup"><span data-stu-id="b0662-126">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="b0662-127">Změňte `console` nastavení na `integratedTerminal` .</span><span class="sxs-lookup"><span data-stu-id="b0662-127">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="b0662-128">Z:</span><span class="sxs-lookup"><span data-stu-id="b0662-128">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="b0662-129">Do:</span><span class="sxs-lookup"><span data-stu-id="b0662-129">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="b0662-130">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="b0662-130">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="b0662-131">Spustit ladění</span><span class="sxs-lookup"><span data-stu-id="b0662-131">Start debugging</span></span>

1. <span data-ttu-id="b0662-132">Otevřete zobrazení ladění výběrem ikony ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="b0662-132">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Otevřete kartu ladění v Visual Studio Code":::

1. <span data-ttu-id="b0662-134">Spustit ladění tak, že vyberete zelenou šipku v horní části podokna, vedle možnosti **spuštění .NET Core (konzola)**.</span><span class="sxs-lookup"><span data-stu-id="b0662-134">Start debugging by selecting the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span>  <span data-ttu-id="b0662-135">Dalším způsobem, jak spustit ladění, je stisknout klávesu <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-135">Another way to start debugging is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Spustit ladění":::

1. <span data-ttu-id="b0662-137">Vyberte kartu **terminál** , pokud chcete zobrazit "Co je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="b0662-137">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="b0662-138">před čekáním na odpověď se zobrazí výzva k zadání programu.</span><span class="sxs-lookup"><span data-stu-id="b0662-138">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Výběr karty terminálu":::

1. <span data-ttu-id="b0662-140">V okně **terminálu** zadejte řetězec jako odpověď na výzvu pro název a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-140">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="b0662-141">Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="b0662-141">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="b0662-142">Oddíl **místních** hodnot v okně **proměnné** zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="b0662-142">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Pozice zarážky, zobrazení lokálních hodnot":::

## <a name="change-variable-values"></a><span data-ttu-id="b0662-144">Změnit hodnoty proměnných</span><span class="sxs-lookup"><span data-stu-id="b0662-144">Change variable values</span></span>

<span data-ttu-id="b0662-145">Okno **konzoly ladění** vám umožní pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="b0662-145">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="b0662-146">Můžete změnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.</span><span class="sxs-lookup"><span data-stu-id="b0662-146">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="b0662-147">Vyberte kartu **Konzola ladění** .</span><span class="sxs-lookup"><span data-stu-id="b0662-147">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="b0662-148">Zadejte `name = "Gracie"` na příkazovém řádku v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="b0662-148">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Změnit hodnoty proměnných":::

1. <span data-ttu-id="b0662-150">Zadejte `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` v dolní části okna **konzoly ladění** a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="b0662-150">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="b0662-151">V okně **proměnné** se zobrazí nové hodnoty `name` `date` proměnných a.</span><span class="sxs-lookup"><span data-stu-id="b0662-151">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="b0662-152">Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** .</span><span class="sxs-lookup"><span data-stu-id="b0662-152">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="b0662-153">Dalším způsobem, jak pokračovat, je stisknout klávesu <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-153">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Pokračovat v ladění":::

1. <span data-ttu-id="b0662-155">Znovu vyberte kartu **terminálu** .</span><span class="sxs-lookup"><span data-stu-id="b0662-155">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="b0662-156">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **konzole ladění**.</span><span class="sxs-lookup"><span data-stu-id="b0662-156">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminál znázorňující zadané hodnoty":::

1. <span data-ttu-id="b0662-158">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="b0662-158">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="b0662-159">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="b0662-159">Set a conditional breakpoint</span></span>

<span data-ttu-id="b0662-160">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="b0662-160">The program displays the string that the user enters.</span></span> <span data-ttu-id="b0662-161">Co se stane, když uživatel nezadá něco?</span><span class="sxs-lookup"><span data-stu-id="b0662-161">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="b0662-162">Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.</span><span class="sxs-lookup"><span data-stu-id="b0662-162">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="b0662-163">Klikněte pravým tlačítkem myši (<kbd>CTRL</kbd>+ kliknutí na MacOS) na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="b0662-163">Right-click (<kbd>Ctrl</kbd>+click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="b0662-164">V místní nabídce vyberte **Upravit zarážku** , aby se otevřelo dialogové okno, které vám umožní zadat podmíněný výraz.</span><span class="sxs-lookup"><span data-stu-id="b0662-164">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Místní nabídka zarážky":::

1. <span data-ttu-id="b0662-166">`Expression`V rozevíracím seznamu vyberte, zadejte následující podmíněný výraz a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-166">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Zadejte podmíněný výraz.":::

   <span data-ttu-id="b0662-168">Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="b0662-168">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="b0662-169">Místo podmíněného výrazu lze určit *Počet volání*, který přerušuje spuštění programu před provedením určitého příkazu, nebo *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="b0662-169">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="b0662-170">Spusťte program s laděním stisknutím klávesy <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-170">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="b0662-171">Na kartě **terminál** po zobrazení výzvy k zadání názvu stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="b0662-171">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="b0662-172">Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ) je splněná, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="b0662-172">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="b0662-173">Okno **proměnné** ukazuje, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b0662-173">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="b0662-174">Zadáním následujícího příkazu na příkazovém řádku **konzoly ladění** a stisknutím klávesy <kbd>ENTER</kbd>potvrďte, že hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="b0662-174">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="b0662-175">Výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="b0662-175">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Ladit konzolu vracející hodnotu true po provedení příkazu":::

1. <span data-ttu-id="b0662-177">Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="b0662-177">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="b0662-178">Vyberte kartu **terminál** a stisknutím libovolné klávesy ukončete program a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="b0662-178">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="b0662-179">Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="b0662-179">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="b0662-180">Dalším způsobem, jak zrušit zarážku, je stisknutí klávesy <kbd>F9</kbd> při výběru řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="b0662-180">Another way to clear a breakpoint is by pressing <kbd>F9</kbd> while the line of code is selected.</span></span>

1. <span data-ttu-id="b0662-181">Pokud se zobrazí upozornění, že bude ztracena Podmínka zarážky, vyberte možnost **odebrat zarážku**.</span><span class="sxs-lookup"><span data-stu-id="b0662-181">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="b0662-182">Krokovat program</span><span class="sxs-lookup"><span data-stu-id="b0662-182">Step through a program</span></span>

<span data-ttu-id="b0662-183">Visual Studio Code také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="b0662-183">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="b0662-184">Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="b0662-184">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="b0662-185">Vzhledem k tomu, že je tento program malý, můžete projít celým programem.</span><span class="sxs-lookup"><span data-stu-id="b0662-185">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="b0662-186">Nastavte zarážku na levou složenou závorku `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="b0662-186">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="b0662-187">Stisknutím klávesy <kbd>F5</kbd> spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="b0662-187">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="b0662-188">Visual Studio Code zvýrazní řádek zarážky.</span><span class="sxs-lookup"><span data-stu-id="b0662-188">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="b0662-189">V tomto okamžiku okno **proměnné** ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b0662-189">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="b0662-190">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-190">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Tlačítko Krokovat s vnořením":::

   <span data-ttu-id="b0662-192">Visual Studio Code zvýrazní další řádek.</span><span class="sxs-lookup"><span data-stu-id="b0662-192">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="b0662-193">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-193">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="b0662-194">Visual Studio Code spustí `Console.WriteLine` pro příkazový řádek název a zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="b0662-194">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="b0662-195">Další řádek je `Console.ReadLine` pro `name` .</span><span class="sxs-lookup"><span data-stu-id="b0662-195">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="b0662-196">Okno **proměnné** se nezměnilo a karta **terminálu** zobrazuje "Co je vaše jméno?"</span><span class="sxs-lookup"><span data-stu-id="b0662-196">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="b0662-197">výzv.</span><span class="sxs-lookup"><span data-stu-id="b0662-197">prompt.</span></span>

1. <span data-ttu-id="b0662-198">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-198">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="b0662-199">Visual Studio zvýrazní `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0662-199">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="b0662-200">V okně **proměnné** se zobrazí, že `name` je stále `null` .</span><span class="sxs-lookup"><span data-stu-id="b0662-200">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="b0662-201">Na výzvu odpovězte zadáním řetězce na kartě terminálu a stisknutím klávesy <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-201">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="b0662-202">Karta **terminálu** nezobrazuje řetězec, který zadáte při zadávání, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda zachytí vstup.</span><span class="sxs-lookup"><span data-stu-id="b0662-202">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="b0662-203">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-203">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="b0662-204">Visual Studio Code zvýrazní `date` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0662-204">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="b0662-205">Okno **proměnné** zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b0662-205">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b0662-206">Na kartě **terminál** se zobrazí řetězec, který jste zadali na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b0662-206">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="b0662-207">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-207">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="b0662-208">Okno **proměnné** zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b0662-208">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="b0662-209">Vyberte **Krok do** nebo stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-209">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="b0662-210">Visual Studio Code volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="b0662-210">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b0662-211">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="b0662-211">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="b0662-212">Vyberte **Krok ven** nebo stiskněte klávesu <kbd>SHIFT</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0662-212">Select **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Tlačítko pro krokování":::

1. <span data-ttu-id="b0662-214">Vyberte kartu **terminál** .</span><span class="sxs-lookup"><span data-stu-id="b0662-214">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="b0662-215">Terminál zobrazí "při ukončení stiskněte libovolnou klávesu..."</span><span class="sxs-lookup"><span data-stu-id="b0662-215">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="b0662-216">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="b0662-216">Press any key to exit the program.</span></span>

## <a name="select-release-build-configuration"></a><span data-ttu-id="b0662-217">Vybrat konfiguraci sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="b0662-217">Select Release build configuration</span></span>

<span data-ttu-id="b0662-218">Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="b0662-218">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="b0662-219">Verze Release zahrnuje optimalizace kompilátoru, které mohou ovlivnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0662-219">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="b0662-220">Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="b0662-220">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="b0662-221">Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, otevřete **terminál** a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b0662-221">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="b0662-222">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b0662-222">Additional resources</span></span>

* [<span data-ttu-id="b0662-223">Ladění v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b0662-223">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="b0662-224">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b0662-224">Next steps</span></span>

<span data-ttu-id="b0662-225">V tomto kurzu jste použili Visual Studio Code ladicí nástroje.</span><span class="sxs-lookup"><span data-stu-id="b0662-225">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="b0662-226">Informace o tom, jak publikovat nasazovatelné verze aplikace, najdete v tématu [publikování aplikace](cli-create-console-app.md#publish-your-app).</span><span class="sxs-lookup"><span data-stu-id="b0662-226">To learn how to publish a deployable version of the app, see [Publish your app](cli-create-console-app.md#publish-your-app).</span></span>

<!--In the next tutorial, you publish a deployable version of the app.

> [!div class="nextstepaction"]
> [Publish a .NET Core console application with Visual Studio Code](publishing-with-visual-studio-code.md)
-->
