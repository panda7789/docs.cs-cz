---
title: Ladění aplikace Hello World .NET Core pomocí sady Visual Studio
description: Přečtěte si, jak ladit aplikaci Hello World napsanou v jazyce C# nebo Visual Basic pomocí sady Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156670"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a><span data-ttu-id="77737-103">Ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77737-103">Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio</span></span>

<span data-ttu-id="77737-104">Zatím jste postupovali podle kroků v [části Vytvoření první aplikace konzoly .NET Core v sadě Visual Studio 2019](with-visual-studio.md) k vytvoření a spuštění jednoduché konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="77737-104">So far, you've followed the steps in [Create your first .NET Core console application in Visual Studio 2019](with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="77737-105">Jakmile jste napsali a zkompilovali aplikaci, můžete ji začít testovat.</span><span class="sxs-lookup"><span data-stu-id="77737-105">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="77737-106">Visual Studio obsahuje komplexní sadu ladicích nástrojů, které můžete použít k řešení potíží s aplikací.</span><span class="sxs-lookup"><span data-stu-id="77737-106">Visual Studio includes a comprehensive set of debugging tools that you can use to troubleshoot your application.</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="77737-107">Ladění konfigurace sestavení</span><span class="sxs-lookup"><span data-stu-id="77737-107">Debug build configuration</span></span>

