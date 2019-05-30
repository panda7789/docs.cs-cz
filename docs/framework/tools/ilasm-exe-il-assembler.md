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
ms.openlocfilehash: 2fa95755142b5ea3999cca127c868bc878da516e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378585"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="15d48-102">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="15d48-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="15d48-103">Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="15d48-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="15d48-104">(Další informace o jazyku IL naleznete v tématu [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) Výsledný spustitelný soubor obsahující jazyk IL a potřebná metadata lze spustit, a určit tak, zda IL funguje dle očekávání.</span><span class="sxs-lookup"><span data-stu-id="15d48-104">(For more information on IL, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="15d48-105">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15d48-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="15d48-106">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="15d48-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="15d48-107">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="15d48-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="15d48-108">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="15d48-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="15d48-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15d48-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="15d48-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="15d48-110">Parameters</span></span>

| <span data-ttu-id="15d48-111">Argument</span><span class="sxs-lookup"><span data-stu-id="15d48-111">Argument</span></span> | <span data-ttu-id="15d48-112">Popis</span><span class="sxs-lookup"><span data-stu-id="15d48-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="15d48-113">Název zdrojového souboru .il.</span><span class="sxs-lookup"><span data-stu-id="15d48-113">The name of the .il source file.</span></span> <span data-ttu-id="15d48-114">Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL.</span><span class="sxs-lookup"><span data-stu-id="15d48-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="15d48-115">Lze je zadat několik argumentů zdrojového souboru, k vytvoření jediného souboru PE pomocí *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="15d48-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="15d48-116">**Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru .il neobsahuje prázdný znak ani znak ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="15d48-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="15d48-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="15d48-117">Option</span></span> | <span data-ttu-id="15d48-118">Popis</span><span class="sxs-lookup"><span data-stu-id="15d48-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="15d48-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="15d48-119">**/32bitpreferred**</span></span>|<span data-ttu-id="15d48-120">Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).</span><span class="sxs-lookup"><span data-stu-id="15d48-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="15d48-121">**/ Alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="15d48-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="15d48-122">Nastaví hodnotu FileAlignment na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="15d48-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="15d48-123">Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="15d48-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="15d48-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="15d48-124">**/appcontainer**</span></span>|<span data-ttu-id="15d48-125">Vytvoří *.dll* nebo *.exe* soubor, který běží v kontejneru pro aplikace Windows, jako výstup.</span><span class="sxs-lookup"><span data-stu-id="15d48-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="15d48-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="15d48-126">**/arm**</span></span>|<span data-ttu-id="15d48-127">Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="15d48-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="15d48-128">Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="15d48-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="15d48-129">**propojovacího:** `integer`</span><span class="sxs-lookup"><span data-stu-id="15d48-129">**/base:** `integer`</span></span>|<span data-ttu-id="15d48-130">Nastaví hodnotu ImageBase na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="15d48-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="15d48-131">Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="15d48-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="15d48-132">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="15d48-132">**/clock**</span></span>|<span data-ttu-id="15d48-133">Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:</span><span class="sxs-lookup"><span data-stu-id="15d48-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="15d48-134">**Total Run**: Celkový čas strávený provádění určitých operací, které následují.</span><span class="sxs-lookup"><span data-stu-id="15d48-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="15d48-135">**Startup**: Načtení a otevírání souboru.</span><span class="sxs-lookup"><span data-stu-id="15d48-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="15d48-136">**Emitting MD**: Generování metadat.</span><span class="sxs-lookup"><span data-stu-id="15d48-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="15d48-137">**REF to Def Resolution**: Vyhodnocování odkazů na definice v souboru.</span><span class="sxs-lookup"><span data-stu-id="15d48-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="15d48-138">**CEE File Generation**: Generuje se bitová kopie souboru v paměti.</span><span class="sxs-lookup"><span data-stu-id="15d48-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="15d48-139">**PE File Writing**: Zápis bitové kopie do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="15d48-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="15d48-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="15d48-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="15d48-141">Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků).</span><span class="sxs-lookup"><span data-stu-id="15d48-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="15d48-142">Vytvoří soubor PDB.</span><span class="sxs-lookup"><span data-stu-id="15d48-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="15d48-143">**/ debug** bez dalších hodnot zakáže optimalizaci JIT a použije body posloupnosti ze souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="15d48-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="15d48-144">**IMPL** zakáže optimalizaci JIT a použije implicitní body posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="15d48-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="15d48-145">**OPT** povolí optimalizaci JIT a použije implicitní body posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="15d48-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="15d48-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="15d48-146">**/dll**</span></span>|<span data-ttu-id="15d48-147">Vytvoří *.dll* soubor jako výstup.</span><span class="sxs-lookup"><span data-stu-id="15d48-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="15d48-148">**/ENC:** `file`</span><span class="sxs-lookup"><span data-stu-id="15d48-148">**/enc:** `file`</span></span>|<span data-ttu-id="15d48-149">Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="15d48-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="15d48-150">Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.</span><span class="sxs-lookup"><span data-stu-id="15d48-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="15d48-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="15d48-151">**/exe**</span></span>|<span data-ttu-id="15d48-152">Vytvoří jako výstup spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="15d48-152">Produces an executable file as output.</span></span> <span data-ttu-id="15d48-153">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="15d48-153">This is the default.</span></span>|
|<span data-ttu-id="15d48-154">**Flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="15d48-154">**/flags:** `integer`</span></span>|<span data-ttu-id="15d48-155">Nastaví hodnotu ImageFlags na hodnotu zadanou pomocí `integer` v hlavičce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="15d48-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="15d48-156">Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="15d48-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="15d48-157">Zobrazit Comimage_flags corhdr.h seznam platných hodnot pro *celé číslo*.</span><span class="sxs-lookup"><span data-stu-id="15d48-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="15d48-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="15d48-158">**/fold**</span></span>|<span data-ttu-id="15d48-159">Sloučí identická těla metod do jednoho.</span><span class="sxs-lookup"><span data-stu-id="15d48-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="15d48-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="15d48-160">/**highentropyva**</span></span>|<span data-ttu-id="15d48-161">Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="15d48-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="15d48-162">(Výchozí pro **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="15d48-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="15d48-163">**/ include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="15d48-163">**/include:** `includePath`</span></span>|<span data-ttu-id="15d48-164">Nastavuje cestu pro vyhledávání souborů zahrnutých v `#include`.</span><span class="sxs-lookup"><span data-stu-id="15d48-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="15d48-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="15d48-165">**/itanium**</span></span>|<span data-ttu-id="15d48-166">Určí jako cílový procesor Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="15d48-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="15d48-167">Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="15d48-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="15d48-168">**uveden:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="15d48-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="15d48-169">Zkompiluje `filename` se silným podpisem za použití soukromého klíče obsaženého v `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="15d48-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="15d48-170">**uveden:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="15d48-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="15d48-171">Zkompiluje `filename` se silným podpisem pomocí soukromého klíče vytvořeného ve `keySource`.</span><span class="sxs-lookup"><span data-stu-id="15d48-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="15d48-172">**/ výpis**</span><span class="sxs-lookup"><span data-stu-id="15d48-172">**/listing**</span></span>|<span data-ttu-id="15d48-173">Vytvoří na standardním výstupu soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="15d48-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="15d48-174">Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="15d48-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="15d48-175">Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="15d48-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="15d48-176">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="15d48-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="15d48-177">Nastaví řetězec verze metadat.</span><span class="sxs-lookup"><span data-stu-id="15d48-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="15d48-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="15d48-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="15d48-179">Nastaví verzi datového proudu metadat, kam `major` a `minor` jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="15d48-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="15d48-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="15d48-180">**/noautoinherit**</span></span>|<span data-ttu-id="15d48-181">Zakáže výchozí dědění ze <xref:System.Object> Pokud je zadaný žádnou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="15d48-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="15d48-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="15d48-182">**/nocorstub**</span></span>|<span data-ttu-id="15d48-183">Potlačí generování zástupné procedury CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="15d48-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="15d48-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="15d48-184">**/nologo**</span></span>|<span data-ttu-id="15d48-185">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="15d48-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="15d48-186">**/ output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="15d48-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="15d48-187">Určuje název výstupního souboru a příponu.</span><span class="sxs-lookup"><span data-stu-id="15d48-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="15d48-188">Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="15d48-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="15d48-189">Výchozí příponou je *.exe*.</span><span class="sxs-lookup"><span data-stu-id="15d48-189">The default extension is *.exe*.</span></span> <span data-ttu-id="15d48-190">Pokud zadáte **/dll** možnost, je výchozí příponou *.dll*.</span><span class="sxs-lookup"><span data-stu-id="15d48-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="15d48-191">**Poznámka:** Určení **/output**: myfile.dll není nastavený **/dll** možnost.</span><span class="sxs-lookup"><span data-stu-id="15d48-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="15d48-192">Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *soubor.dll*.</span><span class="sxs-lookup"><span data-stu-id="15d48-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="15d48-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="15d48-193">**/optimize**</span></span>|<span data-ttu-id="15d48-194">Optimalizuje dlouhé instrukce na krátké.</span><span class="sxs-lookup"><span data-stu-id="15d48-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="15d48-195">Například `br` k `br.s`.</span><span class="sxs-lookup"><span data-stu-id="15d48-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="15d48-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="15d48-196">**/pe64**</span></span>|<span data-ttu-id="15d48-197">Vytvoří 64bitovou kopii (PE32+).</span><span class="sxs-lookup"><span data-stu-id="15d48-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="15d48-198">Pokud není zadán žádný cílový procesor, výchozí hodnota je `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="15d48-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="15d48-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="15d48-199">**/pdb**</span></span>|<span data-ttu-id="15d48-200">Vytvoří soubor PDB bez povolení sledování informací o ladění.</span><span class="sxs-lookup"><span data-stu-id="15d48-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="15d48-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="15d48-201">**/quiet**</span></span>|<span data-ttu-id="15d48-202">Určuje tichý režim, který neoznamuje průběh sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d48-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="15d48-203">**/ Resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="15d48-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="15d48-204">Zahrnuje soubor zadaný prostředek v \*res formátu ve výsledné *.exe* nebo *.dll* souboru.</span><span class="sxs-lookup"><span data-stu-id="15d48-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="15d48-205">Je možné zadat jenom jeden soubor. res při **/Resource** možnost.</span><span class="sxs-lookup"><span data-stu-id="15d48-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="15d48-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="15d48-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="15d48-207">Nastaví číslo verze podsystému ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="15d48-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="15d48-208">Pro **/appcontainer** a **/arm** je minimálním číslem verze 6.02.</span><span class="sxs-lookup"><span data-stu-id="15d48-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="15d48-209">**/ Stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="15d48-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="15d48-210">Nastaví hodnotu SizeOfStackReserve ve volitelné hlavičce NT na `stackSize`.</span><span class="sxs-lookup"><span data-stu-id="15d48-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="15d48-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="15d48-211">**/stripreloc**</span></span>|<span data-ttu-id="15d48-212">Určuje, že není zapotřebí žádné přemisťování základu.</span><span class="sxs-lookup"><span data-stu-id="15d48-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="15d48-213">**/ Subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="15d48-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="15d48-214">Nastaví hodnotu subsystem na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="15d48-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="15d48-215">Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše.</span><span class="sxs-lookup"><span data-stu-id="15d48-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="15d48-216">Viz soubor winnt.h, IMAGE_SUBSYSTEM seznam platných hodnot pro `integer`.</span><span class="sxs-lookup"><span data-stu-id="15d48-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="15d48-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="15d48-217">**/x64**</span></span>|<span data-ttu-id="15d48-218">Určí jako cílový procesor 64bitový procesor společnosti AMD.</span><span class="sxs-lookup"><span data-stu-id="15d48-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="15d48-219">Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="15d48-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="15d48-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="15d48-220">**/?**</span></span>|<span data-ttu-id="15d48-221">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="15d48-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="15d48-222">Všechny možnosti pro *Ilasm.exe* jsou malá a velká písmena rozpoznávány dle prvních tří písmen.</span><span class="sxs-lookup"><span data-stu-id="15d48-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="15d48-223">Například **/lis** je ekvivalentní **/listing** a **/res**: myresfile.res je ekvivalentní možnosti **/Resource**: myresfile.res. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="15d48-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="15d48-224">Například **/output**:*file.ext* je ekvivalentní **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="15d48-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="15d48-225">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15d48-225">Remarks</span></span>

