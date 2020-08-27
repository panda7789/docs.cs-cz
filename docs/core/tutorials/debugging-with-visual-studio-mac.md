---
title: Ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí sady Visual Studio Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 011647a6e3e676909880befa3b770205eb9616d6
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957522"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="0d331-103">Kurz: ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="0d331-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="0d331-104">V tomto kurzu se seznámíte s ladicími nástroji dostupnými v Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="0d331-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d331-105">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="0d331-105">Prerequisites</span></span>

- <span data-ttu-id="0d331-106">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="0d331-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="0d331-107">Použít konfiguraci sestavení pro ladění</span><span class="sxs-lookup"><span data-stu-id="0d331-107">Use Debug build configuration</span></span>

<span data-ttu-id="0d331-108">*Ladění* a *vydání* jsou integrované konfigurace sestavení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d331-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="0d331-109">Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="0d331-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="0d331-110">V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="0d331-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="0d331-111">Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.</span><span class="sxs-lookup"><span data-stu-id="0d331-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="0d331-112">Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.</span><span class="sxs-lookup"><span data-stu-id="0d331-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="0d331-113">Ve výchozím nastavení Visual Studio pro Mac používá konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.</span><span class="sxs-lookup"><span data-stu-id="0d331-113">By default, Visual Studio for Mac uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="0d331-114">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="0d331-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="0d331-115">Otevřete projekt, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="0d331-115">Open the project that you created in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="0d331-116">Aktuální konfigurace sestavení se zobrazí na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0d331-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="0d331-117">Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="0d331-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Panel nástrojů sady Visual Studio se zvýrazněným laděním":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="0d331-119">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="0d331-119">Set a breakpoint</span></span>

<span data-ttu-id="0d331-120">*Zarážka* dočasně přerušuje provádění aplikace před provedením řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="0d331-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="0d331-121">Nastavte zarážku na řádku, který zobrazuje název, datum a čas.</span><span class="sxs-lookup"><span data-stu-id="0d331-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="0d331-122">Chcete-li to provést, umístěte kurzor na řádek kódu a stiskněte <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>příkaz</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="0d331-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="0d331-123">Další způsob, jak nastavit zarážku, je vybrat možnost **Spustit**  >  **přepínací zarážku** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="0d331-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="0d331-124">Sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červené tečky na levém okraji.</span><span class="sxs-lookup"><span data-stu-id="0d331-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Okno programu Visual Studio se sadou zarážek":::

1. <span data-ttu-id="0d331-126">Stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>) spusťte program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="0d331-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="0d331-127">Další způsob, jak spustit ladění, je kliknutím na příkaz **Spustit**  >  **ladění** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="0d331-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="0d331-128">V okně terminálu zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0d331-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="0d331-129">Spuštění programu se zastaví, když dosáhne zarážky, než se `Console.WriteLine` spustí metoda.</span><span class="sxs-lookup"><span data-stu-id="0d331-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Snímek obrazovky se zarážkou v aplikaci Visual Studio":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="0d331-131">Použít příkazové okno</span><span class="sxs-lookup"><span data-stu-id="0d331-131">Use the Immediate window</span></span>

<span data-ttu-id="0d331-132">**Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="0d331-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="0d331-133">Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.</span><span class="sxs-lookup"><span data-stu-id="0d331-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="0d331-134">Pokud není okno **okamžité** , zobrazte ho tak, že kliknete na **Zobrazit**  >  **ladicí panely**  >  **okamžitě**.</span><span class="sxs-lookup"><span data-stu-id="0d331-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="0d331-135">`name = "Gracie"`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0d331-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="0d331-136">`date = date.AddDays(1)`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0d331-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="0d331-137">V **příkazovém** okně se zobrazí nová hodnota řetězcové proměnné a vlastnosti <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0d331-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Okamžité okno v aplikaci Visual Studio":::

   <span data-ttu-id="0d331-139">V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="0d331-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="0d331-140">Hodnoty proměnných, které jste právě změnili, jsou aktualizovány v okně **místních** hodnot.</span><span class="sxs-lookup"><span data-stu-id="0d331-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Okno místních hodnot v aplikaci Visual Studio":::

1. <span data-ttu-id="0d331-142">Pokud chcete pokračovat v ladění, stiskněte <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="0d331-143">Hodnoty zobrazené v terminálu odpovídají změnám, které jste provedli v **příkazovém** okně.</span><span class="sxs-lookup"><span data-stu-id="0d331-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="0d331-144">Pokud terminál nevidíte, vyberte v dolním navigačním panelu položku **Terminal-HelloWorld** .</span><span class="sxs-lookup"><span data-stu-id="0d331-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Hello World terminálu v dolním navigačním panelu":::

