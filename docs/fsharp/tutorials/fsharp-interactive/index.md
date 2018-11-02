---
title: Interaktivní referenční dokumentace F# (fsi.exe)
description: Zjistěte, jak F# Interactive (fsi.exe) se používá ke spouštění F# kódu interaktivní konzoly nebo k provádění F# skripty.
ms.date: 05/16/2016
ms.openlocfilehash: 459a2a4ba49ba0f55455797617781d010efecc0b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50195252"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="21dad-103">Interaktivní programování s jazykem F#</span><span class="sxs-lookup"><span data-stu-id="21dad-103">Interactive Programming with F#</span></span> #

> [!NOTE]
<span data-ttu-id="21dad-104">Tento článek popisuje aktuálně prostředí jenom pro Windows.</span><span class="sxs-lookup"><span data-stu-id="21dad-104">This article currently describes the experience for Windows only.</span></span>  <span data-ttu-id="21dad-105">Bude přepsán.</span><span class="sxs-lookup"><span data-stu-id="21dad-105">It will be rewritten.</span></span>

> [!NOTE]
<span data-ttu-id="21dad-106">Odkaz rozhraní API se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="21dad-106">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="21dad-107">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="21dad-107">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="21dad-108">Program F# Interactive (fsi.exe) se používá pro interaktivní spuštění kódu jazyka F# v konzole nebo pro spuštění skriptů jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="21dad-108">F# Interactive (fsi.exe) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="21dad-109">Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.</span><span class="sxs-lookup"><span data-stu-id="21dad-109">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="21dad-110">Chcete-li spustit jazyk F# Interactive z konzoly, spusťte program fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="21dad-110">To run F# Interactive from the console, run fsi.exe.</span></span>  <span data-ttu-id="21dad-111">Zjistíte fsi.exe v:</span><span class="sxs-lookup"><span data-stu-id="21dad-111">You will find fsi.exe in:</span></span>