<span data-ttu-id="77737-108">*Ladění* a *vydání* jsou dvě výchozí konfigurace sestavení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77737-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="77737-109">Aktuální konfigurace sestavení je zobrazena na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="77737-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="77737-110">Následující obrázek panelu nástrojů ukazuje, že Visual Studio je nakonfigurováno pro kompilaci ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="77737-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![Panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="77737-112">Začněte spuštěním verze ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="77737-112">Begin by running the Debug version of your app.</span></span> <span data-ttu-id="77737-113">Konfigurace sestavení ladění vypne většinu optimalizace kompilátoru a poskytuje bohatší informace během procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="77737-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="77737-114">Nastavení zarážky</span><span class="sxs-lookup"><span data-stu-id="77737-114">Set a breakpoint</span></span>

<span data-ttu-id="77737-115">Spusťte program a vyzkoušejte několik funkcí ladění:</span><span class="sxs-lookup"><span data-stu-id="77737-115">Run your program and try a few debugging features:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="77737-116">C #</span><span class="sxs-lookup"><span data-stu-id="77737-116">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="77737-117">Nastavte *zarážku* na `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` řádku, který čte kliknutím na levém okraji okna kódu na tomto řádku.</span><span class="sxs-lookup"><span data-stu-id="77737-117">Set a *breakpoint* on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="77737-118">Zarážku můžete také nastavit umístěním stříšky do řádku kódu a stisknutím **klávesy F9** nebo výběrem **možnosti Ladění** > **přepínací zarážky z** řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="77737-118">You can also set a breakpoint by placing the caret in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="77737-119">Zarážka dočasně přeruší provádění aplikace *před* provedením řádku s zarážkou.</span><span class="sxs-lookup"><span data-stu-id="77737-119">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="77737-120">Jak ukazuje následující obrázek, Visual Studio označuje řádek, na kterém je zarážka nastavena zvýrazněním a zobrazením červeného kruhu v levém okraji.</span><span class="sxs-lookup"><span data-stu-id="77737-120">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![Okno Programu sady Visual Studio s nastavenou zarážkou](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="77737-122">Spusťte program v režimu ladění výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknutím **klávesy F5**nebo volbou **Ladění** > **ladění spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="77737-122">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="77737-123">Když program vyzve k zadání názvu, zadejte řetězec do okna konzoly a stiskněte **klávesu Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-123">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="77737-124">Spuštění programu se zastaví, když dosáhne `Console.WriteLine` zarážky a před spuštěním metody.</span><span class="sxs-lookup"><span data-stu-id="77737-124">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="77737-125">Místní **Locals** okno zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="77737-125">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Snímek obrazovky s zarážkou v Sadě Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="77737-127">Okno **Okamžité** umožňuje interakci s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="77737-127">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="77737-128">Můžete interaktivně změnit hodnotu proměnných a zjistit, jak ovlivňuje váš program.</span><span class="sxs-lookup"><span data-stu-id="77737-128">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="77737-129">Pokud okno **Okamžité** není viditelné, zobrazte ho tak, že zvolíte **Ladění** > **systému Windows** > **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="77737-129">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="77737-130">Zadejte `name = "Gracie"` do okna **Okamžité** a stiskněte klávesu **Enter.**</span><span class="sxs-lookup"><span data-stu-id="77737-130">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="77737-131">Zadejte `date = DateTime.Parse("11/16/2019 5:25 PM")` do okna **Okamžité** a stiskněte klávesu **Enter.**</span><span class="sxs-lookup"><span data-stu-id="77737-131">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="77737-132">Okno **Okamžité** zobrazuje hodnotu proměnné řetězce a <xref:System.DateTime> vlastnosti hodnoty.</span><span class="sxs-lookup"><span data-stu-id="77737-132">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="77737-133">Kromě toho jsou aktualizovány hodnoty proměnných v okně **Locals.**</span><span class="sxs-lookup"><span data-stu-id="77737-133">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Místní a okamžitá okna windows ve Visual Studiu 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="77737-135">Pokračujte v provádění programu výběrem tlačítka **Pokračovat** na panelu nástrojů nebo výběrem **možnosti Pokračovat** > **v**ladění .</span><span class="sxs-lookup"><span data-stu-id="77737-135">Continue program execution by selecting the **Continue** button in the toolbar or by selecting **Debug** > **Continue**.</span></span> <span data-ttu-id="77737-136">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v okně **Okamžité.**</span><span class="sxs-lookup"><span data-stu-id="77737-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="77737-138">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-138">Press any key to exit the application and stop debugging.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="77737-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77737-139">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="77737-140">Nastavte *zarážku* na `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` řádku, který čte kliknutím na levém okraji okna kódu na tomto řádku.</span><span class="sxs-lookup"><span data-stu-id="77737-140">Set a *breakpoint* on the line that reads `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="77737-141">Zarážku můžete také nastavit umístěním stříšky na požadovaný řádek a pak zvolte **ladění** > **přepnout zarážku** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="77737-141">You can also set a breakpoint by placing the caret on the desired line and then choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="77737-142">Zarážka dočasně přeruší provádění aplikace *před* provedením řádku s zarážkou.</span><span class="sxs-lookup"><span data-stu-id="77737-142">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="77737-143">Jak ukazuje následující obrázek, Visual Studio označuje řádek, na kterém je zarážka nastavena zvýrazněním a zobrazením červeného kruhu v levém okraji.</span><span class="sxs-lookup"><span data-stu-id="77737-143">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![Okno Programu sady Visual Studio s nastavenou zarážkou](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. <span data-ttu-id="77737-145">Spusťte program v režimu ladění výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů, stisknutím **klávesy F5**nebo volbou **Ladění** > **ladění spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="77737-145">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="77737-146">Když program vyzve k zadání názvu, zadejte řetězec do okna konzoly a stiskněte **klávesu Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-146">Enter a string in the console window when the program prompts for a name and press **Enter**.</span></span>

1. <span data-ttu-id="77737-147">Spuštění programu se zastaví, když dosáhne `Console.WriteLine` zarážky a před spuštěním metody.</span><span class="sxs-lookup"><span data-stu-id="77737-147">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="77737-148">Místní **Locals** okno zobrazuje hodnoty proměnných, které jsou definovány v aktuálně spuštěné metodě.</span><span class="sxs-lookup"><span data-stu-id="77737-148">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

1. <span data-ttu-id="77737-149">Okno **Okamžité** umožňuje interakci s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="77737-149">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="77737-150">Můžete interaktivně změnit hodnotu proměnných a zjistit, jak ovlivňuje váš program.</span><span class="sxs-lookup"><span data-stu-id="77737-150">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="77737-151">Pokud okno **Okamžité** není viditelné, zobrazte ho tak, že zvolíte **Ladění** > **systému Windows** > **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="77737-151">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="77737-152">Zadejte `name = "Gracie"` do okna **Okamžité** a stiskněte klávesu **Enter.**</span><span class="sxs-lookup"><span data-stu-id="77737-152">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="77737-153">Zadejte `date = DateTime.Parse("11/16/2019 5:25 PM")` do okna **Okamžité** a stiskněte klávesu **Enter.**</span><span class="sxs-lookup"><span data-stu-id="77737-153">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="77737-154">Hodnoty proměnných jsou aktualizovány v okně **Locals.**</span><span class="sxs-lookup"><span data-stu-id="77737-154">The values of the variables are updated in the **Locals** window.</span></span>

1. <span data-ttu-id="77737-155">Pokračujte v provádění programu výběrem tlačítka **Pokračovat** na panelu nástrojů nebo výběrem položky**nabídky** Pokračovat v **ladění.** > </span><span class="sxs-lookup"><span data-stu-id="77737-155">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="77737-156">Hodnoty zobrazené v okně konzoly odpovídají změnám, které jste provedli v okně **Okamžité.**</span><span class="sxs-lookup"><span data-stu-id="77737-156">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konzoly zobrazující zadané hodnoty](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="77737-158">Stisknutím libovolné klávesy ukončete aplikaci a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-158">Press any key to exit the application and stop debugging.</span></span>

---

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="77737-159">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="77737-159">Set a conditional breakpoint</span></span>

<span data-ttu-id="77737-160">Program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="77737-160">Your program displays the string that the user enters.</span></span> <span data-ttu-id="77737-161">Co se stane, když uživatel nic nezadá?</span><span class="sxs-lookup"><span data-stu-id="77737-161">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="77737-162">Můžete otestovat pomocí užitečné funkce ladění s názvem *podmíněné zarážky*, která přeruší spuštění programu, pokud jsou splněny jednu nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="77737-162">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="77737-163">Chcete-li nastavit podmíněnou zarážku a otestovat, co se stane, když uživatel nezadá řetězec, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="77737-163">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="c"></a>[<span data-ttu-id="77737-164">C #</span><span class="sxs-lookup"><span data-stu-id="77737-164">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="77737-165">Klikněte pravým tlačítkem myši na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="77737-165">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="77737-166">V místní nabídce vyberte **Podmínky,** chcete-li otevřít dialogové okno **Nastavení zarážky.**</span><span class="sxs-lookup"><span data-stu-id="77737-166">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="77737-167">Zaškrtněte políčko **Podmínky,** pokud ještě není vybrané.</span><span class="sxs-lookup"><span data-stu-id="77737-167">Check the box for **Conditions** if it's not already selected.</span></span>

   ![Editor zobrazující panel nastavení zarážky - C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="77737-169">Pro **podmíněný výraz**nahraďte "např. x == 5" následujícím:</span><span class="sxs-lookup"><span data-stu-id="77737-169">For the **Conditional Expression**, replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="77737-170">Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody `true` je `name` buď proto, že nebyla přiřazena hodnota, nebo protože jeho hodnota je prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="77737-170">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="77737-171">Namísto podmíněného výrazu můžete také určit *počet přístupů*, který přeruší spuštění programu před provedením příkazu zadaným počtem opakování nebo *podmínkou filtru*, která přeruší spuštění programu na základě těchto atributů, jako je identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="77737-171">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="77737-172">Chcete-li zavřít dialogové okno, vyberte **Zavřít.**</span><span class="sxs-lookup"><span data-stu-id="77737-172">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="77737-173">Spusťte program s laděním stisknutím **klávesy F5**.</span><span class="sxs-lookup"><span data-stu-id="77737-173">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="77737-174">V okně konzoly stiskněte klávesu **Enter,** když se zobrazí výzva k zadání jména.</span><span class="sxs-lookup"><span data-stu-id="77737-174">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="77737-175">Vzhledem `name` k tomu, `null` že <xref:System.String.Empty?displayProperty=nameWithType>zadaná podmínka je buď nebo , byla splněna, provádění programu se zastaví, jakmile dosáhne zarážky a před spuštěním `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="77737-175">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="77737-176">Vyberte okno **Locals,** které zobrazuje hodnoty proměnných, které jsou místní pro aktuálně spuštěnou metodu.</span><span class="sxs-lookup"><span data-stu-id="77737-176">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="77737-177">V tomto `Main` případě je aktuálně spuštěná metoda.</span><span class="sxs-lookup"><span data-stu-id="77737-177">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="77737-178">Všimněte si, `name` že `""`hodnota <xref:System.String.Empty?displayProperty=nameWithType>proměnné je , nebo .</span><span class="sxs-lookup"><span data-stu-id="77737-178">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="77737-179">Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu do okna **Okamžité** a stisknutím **klávesy Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-179">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="77737-180">Výsledkem `true`je .</span><span class="sxs-lookup"><span data-stu-id="77737-180">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![Okamžité okno vrací hodnotu true po provedení příkazu - C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="77737-182">Chcete-li pokračovat v provádění programu, vyberte na panelu nástrojů tlačítko **Pokračovat.**</span><span class="sxs-lookup"><span data-stu-id="77737-182">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="77737-183">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-183">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="77737-184">Zrušte zarážku kliknutím na tečku v levém okraji okna kódu nebo výběrem **možnosti Ladění > Přepnout zarážku,** když je vybrán řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="77737-184">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="77737-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77737-185">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="77737-186">Klikněte pravým tlačítkem myši na červenou tečku, která představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="77737-186">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="77737-187">V místní nabídce vyberte **Podmínky,** chcete-li otevřít dialogové okno **Nastavení zarážky.**</span><span class="sxs-lookup"><span data-stu-id="77737-187">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="77737-188">Zaškrtněte políčko **Podmínky**.</span><span class="sxs-lookup"><span data-stu-id="77737-188">Check the box for **Conditions**.</span></span>

   ![Editor zobrazující panel nastavení zarážky – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="77737-190">Podmíněný **výraz** nahraďte "např. x = 5" následujícím:</span><span class="sxs-lookup"><span data-stu-id="77737-190">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="77737-191">Testujete podmínku kódu, že `String.IsNullOrEmpty(name)` volání metody `true` je `name` buď proto, že nebyla přiřazena hodnota, nebo protože jeho hodnota je prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="77737-191">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="77737-192">Namísto podmíněného výrazu můžete také určit *počet přístupů*, který přeruší spuštění programu před provedením příkazu zadaným počtem opakování nebo *podmínkou filtru*, která přeruší spuštění programu na základě těchto atributů, jako je identifikátor vlákna, název procesu nebo název vlákna.</span><span class="sxs-lookup"><span data-stu-id="77737-192">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="77737-193">Chcete-li zavřít dialogové okno, vyberte **Zavřít.**</span><span class="sxs-lookup"><span data-stu-id="77737-193">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="77737-194">Spusťte program s laděním stisknutím **klávesy F5**.</span><span class="sxs-lookup"><span data-stu-id="77737-194">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="77737-195">V okně konzoly stiskněte klávesu **Enter,** když se zobrazí výzva k zadání jména.</span><span class="sxs-lookup"><span data-stu-id="77737-195">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="77737-196">Vzhledem `name` k tomu, `null` že <xref:System.String.Empty?displayProperty=nameWithType>zadaná podmínka je buď nebo , byla splněna, provádění programu se zastaví, jakmile dosáhne zarážky a před spuštěním `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="77737-196">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="77737-197">Vyberte okno **Locals,** které zobrazuje hodnoty proměnných, které jsou místní pro aktuálně spuštěnou metodu.</span><span class="sxs-lookup"><span data-stu-id="77737-197">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="77737-198">V tomto `Main` případě je aktuálně spuštěná metoda.</span><span class="sxs-lookup"><span data-stu-id="77737-198">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="77737-199">Všimněte si, `name` že `""`hodnota <xref:System.String.Empty?displayProperty=nameWithType>proměnné je , nebo .</span><span class="sxs-lookup"><span data-stu-id="77737-199">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="77737-200">Potvrďte, že hodnota je prázdný řetězec zadáním následujícího příkazu do okna **Okamžité** a stisknutím **klávesy Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-200">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="77737-201">Výsledkem `true`je .</span><span class="sxs-lookup"><span data-stu-id="77737-201">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Okamžité okno vrací hodnotu true po provedení příkazu - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. <span data-ttu-id="77737-203">Chcete-li pokračovat v provádění programu, vyberte na panelu nástrojů tlačítko **Pokračovat.**</span><span class="sxs-lookup"><span data-stu-id="77737-203">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="77737-204">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-204">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="77737-205">Zrušte zarážku kliknutím na tečku v levém okraji okna kódu nebo výběrem položky nabídky **Ladění > Přepnout zarážku** s vybraným řádkem.</span><span class="sxs-lookup"><span data-stu-id="77737-205">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="step-through-a-program"></a><span data-ttu-id="77737-206">Krokovat programem</span><span class="sxs-lookup"><span data-stu-id="77737-206">Step through a program</span></span>

<span data-ttu-id="77737-207">Visual Studio také umožňuje krok krok za krokem prostřednictvím programu a sledovat jeho provádění.</span><span class="sxs-lookup"><span data-stu-id="77737-207">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="77737-208">Obvykle byste nastavili zarážku a pomocí této funkce sledovali tok programu přes malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="77737-208">Ordinarily, you'd set a breakpoint and use this feature to follow program flow through a small part of your program code.</span></span> <span data-ttu-id="77737-209">Vzhledem k tomu, že váš program je malý, můžete krokovat celý program:</span><span class="sxs-lookup"><span data-stu-id="77737-209">Since your program is small, you can step through the entire program:</span></span>

# <a name="c"></a>[<span data-ttu-id="77737-210">C #</span><span class="sxs-lookup"><span data-stu-id="77737-210">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="77737-211">Na řádku nabídek zvolte **Ladění** > **kroku do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-211">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-212">Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.</span><span class="sxs-lookup"><span data-stu-id="77737-212">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio krok do metody - C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="77737-214">V tomto okamžiku **locals** okno ukazuje, že váš `args`program definoval pouze jednu proměnnou, .</span><span class="sxs-lookup"><span data-stu-id="77737-214">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="77737-215">Vzhledem k tomu, že jste programu nepředali žádné argumenty příkazového řádku, jeho hodnotou je prázdné pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="77737-215">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="77737-216">Kromě toho visual studio otevřelprázdné okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="77737-216">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="77737-217">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-217">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-218">Visual Studio nyní zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="77737-218">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="77737-219">Jak ukazuje obrázek, trvalo méně než jednu milisekundu spustit kód mezi poslední příkaz a tento.</span><span class="sxs-lookup"><span data-stu-id="77737-219">As the image shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="77737-220">`args`zůstává jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.</span><span class="sxs-lookup"><span data-stu-id="77737-220">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Krok visual studia ve zdroji metody - C #](./media/debugging-with-visual-studio/step-into-source-method.png)

1. <span data-ttu-id="77737-222">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-222">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-223">Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `name` proměnné.</span><span class="sxs-lookup"><span data-stu-id="77737-223">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="77737-224">Místní **Locals** okno ukazuje, že `name` je `null`a v okně konzoly se zobrazí řetězec "Jaké je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="77737-224">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="77737-225">Na výzvu odpovíte zadáním řetězce v okně konzoly a stisknutím **klávesy Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-225">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="77737-226">Konzole neodpovídá a zadaný řetězec se v okně konzoly nezobrazí, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda přesto zachytí váš vstup.</span><span class="sxs-lookup"><span data-stu-id="77737-226">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="77737-227">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-227">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-228">Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `date` proměnné.</span><span class="sxs-lookup"><span data-stu-id="77737-228">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="77737-229">Místní **Locals** okno zobrazuje hodnotu vrácenou <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="77737-229">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="77737-230">V okně konzoly se také zobrazí řetězec, který jste zadali na výzvu.</span><span class="sxs-lookup"><span data-stu-id="77737-230">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="77737-231">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-231">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-232">Místní **Locals** okno zobrazuje hodnotu `date` proměnné po přiřazení <xref:System.DateTime.Now?displayProperty=nameWithType> z vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="77737-232">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="77737-233">Okno konzoly se nezmění.</span><span class="sxs-lookup"><span data-stu-id="77737-233">The console window is unchanged.</span></span>

1. <span data-ttu-id="77737-234">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-234">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-235">Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> volá metodu.</span><span class="sxs-lookup"><span data-stu-id="77737-235">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="77737-236">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="77737-236">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="77737-237">Vyberte **Možnost Ladění krok** > **ven** nebo stiskněte **Shift**+**F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-237">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="77737-238">To zastaví provádění krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="77737-238">This stops step-by-step execution.</span></span> <span data-ttu-id="77737-239">V okně konzoly se zobrazí zpráva a čeká, až stisknete klávesu.</span><span class="sxs-lookup"><span data-stu-id="77737-239">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="77737-240">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-240">Press any key to close the console window and stop debugging.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="77737-241">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77737-241">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="77737-242">Na řádku nabídek zvolte **Ladění** > **kroku do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-242">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-243">Visual Studio zvýrazní a zobrazí šipku vedle dalšího řádku provádění.</span><span class="sxs-lookup"><span data-stu-id="77737-243">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio krok do metody - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="77737-245">V tomto okamžiku **locals** okno ukazuje, že váš `args`program definoval pouze jednu proměnnou, .</span><span class="sxs-lookup"><span data-stu-id="77737-245">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="77737-246">Vzhledem k tomu, že jste programu nepředali žádné argumenty příkazového řádku, jeho hodnotou je prázdné pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="77737-246">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="77737-247">Kromě toho visual studio otevřelprázdné okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="77737-247">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="77737-248">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-248">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-249">Visual Studio nyní zvýrazní další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="77737-249">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="77737-250">Jak ukazuje obrázek, trvalo méně než jednu milisekundu spustit kód mezi poslední příkaz a tento.</span><span class="sxs-lookup"><span data-stu-id="77737-250">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="77737-251">`args`zůstává jedinou deklarovanou proměnnou a okno konzoly zůstane prázdné.</span><span class="sxs-lookup"><span data-stu-id="77737-251">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio krok do zdroje metody - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="77737-253">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-253">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-254">Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `name` proměnné.</span><span class="sxs-lookup"><span data-stu-id="77737-254">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="77737-255">Místní **Locals** okno ukazuje, že `name` je `Nothing`a v okně konzoly se zobrazí řetězec "Jaké je vaše jméno?".</span><span class="sxs-lookup"><span data-stu-id="77737-255">The **Locals** window shows that `name` is `Nothing`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="77737-256">Na výzvu odpovíte zadáním řetězce v okně konzoly a stisknutím **klávesy Enter**.</span><span class="sxs-lookup"><span data-stu-id="77737-256">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="77737-257">Konzole neodpovídá a řetězec, který zadáte, se nezobrazí v okně <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> konzoly, ale metoda přesto zachytí váš vstup.</span><span class="sxs-lookup"><span data-stu-id="77737-257">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="77737-258">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-258">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-259">Visual Studio zvýrazní příkaz, který zahrnuje přiřazení `currentDate` proměnné.</span><span class="sxs-lookup"><span data-stu-id="77737-259">Visual Studio highlights the statement that includes the `currentDate` variable assignment.</span></span> <span data-ttu-id="77737-260">Místní **Locals** okno zobrazuje hodnotu vrácenou <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="77737-260">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="77737-261">V okně konzoly se také zobrazí řetězec zadaný, když konzole vyzvala k zadání vstupu.</span><span class="sxs-lookup"><span data-stu-id="77737-261">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="77737-262">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-262">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-263">Okno konzoly se nezmění.</span><span class="sxs-lookup"><span data-stu-id="77737-263">The console window is unchanged.</span></span>

1. <span data-ttu-id="77737-264">Vyberte **možnost Ladit** > **krok do** nebo stiskněte **klávesu F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-264">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="77737-265">Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> volá metodu.</span><span class="sxs-lookup"><span data-stu-id="77737-265">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="77737-266">V okně konzoly se zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="77737-266">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="77737-267">Vyberte **Možnost Ladění krok** > **ven** nebo stiskněte **Shift**+**F11**.</span><span class="sxs-lookup"><span data-stu-id="77737-267">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="77737-268">To zastaví provádění krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="77737-268">This stops step-by-step execution.</span></span> <span data-ttu-id="77737-269">V okně konzoly se zobrazí zpráva a čeká, až stisknete klávesu.</span><span class="sxs-lookup"><span data-stu-id="77737-269">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="77737-270">Stisknutím libovolné klávesy zavřete okno konzoly a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="77737-270">Press any key to close the console window and stop debugging.</span></span>

---

## <a name="build-a-release-version"></a><span data-ttu-id="77737-271">Vytvoření verze vydání</span><span class="sxs-lookup"><span data-stu-id="77737-271">Build a Release version</span></span>

<span data-ttu-id="77737-272">Po otestování verze ladění aplikace, měli byste také zkompilovat a otestovat verzi vydání.</span><span class="sxs-lookup"><span data-stu-id="77737-272">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="77737-273">Verze verze obsahuje optimalizace kompilátoru, které mohou někdy negativně ovlivnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="77737-273">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="77737-274">Například optimalizace kompilátoru, které jsou navrženy ke zlepšení výkonu můžete vytvořit podmínky časování v aplikacích s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="77737-274">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="77737-275">Chcete-li vytvořit a otestovat verzi aplikace konzoly, změňte konfiguraci sestavení na panelu nástrojů z **Ladění** na **Verzi**.</span><span class="sxs-lookup"><span data-stu-id="77737-275">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![výchozí panel nástrojů sady Visual Studio se zvýrazněným laděním](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="77737-277">Když stisknete **klávesu F5** nebo zvolte **sestavit řešení** z nabídky **Sestavení,** Visual Studio zkompiluje verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="77737-277">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="77737-278">Můžete jej otestovat stejně jako ladicí verze.</span><span class="sxs-lookup"><span data-stu-id="77737-278">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="77737-279">Další kroky</span><span class="sxs-lookup"><span data-stu-id="77737-279">Next steps</span></span>

<span data-ttu-id="77737-280">Po odladění aplikace je dalším krokem publikování nasaditelné verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="77737-280">Once you've debugged your application, the next step is to publish a deployable version of the app.</span></span> <span data-ttu-id="77737-281">Informace o tom, jak to provést, naleznete [v tématu publikování aplikace .NET Core Hello World pomocí sady Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="77737-281">For information on how to do this, see [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>
