---
title: Ilasm.exe (IL Assembler)
description: Začínáme s Ilasm.exe, assemblerem IL. Tento nástroj generuje přenosný spustitelný soubor (PE) z mezilehlého jazyka (IL).
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166977"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="a1e48-104">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="a1e48-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="a1e48-105">Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a1e48-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="a1e48-106">(Další informace o IL najdete v tématu [spravovaný proces spuštění](../../standard/managed-execution-process.md).) Můžete spustit výsledný spustitelný soubor, který obsahuje IL a požadovaná metadata, abyste zjistili, jestli IL funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a1e48-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="a1e48-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1e48-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a1e48-108">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a1e48-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a1e48-109">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a1e48-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="a1e48-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="a1e48-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="a1e48-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1e48-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="a1e48-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1e48-112">Parameters</span></span>

| <span data-ttu-id="a1e48-113">Argument</span><span class="sxs-lookup"><span data-stu-id="a1e48-113">Argument</span></span> | <span data-ttu-id="a1e48-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e48-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="a1e48-115">Název zdrojového souboru .il.</span><span class="sxs-lookup"><span data-stu-id="a1e48-115">The name of the .il source file.</span></span> <span data-ttu-id="a1e48-116">Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL.</span><span class="sxs-lookup"><span data-stu-id="a1e48-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="a1e48-117">K vytvoření jednoho souboru PE s *Ilasm.exe*lze zadat více argumentů zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="a1e48-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="a1e48-118">**Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru. Il má buď koncovou mezeru, nebo znak konce řádku.</span><span class="sxs-lookup"><span data-stu-id="a1e48-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="a1e48-119">Možnost</span><span class="sxs-lookup"><span data-stu-id="a1e48-119">Option</span></span> | <span data-ttu-id="a1e48-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e48-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="a1e48-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="a1e48-121">**/32bitpreferred**</span></span>|<span data-ttu-id="a1e48-122">Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).</span><span class="sxs-lookup"><span data-stu-id="a1e48-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="a1e48-123">**/alignment:**`integer`</span><span class="sxs-lookup"><span data-stu-id="a1e48-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="a1e48-124">Nastaví zarovnání souborů na hodnotu zadanou `integer` v volitelné HLAVIČCE NT.</span><span class="sxs-lookup"><span data-stu-id="a1e48-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a1e48-125">Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="a1e48-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="a1e48-126">**/AppContainer**</span><span class="sxs-lookup"><span data-stu-id="a1e48-126">**/appcontainer**</span></span>|<span data-ttu-id="a1e48-127">Vytvoří soubor *. dll* nebo *. exe* , který je spuštěn v kontejneru aplikace systému Windows, jako výstup.</span><span class="sxs-lookup"><span data-stu-id="a1e48-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="a1e48-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="a1e48-128">**/arm**</span></span>|<span data-ttu-id="a1e48-129">Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="a1e48-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="a1e48-130">Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="a1e48-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="a1e48-131">**/Base:**`integer`</span><span class="sxs-lookup"><span data-stu-id="a1e48-131">**/base:** `integer`</span></span>|<span data-ttu-id="a1e48-132">Nastaví ImageBase na hodnotu zadanou `integer` v volitelné HLAVIČCE NT.</span><span class="sxs-lookup"><span data-stu-id="a1e48-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a1e48-133">Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="a1e48-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="a1e48-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="a1e48-134">**/clock**</span></span>|<span data-ttu-id="a1e48-135">Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:</span><span class="sxs-lookup"><span data-stu-id="a1e48-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="a1e48-136">**Celková doba spuštění**: celkový čas strávený prováděním všech konkrétních operací, které následují.</span><span class="sxs-lookup"><span data-stu-id="a1e48-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="a1e48-137">**Po spuštění**: načítání a otevírání souboru.</span><span class="sxs-lookup"><span data-stu-id="a1e48-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="a1e48-138">**Generování MD**: generování metadat</span><span class="sxs-lookup"><span data-stu-id="a1e48-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="a1e48-139">**Odkaz na def rozlišení**: řešení odkazů na definice v souboru.</span><span class="sxs-lookup"><span data-stu-id="a1e48-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="a1e48-140">**CEE generace souborů**: generování image souboru v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1e48-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="a1e48-141">**Zápis do souboru PE**: zápis image do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="a1e48-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="a1e48-142">**/Debug**[:**impl**&#124;**opt**]</span><span class="sxs-lookup"><span data-stu-id="a1e48-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="a1e48-143">Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků).</span><span class="sxs-lookup"><span data-stu-id="a1e48-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="a1e48-144">Vytvoří soubor PDB.</span><span class="sxs-lookup"><span data-stu-id="a1e48-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="a1e48-145">**/Debug** bez další hodnoty ZAKÁŽE optimalizaci JIT a použije body sekvence ze souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="a1e48-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="a1e48-146">**Impl** ZAKÁŽE optimalizaci JIT a použije implicitní body sekvence.</span><span class="sxs-lookup"><span data-stu-id="a1e48-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="a1e48-147">Možnost **opt** POVOLÍ optimalizaci JIT a použije implicitní body sekvence.</span><span class="sxs-lookup"><span data-stu-id="a1e48-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="a1e48-148">**/DLL**</span><span class="sxs-lookup"><span data-stu-id="a1e48-148">**/dll**</span></span>|<span data-ttu-id="a1e48-149">Vytvoří jako výstup soubor *. dll* .</span><span class="sxs-lookup"><span data-stu-id="a1e48-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="a1e48-150">**/ENC:**`file`</span><span class="sxs-lookup"><span data-stu-id="a1e48-150">**/enc:** `file`</span></span>|<span data-ttu-id="a1e48-151">Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="a1e48-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="a1e48-152">Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.</span><span class="sxs-lookup"><span data-stu-id="a1e48-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="a1e48-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="a1e48-153">**/exe**</span></span>|<span data-ttu-id="a1e48-154">Vytvoří jako výstup spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="a1e48-154">Produces an executable file as output.</span></span> <span data-ttu-id="a1e48-155">Tato možnost je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a1e48-155">This is the default.</span></span>|
|<span data-ttu-id="a1e48-156">**/Flags:**`integer`</span><span class="sxs-lookup"><span data-stu-id="a1e48-156">**/flags:** `integer`</span></span>|<span data-ttu-id="a1e48-157">Nastaví ImageFlags na hodnotu zadanou `integer` v hlavičce společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a1e48-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="a1e48-158">Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="a1e48-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="a1e48-159">Seznam platných hodnot pro *celé číslo*naleznete v tématu corhdr. h COMIMAGE_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="a1e48-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="a1e48-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="a1e48-160">**/fold**</span></span>|<span data-ttu-id="a1e48-161">Sloučí identická těla metod do jednoho.</span><span class="sxs-lookup"><span data-stu-id="a1e48-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="a1e48-162">/**HIGHENTROPYVA**</span><span class="sxs-lookup"><span data-stu-id="a1e48-162">/**highentropyva**</span></span>|<span data-ttu-id="a1e48-163">Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="a1e48-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="a1e48-164">(Výchozí pro **/AppContainer**.)</span><span class="sxs-lookup"><span data-stu-id="a1e48-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="a1e48-165">**/include:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="a1e48-165">**/include:** `includePath`</span></span>|<span data-ttu-id="a1e48-166">Nastaví cestu pro vyhledávání souborů, které jsou součástí `#include` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="a1e48-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="a1e48-167">**/itanium**</span></span>|<span data-ttu-id="a1e48-168">Určí jako cílový procesor Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="a1e48-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="a1e48-169">Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="a1e48-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="a1e48-170">**/Key:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="a1e48-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="a1e48-171">Zkompiluje `filename` se silným podpisem pomocí privátního klíče obsaženého v `keyFile` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="a1e48-172">**zkrat** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="a1e48-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="a1e48-173">Zkompiluje `filename` se silným podpisem pomocí privátního klíče vytvořeného v `keySource` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="a1e48-174">**/listing**</span><span class="sxs-lookup"><span data-stu-id="a1e48-174">**/listing**</span></span>|<span data-ttu-id="a1e48-175">Vytvoří na standardním výstupu soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="a1e48-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="a1e48-176">Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="a1e48-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="a1e48-177">Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="a1e48-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="a1e48-178">**/MDV:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="a1e48-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="a1e48-179">Nastaví řetězec verze metadat.</span><span class="sxs-lookup"><span data-stu-id="a1e48-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="a1e48-180">**/MSV:** `major` .`minor`</span><span class="sxs-lookup"><span data-stu-id="a1e48-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="a1e48-181">Nastaví verzi streamu metadat, kde `major` a `minor` jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a1e48-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="a1e48-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="a1e48-182">**/noautoinherit**</span></span>|<span data-ttu-id="a1e48-183">Zakáže výchozí dědění z <xref:System.Object> , pokud není zadána žádná základní třída.</span><span class="sxs-lookup"><span data-stu-id="a1e48-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="a1e48-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="a1e48-184">**/nocorstub**</span></span>|<span data-ttu-id="a1e48-185">Potlačí generování zástupné procedury CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="a1e48-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="a1e48-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="a1e48-186">**/nologo**</span></span>|<span data-ttu-id="a1e48-187">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a1e48-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="a1e48-188">**/output:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="a1e48-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="a1e48-189">Určuje název výstupního souboru a příponu.</span><span class="sxs-lookup"><span data-stu-id="a1e48-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="a1e48-190">Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="a1e48-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="a1e48-191">Výchozí přípona je *. exe*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-191">The default extension is *.exe*.</span></span> <span data-ttu-id="a1e48-192">Pokud zadáte možnost **/DLL** , je výchozí příponou *. dll*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="a1e48-193">**Poznámka:** Zadáním:myfile.dll **/Output** není nastavená možnost **/DLL** .</span><span class="sxs-lookup"><span data-stu-id="a1e48-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="a1e48-194">Pokud nezadáte **/DLL**, bude výsledkem spustitelný soubor s názvem *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="a1e48-195">**/Optimize**</span><span class="sxs-lookup"><span data-stu-id="a1e48-195">**/optimize**</span></span>|<span data-ttu-id="a1e48-196">Optimalizuje dlouhé instrukce na krátké.</span><span class="sxs-lookup"><span data-stu-id="a1e48-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="a1e48-197">Například `br` na `br.s` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="a1e48-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="a1e48-198">**/pe64**</span></span>|<span data-ttu-id="a1e48-199">Vytvoří 64bitovou kopii (PE32+).</span><span class="sxs-lookup"><span data-stu-id="a1e48-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="a1e48-200">Pokud není zadaný žádný cílový procesor, výchozí hodnota je `/itanium` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="a1e48-201">**/PDB**</span><span class="sxs-lookup"><span data-stu-id="a1e48-201">**/pdb**</span></span>|<span data-ttu-id="a1e48-202">Vytvoří soubor PDB bez povolení sledování informací o ladění.</span><span class="sxs-lookup"><span data-stu-id="a1e48-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="a1e48-203">**parametr**</span><span class="sxs-lookup"><span data-stu-id="a1e48-203">**/quiet**</span></span>|<span data-ttu-id="a1e48-204">Určuje tichý režim, který neoznamuje průběh sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1e48-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="a1e48-205">**/Resource:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="a1e48-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="a1e48-206">Obsahuje zadaný soubor prostředků ve \* formátu. res ve výsledném souboru *. exe* nebo *. dll* .</span><span class="sxs-lookup"><span data-stu-id="a1e48-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="a1e48-207">Pomocí možnosti **/Resource** lze zadat pouze jeden soubor. res.</span><span class="sxs-lookup"><span data-stu-id="a1e48-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="a1e48-208">**/ssver:** `int` .`int`</span><span class="sxs-lookup"><span data-stu-id="a1e48-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="a1e48-209">Nastaví číslo verze podsystému ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="a1e48-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="a1e48-210">Pro **/AppContainer** a **/ARM** minimální číslo verze je 6,02.</span><span class="sxs-lookup"><span data-stu-id="a1e48-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="a1e48-211">**/stack:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="a1e48-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="a1e48-212">Nastaví hodnotu SizeOfStackReserve v volitelné hlavičce NT na `stackSize` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="a1e48-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="a1e48-213">**/stripreloc**</span></span>|<span data-ttu-id="a1e48-214">Určuje, že není zapotřebí žádné přemisťování základu.</span><span class="sxs-lookup"><span data-stu-id="a1e48-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="a1e48-215">**/SUBSYSTEM:**`integer`</span><span class="sxs-lookup"><span data-stu-id="a1e48-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="a1e48-216">Nastaví podsystém na hodnotu zadanou `integer` v volitelné HLAVIČCE NT.</span><span class="sxs-lookup"><span data-stu-id="a1e48-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a1e48-217">Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše.</span><span class="sxs-lookup"><span data-stu-id="a1e48-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="a1e48-218">Seznam platných hodnot pro můžete zobrazit v souboru Winnt. h IMAGE_SUBSYSTEM `integer` .</span><span class="sxs-lookup"><span data-stu-id="a1e48-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="a1e48-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="a1e48-219">**/x64**</span></span>|<span data-ttu-id="a1e48-220">Určí jako cílový procesor 64bitový procesor společnosti AMD.</span><span class="sxs-lookup"><span data-stu-id="a1e48-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="a1e48-221">Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="a1e48-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="a1e48-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="a1e48-222">**/?**</span></span>|<span data-ttu-id="a1e48-223">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a1e48-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="a1e48-224">Všechny možnosti pro *Ilasm.exe* rozlišují velká a malá písmena, která jsou rozpoznána prvními třemi písmeny.</span><span class="sxs-lookup"><span data-stu-id="a1e48-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="a1e48-225">Například **/lis** je ekvivalentem **/listing** a **/res**: myresfile. res je ekvivalentem **/Resource**: myresfile. res. Možnosti, které určují argumenty, přijímají buď dvojtečku (:) nebo symbol rovná se (=) jako oddělovač mezi možností a argumentem.</span><span class="sxs-lookup"><span data-stu-id="a1e48-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="a1e48-226">Například **/Output**:*File. ext* je ekvivalentní souboru **/Output** = *. ext*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1e48-227">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1e48-227">Remarks</span></span>