```console
C:\Program Files (x86)\Microsoft Visual Studio\2017\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

<span data-ttu-id="21dad-112">kde `sku` je buď `Community`, `Professional`, nebo `Enterprise`.</span><span class="sxs-lookup"><span data-stu-id="21dad-112">where `sku` is either `Community`, `Professional`, or `Enterprise`.</span></span>

<span data-ttu-id="21dad-113">Informace o dostupných možnostech příkazového řádku najdete v tématu [ F# interaktivní možnosti](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="21dad-113">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="21dad-114">Ke spuštění F# interaktivní prostřednictvím sady Visual Studio, můžete kliknutí na příslušné tlačítko s popiskem  **F# interaktivní**, nebo pomocí kláves **Ctrl + Alt + F**.</span><span class="sxs-lookup"><span data-stu-id="21dad-114">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="21dad-115">Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="21dad-115">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="21dad-116">Můžete také vybrat část kódu, které chcete spustit v interaktivním okně a stisknout kombinaci kláves **ALT + ENTER**.</span><span class="sxs-lookup"><span data-stu-id="21dad-116">You can also select some code that you want to run in the interactive window and hit the key combination **ALT+ENTER**.</span></span> <span data-ttu-id="21dad-117">F#V panelu nástrojů označené jako interaktivní spuštění  **F# interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="21dad-117">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="21dad-118">Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.</span><span class="sxs-lookup"><span data-stu-id="21dad-118">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="21dad-119">Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání.</span><span class="sxs-lookup"><span data-stu-id="21dad-119">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="21dad-120">Zde je možné zadat kód stejně jako v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="21dad-120">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="21dad-121">Chcete-li zkompilovat a spustit kód, zadáním dvou středníků (**;** ) ukončete řádek nebo několik řádků vstupu.</span><span class="sxs-lookup"><span data-stu-id="21dad-121">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="21dad-122">Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="21dad-122">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="21dad-123">Pokud dojde k chybám, překladač vytiskne chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="21dad-123">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="21dad-124">Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy.</span><span class="sxs-lookup"><span data-stu-id="21dad-124">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="21dad-125">Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.</span><span class="sxs-lookup"><span data-stu-id="21dad-125">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="21dad-126">Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.</span><span class="sxs-lookup"><span data-stu-id="21dad-126">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="21dad-127">Pokud máte-li otevřen projekt, který odkazuje na některé knihovny, můžete odkazovat v F# interaktivní prostřednictvím **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="21dad-127">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="21dad-128">Odkaz knihovny F# interaktivní, rozbalte **odkazy** uzel, otevřete místní nabídku knihovny a zvolte **odeslat F# interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="21dad-128">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="21dad-129">Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení.</span><span class="sxs-lookup"><span data-stu-id="21dad-129">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="21dad-130">Na **nástroje** příkaz **možnosti...** a potom rozbalte  **F# nástroje**.</span><span class="sxs-lookup"><span data-stu-id="21dad-130">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="21dad-131">Jsou dvě nastavení, které můžete změnit F# interaktivní možnosti a **64-bit F# interaktivní** nastavení, která je relevantní pouze v případě, že používáte F# Interactive v 64bitovém počítači.</span><span class="sxs-lookup"><span data-stu-id="21dad-131">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="21dad-132">Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="21dad-132">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>


## <a name="scripting-with-f"></a><span data-ttu-id="21dad-133">Skriptování pomocí jazyka F#</span><span class="sxs-lookup"><span data-stu-id="21dad-133">Scripting with F#</span></span> #
<span data-ttu-id="21dad-134">Skripty používají příponu souboru **.fsx** nebo **.fsscript**.</span><span class="sxs-lookup"><span data-stu-id="21dad-134">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="21dad-135">Namísto zkompilování zdrojového kódu a následného spuštění zkompilovaného sestavení, lze pouze spustit **fsi.exe** a zadejte název souboru skriptu F# zdrojový kód, a F# interactive tento kód načte a spustí v reálném čas.</span><span class="sxs-lookup"><span data-stu-id="21dad-135">Instead of compiling source code and then later running the compiled assembly, you can just run **fsi.exe** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="21dad-136">Rozdíly mezi interaktivním, skriptovacím a kompilovaným prostředím</span><span class="sxs-lookup"><span data-stu-id="21dad-136">Differences Between the Interactive, Scripting and Compiled Environments</span></span>
<span data-ttu-id="21dad-137">Při kompilaci kódu v F# interaktivní, zda jsou spustíte interaktivně nebo spustíte skript, symbol **interaktivní** je definována.</span><span class="sxs-lookup"><span data-stu-id="21dad-137">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="21dad-138">Při kompilaci kódu v kompilátoru, symbol **ZKOMPILOVANÉ** je definována.</span><span class="sxs-lookup"><span data-stu-id="21dad-138">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="21dad-139">Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.</span><span class="sxs-lookup"><span data-stu-id="21dad-139">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="21dad-140">Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="21dad-140">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="21dad-141">Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="21dad-141">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="21dad-142">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="21dad-142">Directive</span></span>|<span data-ttu-id="21dad-143">Popis</span><span class="sxs-lookup"><span data-stu-id="21dad-143">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="21dad-144">**#help**</span><span class="sxs-lookup"><span data-stu-id="21dad-144">**#help**</span></span>|<span data-ttu-id="21dad-145">Zobrazí informace o dostupných direktivách.</span><span class="sxs-lookup"><span data-stu-id="21dad-145">Displays information about available directives.</span></span>|
|<span data-ttu-id="21dad-146">**#I**</span><span class="sxs-lookup"><span data-stu-id="21dad-146">**#I**</span></span>|<span data-ttu-id="21dad-147">Určí vyhledávací cestu k sestavení v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="21dad-147">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="21dad-148">**#load**</span><span class="sxs-lookup"><span data-stu-id="21dad-148">**#load**</span></span>|<span data-ttu-id="21dad-149">Přečte zdrojový soubor, zkompiluje jej a spustí.</span><span class="sxs-lookup"><span data-stu-id="21dad-149">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="21dad-150">**#quit**</span><span class="sxs-lookup"><span data-stu-id="21dad-150">**#quit**</span></span>|<span data-ttu-id="21dad-151">Ukončí relaci jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="21dad-151">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="21dad-152">**#r**</span><span class="sxs-lookup"><span data-stu-id="21dad-152">**#r**</span></span>|<span data-ttu-id="21dad-153">Odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="21dad-153">References an assembly.</span></span>|
|<span data-ttu-id="21dad-154">**#time ["na"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="21dad-154">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="21dad-155">Samostatně **#time** přepíná, jestli se má zobrazit informace o výkonu.</span><span class="sxs-lookup"><span data-stu-id="21dad-155">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="21dad-156">Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.</span><span class="sxs-lookup"><span data-stu-id="21dad-156">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="21dad-157">Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál.</span><span class="sxs-lookup"><span data-stu-id="21dad-157">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="21dad-158">Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="21dad-158">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="21dad-159">Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="21dad-159">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="21dad-160">To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="21dad-160">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="21dad-161">Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="21dad-161">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="21dad-162">V kompilovaném režimu použijte **System.Environment.GetCommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="21dad-162">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="21dad-163">Ve skriptech použijte **fsi.CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="21dad-163">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="21dad-164">Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="21dad-164">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="21dad-165">První soubor kódu **MyAssembly.fs**, je kód pro sestavení, na kterou se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="21dad-165">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="21dad-166">Zkompilujte tento soubor s příkazovým řádkem: **fsc - a MyAssembly.fs** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **fsi - exec file1.fsx** testování</span><span class="sxs-lookup"><span data-stu-id="21dad-166">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="21dad-167">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="21dad-167">The output is as follows:</span></span>

```
Command line arguments: 
file1.fsx
test
90
```

## <a name="related-topics"></a><span data-ttu-id="21dad-168">Související témata</span><span class="sxs-lookup"><span data-stu-id="21dad-168">Related Topics</span></span>

|<span data-ttu-id="21dad-169">Název</span><span class="sxs-lookup"><span data-stu-id="21dad-169">Title</span></span>|<span data-ttu-id="21dad-170">Popis</span><span class="sxs-lookup"><span data-stu-id="21dad-170">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="21dad-171">Možnosti F# Interactive</span><span class="sxs-lookup"><span data-stu-id="21dad-171">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="21dad-172">Popisuje syntaxi příkazového řádku a možnosti F# Interactive, fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="21dad-172">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="21dad-173">F#Interaktivní referenční dokumentace knihovny</span><span class="sxs-lookup"><span data-stu-id="21dad-173">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="21dad-174">Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="21dad-174">Describes library functionality available when executing code in F# interactive.</span></span>|
