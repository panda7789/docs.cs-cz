---
title: Interaktivní možnosti
description: Přečtěte si o možnostech příkazového řádku, které podporuje F# Interactive, fsi.exe.
ms.date: 08/15/2020
ms.openlocfilehash: da2251c1d2e57090ed926e501cebf3c53ac58052
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558605"
---
# <a name="f-interactive-options"></a><span data-ttu-id="a8996-103">Možnosti F# Interactive</span><span class="sxs-lookup"><span data-stu-id="a8996-103">F# Interactive options</span></span>

<span data-ttu-id="a8996-104">Tento článek popisuje možnosti příkazového řádku, které podporuje F# Interactive, `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="a8996-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="a8996-105">F# Interactive přijímá mnoho ze stejných možností příkazového řádku jako kompilátor F #, ale také přijímá některé další možnosti.</span><span class="sxs-lookup"><span data-stu-id="a8996-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="a8996-106">Použití F# Interactive pro skriptování</span><span class="sxs-lookup"><span data-stu-id="a8996-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="a8996-107">F# Interactive, `dotnet fsi` , lze spustit interaktivně nebo je lze spustit z příkazového řádku pro spuštění skriptu.</span><span class="sxs-lookup"><span data-stu-id="a8996-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="a8996-108">Syntaxe příkazového řádku je</span><span class="sxs-lookup"><span data-stu-id="a8996-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="a8996-109">Přípona souboru pro soubory skriptu F # je `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="a8996-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="a8996-110">Tabulka možností F# Interactive</span><span class="sxs-lookup"><span data-stu-id="a8996-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="a8996-111">Následující tabulka shrnuje možnosti podporované nástrojem F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="a8996-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="a8996-112">Tyto možnosti lze nastavit na příkazovém řádku nebo v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8996-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="a8996-113">Chcete-li nastavit tyto možnosti v integrovaném vývojovém prostředí sady Visual Studio, otevřete nabídku **nástroje** , vyberte možnost **Možnosti**, rozbalte uzel **nástroje F #** a vyberte možnost **F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="a8996-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="a8996-114">Kde se zobrazí seznamy v argumentech možností F# Interactive, prvky seznamu jsou odděleny středníky ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="a8996-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="a8996-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="a8996-115">Option</span></span>|<span data-ttu-id="a8996-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a8996-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="a8996-117">Slouží k pokynu F# Interactive, aby považovala zbývající argumenty za argumenty příkazového řádku pro program nebo skript jazyka F #, ke kterému můžete přistupovat v kódu pomocí seznamu **FSI. CommandLineArgs –**.</span><span class="sxs-lookup"><span data-stu-id="a8996-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="a8996-118">**--zaškrtnuto**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-119">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-120">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-121">**--codepage: &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="a8996-122">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-123">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-125">Vypíše upozornění a chybové zprávy barevně.</span><span class="sxs-lookup"><span data-stu-id="a8996-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="a8996-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-127">Povolí nebo zakáže optimalizace mezi moduly.</span><span class="sxs-lookup"><span data-stu-id="a8996-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="a8996-128">**--Debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="a8996-129">**--debug:**[**full**&#124;**pdbonly**&#124;**přenosných**&#124;**vložených**]</span><span class="sxs-lookup"><span data-stu-id="a8996-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="a8996-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="a8996-131">**-g:**[**full**&#124;**pdbonly**&#124;**přenosných**&#124;**vložených**]</span><span class="sxs-lookup"><span data-stu-id="a8996-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="a8996-132">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-133">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-134">**--define: &lt; String&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="a8996-135">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-136">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-137">**--deterministické**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-138">Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka).</span><span class="sxs-lookup"><span data-stu-id="a8996-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="a8996-139">**--Exec**</span><span class="sxs-lookup"><span data-stu-id="a8996-139">**--exec**</span></span>|<span data-ttu-id="a8996-140">Instruuje F # Interactive, aby se ukončil po načtení souborů nebo spuštění souboru skriptu zadaného na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a8996-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="a8996-141">**--fullpaths –**</span><span class="sxs-lookup"><span data-stu-id="a8996-141">**--fullpaths**</span></span>|<span data-ttu-id="a8996-142">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-143">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-145">Povolí nebo zakáže smyčku události model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8996-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="a8996-146">Výchozí hodnota je povolena.</span><span class="sxs-lookup"><span data-stu-id="a8996-146">The default is enabled.</span></span>|
|<span data-ttu-id="a8996-147">**--Help**</span><span class="sxs-lookup"><span data-stu-id="a8996-147">**--help**</span></span><br /><br /><span data-ttu-id="a8996-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="a8996-148">**-?**</span></span>|<span data-ttu-id="a8996-149">Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.</span><span class="sxs-lookup"><span data-stu-id="a8996-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="a8996-150">**--lib: &lt; Folder-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="a8996-151">**-I: &lt; seznam složek&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="a8996-152">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-153">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-154">**--Load: &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="a8996-155">Zkompiluje daný zdrojový kód při spuštění a načte zkompilované konstrukce F # do relace.</span><span class="sxs-lookup"><span data-stu-id="a8996-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="a8996-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="a8996-156">**--mlcompatibility**</span></span>|<span data-ttu-id="a8996-157">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-158">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-159">**--nerozhraní**</span><span class="sxs-lookup"><span data-stu-id="a8996-159">**--noframework**</span></span>|<span data-ttu-id="a8996-160">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-161">Další informace najdete v tématu [Možnosti kompilátoru](compiler-options.md) .</span><span class="sxs-lookup"><span data-stu-id="a8996-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="a8996-162">**--logo**</span><span class="sxs-lookup"><span data-stu-id="a8996-162">**--nologo**</span></span>|<span data-ttu-id="a8996-163">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-164">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-165">**--upozornit: &lt; Upozornění – seznam&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="a8996-166">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-167">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-168">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-169">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-170">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-171">**--preferreduilang –: &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="a8996-172">Určuje preferovaný název jazykové verze jazyka (například ES-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="a8996-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="a8996-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="a8996-173">**--quiet**</span></span>|<span data-ttu-id="a8996-174">Potlačí výstup F# Interactive do datového proudu **stdout** .</span><span class="sxs-lookup"><span data-stu-id="a8996-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="a8996-175">**--quotes – ladění**</span><span class="sxs-lookup"><span data-stu-id="a8996-175">**--quotations-debug**</span></span>|<span data-ttu-id="a8996-176">Určuje, že se mají vygenerovat dodatečné informace o ladění pro výrazy, které jsou odvozeny z literálů uvozovek F # a reflektované definice.</span><span class="sxs-lookup"><span data-stu-id="a8996-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="a8996-177">Informace o ladění jsou přidány do vlastních atributů uzlu stromu výrazu F #.</span><span class="sxs-lookup"><span data-stu-id="a8996-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="a8996-178">Viz [citace kódu](code-quotations.md) a [expr. CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="a8996-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="a8996-179">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-180">Povolí nebo zakáže dokončování tabulátorů v interaktivním režimu.</span><span class="sxs-lookup"><span data-stu-id="a8996-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="a8996-181">**--Reference: &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="a8996-182">**-r: &lt; název souboru&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="a8996-183">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-184">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-185">**--volání funkce tail**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-186">Povolí nebo zakáže použití instrukcí Tail IL, což způsobí, že se rámec zásobníku znovu použije pro rekurzivní funkce tail.</span><span class="sxs-lookup"><span data-stu-id="a8996-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="a8996-187">Tato možnost je ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="a8996-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="a8996-188">**--targetprofile: &lt; String&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="a8996-189">Určuje profil cílového rozhraní tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8996-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="a8996-190">Platné hodnoty jsou `mscorlib` , `netcore` nebo `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="a8996-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="a8996-191">Výchozí formát je `mscorlib`.</span><span class="sxs-lookup"><span data-stu-id="a8996-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="a8996-192">**--použít: &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="a8996-193">Říká Překladači použití daného souboru při spuštění jako počáteční vstup.</span><span class="sxs-lookup"><span data-stu-id="a8996-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="a8996-194">**--Utf8Output –**</span><span class="sxs-lookup"><span data-stu-id="a8996-194">**--utf8output**</span></span>|<span data-ttu-id="a8996-195">Stejné jako možnost kompilátoru fsc.exe.</span><span class="sxs-lookup"><span data-stu-id="a8996-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="a8996-196">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-197">**--Warn: &lt; úroveň upozornění&gt;**</span><span class="sxs-lookup"><span data-stu-id="a8996-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="a8996-198">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-199">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-200">**--warnaserror –**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="a8996-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="a8996-201">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-202">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="a8996-203">**--warnaserror –**[ **+**&#124;**-** ]:\*\* &lt; int-list &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="a8996-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="a8996-204">Stejné jako možnost kompilátoru **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="a8996-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="a8996-205">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="a8996-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="a8996-206">F# Interactive strukturovaný tisk</span><span class="sxs-lookup"><span data-stu-id="a8996-206">F# Interactive structured printing</span></span>

