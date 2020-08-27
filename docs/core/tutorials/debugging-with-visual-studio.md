---
title: Ladění aplikace konzoly .NET Core pomocí sady Visual Studio
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí sady Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4e408d5bd0976d88f368615860ac373142d0fe1e
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957222"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="83a50-103">Kurz: ladění konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a50-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="83a50-104">V tomto kurzu se seznámíte s ladicími nástroji dostupnými v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83a50-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="83a50-105">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="83a50-105">Prerequisites</span></span>

- <span data-ttu-id="83a50-106">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="83a50-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="83a50-107">Použít konfiguraci sestavení pro ladění</span><span class="sxs-lookup"><span data-stu-id="83a50-107">Use Debug build configuration</span></span>

<span data-ttu-id="83a50-108">*Ladění* a *vydání* jsou integrované konfigurace sestavení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83a50-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="83a50-109">Použijete konfiguraci sestavení ladění pro ladění a konfiguraci vydání pro finální distribuci vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="83a50-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="83a50-110">V konfiguraci ladění program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="83a50-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="83a50-111">Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.</span><span class="sxs-lookup"><span data-stu-id="83a50-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="83a50-112">Konfigurace pro vydání programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována.</span><span class="sxs-lookup"><span data-stu-id="83a50-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="83a50-113">Ve výchozím nastavení používá Visual Studio konfiguraci sestavení ladění, takže je nemusíte před laděním měnit.</span><span class="sxs-lookup"><span data-stu-id="83a50-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="83a50-114">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83a50-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="83a50-115">Otevřete projekt, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="83a50-115">Open the project that you created in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

   <span data-ttu-id="83a50-116">Aktuální konfigurace sestavení se zobrazí na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="83a50-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="83a50-117">Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="83a50-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   ![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a><span data-ttu-id="83a50-119">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="83a50-119">Set a breakpoint</span></span>

<span data-ttu-id="83a50-120">*Zarážka* dočasně přerušuje provádění aplikace před provedením řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="83a50-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="83a50-121">Nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód) na řádku.</span><span class="sxs-lookup"><span data-stu-id="83a50-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="83a50-122">Levý okraj je nalevo od čísel řádků.</span><span class="sxs-lookup"><span data-stu-id="83a50-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="83a50-123">Další způsoby, jak nastavit zarážku, je umístěním kurzoru do řádku kódu a následným stisknutím klávesy <kbd>F9</kbd> nebo zvolením možnosti **ladit**  >  **Přepnout zarážku** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="83a50-123">Other ways to set a breakpoint are by placing the cursor in the line of code and then pressing <kbd>F9</kbd> or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="83a50-124">Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červené tečky na levém okraji.</span><span class="sxs-lookup"><span data-stu-id="83a50-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="83a50-126">Stisknutím klávesy <kbd>F5</kbd> spusťte program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="83a50-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="83a50-127">Dalším způsobem, jak spustit ladění, je kliknutím na **ladění**  >  **Spustit ladění** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="83a50-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="83a50-128">V okně konzoly zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="83a50-129">Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="83a50-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="83a50-130">V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="83a50-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Snímek obrazovky se zarážkou v aplikaci Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a><span data-ttu-id="83a50-132">Použít příkazové okno</span><span class="sxs-lookup"><span data-stu-id="83a50-132">Use the Immediate window</span></span>

<span data-ttu-id="83a50-133">**Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="83a50-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="83a50-134">Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.</span><span class="sxs-lookup"><span data-stu-id="83a50-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="83a50-135">Pokud okno **okamžité** není viditelné, zobrazte ho tak, že kliknete na možnost **ladění**  >  **oken**  >  **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="83a50-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="83a50-136">`name = "Gracie"`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="83a50-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="83a50-137">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`Do příkazového **podokna** zadejte a stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="83a50-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="83a50-138">V **příkazovém** okně se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="83a50-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="83a50-139">Kromě toho jsou hodnoty proměnných aktualizovány v okně **místních** hodnot.</span><span class="sxs-lookup"><span data-stu-id="83a50-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Místní a bezprostřední okna v aplikaci Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="83a50-141">Stisknutím klávesy <kbd>F5</kbd> pokračujte v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="83a50-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="83a50-142">Dalším způsobem, jak pokračovat, je vybrat v nabídce možnost **ladění**  >  **pokračovat** .</span><span class="sxs-lookup"><span data-stu-id="83a50-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="83a50-143">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém** okně.</span><span class="sxs-lookup"><span data-stu-id="83a50-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="83a50-145">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="83a50-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="83a50-146">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="83a50-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="83a50-147">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="83a50-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="83a50-148">Co se stane, když uživatel nezadá něco?</span><span class="sxs-lookup"><span data-stu-id="83a50-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="83a50-149">Můžete to otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*.</span><span class="sxs-lookup"><span data-stu-id="83a50-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="83a50-150">Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="83a50-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="83a50-151">V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** .</span><span class="sxs-lookup"><span data-stu-id="83a50-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="83a50-152">Zaškrtněte políčko pro **podmínky** , pokud již není vybráno.</span><span class="sxs-lookup"><span data-stu-id="83a50-152">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Editor znázorňující panel nastavení zarážky – C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="83a50-154">Pro **podmíněný výraz**zadejte následující kód do pole, které obsahuje ukázkový kód, který testuje, pokud `x` je 5.</span><span class="sxs-lookup"><span data-stu-id="83a50-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="83a50-155">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="83a50-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="83a50-156">Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="83a50-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="83a50-157">Místo podmíněného výrazu můžete zadat *počet*průchodů, který přerušuje spuštění programu před provedením příkazu určeného počtu.</span><span class="sxs-lookup"><span data-stu-id="83a50-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="83a50-158">Další možností je určit *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="83a50-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="83a50-159">Kliknutím na **Zavřít** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="83a50-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="83a50-160">Spusťte program s laděním stisknutím klávesy <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="83a50-161">Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="83a50-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="83a50-162">Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ), byla splněna, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="83a50-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="83a50-163">Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu.</span><span class="sxs-lookup"><span data-stu-id="83a50-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="83a50-164">V tomto případě `Main` je právě spuštěná metoda.</span><span class="sxs-lookup"><span data-stu-id="83a50-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="83a50-165">Všimněte si, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="83a50-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="83a50-166">Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém** okně a stisknutím klávesy <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="83a50-167">Výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="83a50-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="83a50-168">Otazník nasměruje okamžité okno k [vyhodnocení výrazu](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="83a50-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Okamžité okno vracející hodnotu true po provedení příkazu – C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="83a50-170">Stisknutím klávesy <kbd>F5</kbd> pokračujte v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="83a50-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="83a50-171">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="83a50-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="83a50-172">Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="83a50-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="83a50-173">Další způsoby, jak zarážku vymazat, jsou stisknutí klávesy <kbd>F9</kbd> nebo výběrem možnosti **ladění > přepínací zarážku** , když je vybraný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="83a50-173">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="83a50-174">Krokovat program</span><span class="sxs-lookup"><span data-stu-id="83a50-174">Step through a program</span></span>

<span data-ttu-id="83a50-175">Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="83a50-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="83a50-176">Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="83a50-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="83a50-177">Vzhledem k tomu, že je tento program malý, můžete projít celým programem.</span><span class="sxs-lookup"><span data-stu-id="83a50-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="83a50-178">Vyberte možnost **ladit**  >  **Krok do**.</span><span class="sxs-lookup"><span data-stu-id="83a50-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="83a50-179">Dalším způsobem, jak najednou ladit jeden příkaz, je stisknutí klávesy <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="83a50-180">Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.</span><span class="sxs-lookup"><span data-stu-id="83a50-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="83a50-181">C#</span><span class="sxs-lookup"><span data-stu-id="83a50-181">C#</span></span>

   ![Krok v aplikaci Visual Studio do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="83a50-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83a50-183">Visual Basic</span></span>

   ![Metoda Visual Studio Step Into – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="83a50-185">V tomto okamžiku okno **místních** hodnot ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="83a50-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="83a50-186">Kromě toho Visual Studio otevřelo prázdné okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="83a50-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="83a50-187">Stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="83a50-188">Visual Studio teď zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="83a50-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="83a50-189">Okno **místní** hodnoty se nezměnilo a okno konzoly zůstane prázdné.</span><span class="sxs-lookup"><span data-stu-id="83a50-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="83a50-190">C#</span><span class="sxs-lookup"><span data-stu-id="83a50-190">C#</span></span>

   ![Krok sady Visual Studio ve zdroji metody – C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="83a50-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83a50-192">Visual Basic</span></span>

   ![Krok do zdroje metody v aplikaci Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="83a50-194">Stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="83a50-195">Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="83a50-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="83a50-196">Okno **místní** hodnoty ukazuje, `name` `null` a okno konzoly zobrazuje řetězec "Co je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="83a50-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="83a50-197">Zadáním řetězce v okně konzoly a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="83a50-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="83a50-198">Konzola nereaguje a řetězec, který jste zadali, se nezobrazuje v okně konzoly, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda bude nicméně zachytávání vstupu.</span><span class="sxs-lookup"><span data-stu-id="83a50-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="83a50-199">Stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="83a50-200">Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné ( `currentDate` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="83a50-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="83a50-201">Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="83a50-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="83a50-202">V okně konzoly se zobrazí také řetězec, který jste zadali na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="83a50-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="83a50-203">Stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="83a50-204">Okno **místní** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83a50-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="83a50-205">Okno konzoly se nezměnilo.</span><span class="sxs-lookup"><span data-stu-id="83a50-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="83a50-206">Stiskněte klávesu <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="83a50-207">Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="83a50-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="83a50-208">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="83a50-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="83a50-209">Vyberte **ladit**  >  **Krok ven**. Dalším způsobem, jak zastavit krok za krokem, je stisknutí klávesy <kbd>SHIFT</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="83a50-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="83a50-210">V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="83a50-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="83a50-211">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="83a50-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="83a50-212">Použít konfiguraci sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="83a50-212">Use Release build configuration</span></span>

<span data-ttu-id="83a50-213">Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="83a50-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="83a50-214">Verze Release zahrnuje optimalizace kompilátoru, které mohou být někdy negativně ovlivněny chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="83a50-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="83a50-215">Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="83a50-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="83a50-216">Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="83a50-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="83a50-218">Když stisknete klávesu <kbd>F5</kbd> nebo zvolíte **Sestavit řešení** z nabídky **sestavit** , Visual Studio zkompiluje verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="83a50-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="83a50-219">Můžete ho otestovat stejně, jako jste použili ladicí verzi.</span><span class="sxs-lookup"><span data-stu-id="83a50-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83a50-220">Další kroky</span><span class="sxs-lookup"><span data-stu-id="83a50-220">Next steps</span></span>

<span data-ttu-id="83a50-221">V tomto kurzu jste použili ladicí nástroje sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83a50-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="83a50-222">V dalším kurzu publikujete nasazovatelné verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="83a50-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83a50-223">Publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83a50-223">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
