---
title: Peverify.exe (nástroj PEVerify)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104985"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="00016-102">Peverify.exe (nástroj PEVerify)</span><span class="sxs-lookup"><span data-stu-id="00016-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="00016-103">Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="00016-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="00016-104">Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím.</span><span class="sxs-lookup"><span data-stu-id="00016-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="00016-105">Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="00016-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="00016-106">V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.</span><span class="sxs-lookup"><span data-stu-id="00016-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="00016-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00016-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="00016-108">Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="00016-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="00016-109">Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="00016-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="00016-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="00016-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00016-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00016-111">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="00016-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="00016-112">Parameters</span></span>  
  
|<span data-ttu-id="00016-113">Argument</span><span class="sxs-lookup"><span data-stu-id="00016-113">Argument</span></span>|<span data-ttu-id="00016-114">Popis</span><span class="sxs-lookup"><span data-stu-id="00016-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="00016-115">*Název_souboru*</span><span class="sxs-lookup"><span data-stu-id="00016-115">*filename*</span></span>|<span data-ttu-id="00016-116">Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.</span><span class="sxs-lookup"><span data-stu-id="00016-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="00016-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="00016-117">Option</span></span>|<span data-ttu-id="00016-118">Popis</span><span class="sxs-lookup"><span data-stu-id="00016-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="00016-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="00016-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="00016-120">Přeruší ověřování po chybách *maxErrorCount.*</span><span class="sxs-lookup"><span data-stu-id="00016-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="00016-121">Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="00016-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="00016-122">**/hodiny**</span><span class="sxs-lookup"><span data-stu-id="00016-122">**/clock**</span></span>|<span data-ttu-id="00016-123">Změří a oznámí následující časy ověření v milisekundách:</span><span class="sxs-lookup"><span data-stu-id="00016-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="00016-124">**MD Val. cyklus**</span><span class="sxs-lookup"><span data-stu-id="00016-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="00016-125">Cyklus ověření metadat</span><span class="sxs-lookup"><span data-stu-id="00016-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="00016-126">**MD Val. čistý**</span><span class="sxs-lookup"><span data-stu-id="00016-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="00016-127">Čisté ověření metadat</span><span class="sxs-lookup"><span data-stu-id="00016-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="00016-128">**IL Ver. cyklus**</span><span class="sxs-lookup"><span data-stu-id="00016-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="00016-129">Cyklus ověřování Microsoft Intermediate Language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="00016-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="00016-130">**IL Ver čistý**</span><span class="sxs-lookup"><span data-stu-id="00016-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="00016-131">Čisté ověřování MSIL</span><span class="sxs-lookup"><span data-stu-id="00016-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="00016-132">**Cyklus MD Val.** a **otevírací doba IL Ver.** zahrnují čas potřebný k provedení nezbytných postupů spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="00016-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="00016-133">**MD Val. pure** a **IL Ver pure** times odrážejí čas potřebný k provedení pouze ověření nebo ověření.</span><span class="sxs-lookup"><span data-stu-id="00016-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="00016-134">**/nápověda**</span><span class="sxs-lookup"><span data-stu-id="00016-134">**/help**</span></span>|<span data-ttu-id="00016-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="00016-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="00016-136">**/hvýsledek**</span><span class="sxs-lookup"><span data-stu-id="00016-136">**/hresult**</span></span>|<span data-ttu-id="00016-137">Zobrazí kódy chyb v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="00016-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="00016-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="00016-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="00016-139">Ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="00016-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="00016-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="00016-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="00016-141">Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="00016-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="00016-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="00016-142">**/il**</span></span>|<span data-ttu-id="00016-143">Provádí kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení určeném *názvem souboru*.</span><span class="sxs-lookup"><span data-stu-id="00016-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="00016-144">Nástroj vrátí podrobné popisy pro každý nalezený problém, pokud nezadáte **/quiet** možnost.</span><span class="sxs-lookup"><span data-stu-id="00016-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="00016-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="00016-145">**/md**</span></span>|<span data-ttu-id="00016-146">Provádí kontroly ověření metadat u sestavení určeného *názvem souboru*.</span><span class="sxs-lookup"><span data-stu-id="00016-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="00016-147">Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.</span><span class="sxs-lookup"><span data-stu-id="00016-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="00016-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="00016-148">**/nologo**</span></span>|<span data-ttu-id="00016-149">Potlačí zobrazení informací o verzi a autorských právech produktu.</span><span class="sxs-lookup"><span data-stu-id="00016-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="00016-150">**/nosymboly**</span><span class="sxs-lookup"><span data-stu-id="00016-150">**/nosymbols**</span></span>|<span data-ttu-id="00016-151">V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="00016-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="00016-152">**/tichý**</span><span class="sxs-lookup"><span data-stu-id="00016-152">**/quiet**</span></span>|<span data-ttu-id="00016-153">Nastaví tichý režim; potlačí výstup hlášení problémů ověření.</span><span class="sxs-lookup"><span data-stu-id="00016-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="00016-154">Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.</span><span class="sxs-lookup"><span data-stu-id="00016-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="00016-155">Ověří pouze transparentní metody.</span><span class="sxs-lookup"><span data-stu-id="00016-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="00016-156">**/jedinečný**</span><span class="sxs-lookup"><span data-stu-id="00016-156">**/unique**</span></span>|<span data-ttu-id="00016-157">Ignoruje opakující se kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="00016-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="00016-158">**/podrobné informace**</span><span class="sxs-lookup"><span data-stu-id="00016-158">**/verbose**</span></span>|<span data-ttu-id="00016-159">V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.</span><span class="sxs-lookup"><span data-stu-id="00016-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="00016-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="00016-160">**/?**</span></span>|<span data-ttu-id="00016-161">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="00016-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00016-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00016-162">Remarks</span></span>  
 <span data-ttu-id="00016-163">Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů.</span><span class="sxs-lookup"><span data-stu-id="00016-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="00016-164">Za normálních okolností kód, který není [prokazatelně typ bezpečné](../../standard/security/key-security-concepts.md#type-safety-and-security) nelze spustit, i když můžete nastavit zásady zabezpečení povolit provádění důvěryhodného, ale neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="00016-164">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="00016-165">Pokud nejsou zadány možnosti **/md** ani **/il,** program Peverify.exe provede oba typy kontrol.</span><span class="sxs-lookup"><span data-stu-id="00016-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="00016-166">Peverify.exe nejprve provede **kontroly /md.**</span><span class="sxs-lookup"><span data-stu-id="00016-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="00016-167">Pokud nejsou žádné chyby, **/il** kontroly jsou prováděny.</span><span class="sxs-lookup"><span data-stu-id="00016-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="00016-168">Pokud zadáte **/md** a **/il**, **/il** kontroly jsou prováděny i v případě, že jsou chyby v metadatech.</span><span class="sxs-lookup"><span data-stu-id="00016-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="00016-169">Pokud tedy nejsou k dispozici žádné chyby metadat, **peverify** *peverify název souboru* je ekvivalentní **peverify** *název souboru* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="00016-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="00016-170">Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel.</span><span class="sxs-lookup"><span data-stu-id="00016-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="00016-171">Podrobné informace o kontrolách, které nástroj Peverify.exe provádí, naleznete v části Specifikace ověření metadat a Specifikace sady instrukcí msil ve složce Tools Developers Guide v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="00016-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="00016-172">Všimněte si, že rozhraní .NET Framework verze `byref` 2.0 nebo novější podporuje `dup` `ldsflda`ověřitelné `ldelema` `call` výnosy zadané pomocí následujících pokynů msil: , , `unbox` `ldflda`, a .</span><span class="sxs-lookup"><span data-stu-id="00016-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="00016-173">Příklady</span><span class="sxs-lookup"><span data-stu-id="00016-173">Examples</span></span>  
 <span data-ttu-id="00016-174">Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="00016-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="00016-175">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="00016-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="00016-176">Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="00016-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="00016-177">Nástroj zobrazí čas potřebný k provedení těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="00016-177">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="00016-178">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="00016-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="00016-179">Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="00016-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="00016-180">Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb.</span><span class="sxs-lookup"><span data-stu-id="00016-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="00016-181">Tento nástroj rovněž ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="00016-181">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="00016-182">Následující příkaz vytváří stejný výsledek jako předchozí příklad, ale určuje kódy chyb, `ignoreErrors.rsp`které chcete ignorovat v souboru odpovědí .</span><span class="sxs-lookup"><span data-stu-id="00016-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="00016-183">Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="00016-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="00016-184">Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.</span><span class="sxs-lookup"><span data-stu-id="00016-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="00016-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="00016-185">See also</span></span>

- [<span data-ttu-id="00016-186">Nástroje</span><span class="sxs-lookup"><span data-stu-id="00016-186">Tools</span></span>](index.md)
- [<span data-ttu-id="00016-187">Psaní ověřitelně typově bezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="00016-187">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="00016-188">Bezpečnost a zabezpečení typů</span><span class="sxs-lookup"><span data-stu-id="00016-188">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="00016-189">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="00016-189">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
