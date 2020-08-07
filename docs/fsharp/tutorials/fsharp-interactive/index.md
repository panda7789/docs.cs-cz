---
title: Interaktivní referenční dokumentace F# (fsi.exe)
description: 'Přečtěte si, jak se F# Interactive (fsi.exe) používá ke interaktivnímu spouštění kódu F # v konzole nebo ke spouštění skriptů F #.'
ms.date: 05/16/2016
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 8bb1563ad34e65101fb9f09d6e347278e4b0de78
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854942"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="53600-103">Interaktivní programování s použitím F\#</span><span class="sxs-lookup"><span data-stu-id="53600-103">Interactive programming with F\#</span></span>

> [!NOTE]
> <span data-ttu-id="53600-104">V tomto článku se aktuálně popisuje prostředí jenom pro Windows.</span><span class="sxs-lookup"><span data-stu-id="53600-104">This article currently describes the experience for Windows only.</span></span>

<span data-ttu-id="53600-105">Program F# Interactive (fsi.exe) se používá pro interaktivní spuštění kódu jazyka F# v konzole nebo pro spuštění skriptů jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="53600-105">F# Interactive (fsi.exe) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="53600-106">Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.</span><span class="sxs-lookup"><span data-stu-id="53600-106">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="53600-107">Chcete-li spustit jazyk F# Interactive z konzoly, spusťte program fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="53600-107">To run F# Interactive from the console, run fsi.exe.</span></span> <span data-ttu-id="53600-108">Najdete fsi.exe v:</span><span class="sxs-lookup"><span data-stu-id="53600-108">You will find fsi.exe in:</span></span>

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

<span data-ttu-id="53600-109">kde `sku` je buď `Community` , `Professional` nebo `Enterprise` .</span><span class="sxs-lookup"><span data-stu-id="53600-109">where `sku` is either `Community`, `Professional`, or `Enterprise`.</span></span>