<span data-ttu-id="a1e48-228">Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL.</span><span class="sxs-lookup"><span data-stu-id="a1e48-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="a1e48-229">Pomocí *Ilasm.exe*se vývojáři nástrojů a kompilátoru můžou soustředit na generování Il a metadat, aniž by se museli zabývat tím, že se ve formátu PE zadávají Il.</span><span class="sxs-lookup"><span data-stu-id="a1e48-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="a1e48-230">Podobně jako jiné kompilátory, které cílí na modul runtime, jako je C# a Visual Basic, *Ilasm.exe* nevytváří zprostředkující soubory objektů a nevyžaduje fázi propojování pro vytvoření souboru PE.</span><span class="sxs-lookup"><span data-stu-id="a1e48-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="a1e48-231">Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="a1e48-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="a1e48-232">To umožňuje spravovanému kódu napsanému v některém z těchto programovacích jazyků přiměřeně vyjádřit v rámci IL Assembler a kompilována s *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="a1e48-233">Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="a1e48-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="a1e48-234">*Ilasm.exe* můžete použít ve spojení s jeho doprovodným nástrojem [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="a1e48-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="a1e48-235">*Ildasm.exe* převezme soubor PE obsahující kód Il a vytvoří textový soubor vhodný jako vstup pro *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="a1e48-236">Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a1e48-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="a1e48-237">Po zkompilování kódu a spuštění výstupu prostřednictvím *Ildasm.exe*lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy.</span><span class="sxs-lookup"><span data-stu-id="a1e48-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="a1e48-238">Pak můžete tento textový soubor spustit pomocí *Ilasm.exe* a vytvořit konečný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="a1e48-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="a1e48-239">Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.</span><span class="sxs-lookup"><span data-stu-id="a1e48-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="a1e48-240">Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).</span><span class="sxs-lookup"><span data-stu-id="a1e48-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="a1e48-241">Aby toto kombinované použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení Assembler nenahrazuje krátká kódování pro dlouhé hodnoty, které jste mohli napsáni ve vašich zdrojích Il (nebo které mohou být vygenerovány jiným kompilátorem).</span><span class="sxs-lookup"><span data-stu-id="a1e48-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="a1e48-242">Pokud je to možné, použijte možnost **/optimize** k nahrazení krátkých kódování.</span><span class="sxs-lookup"><span data-stu-id="a1e48-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="a1e48-243">*Ildasm.exe* pracuje pouze se soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="a1e48-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="a1e48-244">Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1e48-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="a1e48-245">Další informace o gramatice IL najdete v souboru asmparse. gramatiky v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a1e48-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="a1e48-246">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="a1e48-246">Version Information</span></span>