1. <span data-ttu-id="0d331-146">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="0d331-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="0d331-147">Zavřete okno terminálu.</span><span class="sxs-lookup"><span data-stu-id="0d331-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="0d331-148">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="0d331-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="0d331-149">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="0d331-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="0d331-150">Co se stane, když uživatel nezadá něco?</span><span class="sxs-lookup"><span data-stu-id="0d331-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="0d331-151">Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.</span><span class="sxs-lookup"><span data-stu-id="0d331-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="0d331-152"><kbd>stiskněte klávesu CTRL</kbd>a klikněte na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="0d331-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="0d331-153">V místní nabídce vyberte **Upravit zarážku**.</span><span class="sxs-lookup"><span data-stu-id="0d331-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="0d331-154">V dialogovém okně **Upravit zarážku** zadejte do následujícího pole následující kód **a následující podmínka je pravdivá**a vyberte **použít**.</span><span class="sxs-lookup"><span data-stu-id="0d331-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Editor znázorňující panel nastavení zarážky":::

   <span data-ttu-id="0d331-156">Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="0d331-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="0d331-157">Místo podmíněného výrazu můžete zadat *počet*průchodů, který přerušuje spuštění programu před provedením příkazu určeného počtu.</span><span class="sxs-lookup"><span data-stu-id="0d331-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="0d331-158">Spusťte ladění stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="0d331-159">V okně terminálu po zobrazení výzvy k zadání jména stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="0d331-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="0d331-160">Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ), byla splněna, spuštění programu se zastaví při dosažení zarážky.</span><span class="sxs-lookup"><span data-stu-id="0d331-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="0d331-161">Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu.</span><span class="sxs-lookup"><span data-stu-id="0d331-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="0d331-162">V tomto případě `Main` je právě spuštěná metoda.</span><span class="sxs-lookup"><span data-stu-id="0d331-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="0d331-163">Všimněte si, že hodnota `name` proměnné je `""` , to znamená <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0d331-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="0d331-164">Můžete také zjistit, že hodnota je prázdný řetězec zadáním `name` názvu proměnné v **příkazovém podokně** a stisknutím klávesy <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0d331-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="Příkazové okno se zobrazeným názvem je prázdným řetězcem.":::

1. <span data-ttu-id="0d331-166">Pokud chcete pokračovat v ladění, stiskněte <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="0d331-167">V okně terminálu ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="0d331-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="0d331-168">Zavřete okno terminálu.</span><span class="sxs-lookup"><span data-stu-id="0d331-168">Close the terminal window.</span></span>

1. <span data-ttu-id="0d331-169">Vymažte zarážku kliknutím na červenou tečku na levém okraji okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="0d331-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="0d331-170">Dalším způsobem, jak zrušit zarážku, je výběrem možnosti **spustit > Přepnout zarážku** , když je vybraný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="0d331-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="0d331-171">Krokovat program</span><span class="sxs-lookup"><span data-stu-id="0d331-171">Step through a program</span></span>

<span data-ttu-id="0d331-172">Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="0d331-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="0d331-173">Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="0d331-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="0d331-174">Vzhledem k tomu, že je tento program malý, můžete projít celým programem.</span><span class="sxs-lookup"><span data-stu-id="0d331-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="0d331-175">Nastavte zarážku na složenou závorku, která označuje začátek `Main` metody (stiskněte <kbd>příkaz</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="0d331-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="0d331-176">Spusťte ladění stisknutím <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Command</kbd> + <kbd>ENTER</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="0d331-177">Visual Studio se zastaví na řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="0d331-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="0d331-178">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>) nebo vyberte **Spustit**  >  **Krok do** pro posunutí jednoho řádku.</span><span class="sxs-lookup"><span data-stu-id="0d331-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="0d331-179">Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.</span><span class="sxs-lookup"><span data-stu-id="0d331-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Metoda kroku v aplikaci Visual Studio":::

   <span data-ttu-id="0d331-181">V tomto okamžiku okno **místních** hodnot ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0d331-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="0d331-182">Kromě toho Visual Studio otevřelo prázdného terminálu.</span><span class="sxs-lookup"><span data-stu-id="0d331-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="0d331-183">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="0d331-184">Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="0d331-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="0d331-185">V okně **místní** hodnoty se zobrazí `name` to `null` a terminál zobrazí řetězec "Co je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="0d331-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="0d331-186">Zadáním řetězce v okně konzoly a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="0d331-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="0d331-187">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="0d331-188">Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="0d331-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="0d331-189">Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0d331-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d331-190">Terminál zobrazí řetězec, který jste zadali na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0d331-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="0d331-191">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="0d331-192">Okno **místní** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d331-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0d331-193">Terminál je beze změny.</span><span class="sxs-lookup"><span data-stu-id="0d331-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="0d331-194">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="0d331-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="0d331-195">Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="0d331-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d331-196">Terminál zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0d331-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="0d331-197">Stiskněte <kbd>⇧</kbd><kbd>⌘</kbd><kbd>u</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>u</kbd>) nebo vyberte **Spustit**  >  **Krok ven**.</span><span class="sxs-lookup"><span data-stu-id="0d331-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="0d331-198">Terminál zobrazí zprávu a počká, až stisknete klávesu.</span><span class="sxs-lookup"><span data-stu-id="0d331-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="0d331-199">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="0d331-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="0d331-200">Použít konfiguraci sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="0d331-200">Use Release build configuration</span></span>

<span data-ttu-id="0d331-201">Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="0d331-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="0d331-202">Verze Release zahrnuje optimalizace kompilátoru, které mohou negativně ovlivnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d331-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="0d331-203">Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="0d331-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="0d331-204">Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="0d331-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="0d331-205">Změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="0d331-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním":::

1. <span data-ttu-id="0d331-207">Stiskněte <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>) a spusťte bez ladění.</span><span class="sxs-lookup"><span data-stu-id="0d331-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0d331-208">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0d331-208">Next steps</span></span>

<span data-ttu-id="0d331-209">V tomto kurzu jste použili ladicí nástroje sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d331-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="0d331-210">V dalším kurzu publikujete nasazovatelné verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d331-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d331-211">Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="0d331-211">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