<span data-ttu-id="53600-110">Informace o dostupných možnostech příkazového řádku naleznete v tématu [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="53600-110">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="53600-111">Pokud chcete spustit F# Interactive prostřednictvím sady Visual Studio, můžete kliknout na příslušné tlačítko panelu nástrojů s označením **F# Interactive**nebo použít klávesy **CTRL + ALT + F**.</span><span class="sxs-lookup"><span data-stu-id="53600-111">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="53600-112">Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="53600-112">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="53600-113">Můžete také vybrat nějaký kód, který chcete spustit v interaktivním okně, a stisknout kombinaci kláves **ALT + ENTER**.</span><span class="sxs-lookup"><span data-stu-id="53600-113">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="53600-114">F# Interactive se spustí v okně nástroje s označením **F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="53600-114">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="53600-115">Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.</span><span class="sxs-lookup"><span data-stu-id="53600-115">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="53600-116">Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání.</span><span class="sxs-lookup"><span data-stu-id="53600-116">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="53600-117">Zde je možné zadat kód stejně jako v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="53600-117">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="53600-118">Chcete-li zkompilovat a spustit kód, zadejte dvě středníky (**;;**) pro ukončení řádku nebo několika řádků vstupu.</span><span class="sxs-lookup"><span data-stu-id="53600-118">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="53600-119">Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="53600-119">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="53600-120">Pokud dojde k chybám, překladač vytiskne chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="53600-120">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="53600-121">Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy.</span><span class="sxs-lookup"><span data-stu-id="53600-121">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="53600-122">Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.</span><span class="sxs-lookup"><span data-stu-id="53600-122">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="53600-123">Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.</span><span class="sxs-lookup"><span data-stu-id="53600-123">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="53600-124">Pokud máte otevřený projekt, který odkazuje na některé knihovny, můžete na ně odkazovat pomocí **Průzkumník řešení**F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="53600-124">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="53600-125">Chcete-li odkazovat na knihovnu v F# Interactive, rozbalte uzel **odkazy** , otevřete místní nabídku knihovny a vyberte možnost **Odeslat do F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="53600-125">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="53600-126">Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení.</span><span class="sxs-lookup"><span data-stu-id="53600-126">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="53600-127">V nabídce **nástroje** vyberte **Možnosti...** a potom rozbalte **Nástroje jazyka F #**.</span><span class="sxs-lookup"><span data-stu-id="53600-127">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="53600-128">Dvě nastavení, která můžete změnit, jsou možnosti F# Interactive a nastavení **64 F# Interactive** , které je relevantní pouze v případě, že používáte F# Interactive na 64 počítači.</span><span class="sxs-lookup"><span data-stu-id="53600-128">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="53600-129">Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="53600-129">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="53600-130">Skriptování s F\#</span><span class="sxs-lookup"><span data-stu-id="53600-130">Scripting with F\#</span></span>

<span data-ttu-id="53600-131">Skripty používají příponu souboru **. fsx** nebo **. fsscript**.</span><span class="sxs-lookup"><span data-stu-id="53600-131">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="53600-132">Namísto kompilování zdrojového kódu a pozdějšího spuštění zkompilovaného sestavení můžete pouze spustit **fsi.exe** a zadat název souboru skriptu zdrojového kódu f # a f # Interactive přečte kód a provede ho v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="53600-132">Instead of compiling source code and then later running the compiled assembly, you can just run **fsi.exe** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="53600-133">Rozdíly mezi interaktivním, skriptovacím a zkompilovaným prostředím</span><span class="sxs-lookup"><span data-stu-id="53600-133">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="53600-134">Pokud kompilujete kód v F# Interactive bez ohledu na to, jestli používáte interaktivně nebo spuštěný skript, je definovaný symbol **Interactive** .</span><span class="sxs-lookup"><span data-stu-id="53600-134">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="53600-135">Při kompilování kódu v kompilátoru je definován symbol **kompilovaný** .</span><span class="sxs-lookup"><span data-stu-id="53600-135">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="53600-136">Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.</span><span class="sxs-lookup"><span data-stu-id="53600-136">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="53600-137">Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="53600-137">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="53600-138">Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="53600-138">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="53600-139">Směrnici</span><span class="sxs-lookup"><span data-stu-id="53600-139">Directive</span></span>|<span data-ttu-id="53600-140">Popis</span><span class="sxs-lookup"><span data-stu-id="53600-140">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="53600-141">**#help**</span><span class="sxs-lookup"><span data-stu-id="53600-141">**#help**</span></span>|<span data-ttu-id="53600-142">Zobrazí informace o dostupných direktivách.</span><span class="sxs-lookup"><span data-stu-id="53600-142">Displays information about available directives.</span></span>|
|<span data-ttu-id="53600-143">**#I**</span><span class="sxs-lookup"><span data-stu-id="53600-143">**#I**</span></span>|<span data-ttu-id="53600-144">Určí vyhledávací cestu k sestavení v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="53600-144">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="53600-145">**#load**</span><span class="sxs-lookup"><span data-stu-id="53600-145">**#load**</span></span>|<span data-ttu-id="53600-146">Přečte zdrojový soubor, zkompiluje jej a spustí.</span><span class="sxs-lookup"><span data-stu-id="53600-146">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="53600-147">**#quit**</span><span class="sxs-lookup"><span data-stu-id="53600-147">**#quit**</span></span>|<span data-ttu-id="53600-148">Ukončí relaci jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="53600-148">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="53600-149">**#r**</span><span class="sxs-lookup"><span data-stu-id="53600-149">**#r**</span></span>|<span data-ttu-id="53600-150">Odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="53600-150">References an assembly.</span></span>|
|<span data-ttu-id="53600-151">**#time ["on" &#124; "]**</span><span class="sxs-lookup"><span data-stu-id="53600-151">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="53600-152">**#Time** sám o sobě přepíná, zda se mají zobrazovat informace o výkonu.</span><span class="sxs-lookup"><span data-stu-id="53600-152">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="53600-153">Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.</span><span class="sxs-lookup"><span data-stu-id="53600-153">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="53600-154">Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál.</span><span class="sxs-lookup"><span data-stu-id="53600-154">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="53600-155">Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="53600-155">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="53600-156">Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="53600-156">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="53600-157">To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="53600-157">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="53600-158">Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="53600-158">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="53600-159">V kompilovaném režimu použijte **System. Environment. GetCommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="53600-159">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="53600-160">Ve skriptech použijte **FSI. CommandLineArgs –**.</span><span class="sxs-lookup"><span data-stu-id="53600-160">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="53600-161">Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="53600-161">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="53600-162">První soubor kódu, **MyAssembly. FS**, je kód pro odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="53600-162">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="53600-163">Zkompilujte tento soubor pomocí příkazového řádku: **FSC-a MyAssembly. FS** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **FSI--exec Soubor1. fsx** test</span><span class="sxs-lookup"><span data-stu-id="53600-163">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

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

<span data-ttu-id="53600-164">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="53600-164">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-articles"></a><span data-ttu-id="53600-165">Související články</span><span class="sxs-lookup"><span data-stu-id="53600-165">Related articles</span></span>

|<span data-ttu-id="53600-166">Nadpis</span><span class="sxs-lookup"><span data-stu-id="53600-166">Title</span></span>|<span data-ttu-id="53600-167">Popis</span><span class="sxs-lookup"><span data-stu-id="53600-167">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="53600-168">Možnosti F# Interactive</span><span class="sxs-lookup"><span data-stu-id="53600-168">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="53600-169">Popisuje syntaxi a možnosti příkazového řádku pro F# Interactive fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="53600-169">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="53600-170">Odkaz na knihovnu F# Interactive</span><span class="sxs-lookup"><span data-stu-id="53600-170">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="53600-171">Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="53600-171">Describes library functionality available when executing code in F# interactive.</span></span>|
