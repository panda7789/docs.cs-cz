---
title: "Ladění aplikace C# Hello, World s Visual Studio 2017"
description: "Postup ladění aplikace Hello World napsané v C# a Visual Studio 2017."
keywords: ".NET core, .NET Core Konzolová aplikace, ladění v rozhraní .NET Core"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
ms.workload: dotnetcore
ms.openlocfilehash: 3ab19566acb36cb96e0572931ba39f2ae99a3ca7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="fe6f1-104">Ladění aplikace Hello World s Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fe6f1-104">Debug your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="fe6f1-105">Pokud jste postupovali podle kroků v [sestavení C# Hello World aplikace s .NET Core ve Visual Studio 2017](.\with-visual-studio.md) nebo [sestavení jazyka Visual Basic Hello World aplikace s .NET Core ve Visual Studio 2017](vb-with-visual-studio.md) k vytvoření a spusťte jednoduché konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-105">So far, you've followed the steps in [Build a C# Hello World Application with .NET Core in Visual Studio 2017](.\with-visual-studio.md) or [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="fe6f1-106">Jakmile jste zapisovat a kompilované aplikace, můžete zahájit testování ho.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-106">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="fe6f1-107">Visual Studio zahrnuje komplexní sadu ladicí nástroje, které můžete použít při testování a řešení potíží s vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-107">Visual Studio includes a comprehensive set of debugging tools that you can use when testing and troubleshooting your application.</span></span>

## <a name="debugging-in-debug-mode"></a><span data-ttu-id="fe6f1-108">Ladění v režimu ladění</span><span class="sxs-lookup"><span data-stu-id="fe6f1-108">Debugging in Debug mode</span></span>

<span data-ttu-id="fe6f1-109">*Ladění* a *verze* jsou dvě sady Visual Studio výchozí konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-109">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="fe6f1-110">Aktuální konfigurace sestavení se zobrazí na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-110">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="fe6f1-111">Na následujícím obrázku panelu nástrojů zobrazují, která je konfigurace zkompilovat svoji aplikaci v sadě Visual Studio **ladění** režimu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-111">The following toolbar image shows that Visual Studio is configured to compile your application in **Debug** mode.</span></span>

   ![Panel nástrojů Visual Studio](./media/debugging-with-visual-studio/toolbar1.png)

<span data-ttu-id="fe6f1-113">Vždy začít testování váš program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-113">You should always begin by testing your program in Debug mode.</span></span> <span data-ttu-id="fe6f1-114">Ladění režimu vypne většina optimalizace kompilátoru a poskytuje bohatší informace během procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-114">Debug mode turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="setting-a-breakpoint"></a><span data-ttu-id="fe6f1-115">Nastavení boru přerušení</span><span class="sxs-lookup"><span data-stu-id="fe6f1-115">Setting a breakpoint</span></span>

<span data-ttu-id="fe6f1-116">Spustit program v režimu ladění a zkuste několik ladění funkcí:</span><span class="sxs-lookup"><span data-stu-id="fe6f1-116">Run your program in Debug mode and try a few debugging features:</span></span>

1. <span data-ttu-id="fe6f1-117">A *zarážek* dočasně přeruší provádění aplikace *před* řádek se zarážkou spustí.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-117">A *breakpoint* temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-118">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-118">C#</span></span>](#tab/csharp)
   <span data-ttu-id="fe6f1-119">Nastavte zarážky v řádku, který čte `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kliknutím na levém okraji okna kódu na tomto řádku nebo výběrem **ladění** > **Přepnout zarážku** položky nabídky řádek Vybrat.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-119">Set a breakpoint on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="fe6f1-120">Jak ukazuje následující obrázek, označuje Visual Studio na řádku, na kterém je nastaven breakpoint zvýraznění ho a zobrazením červené kolečko jeho levého okraje.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-120">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![Visual Studio Program okno sadou zarážek](./media/debugging-with-visual-studio/setbreakpoint.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-122">Visual Basic</span></span>](#tab/visual-basic)
   <span data-ttu-id="fe6f1-123">Nastavte zarážky v řádku, který čte `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kliknutím na levém okraji okna kódu na tomto řádku nebo výběrem **ladění** > **Přepnout zarážku** položky nabídky řádek Vybrat.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-123">Set a breakpoint on the line that reads `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="fe6f1-124">Jak ukazuje následující obrázek, označuje Visual Studio na řádku, na kterém je nastaven breakpoint zvýraznění ho a zobrazením červené kolečko jeho levého okraje.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-124">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   <a name="visual-studio-program-window-with-breakpoint-setmediadebugging-with-visual-studiovb-setbreakpointpng"></a>![Visual Studio Program okno sadou zarážek](./media/debugging-with-visual-studio/vb-setbreakpoint.png)