<span data-ttu-id="15d48-226">Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL.</span><span class="sxs-lookup"><span data-stu-id="15d48-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="15d48-227">Pomocí *Ilasm.exe*, vývojáři nástrojů a kompilátorů umožňuje soustředit se na IL a generování metadat bez nutnosti zabývat se generováním kódu IL v souborovém formátu PE.</span><span class="sxs-lookup"><span data-stu-id="15d48-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="15d48-228">Podobně jako jiné kompilátory cílené na modul runtime, jako například C# a Visual Basic, *Ilasm.exe* nevytváří soubory objektů a nevyžaduje souboru PE propojovací fázi.</span><span class="sxs-lookup"><span data-stu-id="15d48-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="15d48-229">Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="15d48-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="15d48-230">To umožňuje spravovaného kódu napsaného v libovolném z těchto programovacích jazyků v nástroji IL Assembler adekvátní vyjádření a zkompilovaná *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="15d48-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="15d48-231">Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="15d48-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="15d48-232">Můžete použít *Ilasm.exe* ve spojení s jeho doprovodným nástrojem [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="15d48-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="15d48-233">*Ildasm.exe* přijímá soubory PE obsahující kód IL a vytváří textový soubor vhodný jako vstup do *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="15d48-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="15d48-234">Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="15d48-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="15d48-235">Po zkompilování kódu a zpracování výstupu nástrojem *Ildasm.exe*, lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy.</span><span class="sxs-lookup"><span data-stu-id="15d48-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="15d48-236">Poté lze tento textový soubor *Ilasm.exe* a vytvořit konečný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="15d48-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="15d48-237">Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.</span><span class="sxs-lookup"><span data-stu-id="15d48-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="15d48-238">Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).</span><span class="sxs-lookup"><span data-stu-id="15d48-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="15d48-239">Chcete-li toto kombinované použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembler nenahrazuje krátká kódování pro dlouhé ty kódování napsaná ve zdrojích IL (nebo který může být vygenerována jiným kompilátorem).</span><span class="sxs-lookup"><span data-stu-id="15d48-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="15d48-240">Použití **/ optimize** možnost nahradit krátká kódování, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="15d48-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="15d48-241">*Ildasm.exe* pracuje pouze se soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="15d48-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="15d48-242">Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d48-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="15d48-243">Další informace o gramatice jazyka IL, najdete v souboru asmparse.Grammar sady [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15d48-243">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="version-information"></a><span data-ttu-id="15d48-244">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="15d48-244">Version Information</span></span>

