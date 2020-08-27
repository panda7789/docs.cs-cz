---
title: F# Interactive (dotnet) – referenční informace
description: 'Přečtěte si, jak F# Interactive (dotnet FSI) se používá ke interaktivnímu spouštění kódu F # v konzole nebo ke spouštění skriptů F #.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 760b096c8a3ee0d495b893ab66fa6f9007cdbbf9
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867617"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="09265-103">Interaktivní programování s použitím F\#</span><span class="sxs-lookup"><span data-stu-id="09265-103">Interactive programming with F\#</span></span>

<span data-ttu-id="09265-104">F# Interactive (dotnet FSI) se používá ke interaktivnímu spuštění kódu F # v konzole nebo ke spouštění skriptů F #.</span><span class="sxs-lookup"><span data-stu-id="09265-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="09265-105">Jinými slovy, interaktivní jazyk F# provede operace REPL (čtení, vyhodnocení, smyčka tisku) pro jazyk F#.</span><span class="sxs-lookup"><span data-stu-id="09265-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="09265-106">Chcete-li spustit F# Interactive z konzoly, spusťte příkaz `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="09265-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="09265-107">Najdete ho `dotnet fsi` v libovolné sadě .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="09265-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="09265-108">Informace o dostupných možnostech příkazového řádku naleznete v tématu [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="09265-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="09265-109">Pokud chcete spustit F# Interactive prostřednictvím sady Visual Studio, můžete kliknout na příslušné tlačítko panelu nástrojů s označením **F# Interactive**nebo použít klávesy **CTRL + ALT + F**.</span><span class="sxs-lookup"><span data-stu-id="09265-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="09265-110">Tím otevřete interaktivní okno nástroje, ve kterém běží relace jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="09265-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="09265-111">Můžete také vybrat nějaký kód, který chcete spustit v interaktivním okně, a stisknout kombinaci kláves **ALT + ENTER**.</span><span class="sxs-lookup"><span data-stu-id="09265-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="09265-112">F# Interactive se spustí v okně nástroje s označením **F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="09265-112">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="09265-113">Použijete-li tuto kombinaci kláves, ujistěte se, že má okno editoru fokus.</span><span class="sxs-lookup"><span data-stu-id="09265-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="09265-114">Pokud používáte konzolu nebo sadu Visual Studio, zobrazí se příkazový řádek a překladač čeká na zadání.</span><span class="sxs-lookup"><span data-stu-id="09265-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="09265-115">Zde je možné zadat kód stejně jako v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="09265-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="09265-116">Chcete-li zkompilovat a spustit kód, zadejte dvě středníky (**;;**) pro ukončení řádku nebo několika řádků vstupu.</span><span class="sxs-lookup"><span data-stu-id="09265-116">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="09265-117">Jazyk F# Interactive se pokusí zkompilovat kód a v případě úspěchu kód spustí a vytiskne podpis zkompilovaných typů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="09265-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="09265-118">Pokud dojde k chybám, překladač vytiskne chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="09265-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="09265-119">Kód zadaný ve stejné relaci má přístup k libovolné konstrukci zadané dříve, takže lze sestavit programy.</span><span class="sxs-lookup"><span data-stu-id="09265-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="09265-120">Rozsáhlá vyrovnávací paměť okna nástroje umožňuje v případě potřeby zkopírovat kód do souboru.</span><span class="sxs-lookup"><span data-stu-id="09265-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="09265-121">Při spuštění v sadě Visual Studio se jazyk F# Interactive spustí nezávisle na projektu, tedy například nelze použít konstrukce definované v projektu v jazyce F# Interactive, pokud nezkopírujete kód této funkce do interaktivního okna.</span><span class="sxs-lookup"><span data-stu-id="09265-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="09265-122">Pokud máte otevřený projekt, který odkazuje na některé knihovny, můžete na ně odkazovat pomocí **Průzkumník řešení**F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="09265-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="09265-123">Chcete-li odkazovat na knihovnu v F# Interactive, rozbalte uzel **odkazy** , otevřete místní nabídku knihovny a vyberte možnost **Odeslat do F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="09265-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="09265-124">Argumenty příkazového řádku (možnosti) jazyka F# Interactive lze řídit úpravou nastavení.</span><span class="sxs-lookup"><span data-stu-id="09265-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="09265-125">V nabídce **nástroje** vyberte **Možnosti...** a potom rozbalte **Nástroje jazyka F #**.</span><span class="sxs-lookup"><span data-stu-id="09265-125">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="09265-126">Dvě nastavení, která můžete změnit, jsou možnosti F# Interactive a nastavení **64 F# Interactive** , které je relevantní pouze v případě, že používáte F# Interactive na 64 počítači.</span><span class="sxs-lookup"><span data-stu-id="09265-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="09265-127">Toto nastavení určuje, zda chcete spustit vyhrazenou 64bitovou verzi programu fsi.exe nebo fsianycpu.exe, který pomocí architektury počítače určí, zda se má spustit jako 32bitový nebo 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="09265-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="09265-128">Skriptování s F\#</span><span class="sxs-lookup"><span data-stu-id="09265-128">Scripting with F\#</span></span>

