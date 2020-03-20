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
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105093"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="f606b-102">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="f606b-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="f606b-103">Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="f606b-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="f606b-104">(Další informace o IL, naleznete [v tématu proces ustálené spuštění](../../standard/managed-execution-process.md).) Můžete spustit výsledný spustitelný soubor, který obsahuje IL a požadovaná metadata, chcete-li zjistit, zda IL provádí podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f606b-104">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="f606b-105">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f606b-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f606b-106">Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f606b-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f606b-107">Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f606b-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="f606b-108">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="f606b-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="f606b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f606b-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="f606b-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="f606b-110">Parameters</span></span>

| <span data-ttu-id="f606b-111">Argument</span><span class="sxs-lookup"><span data-stu-id="f606b-111">Argument</span></span> | <span data-ttu-id="f606b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f606b-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="f606b-113">Název zdrojového souboru .il.</span><span class="sxs-lookup"><span data-stu-id="f606b-113">The name of the .il source file.</span></span> <span data-ttu-id="f606b-114">Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL.</span><span class="sxs-lookup"><span data-stu-id="f606b-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="f606b-115">K vytvoření jednoho souboru PE pomocí souboru *Ilasm.exe*lze zadat více argumentů zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="f606b-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="f606b-116">**Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru .il má koncové prázdné znaky nebo znak konce řádku.</span><span class="sxs-lookup"><span data-stu-id="f606b-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="f606b-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="f606b-117">Option</span></span> | <span data-ttu-id="f606b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f606b-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="f606b-119">**/32bitpreferred /32bitpreferred /32bitpreferred /3**</span><span class="sxs-lookup"><span data-stu-id="f606b-119">**/32bitpreferred**</span></span>|<span data-ttu-id="f606b-120">Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).</span><span class="sxs-lookup"><span data-stu-id="f606b-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="f606b-121">**/zarovnání:**`integer`</span><span class="sxs-lookup"><span data-stu-id="f606b-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="f606b-122">Nastaví zarovnání souborů `integer` na hodnotu určenou v volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="f606b-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f606b-123">Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="f606b-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="f606b-124">**/kontejner aplikace**</span><span class="sxs-lookup"><span data-stu-id="f606b-124">**/appcontainer**</span></span>|<span data-ttu-id="f606b-125">Vytvoří soubor *DLL* nebo *EXE,* který běží v kontejneru aplikací pro Windows jako výstup.</span><span class="sxs-lookup"><span data-stu-id="f606b-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="f606b-126">**/rameno**</span><span class="sxs-lookup"><span data-stu-id="f606b-126">**/arm**</span></span>|<span data-ttu-id="f606b-127">Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="f606b-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="f606b-128">Pokud není zadána žádná bitová vztažnost obrazu, je výchozí hodnota **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="f606b-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="f606b-129">**/základna:**`integer`</span><span class="sxs-lookup"><span data-stu-id="f606b-129">**/base:** `integer`</span></span>|<span data-ttu-id="f606b-130">Nastaví imagebase na `integer` hodnotu určenou v volitelné masce NT.</span><span class="sxs-lookup"><span data-stu-id="f606b-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f606b-131">Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="f606b-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="f606b-132">**/hodiny**</span><span class="sxs-lookup"><span data-stu-id="f606b-132">**/clock**</span></span>|<span data-ttu-id="f606b-133">Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:</span><span class="sxs-lookup"><span data-stu-id="f606b-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="f606b-134">**Celkový běh**: Celkový čas strávený prováděním všech konkrétních operací, které následují.</span><span class="sxs-lookup"><span data-stu-id="f606b-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="f606b-135">**Spuštění**: Načítání a otevírání souboru.</span><span class="sxs-lookup"><span data-stu-id="f606b-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="f606b-136">**Emitting MD**: Emitující metadata.</span><span class="sxs-lookup"><span data-stu-id="f606b-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="f606b-137">**Ref to Def Rozlišení**: Řešení odkazů na definice v souboru.</span><span class="sxs-lookup"><span data-stu-id="f606b-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="f606b-138">**Generování souborů ve výjaku**: Generování obrazu souboru v paměti.</span><span class="sxs-lookup"><span data-stu-id="f606b-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="f606b-139">**Psaní souboru PE**: Zápis obrazu do souboru PE.</span><span class="sxs-lookup"><span data-stu-id="f606b-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="f606b-140">**/ladění**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="f606b-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="f606b-141">Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků).</span><span class="sxs-lookup"><span data-stu-id="f606b-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="f606b-142">Vytvoří soubor PDB.</span><span class="sxs-lookup"><span data-stu-id="f606b-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="f606b-143">**/debug** bez další hodnoty zakáže optimalizaci JIT a použije sekvenční body ze souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="f606b-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="f606b-144">**IMPL** zakáže optimalizaci JIT a používá implicitní sekvenční body.</span><span class="sxs-lookup"><span data-stu-id="f606b-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="f606b-145">**OPT** umožňuje optimalizaci JIT a používá implicitní sekvenční body.</span><span class="sxs-lookup"><span data-stu-id="f606b-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="f606b-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="f606b-146">**/dll**</span></span>|<span data-ttu-id="f606b-147">Vytvoří soubor *DLL* jako výstup.</span><span class="sxs-lookup"><span data-stu-id="f606b-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="f606b-148">**/enc:**`file`</span><span class="sxs-lookup"><span data-stu-id="f606b-148">**/enc:** `file`</span></span>|<span data-ttu-id="f606b-149">Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="f606b-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="f606b-150">Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.</span><span class="sxs-lookup"><span data-stu-id="f606b-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="f606b-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="f606b-151">**/exe**</span></span>|<span data-ttu-id="f606b-152">Vytvoří jako výstup spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f606b-152">Produces an executable file as output.</span></span> <span data-ttu-id="f606b-153">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f606b-153">This is the default.</span></span>|
|<span data-ttu-id="f606b-154">**/příznaky:**`integer`</span><span class="sxs-lookup"><span data-stu-id="f606b-154">**/flags:** `integer`</span></span>|<span data-ttu-id="f606b-155">Nastaví ImageFlags na `integer` hodnotu určenou v záhlaví běžného jazyka runtime.</span><span class="sxs-lookup"><span data-stu-id="f606b-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="f606b-156">Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje.</span><span class="sxs-lookup"><span data-stu-id="f606b-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="f606b-157">Seznam platných hodnot pro celé číslo naleznete *v*COMIMAGE_FLAGS corhdr.h.</span><span class="sxs-lookup"><span data-stu-id="f606b-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="f606b-158">**/přeložení**</span><span class="sxs-lookup"><span data-stu-id="f606b-158">**/fold**</span></span>|<span data-ttu-id="f606b-159">Sloučí identická těla metod do jednoho.</span><span class="sxs-lookup"><span data-stu-id="f606b-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="f606b-160">/**highentropieva**</span><span class="sxs-lookup"><span data-stu-id="f606b-160">/**highentropyva**</span></span>|<span data-ttu-id="f606b-161">Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="f606b-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="f606b-162">(Výchozí pro **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="f606b-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="f606b-163">**/zahrnout:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="f606b-163">**/include:** `includePath`</span></span>|<span data-ttu-id="f606b-164">Nastaví cestu k hledání `#include`souborů, které jsou součástí aplikace .</span><span class="sxs-lookup"><span data-stu-id="f606b-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="f606b-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="f606b-165">**/itanium**</span></span>|<span data-ttu-id="f606b-166">Určí jako cílový procesor Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="f606b-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="f606b-167">Pokud není zadána žádná bitová vzbitost obrazu, je výchozí **hodnota /pe64**.</span><span class="sxs-lookup"><span data-stu-id="f606b-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="f606b-168">**/klíč:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="f606b-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="f606b-169">Zkompiluje `filename` se silným podpisem `keyFile`pomocí soukromého klíče obsaženého v .</span><span class="sxs-lookup"><span data-stu-id="f606b-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="f606b-170">**/klíč:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="f606b-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="f606b-171">Zkompiluje `filename` se silným podpisem `keySource`pomocí soukromého klíče vytvořeného na adrese .</span><span class="sxs-lookup"><span data-stu-id="f606b-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="f606b-172">**/výpis**</span><span class="sxs-lookup"><span data-stu-id="f606b-172">**/listing**</span></span>|<span data-ttu-id="f606b-173">Vytvoří na standardním výstupu soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="f606b-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="f606b-174">Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.</span><span class="sxs-lookup"><span data-stu-id="f606b-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="f606b-175">Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="f606b-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="f606b-176">**/mdv:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="f606b-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="f606b-177">Nastaví řetězec verze metadat.</span><span class="sxs-lookup"><span data-stu-id="f606b-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="f606b-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="f606b-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="f606b-179">Nastaví verzi datového `major` proudu `minor` metadat, kde a jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="f606b-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="f606b-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="f606b-180">**/noautoinherit**</span></span>|<span data-ttu-id="f606b-181">Zakáže výchozí <xref:System.Object> dědičnost z doby, kdy není zadána žádná základní třída.</span><span class="sxs-lookup"><span data-stu-id="f606b-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="f606b-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="f606b-182">**/nocorstub**</span></span>|<span data-ttu-id="f606b-183">Potlačí generování zástupné procedury CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="f606b-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="f606b-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="f606b-184">**/nologo**</span></span>|<span data-ttu-id="f606b-185">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f606b-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="f606b-186">**/výstup:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="f606b-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="f606b-187">Určuje název výstupního souboru a příponu.</span><span class="sxs-lookup"><span data-stu-id="f606b-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="f606b-188">Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="f606b-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="f606b-189">Výchozí rozšíření je *.exe*.</span><span class="sxs-lookup"><span data-stu-id="f606b-189">The default extension is *.exe*.</span></span> <span data-ttu-id="f606b-190">Pokud zadáte možnost **/dll,** bude výchozí rozšíření *.dll*.</span><span class="sxs-lookup"><span data-stu-id="f606b-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="f606b-191">**Poznámka:** Zadání **/output**:myfile.dll nenastaví **/dll** možnost.</span><span class="sxs-lookup"><span data-stu-id="f606b-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="f606b-192">Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f606b-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="f606b-193">**/optimalizovat**</span><span class="sxs-lookup"><span data-stu-id="f606b-193">**/optimize**</span></span>|<span data-ttu-id="f606b-194">Optimalizuje dlouhé instrukce na krátké.</span><span class="sxs-lookup"><span data-stu-id="f606b-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="f606b-195">Například `br` do `br.s`.</span><span class="sxs-lookup"><span data-stu-id="f606b-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="f606b-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="f606b-196">**/pe64**</span></span>|<span data-ttu-id="f606b-197">Vytvoří 64bitovou kopii (PE32+).</span><span class="sxs-lookup"><span data-stu-id="f606b-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="f606b-198">Pokud není zadán žádný cílový `/itanium`procesor, výchozí hodnota je .</span><span class="sxs-lookup"><span data-stu-id="f606b-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="f606b-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="f606b-199">**/pdb**</span></span>|<span data-ttu-id="f606b-200">Vytvoří soubor PDB bez povolení sledování informací o ladění.</span><span class="sxs-lookup"><span data-stu-id="f606b-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="f606b-201">**/tichý**</span><span class="sxs-lookup"><span data-stu-id="f606b-201">**/quiet**</span></span>|<span data-ttu-id="f606b-202">Určuje tichý režim, který neoznamuje průběh sestavení.</span><span class="sxs-lookup"><span data-stu-id="f606b-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="f606b-203">**/zdroj:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="f606b-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="f606b-204">Zadaný soubor prostředků \*ve formátu RES zahrne do výsledného souboru *EXE* nebo *DLL.*</span><span class="sxs-lookup"><span data-stu-id="f606b-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="f606b-205">Pomocí možnosti **/resource** lze zadat pouze jeden soubor RES.</span><span class="sxs-lookup"><span data-stu-id="f606b-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="f606b-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="f606b-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="f606b-207">Nastaví číslo verze podsystému ve volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="f606b-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="f606b-208">Pro **/appcontainer** a **/arm** je minimální číslo verze 6.02.</span><span class="sxs-lookup"><span data-stu-id="f606b-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="f606b-209">**/zásobník:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="f606b-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="f606b-210">Nastaví hodnotu SizeOfStackReserve v `stackSize`volitelné hlavičce NT na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="f606b-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="f606b-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="f606b-211">**/stripreloc**</span></span>|<span data-ttu-id="f606b-212">Určuje, že není zapotřebí žádné přemisťování základu.</span><span class="sxs-lookup"><span data-stu-id="f606b-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="f606b-213">**/subsystém:**`integer`</span><span class="sxs-lookup"><span data-stu-id="f606b-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="f606b-214">Nastaví podsystém na `integer` hodnotu určenou v volitelné hlavičce NT.</span><span class="sxs-lookup"><span data-stu-id="f606b-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f606b-215">Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše.</span><span class="sxs-lookup"><span data-stu-id="f606b-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="f606b-216">Seznam platných hodnot pro soubor naleznete v `integer`souboru winnt.h IMAGE_SUBSYSTEM.</span><span class="sxs-lookup"><span data-stu-id="f606b-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="f606b-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="f606b-217">**/x64**</span></span>|<span data-ttu-id="f606b-218">Určí jako cílový procesor 64bitový procesor společnosti AMD.</span><span class="sxs-lookup"><span data-stu-id="f606b-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="f606b-219">Pokud není zadána žádná bitová vzbitost obrazu, je výchozí **hodnota /pe64**.</span><span class="sxs-lookup"><span data-stu-id="f606b-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="f606b-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="f606b-220">**/?**</span></span>|<span data-ttu-id="f606b-221">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="f606b-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="f606b-222">Všechny možnosti pro *ilasm.exe* jsou malá a velká písmena a rozpoznána prvními třemi písmeny.</span><span class="sxs-lookup"><span data-stu-id="f606b-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="f606b-223">Například **/lis** je ekvivalentní **/listing** a **/res**:myresfile.res je ekvivalentní **/resource**:myresfile.res. Možnosti, které určují argumenty, přijímají dvojtečku (:) nebo rovnítko (=) jako oddělovač mezi volbou a argumentem.</span><span class="sxs-lookup"><span data-stu-id="f606b-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="f606b-224">Například **/output**:*file.ext* je ekvivalentní **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="f606b-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="f606b-225">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f606b-225">Remarks</span></span>

