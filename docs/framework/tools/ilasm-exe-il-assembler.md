---
title: Ilasm.exe (IL Assembler)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4009fe4910af81c685ee015c7801b040a90c25aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409786"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="54636-102">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="54636-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="54636-103">Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="54636-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="54636-104">(Další informace o IL najdete v tématu [spravovat proces spuštění](../../../docs/standard/managed-execution-process.md).) Výsledný spustitelný soubor obsahující jazyk IL a potřebná metadata lze spustit, a určit tak, zda IL funguje dle očekávání.</span><span class="sxs-lookup"><span data-stu-id="54636-104">(For more information on IL, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="54636-105">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54636-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="54636-106">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="54636-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="54636-107">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="54636-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="54636-108">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="54636-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="54636-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54636-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a><span data-ttu-id="54636-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="54636-110">Parameters</span></span>

| <span data-ttu-id="54636-111">Argument</span><span class="sxs-lookup"><span data-stu-id="54636-111">Argument</span></span> | <span data-ttu-id="54636-112">Popis</span><span class="sxs-lookup"><span data-stu-id="54636-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="54636-113">Název zdrojového souboru .il.</span><span class="sxs-lookup"><span data-stu-id="54636-113">The name of the .il source file.</span></span> <span data-ttu-id="54636-114">Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL.</span><span class="sxs-lookup"><span data-stu-id="54636-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="54636-115">Můžete je nutné zadat několik argumentů zdrojového souboru k vytvoření jednoho souboru PE s *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="54636-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="54636-116">**Poznámka:** zajistěte, aby poslední řádek kódu ve zdrojovém souboru .il prázdné znaky nebo znakem konec řádku.</span><span class="sxs-lookup"><span data-stu-id="54636-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="54636-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="54636-117">Option</span></span> | <span data-ttu-id="54636-118">Popis</span><span class="sxs-lookup"><span data-stu-id="54636-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="54636-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="54636-119">**/32bitpreferred**</span></span>|<span data-ttu-id="54636-120">Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).</span><span class="sxs-lookup"><span data-stu-id="54636-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="54636-121">**/ Alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="54636-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="54636-122">Nastaví na hodnotu zadanou pomocí FileAlignment `integer` v hlavičce NT volitelné.</span><span class="sxs-lookup"><span data-stu-id="54636-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="54636-123">Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="54636-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="54636-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="54636-124">**/appcontainer**</span></span>|<span data-ttu-id="54636-125">Vytváří *.dll* nebo *.exe* soubor, který běží v kontejneru aplikace systému Windows, jako výstup.</span><span class="sxs-lookup"><span data-stu-id="54636-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="54636-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="54636-126">**/arm**</span></span>|<span data-ttu-id="54636-127">Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="54636-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="54636-128">Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="54636-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="54636-129">**/Base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="54636-129">**/base:** `integer`</span></span>|<span data-ttu-id="54636-130">Nastaví na hodnotu zadanou pomocí ImageBase `integer` v hlavičce NT volitelné.</span><span class="sxs-lookup"><span data-stu-id="54636-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="54636-131">Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="54636-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="54636-132">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="54636-132">**/clock**</span></span>|<span data-ttu-id="54636-133">Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:</span><span class="sxs-lookup"><span data-stu-id="54636-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="54636-134">**Celkový počet spuštění**: celkový čas strávený, provádění určitých operací, které následují.</span><span class="sxs-lookup"><span data-stu-id="54636-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="54636-135">**Spuštění**: načítání a soubor otevřít.</span><span class="sxs-lookup"><span data-stu-id="54636-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="54636-136">**Emitování MD**: generování metadat.</span><span class="sxs-lookup"><span data-stu-id="54636-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="54636-137">**REF Def řešení**: řešení odkazy na definice v souboru.</span><span class="sxs-lookup"><span data-stu-id="54636-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="54636-138">**Generování souboru CEE**: generování souboru bitové kopie v paměti.</span><span class="sxs-lookup"><span data-stu-id="54636-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="54636-139">**Zápis souboru PE**: zápis do souboru PE bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="54636-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="54636-140">**/ debug**[:**IMPL**&#124;**VÝSLOVNÝ**]</span><span class="sxs-lookup"><span data-stu-id="54636-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="54636-141">Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků).</span><span class="sxs-lookup"><span data-stu-id="54636-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="54636-142">Vytvoří soubor PDB.</span><span class="sxs-lookup"><span data-stu-id="54636-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="54636-143">**/ debug** bez další hodnoty zakáže optimalizace JIT a používá pořadí body ze souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="54636-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="54636-144">**IMPL** zakáže optimalizace JIT a používá implicitní pořadí body.</span><span class="sxs-lookup"><span data-stu-id="54636-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="54636-145">**VÝSLOVNÝ** umožňuje optimalizaci JIT a používá implicitní pořadí body.</span><span class="sxs-lookup"><span data-stu-id="54636-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="54636-146">**/ DLL**</span><span class="sxs-lookup"><span data-stu-id="54636-146">**/dll**</span></span>|<span data-ttu-id="54636-147">Vytváří *.dll* souboru jako výstup.</span><span class="sxs-lookup"><span data-stu-id="54636-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="54636-148">**/ENC:** `file`</span><span class="sxs-lookup"><span data-stu-id="54636-148">**/enc:** `file`</span></span>|<span data-ttu-id="54636-149">Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="54636-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="54636-150">Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.</span><span class="sxs-lookup"><span data-stu-id="54636-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="54636-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="54636-151">**/exe**</span></span>|<span data-ttu-id="54636-152">Vytvoří jako výstup spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="54636-152">Produces an executable file as output.</span></span> <span data-ttu-id="54636-153">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="54636-153">This is the default.</span></span>|
|<span data-ttu-id="54636-154">**/ Flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="54636-154">**/flags:** `integer`</span></span>|<span data-ttu-id="54636-155">Nastaví na hodnotu zadanou pomocí ImageFlags `integer` v hlavičce běžné runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="54636-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="54636-156">Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="54636-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="54636-157">V tématu CorHdr.h COMIMAGE_FLAGS seznam platných hodnot pro *celé číslo*.</span><span class="sxs-lookup"><span data-stu-id="54636-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="54636-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="54636-158">**/fold**</span></span>|<span data-ttu-id="54636-159">Sloučí identická těla metod do jednoho.</span><span class="sxs-lookup"><span data-stu-id="54636-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="54636-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="54636-160">/**highentropyva**</span></span>|<span data-ttu-id="54636-161">Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="54636-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="54636-162">(Výchozí pro **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="54636-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="54636-163">**/ include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="54636-163">**/include:** `includePath`</span></span>|<span data-ttu-id="54636-164">Nastaví cestu k vyhledávání souborů, které jsou součástí `#include`.</span><span class="sxs-lookup"><span data-stu-id="54636-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="54636-165">**/Itanium**</span><span class="sxs-lookup"><span data-stu-id="54636-165">**/itanium**</span></span>|<span data-ttu-id="54636-166">Určí jako cílový procesor Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="54636-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="54636-167">Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="54636-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="54636-168">**/Key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="54636-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="54636-169">Zkompiluje `filename` silné podpisem pomocí privátní klíče součástí `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="54636-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="54636-170">**/Key:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="54636-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="54636-171">Zkompiluje `filename` silné podpisem pomocí soukromého klíče vytvořeného v `keySource`.</span><span class="sxs-lookup"><span data-stu-id="54636-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="54636-172">**/ výpis**</span><span class="sxs-lookup"><span data-stu-id="54636-172">**/listing**</span></span>|<span data-ttu-id="54636-173">Vytvoří na standardním výstupu soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="54636-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="54636-174">Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="54636-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="54636-175">Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="54636-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="54636-176">**/MDV:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="54636-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="54636-177">Nastaví řetězec verze metadat.</span><span class="sxs-lookup"><span data-stu-id="54636-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="54636-178">**/mSv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="54636-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="54636-179">Nastaví verze datového proudu metadata, kde `major` a `minor` jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="54636-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="54636-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="54636-180">**/noautoinherit**</span></span>|<span data-ttu-id="54636-181">Zakáže výchozí dědění ze <xref:System.Object> Pokud je zadán žádný základní třídy.</span><span class="sxs-lookup"><span data-stu-id="54636-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="54636-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="54636-182">**/nocorstub**</span></span>|<span data-ttu-id="54636-183">Potlačí generování zástupné procedury CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="54636-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="54636-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="54636-184">**/nologo**</span></span>|<span data-ttu-id="54636-185">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="54636-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="54636-186">**output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="54636-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="54636-187">Určuje název výstupního souboru a příponu.</span><span class="sxs-lookup"><span data-stu-id="54636-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="54636-188">Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="54636-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="54636-189">Výchozí přípona je *.exe*.</span><span class="sxs-lookup"><span data-stu-id="54636-189">The default extension is *.exe*.</span></span> <span data-ttu-id="54636-190">Pokud zadáte **/dll** možnost, je výchozí rozšíření *.dll*.</span><span class="sxs-lookup"><span data-stu-id="54636-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="54636-191">**Poznámka:** zadání **/výstup**: soubor.dll nenastaví **/dll** možnost.</span><span class="sxs-lookup"><span data-stu-id="54636-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="54636-192">Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *soubor.dll*.</span><span class="sxs-lookup"><span data-stu-id="54636-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="54636-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="54636-193">**/optimize**</span></span>|<span data-ttu-id="54636-194">Optimalizuje dlouhé instrukce na krátké.</span><span class="sxs-lookup"><span data-stu-id="54636-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="54636-195">Například `br` k `br.s`.</span><span class="sxs-lookup"><span data-stu-id="54636-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="54636-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="54636-196">**/pe64**</span></span>|<span data-ttu-id="54636-197">Vytvoří 64bitovou kopii (PE32+).</span><span class="sxs-lookup"><span data-stu-id="54636-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="54636-198">Pokud není zadaný žádný cílový procesor, výchozí hodnota je `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="54636-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="54636-199">**/ pdb**</span><span class="sxs-lookup"><span data-stu-id="54636-199">**/pdb**</span></span>|<span data-ttu-id="54636-200">Vytvoří soubor PDB bez povolení sledování informací o ladění.</span><span class="sxs-lookup"><span data-stu-id="54636-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="54636-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="54636-201">**/quiet**</span></span>|<span data-ttu-id="54636-202">Určuje tichý režim, který neoznamuje průběh sestavení.</span><span class="sxs-lookup"><span data-stu-id="54636-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="54636-203">**/ Resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="54636-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="54636-204">Obsahuje soubor zadaný prostředek v \*.res formátu výsledná *.exe* nebo *.dll* souboru.</span><span class="sxs-lookup"><span data-stu-id="54636-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="54636-205">S lze zadat pouze jeden soubor .res **/Resource** možnost.</span><span class="sxs-lookup"><span data-stu-id="54636-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="54636-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="54636-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="54636-207">Nastaví číslo verze podsystému ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="54636-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="54636-208">Pro **/appcontainer** a **/arm** číslo minimální verze je 6.02.</span><span class="sxs-lookup"><span data-stu-id="54636-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="54636-209">**/Stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="54636-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="54636-210">Nastaví hodnotu SizeOfStackReserve v hlavičce NT volitelné k `stackSize`.</span><span class="sxs-lookup"><span data-stu-id="54636-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="54636-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="54636-211">**/stripreloc**</span></span>|<span data-ttu-id="54636-212">Určuje, že není zapotřebí žádné přemisťování základu.</span><span class="sxs-lookup"><span data-stu-id="54636-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="54636-213">**/Subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="54636-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="54636-214">Nastaví na hodnotu zadanou pomocí subsystému `integer` v hlavičce NT volitelné.</span><span class="sxs-lookup"><span data-stu-id="54636-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="54636-215">Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše.</span><span class="sxs-lookup"><span data-stu-id="54636-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="54636-216">Najdete v souboru winnt.h, IMAGE_SUBSYSTEM seznam platných hodnot pro `integer`.</span><span class="sxs-lookup"><span data-stu-id="54636-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="54636-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="54636-217">**/x64**</span></span>|<span data-ttu-id="54636-218">Určí jako cílový procesor 64bitový procesor společnosti AMD.</span><span class="sxs-lookup"><span data-stu-id="54636-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="54636-219">Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="54636-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="54636-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="54636-220">**/?**</span></span>|<span data-ttu-id="54636-221">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="54636-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="54636-222">Všechny možnosti pro *Ilasm.exe* jsou velká a malá písmena a rozpoznaný podle prvních tří písmen.</span><span class="sxs-lookup"><span data-stu-id="54636-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="54636-223">Například **/lis** je ekvivalentní **/výpis** a **/res**: myresfile.res je ekvivalentní **/Resource**: myresfile.res. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="54636-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="54636-224">Například **/výstup**:*file.ext* je ekvivalentní **/výstup**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="54636-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="54636-225">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54636-225">Remarks</span></span>

