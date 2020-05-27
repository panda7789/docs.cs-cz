---
title: Ladění konzolové aplikace .NET Core pomocí sady Visual Studio
description: Naučte se ladit konzolovou aplikaci .NET Core pomocí sady Visual Studio.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005411"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="17a92-103">Kurz: ladění konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17a92-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="17a92-104">V tomto kurzu se seznámíte s ladicími nástroji dostupnými v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17a92-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17a92-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17a92-105">Prerequisites</span></span>

- <span data-ttu-id="17a92-106">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v sadě Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="17a92-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="17a92-107">Ladit konfiguraci sestavení</span><span class="sxs-lookup"><span data-stu-id="17a92-107">Debug build configuration</span></span>

<span data-ttu-id="17a92-108">*Ladění* a *vydání* jsou dvě z výchozích konfigurací sestavení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17a92-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="17a92-109">Aktuální konfigurace sestavení se zobrazí na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="17a92-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="17a92-110">Následující obrázek na panelu nástrojů ukazuje, že je aplikace Visual Studio nakonfigurována pro zkompilování ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="17a92-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="17a92-112">Začněte spuštěním ladicí verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="17a92-112">Begin by running the Debug version of the app.</span></span> <span data-ttu-id="17a92-113">Konfigurace sestavení ladění vypíná většinu optimalizací kompilátoru a poskytuje bohatší informace během procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="17a92-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="17a92-114">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="17a92-114">Set a breakpoint</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="17a92-115">Nastavte *zarážku* na řádku, který zobrazuje název, datum a čas kliknutím na levý okraj okna Code (kód) na řádku.</span><span class="sxs-lookup"><span data-stu-id="17a92-115">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="17a92-116">Další způsob, jak nastavit zarážku, je umístěním kurzoru do řádku kódu a následným stisknutím klávesy **F9** nebo zvolením možnosti **ladit**  >  **Přepnout zarážku** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="17a92-116">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="17a92-117">Zarážka dočasně přerušuje provádění aplikace *před* provedením řádku se zarážkou.</span><span class="sxs-lookup"><span data-stu-id="17a92-117">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="17a92-118">Jak ukazuje následující obrázek, sada Visual Studio označuje řádek, na kterém je zarážka nastavena, zvýrazněním a zobrazením červené tečky na levém okraji.</span><span class="sxs-lookup"><span data-stu-id="17a92-118">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Okno programu Visual Studio se sadou zarážek](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="17a92-120">Spusťte program v režimu ladění tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="17a92-120">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span> <span data-ttu-id="17a92-121">Dalším způsobem, jak spustit ladění, je stisknout klávesu **F5** nebo kliknutím na **ladění**  >  **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="17a92-121">Other ways to start debugging are by pressing **F5** or by choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="17a92-122">V okně konzoly zadejte řetězec, když se program vyzve k zadání názvu a potom stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="17a92-122">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="17a92-123">Spuštění programu se zastaví, když dosáhne zarážky a před tím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="17a92-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="17a92-124">V okně **místní** hodnoty se zobrazí hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="17a92-124">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Snímek obrazovky se zarážkou v aplikaci Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="17a92-126">**Okamžité** okno vám umožní pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="17a92-126">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="17a92-127">Můžete interaktivně měnit hodnotu proměnných, abyste viděli, jak ovlivní váš program.</span><span class="sxs-lookup"><span data-stu-id="17a92-127">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="17a92-128">Pokud okno **okamžité** není viditelné, zobrazte ho tak, že kliknete na možnost **ladění**  >  **oken**  >  **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="17a92-128">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="17a92-129">`name = "Gracie"`Do příkazového **podokna** zadejte a stiskněte klávesu **ENTER** .</span><span class="sxs-lookup"><span data-stu-id="17a92-129">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="17a92-130">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`Do příkazového **podokna** zadejte a stiskněte klávesu **ENTER** .</span><span class="sxs-lookup"><span data-stu-id="17a92-130">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="17a92-131">V **příkazovém** okně se zobrazí hodnota proměnné řetězce a vlastnosti <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="17a92-131">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="17a92-132">Kromě toho jsou hodnoty proměnných aktualizovány v okně **místních** hodnot.</span><span class="sxs-lookup"><span data-stu-id="17a92-132">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Místní a bezprostřední okna v aplikaci Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="17a92-134">Pokračujte v provádění programu tak, že na panelu nástrojů vyberete tlačítko **pokračovat** .</span><span class="sxs-lookup"><span data-stu-id="17a92-134">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="17a92-135">Dalším způsobem, jak pokračovat, je zvolit pokračovat v **ladění**  >  **Continue**.</span><span class="sxs-lookup"><span data-stu-id="17a92-135">Another way to continue is by choosing **Debug** > **Continue**.</span></span>

   <span data-ttu-id="17a92-136">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v **příkazovém** okně.</span><span class="sxs-lookup"><span data-stu-id="17a92-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="17a92-138">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="17a92-138">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="17a92-139">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="17a92-139">Set a conditional breakpoint</span></span>

<span data-ttu-id="17a92-140">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="17a92-140">The program displays the string that the user enters.</span></span> <span data-ttu-id="17a92-141">Co se stane, když uživatel nezadá něco?</span><span class="sxs-lookup"><span data-stu-id="17a92-141">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="17a92-142">Můžete ji otestovat s užitečnou funkcí ladění nazývanou *podmíněná zarážka*, která přerušuje provádění programu, pokud je splněna jedna nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="17a92-142">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="17a92-143">Chcete-li nastavit podmíněný bod přerušení a otestovat, co se stane, když uživatel nezadá řetězec, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="17a92-143">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

1. <span data-ttu-id="17a92-144">Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="17a92-144">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="17a92-145">V místní nabídce vyberte **podmínky** a otevřete tak dialogové okno **Nastavení zarážky** .</span><span class="sxs-lookup"><span data-stu-id="17a92-145">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="17a92-146">Zaškrtněte políčko pro **podmínky** , pokud již není vybráno.</span><span class="sxs-lookup"><span data-stu-id="17a92-146">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Editor znázorňující panel nastavení zarážky – C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="17a92-148">Pro **podmíněný výraz**zadejte následující kód do pole, které obsahuje ukázkový kód, který testuje, pokud `x` je 5.</span><span class="sxs-lookup"><span data-stu-id="17a92-148">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="17a92-149">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="17a92-149">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="17a92-150">Pokaždé, když je dosaženo zarážky, ladicí program volá `String.IsNullOrEmpty(name)` metodu a přeruší se na tomto řádku pouze v případě, že se volání metody vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="17a92-150">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="17a92-151">Místo podmíněného výrazu lze určit *Počet volání*, který přerušuje spuštění programu před provedením určitého příkazu, nebo *podmínku filtru*, která přerušuje spuštění programu na základě takových atributů jako identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="17a92-151">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="17a92-152">Kliknutím na **Zavřít** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="17a92-152">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="17a92-153">Spusťte program s laděním stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="17a92-153">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="17a92-154">Po zobrazení výzvy k zadání názvu v okně konzoly stiskněte klávesu **ENTER** .</span><span class="sxs-lookup"><span data-stu-id="17a92-154">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="17a92-155">Vzhledem k tomu, že podmínka, kterou jste zadali ( `name` je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> ), byla splněna, spuštění programu se zastaví, když dosáhne zarážky a předtím, než se `Console.WriteLine` Metoda spustí.</span><span class="sxs-lookup"><span data-stu-id="17a92-155">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="17a92-156">Vyberte okno **místních** hodnot, které zobrazuje hodnoty proměnných, které jsou místní pro právě spuštěnou metodu.</span><span class="sxs-lookup"><span data-stu-id="17a92-156">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="17a92-157">V tomto případě `Main` je právě spuštěná metoda.</span><span class="sxs-lookup"><span data-stu-id="17a92-157">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="17a92-158">Všimněte si, že hodnota `name` proměnné je `""` nebo <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="17a92-158">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="17a92-159">Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu v **příkazovém** okně a stisknutím klávesy **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="17a92-159">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="17a92-160">Výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="17a92-160">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="17a92-161">Otazník nasměruje okamžité okno k [vyhodnocení výrazu](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="17a92-161">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Okamžité okno vracející hodnotu true po provedení příkazu – C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="17a92-163">Kliknutím na tlačítko **pokračovat** na panelu nástrojů pokračujte v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="17a92-163">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="17a92-164">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="17a92-164">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="17a92-165">Vymažte zarážku kliknutím na tečku na levém okraji okna Code (kód).</span><span class="sxs-lookup"><span data-stu-id="17a92-165">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="17a92-166">Dalším způsobem, jak zrušit zarážku, je vybrat možnost **ladění > přepínat zarážku** , zatímco je vybraný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="17a92-166">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="17a92-167">Krokovat program</span><span class="sxs-lookup"><span data-stu-id="17a92-167">Step through a program</span></span>

<span data-ttu-id="17a92-168">Visual Studio také umožňuje krokovat řádek po řádku programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="17a92-168">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="17a92-169">Obvykle byste měli nastavit zarážku a sledovat tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="17a92-169">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="17a92-170">Vzhledem k tomu, že je váš program malý, můžete projít celým programem.</span><span class="sxs-lookup"><span data-stu-id="17a92-170">Since your program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="17a92-171">Vyberte možnost **ladit**  >  **Krok do**.</span><span class="sxs-lookup"><span data-stu-id="17a92-171">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="17a92-172">Dalším způsobem, jak najednou ladit jeden příkaz, je stisknutí klávesy **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-172">Another way to debug one statement at a time is by pressing **F11**.</span></span>

   <span data-ttu-id="17a92-173">Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.</span><span class="sxs-lookup"><span data-stu-id="17a92-173">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="17a92-174">C#</span><span class="sxs-lookup"><span data-stu-id="17a92-174">C#</span></span>

   ![Krok v aplikaci Visual Studio do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="17a92-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17a92-176">Visual Basic</span></span>

   ![Metoda Visual Studio Step Into – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="17a92-178">V tomto okamžiku okno **místních** hodnot ukazuje, že `args` pole je prázdné a `name` `date` má výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="17a92-178">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="17a92-179">Kromě toho Visual Studio otevřelo prázdné okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="17a92-179">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="17a92-180">Stiskněte klávesu **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-180">Press **F11**.</span></span> <span data-ttu-id="17a92-181">Visual Studio teď zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="17a92-181">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="17a92-182">Okno **místní** hodnoty se nezměnilo a okno konzoly zůstane prázdné.</span><span class="sxs-lookup"><span data-stu-id="17a92-182">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="17a92-183">C#</span><span class="sxs-lookup"><span data-stu-id="17a92-183">C#</span></span>

   ![Krok sady Visual Studio ve zdroji metody – C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="17a92-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17a92-185">Visual Basic</span></span>

   ![Krok do zdroje metody v aplikaci Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="17a92-187">Stiskněte klávesu **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-187">Press **F11**.</span></span> <span data-ttu-id="17a92-188">Visual Studio zvýrazní příkaz, který obsahuje `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="17a92-188">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="17a92-189">Okno **místní** hodnoty ukazuje, `name` `null` a okno konzoly zobrazuje řetězec "Co je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="17a92-189">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="17a92-190">Zadáním řetězce v okně konzoly a stisknutím klávesy **ENTER**odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="17a92-190">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="17a92-191">Konzola nereaguje a řetězec, který jste zadali, se nezobrazuje v okně konzoly, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda bude nicméně zachytávání vstupu.</span><span class="sxs-lookup"><span data-stu-id="17a92-191">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="17a92-192">Stiskněte klávesu **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-192">Press **F11**.</span></span> <span data-ttu-id="17a92-193">Visual Studio zvýrazní příkaz, který obsahuje `date` přiřazení proměnné ( `currentDate` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="17a92-193">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="17a92-194">Okno **místní** hodnoty zobrazuje hodnotu vrácenou voláním <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="17a92-194">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17a92-195">V okně konzoly se zobrazí také řetězec, který jste zadali na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="17a92-195">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="17a92-196">Stiskněte klávesu **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-196">Press **F11**.</span></span> <span data-ttu-id="17a92-197">Okno **místní** hodnoty zobrazuje hodnotu `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17a92-197">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="17a92-198">Okno konzoly se nezměnilo.</span><span class="sxs-lookup"><span data-stu-id="17a92-198">The console window is unchanged.</span></span>

1. <span data-ttu-id="17a92-199">Stiskněte klávesu **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-199">Press **F11**.</span></span> <span data-ttu-id="17a92-200">Visual Studio volá <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="17a92-200">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17a92-201">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="17a92-201">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="17a92-202">Vyberte **ladit**  >  **Krok ven**. Dalším způsobem, jak zastavit krok za krokem, je stisknutí klávesy **SHIFT** + **F11**.</span><span class="sxs-lookup"><span data-stu-id="17a92-202">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing **Shift**+**F11**.</span></span>

   <span data-ttu-id="17a92-203">V okně konzoly se zobrazí zpráva a čeká na stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="17a92-203">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="17a92-204">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="17a92-204">Press any key to close the console window and stop debugging.</span></span>

## <a name="build-a-release-version"></a><span data-ttu-id="17a92-205">Sestavení verze pro vydání</span><span class="sxs-lookup"><span data-stu-id="17a92-205">Build a Release version</span></span>

<span data-ttu-id="17a92-206">Po otestování ladicí verze aplikace byste měli také kompilovat a testovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="17a92-206">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="17a92-207">Verze Release zahrnuje optimalizace kompilátoru, které mohou být někdy negativně ovlivněny chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="17a92-207">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="17a92-208">Například optimalizace kompilátoru, které jsou navrženy pro zlepšení výkonu, mohou vytvářet konflikty časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="17a92-208">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="17a92-209">Chcete-li vytvořit a otestovat verzi pro vydání konzolové aplikace, změňte konfiguraci sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="17a92-209">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="17a92-211">Když stisknete klávesu **F5** nebo zvolíte **Sestavit řešení** z nabídky **sestavit** , Visual Studio zkompiluje verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="17a92-211">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="17a92-212">Můžete ho otestovat stejně, jako jste použili ladicí verzi.</span><span class="sxs-lookup"><span data-stu-id="17a92-212">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="17a92-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="17a92-213">Next steps</span></span>

<span data-ttu-id="17a92-214">V tomto kurzu jste použili ladicí nástroje sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17a92-214">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="17a92-215">V dalším kurzu publikujete nasazovatelné verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="17a92-215">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17a92-216">Publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17a92-216">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