<span data-ttu-id="09265-129">Skripty používají příponu souboru **. fsx** nebo **. fsscript**.</span><span class="sxs-lookup"><span data-stu-id="09265-129">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="09265-130">Namísto kompilování zdrojového kódu a pozdějšího spuštění zkompilovaného sestavení můžete pouze spustit **dotnet FSI** a zadat název souboru skriptu zdrojového kódu f # a jazyk f # Interactive přečte kód a provede jej v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="09265-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="09265-131">Rozdíly mezi interaktivním, skriptovacím a zkompilovaným prostředím</span><span class="sxs-lookup"><span data-stu-id="09265-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="09265-132">Pokud kompilujete kód v F# Interactive bez ohledu na to, jestli používáte interaktivně nebo spuštěný skript, je definovaný symbol **Interactive** .</span><span class="sxs-lookup"><span data-stu-id="09265-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="09265-133">Při kompilování kódu v kompilátoru je definován symbol **kompilovaný** .</span><span class="sxs-lookup"><span data-stu-id="09265-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="09265-134">Pokud tedy kód potřebujete v kompilovaném a interaktivním režimu odlišit, lze pomocí direktivy preprocesoru podmíněné kompilace určit, který kód chcete použít.</span><span class="sxs-lookup"><span data-stu-id="09265-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="09265-135">Některé direktivy, které jsou k dispozici při spuštění skriptů v jazyce F# Interactive, nejsou k dispozici, pokud jsou spuštěny kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="09265-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="09265-136">Následující tabulka uvádí direktivy, které jsou k dispozici při použití jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="09265-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="09265-137">Směrnici</span><span class="sxs-lookup"><span data-stu-id="09265-137">Directive</span></span>|<span data-ttu-id="09265-138">Popis</span><span class="sxs-lookup"><span data-stu-id="09265-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="09265-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="09265-139">**#help**</span></span>|<span data-ttu-id="09265-140">Zobrazí informace o dostupných direktivách.</span><span class="sxs-lookup"><span data-stu-id="09265-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="09265-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="09265-141">**#I**</span></span>|<span data-ttu-id="09265-142">Určí vyhledávací cestu k sestavení v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="09265-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="09265-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="09265-143">**#load**</span></span>|<span data-ttu-id="09265-144">Přečte zdrojový soubor, zkompiluje jej a spustí.</span><span class="sxs-lookup"><span data-stu-id="09265-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="09265-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="09265-145">**#quit**</span></span>|<span data-ttu-id="09265-146">Ukončí relaci jazyka F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="09265-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="09265-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="09265-147">**#r**</span></span>|<span data-ttu-id="09265-148">Odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="09265-148">References an assembly.</span></span>|
|<span data-ttu-id="09265-149">**#time ["on" &#124; "]**</span><span class="sxs-lookup"><span data-stu-id="09265-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="09265-150">**#Time** sám o sobě přepíná, zda se mají zobrazovat informace o výkonu.</span><span class="sxs-lookup"><span data-stu-id="09265-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="09265-151">Pokud je povolena, jazyk F# Interactive měří reálný čas, čas procesoru a informace uvolňování paměti pro každou část kódu, která je interpretována a spuštěna.</span><span class="sxs-lookup"><span data-stu-id="09265-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="09265-152">Pokud v jazyce F# Interactive určíte soubory nebo cesty, očekává se textový literál.</span><span class="sxs-lookup"><span data-stu-id="09265-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="09265-153">Proto musí být soubory a cesty v uvozovkách a musí být použity obvyklé řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="09265-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="09265-154">Lze také použít znak @, který způsobí, že jazyk F# Interactive interpretuje řetězec obsahující cestu jako doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="09265-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="09265-155">To způsobí, že jazyk F# Interactive ignoruje jakékoli řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="09265-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="09265-156">Jedním z rozdílů mezi kompilovaným a interaktivním režimem je způsob přístupu k argumentům příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="09265-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="09265-157">V kompilovaném režimu použijte **System. Environment. GetCommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="09265-157">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="09265-158">Ve skriptech použijte **FSI. CommandLineArgs –**.</span><span class="sxs-lookup"><span data-stu-id="09265-158">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="09265-159">Následující kód ukazuje, jak vytvořit funkci, která čte argumenty příkazového řádku ve skriptu, a také ukazuje, jak ze skriptu odkazovat na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="09265-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="09265-160">První soubor kódu, **MyAssembly. FS**, je kód pro odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="09265-160">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="09265-161">Zkompilujte tento soubor pomocí příkazového řádku: **FSC-a MyAssembly. FS** a potom spusťte druhý soubor jako skript s příkazovým řádkem: **FSI--exec Soubor1. fsx** test</span><span class="sxs-lookup"><span data-stu-id="09265-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

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