<span data-ttu-id="f606b-226">Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL.</span><span class="sxs-lookup"><span data-stu-id="f606b-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="f606b-227">Pomocí *nástroje Ilasm.exe*se vývojáři nástrojů a kompilátorů mohou soustředit na generování IL a metadat, aniž by se zabývali vyzařováním IL ve formátu SOUBORU PE.</span><span class="sxs-lookup"><span data-stu-id="f606b-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="f606b-228">Podobně jako u jiných kompilátorů, které cílí na runtime, například C# a Visual Basic, *ilasm.exe* nevytváří zprostředkující objekt soubory a nevyžaduje propojení fázi tvořit soubor PE.</span><span class="sxs-lookup"><span data-stu-id="f606b-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="f606b-229">Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f606b-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="f606b-230">To umožňuje, aby byl spravovaný kód napsaný v některém z těchto programovacích jazyků adekvátně vyjádřen v IL Assembleru a kompilován pomocí *ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="f606b-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="f606b-231">Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="f606b-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="f606b-232">Nástroj *Ilasm.exe* můžete použít ve spojení s doprovodným nástrojem [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="f606b-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="f606b-233">*Ildasm.exe* přebírá soubor PE, který obsahuje IL kód a vytvoří textový soubor vhodný jako vstup pro *ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="f606b-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="f606b-234">Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f606b-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="f606b-235">Po kompilaci kódu a spuštění výstupu prostřednictvím *ildasm.exe*, výsledný il textový soubor lze ručně upravit přidat chybějící atributy.</span><span class="sxs-lookup"><span data-stu-id="f606b-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="f606b-236">Tento textový soubor pak můžete spustit prostřednictvím souboru *Ilasm.exe* a vytvořit tak konečný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f606b-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="f606b-237">Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.</span><span class="sxs-lookup"><span data-stu-id="f606b-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="f606b-238">Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).</span><span class="sxs-lookup"><span data-stu-id="f606b-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="f606b-239">Aby toto kombinované použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembler nenahrazuje krátké kódování pro dlouhé ty, které jste napsali ve zdrojích IL (nebo které mohou být emitovány jiným kompilátorem).</span><span class="sxs-lookup"><span data-stu-id="f606b-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="f606b-240">Použijte **možnost /optimize** k nahrazení krátkých kódování, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="f606b-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="f606b-241">*Ildasm.exe* pracuje pouze se soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="f606b-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="f606b-242">Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="f606b-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="f606b-243">Další informace o gramatické ml naleznete v souboru asmparse.grammar v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="f606b-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="f606b-244">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="f606b-244">Version Information</span></span>