<span data-ttu-id="15d48-245">Od verze rozhraní .NET Framework 4.5, můžete přidat vlastní atribut na implementaci rozhraní pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="15d48-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

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

<span data-ttu-id="15d48-246">Od verze rozhraní .NET Framework 4.5, můžete zadat libovolný zařazovací objekt BLOB (binární rozsáhlý objekt) s použitím jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="15d48-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="15d48-247">Další informace o gramatice jazyka IL, najdete v souboru asmparse.Grammar sady [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15d48-247">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="examples"></a><span data-ttu-id="15d48-248">Příklady</span><span class="sxs-lookup"><span data-stu-id="15d48-248">Examples</span></span>

<span data-ttu-id="15d48-249">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří spustitelný soubor *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="15d48-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="15d48-250">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* souboru *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="15d48-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="15d48-251">Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* souboru *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="15d48-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="15d48-252">Následující příklad kódu ukazuje velice jednoduchou aplikaci, která se zobrazí "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="15d48-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="15d48-253">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="15d48-253">to the console.</span></span> <span data-ttu-id="15d48-254">Můžete tento kód zkompilovat a pak použít [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj pro vygenerování souboru IL.</span><span class="sxs-lookup"><span data-stu-id="15d48-254">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="15d48-255">Následující příklad kódu IL odpovídá předchozí ukázce kódu C#.</span><span class="sxs-lookup"><span data-stu-id="15d48-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="15d48-256">Tento kód lze zkompilovat do sestavení pomocí nástroje IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="15d48-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="15d48-257">Obě IL a C# příklady kódu zobrazí "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="15d48-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="15d48-258">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="15d48-258">to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15d48-259">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d48-259">See also</span></span>

- [<span data-ttu-id="15d48-260">Nástroje</span><span class="sxs-lookup"><span data-stu-id="15d48-260">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="15d48-261">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="15d48-261">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="15d48-262">Proces spravovaného spuštění</span><span class="sxs-lookup"><span data-stu-id="15d48-262">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)
- [<span data-ttu-id="15d48-263">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="15d48-263">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