<span data-ttu-id="a1e48-247">Počínaje .NET Framework 4,5 můžete k implementaci rozhraní připojit vlastní atribut pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="a1e48-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="a1e48-248">Počínaje .NET Framework 4,5 můžete určit libovolný objekt BLOB pro zařazování (binární rozsáhlý objekt) pomocí jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a1e48-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="a1e48-249">Další informace o gramatice IL najdete v souboru asmparse. gramatiky v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a1e48-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="a1e48-250">Příklady</span><span class="sxs-lookup"><span data-stu-id="a1e48-250">Examples</span></span>

<span data-ttu-id="a1e48-251">Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří spustitelný *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="a1e48-252">Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří soubor *. dll* *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="a1e48-253">Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří soubor *. dll* *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="a1e48-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="a1e48-254">Následující příklad kódu ukazuje extrémně jednoduchou aplikaci, která zobrazuje "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="a1e48-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="a1e48-255">„Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="a1e48-255">to the console.</span></span> <span data-ttu-id="a1e48-256">Tento kód můžete zkompilovat a potom použít nástroj [*Ildasm.exe*](ildasm-exe-il-disassembler.md) k vygenerování souboru Il.</span><span class="sxs-lookup"><span data-stu-id="a1e48-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="a1e48-257">Následující příklad kódu IL odpovídá předchozí ukázce kódu C#.</span><span class="sxs-lookup"><span data-stu-id="a1e48-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="a1e48-258">Tento kód můžete zkompilovat do sestavení pomocí nástroje IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="a1e48-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="a1e48-259">Oba příklady kódu IL i C# zobrazují "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="a1e48-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="a1e48-260">„Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="a1e48-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="a1e48-261">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1e48-261">See also</span></span>

- [<span data-ttu-id="a1e48-262">Nástroje</span><span class="sxs-lookup"><span data-stu-id="a1e48-262">Tools</span></span>](index.md)
- [<span data-ttu-id="a1e48-263">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="a1e48-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="a1e48-264">Proces spravovaného spuštění</span><span class="sxs-lookup"><span data-stu-id="a1e48-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="a1e48-265">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a1e48-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