<span data-ttu-id="f606b-245">Počínaje rozhraním .NET Framework 4.5 můžete k implementaci rozhraní připojit vlastní atribut pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="f606b-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

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

<span data-ttu-id="f606b-246">Počínaje rozhraním .NET Framework 4.5 můžete určit libovolný objekt BLOB zařazování (binární velký objekt) pomocí jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f606b-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="f606b-247">Další informace o gramatické ml naleznete v souboru asmparse.grammar v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="f606b-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="f606b-248">Příklady</span><span class="sxs-lookup"><span data-stu-id="f606b-248">Examples</span></span>

<span data-ttu-id="f606b-249">Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří spustitelný *soubor myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="f606b-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="f606b-250">Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří soubor *DLL* *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f606b-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="f606b-251">Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří soubor *DLL* *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f606b-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="f606b-252">Následující příklad kódu ukazuje velmi jednoduchou aplikaci, která zobrazuje "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f606b-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="f606b-253">„Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="f606b-253">to the console.</span></span> <span data-ttu-id="f606b-254">Tento kód můžete zkompilovat a potom pomocí nástroje [*Ildasm.exe*](ildasm-exe-il-disassembler.md) vygenerovat soubor IL.</span><span class="sxs-lookup"><span data-stu-id="f606b-254">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="f606b-255">Následující příklad kódu IL odpovídá předchozí ukázce kódu C#.</span><span class="sxs-lookup"><span data-stu-id="f606b-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="f606b-256">Tento kód můžete zkompilovat do sestavení pomocí nástroje IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="f606b-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="f606b-257">Příklady kódu IL i C# zobrazují "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f606b-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="f606b-258">„Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="f606b-258">to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f606b-259">Viz také</span><span class="sxs-lookup"><span data-stu-id="f606b-259">See also</span></span>

- [<span data-ttu-id="f606b-260">Nástroje</span><span class="sxs-lookup"><span data-stu-id="f606b-260">Tools</span></span>](index.md)
- [<span data-ttu-id="f606b-261">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="f606b-261">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="f606b-262">Proces spravovaného spouštění</span><span class="sxs-lookup"><span data-stu-id="f606b-262">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="f606b-263">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="f606b-263">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