<span data-ttu-id="54636-226">Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL.</span><span class="sxs-lookup"><span data-stu-id="54636-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="54636-227">Pomocí *Ilasm.exe*, nástroje a kompilátoru vývojářům umožní soustředit se na IL a metadata generování bez se problémem generování IL ve formátu souboru PE.</span><span class="sxs-lookup"><span data-stu-id="54636-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="54636-228">Podobně jako ostatní kompilátory, které používají modul runtime, jako je například C# a Visual Basic, *Ilasm.exe* nevytváří soubory mezilehlých objektů a nevyžaduje serveru linking fáze k vytvoření souboru PE.</span><span class="sxs-lookup"><span data-stu-id="54636-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="54636-229">Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="54636-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="54636-230">To umožňuje spravovaný kód napsaný v některé z těchto programovacích jazyků adekvátní vyjádřeno v IL assembleru a kompilovat s *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="54636-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="54636-231">Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="54636-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="54636-232">Můžete použít *Ilasm.exe* ve spojení s nástrojem jeho doprovodné [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="54636-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="54636-233">*Ildasm.exe* trvá PE souboru, který obsahuje kód IL a vytvoří textový soubor vhodný jako vstup pro *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="54636-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="54636-234">Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="54636-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="54636-235">Po kompilaci kódu a spouštění výstup *Ildasm.exe*, bude výsledný soubor IL text může být ručně upravovat přidat chybějící atributy.</span><span class="sxs-lookup"><span data-stu-id="54636-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="54636-236">Potom můžete spustit tohoto textového souboru *Ilasm.exe* k vytvoření konečné spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="54636-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="54636-237">Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.</span><span class="sxs-lookup"><span data-stu-id="54636-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="54636-238">Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).</span><span class="sxs-lookup"><span data-stu-id="54636-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="54636-239">To lze provést kombinaci použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembleru není nahradit krátký kódování pro dlouho ty, které jsou možná jste napsali v vašich zdrojů IL (nebo který může být vygenerované pomocí jiného kompilátoru).</span><span class="sxs-lookup"><span data-stu-id="54636-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="54636-240">Použití **/ optimize** možnost nahradit krátký kódování, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="54636-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="54636-241">*Ildasm.exe* funguje pouze na soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="54636-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="54636-242">Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="54636-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="54636-243">Další informace o gramatiky IL, naleznete v souboru asmparse.grammar v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54636-243">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="version-information"></a><span data-ttu-id="54636-244">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="54636-244">Version Information</span></span>