<span data-ttu-id="a8996-207">F# Interactive ( `dotnet fsi` ) používá rozšířenou verzi [strukturovaného formátování prostého textu](plaintext-formatting.md) k sestavování hodnot.</span><span class="sxs-lookup"><span data-stu-id="a8996-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="a8996-208">Podporují se všechny funkce `%A` formátování prostého textu a některé jsou navíc přizpůsobitelné.</span><span class="sxs-lookup"><span data-stu-id="a8996-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="a8996-209">Tisk je barevný, pokud konzola výstupu podporuje barvy.</span><span class="sxs-lookup"><span data-stu-id="a8996-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="a8996-210">Limit je umístěn na délku zobrazených řetězců, pokud tento řetězec výslovně nevyhodnocujete.</span><span class="sxs-lookup"><span data-stu-id="a8996-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="a8996-211">Sada uživatelsky definovaných nastavení je k dispozici prostřednictvím `fsi` objektu.</span><span class="sxs-lookup"><span data-stu-id="a8996-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="a8996-212">Dostupná nastavení pro přizpůsobení formátu prostého textu pro hlášené hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a8996-212">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="a8996-213">Přizpůsobení pomocí `AddPrinter` a `AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="a8996-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="a8996-214">Tisk v F# Interactive výstupech lze přizpůsobit pomocí `fsi.AddPrinter` a `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="a8996-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="a8996-215">První funkce poskytuje text, který nahradí tisk objektu.</span><span class="sxs-lookup"><span data-stu-id="a8996-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="a8996-216">Druhá funkce vrátí náhradní objekt, který se zobrazí místo toho.</span><span class="sxs-lookup"><span data-stu-id="a8996-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="a8996-217">Zvažte například následující kód F #:</span><span class="sxs-lookup"><span data-stu-id="a8996-217">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="a8996-218">Pokud spustíte příklad v F# Interactive, vypíše se výstup na základě sady možností formátování.</span><span class="sxs-lookup"><span data-stu-id="a8996-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="a8996-219">V takovém případě má vliv na formátování data a času:</span><span class="sxs-lookup"><span data-stu-id="a8996-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="a8996-220">`fsi.AddPrintTransformer` dá se použít k poskytnutí náhradního objektu pro tisk:</span><span class="sxs-lookup"><span data-stu-id="a8996-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="a8996-221">Tyto výstupy:</span><span class="sxs-lookup"><span data-stu-id="a8996-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="a8996-222">Pokud předaná funkce Transformer předává `fsi.AddPrintTransformer` zpět `null` , je transformátor tisku ignorován.</span><span class="sxs-lookup"><span data-stu-id="a8996-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="a8996-223">To lze použít k filtrování libovolné vstupní hodnoty, a to od typu `obj` .</span><span class="sxs-lookup"><span data-stu-id="a8996-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="a8996-224">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a8996-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="a8996-225">Tyto výstupy:</span><span class="sxs-lookup"><span data-stu-id="a8996-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="a8996-226">Související témata</span><span class="sxs-lookup"><span data-stu-id="a8996-226">Related topics</span></span>

|<span data-ttu-id="a8996-227">Nadpis</span><span class="sxs-lookup"><span data-stu-id="a8996-227">Title</span></span>|<span data-ttu-id="a8996-228">Popis</span><span class="sxs-lookup"><span data-stu-id="a8996-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="a8996-229">Možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="a8996-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="a8996-230">Popisuje možnosti příkazového řádku, které jsou k dispozici pro kompilátor jazyka F # **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="a8996-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