<span data-ttu-id="09265-162">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="09265-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="09265-163">Správa balíčků v F# Interactive</span><span class="sxs-lookup"><span data-stu-id="09265-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="09265-164">Správa balíčků je k dispozici jako funkce ve verzi Preview ve verzích `dotnet fsi` dodaných v sadě .NET SDK a v vyšších verzích sady .NET SDK a `3.1.300` také ve všech `5.*` verzích sady .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="09265-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="09265-165">Pokud ho chcete v této verzi Preview povolit, spusťte `dotnet fsi` s `--langversion:preview` argumentem.</span><span class="sxs-lookup"><span data-stu-id="09265-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="09265-166">Syntaxi pro odkazování na `#r` knihovnu DLL v F# Interactive lze také použít pro odkazování na balíček NuGet pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="09265-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>
```

<span data-ttu-id="09265-167">Například pro odkazování na `FSharp.Data` balíček použijte následující `#r` odkaz:</span><span class="sxs-lookup"><span data-stu-id="09265-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="09265-168">Po spuštění tohoto řádku se do `FSharp.Data` mezipaměti NuGet stáhne nejnovější verze balíčku, na kterou se odkazuje v aktuální F# Interactive relaci.</span><span class="sxs-lookup"><span data-stu-id="09265-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="09265-169">Kromě názvu balíčku lze na konkrétní verze balíčku odkazovat pomocí krátké syntaxe:</span><span class="sxs-lookup"><span data-stu-id="09265-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="09265-170">nebo podrobnějším způsobem:</span><span class="sxs-lookup"><span data-stu-id="09265-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="09265-171">Související články</span><span class="sxs-lookup"><span data-stu-id="09265-171">Related articles</span></span>

|<span data-ttu-id="09265-172">Nadpis</span><span class="sxs-lookup"><span data-stu-id="09265-172">Title</span></span>|<span data-ttu-id="09265-173">Popis</span><span class="sxs-lookup"><span data-stu-id="09265-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="09265-174">Interaktivní možnosti F#</span><span class="sxs-lookup"><span data-stu-id="09265-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="09265-175">Popisuje syntaxi a možnosti příkazového řádku pro F# Interactive fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="09265-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="09265-176">Odkaz na knihovnu F# Interactive</span><span class="sxs-lookup"><span data-stu-id="09265-176">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="09265-177">Popisuje funkce knihovny, které jsou k dispozici při spuštění kódu v jazyce F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="09265-177">Describes library functionality available when executing code in F# interactive.</span></span>|