<span data-ttu-id="54636-245">Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vlastní atribut k implementaci rozhraní můžete připojit pomocí kódu podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="54636-245">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```
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

<span data-ttu-id="54636-246">Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete zadat libovolný zařazování BLOB (binární rozsáhlý objekt) pomocí jeho Nezpracovaná binární reprezentace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="54636-246">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="54636-247">Další informace o gramatiky IL, naleznete v souboru asmparse.grammar v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54636-247">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="examples"></a><span data-ttu-id="54636-248">Příklady</span><span class="sxs-lookup"><span data-stu-id="54636-248">Examples</span></span>

<span data-ttu-id="54636-249">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří spustitelný soubor *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="54636-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="54636-250">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* soubor *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="54636-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="54636-251">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* soubor *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="54636-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="54636-252">Následující příklad kódu ukazuje velmi jednoduché aplikace, která zobrazuje "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="54636-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="54636-253">ke konzole.</span><span class="sxs-lookup"><span data-stu-id="54636-253">to the console.</span></span> <span data-ttu-id="54636-254">Můžete zkompilovat tento kód a potom pomocí [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj pro generování IL souboru.</span><span class="sxs-lookup"><span data-stu-id="54636-254">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="54636-255">Následující příklad kódu IL odpovídá předchozí ukázce kódu C#.</span><span class="sxs-lookup"><span data-stu-id="54636-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="54636-256">Tento kód můžete zkompilovat do sestavení pomocí nástroje assembleru IL.</span><span class="sxs-lookup"><span data-stu-id="54636-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="54636-257">Příklady kódu IL a C# zobrazit "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="54636-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="54636-258">ke konzole.</span><span class="sxs-lookup"><span data-stu-id="54636-258">to the console.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="54636-259">Viz také</span><span class="sxs-lookup"><span data-stu-id="54636-259">See also</span></span>

[<span data-ttu-id="54636-260">Nástroje</span><span class="sxs-lookup"><span data-stu-id="54636-260">Tools</span></span>](../../../docs/framework/tools/index.md)  
[<span data-ttu-id="54636-261">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="54636-261">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[<span data-ttu-id="54636-262">Proces spravovaného spuštění</span><span class="sxs-lookup"><span data-stu-id="54636-262">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)  
[<span data-ttu-id="54636-263">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="54636-263">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