---

1. <span data-ttu-id="fe6f1-126">Spusťte program v režimu ladění výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-126">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing F5, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="fe6f1-127">Zadejte řetězec v okně konzoly, když program vyzve k zadání názvu a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-127">Enter a string in the console window when the program prompts for a name and press Enter.</span></span>

1. <span data-ttu-id="fe6f1-128">Spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-128">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="fe6f1-129">**Automobily** zobrazuje hodnoty proměnných, které se používají kolem aktuálního řádku.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-129">The **Autos** window displays the values of variables that are used around the current line.</span></span> <span data-ttu-id="fe6f1-130">**Místní hodnoty –** okno (které můžete zobrazit kliknutím **místní hodnoty –** kartě) zobrazuje hodnoty proměnných, které jsou definovány v metodě aktuálně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-130">The **Locals** window (which you can view by clicking the **Locals** tab) displays the values of variables that are defined in the currently executing method.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-131">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-131">C#</span></span>](#tab/csharp)
   ![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/break.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-133">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-133">Visual Basic</span></span>](#tab/visual-basic)
   <a name="visual-studio-application-windowmediadebugging-with-visual-studiovb-breakpng"></a>![Okno aplikace Visual Studio](./media/debugging-with-visual-studio/vb-break.png)
---

1. <span data-ttu-id="fe6f1-135">Můžete změnit hodnotu proměnné, které chcete zjistit, jak ho ovlivní vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-135">You can change the value of the variables to see how it affects your program.</span></span> <span data-ttu-id="fe6f1-136">Pokud **hodnot proměnných** nezobrazuje, zobrazit a vybrat **ladění** > **Windows** > **Immediate**položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-136">If the **Immediate Window** is not visible, display it by choosing the **Debug** > **Windows** > **Immediate** menu item.</span></span> <span data-ttu-id="fe6f1-137">**Hodnot proměnných** umožňuje pracovat s aplikací, kterou ladíte.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-137">The **Immediate Window** lets you interact with the application you're debugging.</span></span>

1. <span data-ttu-id="fe6f1-138">Můžete interaktivně změnit hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-138">You can interactively change the values of variables.</span></span> <span data-ttu-id="fe6f1-139">Zadejte `name = "Gracie"` v **hodnot proměnných** a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-139">Enter `name = "Gracie"` in the **Immediate Window** and press the Enter key.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-140">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-140">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="fe6f1-141">Zadejte `date = new DateTime(2016,11,01,11,59,00)` v **hodnot proměnných** a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-141">Enter `date = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

   <span data-ttu-id="fe6f1-142">**Hodnot proměnných** zobrazí hodnotu proměnné řetězce a vlastnosti <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-142">The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="fe6f1-143">Kromě toho se aktualizuje hodnotu proměnné v **automobily** a **místní hodnoty –** systému windows.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-143">In addition, the value of the variables is updated in the **Autos** and **Locals** windows.</span></span>

   ![Automatické hodnoty – okno a příkazové podokno](./media/debugging-with-visual-studio/autosimmediate.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-145">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-145">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="fe6f1-146">Zadejte `currentDate = new DateTime(2016,11,01,11,59,00)` v **hodnot proměnných** a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-146">Enter `currentDate = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

<!-- The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value. In addition, the value of the variables is updated in the **Autos** and **Locals** windows.

   ![Autos window and Immediate Window](./media/debugging-with-visual-studio/vb-autosimmediate.png)
-->
---

1. <span data-ttu-id="fe6f1-147">Pokračujte výběrem spuštění programu **pokračovat** tlačítka na panelu nástrojů nebo výběrem **ladění** > **pokračovat** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-147">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="fe6f1-148">Hodnoty zobrazené v okně konzoly odpovídají změny provedené v **hodnot proměnných**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-148">The values displayed in the console window correspond to the changes you made in the **Immediate Window**.</span></span>

   ![Okno konzoly zobrazující zadanou hodnotou konektoru na to, co je název vaší? řádek následovaný Hello Gracie 11/1/2016 v 11:59 am](./media/debugging-with-visual-studio/changed.png)

1. <span data-ttu-id="fe6f1-150">Stisknutím libovolné klávesy, chcete-li ukončit režim ladění aplikace a end.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-150">Press any key to exit the application and end Debug mode.</span></span>

## <a name="setting-a-conditional-breakpoint"></a><span data-ttu-id="fe6f1-151">Nastavení podmíněné zarážky</span><span class="sxs-lookup"><span data-stu-id="fe6f1-151">Setting a conditional breakpoint</span></span>

<span data-ttu-id="fe6f1-152">Váš program zobrazí řetězec, který uživatel zadá.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-152">Your program displays the string that the user enters.</span></span> <span data-ttu-id="fe6f1-153">Co se stane, když uživatel není zadat nic?</span><span class="sxs-lookup"><span data-stu-id="fe6f1-153">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="fe6f1-154">Toto můžete otestovat s ladění užitečná *podmíněného zarážek*, která zalomení programu spuštění, pokud jeden nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-154">You can test this with a useful debugging feature, the *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="fe6f1-155">Pro nastavení podmíněné zarážky a testování, co se stane, když uživateli nepodaří zadejte řetězec, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="fe6f1-155">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-156">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-156">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="fe6f1-157">Klikněte pravým tlačítkem myši na červenou tečku, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-157">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="fe6f1-158">V místní nabídce vyberte **podmínky** otevřete **nastavení zarážek** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-158">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="fe6f1-159">Zaškrtněte políčko pro **podmínky**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-159">Check the box for **Conditions**.</span></span>

   ![Panel nastavení zarážek](./media/debugging-with-visual-studio/breakpointsettings.png)

1. <span data-ttu-id="fe6f1-161">Pro **podmíněným výrazem** nahradit "například x == 5" s následující:</span><span class="sxs-lookup"><span data-stu-id="fe6f1-161">For the **Conditional Expression** replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-162">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-162">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="fe6f1-163">Klikněte pravým tlačítkem myši na červenou tečku, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-163">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="fe6f1-164">V místní nabídce vyberte **podmínky** otevřete **nastavení zarážek** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-164">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="fe6f1-165">Zaškrtněte políčko pro **podmínky**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-165">Check the box for **Conditions**.</span></span>

   ![Panel nastavení zarážek](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="fe6f1-167">Pro **podmíněným výrazem** nahradit "například x = 5" s následující:</span><span class="sxs-lookup"><span data-stu-id="fe6f1-167">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```
---

   <span data-ttu-id="fe6f1-168">Testujete kód podmínku, který `String.IsNullOrEmpty(name)` volání metody, které je `true` buď protože *název* nemá přiřazenu hodnotu nebo proto, že jeho hodnota může být prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="fe6f1-168">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because *name* has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="fe6f1-169">Můžete také zadat *počet volání*, které přerušení spuštění programu před příkaz provést zadaného počtu opakování, nebo *podmínka filtru*, který přerušení program provádění například podle atributy jako identifikátor přístup z více vláken, název procesu nebo názvu vlákna.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-169">You can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="fe6f1-170">Vyberte **zavřete** tlačítko zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-170">Select the **Close** button to close the dialog.</span></span>

1. <span data-ttu-id="fe6f1-171">Spusťte program v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-171">Run the program in Debug mode.</span></span>

1. <span data-ttu-id="fe6f1-172">V okně konzoly stiskněte klávesu Enter po zobrazení výzvy zadejte své jméno.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-172">In the console window, press the Enter key when prompted to enter your name.</span></span>

1. <span data-ttu-id="fe6f1-173">Vzhledem k tomu, že jsme zadaná podmínka, `name` je buď `null` nebo <xref:System.String.Empty?displayProperty=nameWithType>, byly splněny, spuštění programu zastaví, když se dosáhne zarážce a před `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-173">Because the condition we specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="fe6f1-174">Vyberte **místní hodnoty –** okna, která zobrazuje hodnoty proměnných, které jsou místní vzhledem k aktuálně prováděné metoda, která je `Main` metoda v programu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-174">Select the **Locals** window, which shows the values of variables that are local to the currently executing method, which is the `Main` method in your program.</span></span> <span data-ttu-id="fe6f1-175">Sledovat, která hodnota `name` proměnná `""`, nebo <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-175">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-176">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-176">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="fe6f1-177">Potvrďte hodnota je prázdný řetězec zadáním následujícího příkazu v **hodnot proměnných**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-177">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="fe6f1-178">Výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-178">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![Vrací hodnotu true, po provedení příkazu příkazové podokno](./media/debugging-with-visual-studio/emptystring.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-180">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-180">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="fe6f1-181">Potvrďte hodnota je prázdný řetězec zadáním následujícího příkazu v **hodnot proměnných**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-181">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="fe6f1-182">Výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-182">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Vrací hodnotu true, po provedení příkazu příkazové podokno](./media/debugging-with-visual-studio/vb-emptystring.png)
---

1. <span data-ttu-id="fe6f1-184">Vyberte **pokračovat** tlačítka na panelu nástrojů pro pokračování v provádění programu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-184">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="fe6f1-185">Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-185">Press any key to close the console window and exit Debug mode.</span></span>

1. <span data-ttu-id="fe6f1-186">Zrušte zaškrtnutí zarážce kliknutím na tečky na levém okraji okna kódu nebo výběrem **ladění > Přepnout zarážku** položky nabídky řádek vybraný.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-186">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="stepping-through-a-program"></a><span data-ttu-id="fe6f1-187">Procházení program</span><span class="sxs-lookup"><span data-stu-id="fe6f1-187">Stepping through a program</span></span>

<span data-ttu-id="fe6f1-188">Visual Studio také umožňuje krok řádek po řádku prostřednictvím programu a monitorovat jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-188">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="fe6f1-189">By normálně, nastavit zarážky a pomocí této funkce lze podle toku programu, když malou část kódu programu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-189">Ordinarily, you'd set a breakpoint and use this feature to follow program flow though a small part of your program code.</span></span> <span data-ttu-id="fe6f1-190">Vzhledem k tomu, že váš program je malá, můžete krokovat úplný program následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fe6f1-190">Since your program is small, you can step through the entire program by doing the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="fe6f1-191">C#</span><span class="sxs-lookup"><span data-stu-id="fe6f1-191">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="fe6f1-192">Na řádku nabídek zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-192">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-193">Visual Studio klade důraz a zobrazuje šipku vedle položky na další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-193">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio – okno](./media/debugging-with-visual-studio/stepinto1.png)

   <span data-ttu-id="fe6f1-195">V tomto okamžiku **automobily** ukazuje, že váš program je definovaný jenom jednu proměnnou `args`.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-195">At this point, the **Autos** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="fe6f1-196">Protože žádných argumentů příkazového řádku nebyly předány programu, jeho hodnota může být pole prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-196">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="fe6f1-197">Kromě toho Visual Studio otevřel okna konzoly prázdné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-197">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="fe6f1-198">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-198">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-199">Visual Studio teď klade důraz na další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-199">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="fe6f1-200">Jak ukazuje obrázek, trvá méně než jeden milisekundu ke spouštění kódu vytvořeného mezi poslední příkaz a tato.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-200">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="fe6f1-201">`args`zůstane pouze deklarované proměnnou, a v okně konzoly zůstává prázdné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-201">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio – okno](./media/debugging-with-visual-studio/stepinto2.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="fe6f1-203">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6f1-203">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="fe6f1-204">Na řádku nabídek zvolte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-204">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-205">Visual Studio klade důraz a zobrazuje šipku vedle položky na další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-205">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio – okno](./media/debugging-with-visual-studio/vb-stepinto1.png)

   <span data-ttu-id="fe6f1-207">Na tento bod, protože nebyly předána žádných argumentů příkazového řádku programu, **automobily** okno ukazuje, že hodnota `args` proměnné je pole prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-207">At this point, because you haven't passed any command-line arguments to the program, the **Autos** window shows that the value of the `args` variable is an empty string array.</span></span> <span data-ttu-id="fe6f1-208">Kromě toho Visual Studio otevřel okna konzoly prázdné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-208">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="fe6f1-209">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-209">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-210">Visual Studio teď klade důraz na další řádek provádění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-210">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="fe6f1-211">Jak ukazuje obrázek, trvá méně než jeden milisekundu ke spouštění kódu vytvořeného mezi poslední příkaz a tato.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-211">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="fe6f1-212">`args`zůstane pouze deklarované proměnnou, a v okně konzoly zůstává prázdné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-212">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio – okno](./media/debugging-with-visual-studio/vb-stepinto2.png)
---

1. <span data-ttu-id="fe6f1-214">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-214">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-215">Visual Studio označuje příkaz, který obsahuje `name` přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-215">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="fe6f1-216">**Automobily** okno ukazuje, že `name` je `null` (v jazyku C#) nebo `Nothing` (v jazyku Visual Basic), a v okně konzoly zobrazí řetězec "Jaký je název vaší?".</span><span class="sxs-lookup"><span data-stu-id="fe6f1-216">The **Autos** window shows that `name` is `null` (in C#) or `Nothing` (in Visual Basic), and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="fe6f1-217">Odpověď na výzvu zadáte řetězec v okně konzoly a stisknutím klávesy Enter.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-217">Respond to the prompt by entering a string in the console window and pressing Enter.</span></span> <span data-ttu-id="fe6f1-218">Konzole je reagovat a zadáte řetězec nezobrazuje v okně konzoly ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda jasném zaznamená váš vstup.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-218">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="fe6f1-219">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-219">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-220">Visual Studio označuje příkaz, který obsahuje `date` (v jazyku C#) nebo `currentDate` (v jazyce Visual Basic) přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-220">Visual Studio highlights the statement that includes the `date` (in C#) or `currentDate` (in Visual Basic) variable assignment.</span></span> <span data-ttu-id="fe6f1-221">**Automobily** okno ukazuje <xref:System.DateTime.Now?displayProperty=nameWithType> hodnotu vlastnosti a hodnoty vrácené volání <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-221">The **Autos** window shows the <xref:System.DateTime.Now?displayProperty=nameWithType> property value and the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe6f1-222">V okně konzoly zobrazí také řetězec zadá, když konzole, budete vyzváni k zadání vstupu.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-222">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="fe6f1-223">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-223">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-224">**Automobily** v okně se zobrazí hodnota `date` proměnné po přiřazení z <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-224">The **Autos** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fe6f1-225">V okně konzoly se nezmění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-225">The console window is unchanged.</span></span>

1. <span data-ttu-id="fe6f1-226">Vyberte **ladění** > **Krokovat s vnořením** nebo stiskněte klávesu F11.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-226">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="fe6f1-227">Volání sady Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-227">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe6f1-228">Hodnoty `date` (nebo `currentDate`) a `name` proměnné se zobrazují v **automobily** okno a v okně konzoly zobrazí formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-228">The values of the `date` (or `currentDate`) and `name` variables appear in the **Autos** window, and the console window displays the formatted string.</span></span>

1. <span data-ttu-id="fe6f1-229">Vyberte **ladění** > **Krokovat s Vystoupením** nebo stiskněte klávesu Shift a F11 klíč.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-229">Select **Debug** > **Step Out** or press Shift and the F11 key.</span></span> <span data-ttu-id="fe6f1-230">To zastaví podrobné provádění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-230">This stops step-by-step execution.</span></span> <span data-ttu-id="fe6f1-231">V okně konzoly zobrazí zprávu a čeká na stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-231">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="fe6f1-232">Stisknutím libovolné klávesy zavřete okno konzoly a ukončení režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-232">Press any key to close the console window and exit Debug mode.</span></span>

## <a name="building-a-release-version"></a><span data-ttu-id="fe6f1-233">Vytváření prodejní verzi</span><span class="sxs-lookup"><span data-stu-id="fe6f1-233">Building a Release version</span></span>

<span data-ttu-id="fe6f1-234">Jakmile otestujete sestavení ladicí verze aplikace, musí také sestavit a otestovat prodejní verze.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-234">Once you've tested the Debug build of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="fe6f1-235">Prodejní verze zahrnuje kompilátoru optimalizace, které mohou někdy negativně ovlivnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-235">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="fe6f1-236">Optimalizace kompilátoru, které jsou určeny ke zlepšení výkonu můžete například vytvořit časování v asynchronní nebo vícevláknové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-236">For example, compiler optimizations that are designed to improve performance can create race conditions in asynchronous or multithreaded applications.</span></span>

<span data-ttu-id="fe6f1-237">Pro sestavení a otestování prodejní verze nástroje konzolové aplikace, změnit konfiguraci sestavení na panelu nástrojů z **ladění** k **verze**.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-237">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![Image](./media/debugging-with-visual-studio/toolbar2.png)

<span data-ttu-id="fe6f1-239">Když stisknutím klávesy F5 nebo zvolte **sestavit řešení** z **sestavení** nabídce sady Visual Studio zkompiluje prodejní verze nástroje konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-239">When you press F5 or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of your console application.</span></span> <span data-ttu-id="fe6f1-240">Jej můžete otestovat, jako jste to udělali ladicí verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-240">You can test it as you did the Debug version of the application.</span></span>

<span data-ttu-id="fe6f1-241">Jakmile dokončíte ladění aplikace, dalším krokem je publikovat využít verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe6f1-241">Once you've finished debugging your application, the next step is to publish a deployable version of your application.</span></span> <span data-ttu-id="fe6f1-242">Informace o tom, jak to udělat najdete v tématu [publikovat aplikace Hello World s Visual Studio 2017](./publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fe6f1-242">For information on how to do this, see [Publish the Hello World application with Visual Studio 2017](./publishing-with-visual-studio.md).</span></span>
