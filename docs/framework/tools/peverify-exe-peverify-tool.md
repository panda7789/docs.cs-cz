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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0423946ab32c04274bb3d5656ed8603ec4314d88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128730"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="a123b-102">Peverify.exe (nástroj PEVerify)</span><span class="sxs-lookup"><span data-stu-id="a123b-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="a123b-103">Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="a123b-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="a123b-104">Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím.</span><span class="sxs-lookup"><span data-stu-id="a123b-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="a123b-105">Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="a123b-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="a123b-106">V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.</span><span class="sxs-lookup"><span data-stu-id="a123b-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="a123b-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a123b-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a123b-108">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a123b-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a123b-109">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a123b-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a123b-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="a123b-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a123b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a123b-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="a123b-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="a123b-112">Parameters</span></span>  
  
|<span data-ttu-id="a123b-113">Argument</span><span class="sxs-lookup"><span data-stu-id="a123b-113">Argument</span></span>|<span data-ttu-id="a123b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a123b-114">Description</span></span>|  
|--------------|-----------------|  
|*<span data-ttu-id="a123b-115">filename</span><span class="sxs-lookup"><span data-stu-id="a123b-115">filename</span></span>*|<span data-ttu-id="a123b-116">Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.</span><span class="sxs-lookup"><span data-stu-id="a123b-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="a123b-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="a123b-117">Option</span></span>|<span data-ttu-id="a123b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a123b-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a123b-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="a123b-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="a123b-120">Přeruší ověřování po *maxErrorCount* chyby.</span><span class="sxs-lookup"><span data-stu-id="a123b-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="a123b-121">Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="a123b-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|**<span data-ttu-id="a123b-122">/clock</span><span class="sxs-lookup"><span data-stu-id="a123b-122">/clock</span></span>**|<span data-ttu-id="a123b-123">Změří a oznámí následující časy ověření v milisekundách:</span><span class="sxs-lookup"><span data-stu-id="a123b-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> **<span data-ttu-id="a123b-124">MD Val.</span><span class="sxs-lookup"><span data-stu-id="a123b-124">MD Val.</span></span> <span data-ttu-id="a123b-125">Cyklus</span><span class="sxs-lookup"><span data-stu-id="a123b-125">cycle</span></span>**<br /> <span data-ttu-id="a123b-126">Cyklus ověření metadat</span><span class="sxs-lookup"><span data-stu-id="a123b-126">Metadata validation cycle</span></span><br /><br /> **<span data-ttu-id="a123b-127">MD Val.</span><span class="sxs-lookup"><span data-stu-id="a123b-127">MD Val.</span></span> <span data-ttu-id="a123b-128">pouze</span><span class="sxs-lookup"><span data-stu-id="a123b-128">pure</span></span>**<br /> <span data-ttu-id="a123b-129">Čisté ověření metadat</span><span class="sxs-lookup"><span data-stu-id="a123b-129">Metadata validation pure</span></span><br /><br /> **<span data-ttu-id="a123b-130">IL Ver.</span><span class="sxs-lookup"><span data-stu-id="a123b-130">IL Ver.</span></span> <span data-ttu-id="a123b-131">Cyklus</span><span class="sxs-lookup"><span data-stu-id="a123b-131">cycle</span></span>**<br /> <span data-ttu-id="a123b-132">Cyklus ověřování Microsoft Intermediate Language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="a123b-132">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> **<span data-ttu-id="a123b-133">IL Ver pure</span><span class="sxs-lookup"><span data-stu-id="a123b-133">IL Ver pure</span></span>**<br /> <span data-ttu-id="a123b-134">Čisté ověřování MSIL</span><span class="sxs-lookup"><span data-stu-id="a123b-134">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="a123b-135">**MD Val. cycle** a **IL Ver. cycle** časy zahrnují čas potřebný k provedení potřebné procedur spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="a123b-135">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="a123b-136">**MD Val. pure** a **IL Ver pure** časy odrážet čas potřebný k provedení ověření nebo jenom k ověření.</span><span class="sxs-lookup"><span data-stu-id="a123b-136">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|**<span data-ttu-id="a123b-137">/help</span><span class="sxs-lookup"><span data-stu-id="a123b-137">/help</span></span>**|<span data-ttu-id="a123b-138">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a123b-138">Displays command syntax and options for the tool.</span></span>|  
|**<span data-ttu-id="a123b-139">/hresult</span><span class="sxs-lookup"><span data-stu-id="a123b-139">/hresult</span></span>**|<span data-ttu-id="a123b-140">Zobrazí kódy chyb v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="a123b-140">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="a123b-141">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="a123b-141">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="a123b-142">Ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="a123b-142">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="a123b-143">**/ Ignorovat = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="a123b-143">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="a123b-144">Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="a123b-144">Ignores the error codes listed in the specified response file.</span></span>|  
|**<span data-ttu-id="a123b-145">/il</span><span class="sxs-lookup"><span data-stu-id="a123b-145">/il</span></span>**|<span data-ttu-id="a123b-146">Provádí kontroly ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení určeném parametrem *filename*.</span><span class="sxs-lookup"><span data-stu-id="a123b-146">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="a123b-147">Nástroj Vrátí podrobný popis každého nalezeného problému, pokud zadáte **/quiet** možnost.</span><span class="sxs-lookup"><span data-stu-id="a123b-147">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|**<span data-ttu-id="a123b-148">/md</span><span class="sxs-lookup"><span data-stu-id="a123b-148">/md</span></span>**|<span data-ttu-id="a123b-149">Provádí kontroly ověřování metadat na sestavení určeném parametrem *filename*.</span><span class="sxs-lookup"><span data-stu-id="a123b-149">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="a123b-150">Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.</span><span class="sxs-lookup"><span data-stu-id="a123b-150">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|**<span data-ttu-id="a123b-151">/nologo</span><span class="sxs-lookup"><span data-stu-id="a123b-151">/nologo</span></span>**|<span data-ttu-id="a123b-152">Potlačí zobrazení informací o verzi a autorských právech produktu.</span><span class="sxs-lookup"><span data-stu-id="a123b-152">Suppresses the display of product version and copyright information.</span></span>|  
|**<span data-ttu-id="a123b-153">/nosymbols</span><span class="sxs-lookup"><span data-stu-id="a123b-153">/nosymbols</span></span>**|<span data-ttu-id="a123b-154">V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="a123b-154">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|**<span data-ttu-id="a123b-155">/quiet</span><span class="sxs-lookup"><span data-stu-id="a123b-155">/quiet</span></span>**|<span data-ttu-id="a123b-156">Nastaví tichý režim; potlačí výstup hlášení problémů ověření.</span><span class="sxs-lookup"><span data-stu-id="a123b-156">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="a123b-157">Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.</span><span class="sxs-lookup"><span data-stu-id="a123b-157">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="a123b-158">Ověří pouze transparentní metody.</span><span class="sxs-lookup"><span data-stu-id="a123b-158">Verify only the transparent methods.</span></span>|  
|**<span data-ttu-id="a123b-159">/unique</span><span class="sxs-lookup"><span data-stu-id="a123b-159">/unique</span></span>**|<span data-ttu-id="a123b-160">Ignoruje opakující se kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="a123b-160">Ignores repeating error codes.</span></span>|  
|**<span data-ttu-id="a123b-161">/verbose</span><span class="sxs-lookup"><span data-stu-id="a123b-161">/verbose</span></span>**|<span data-ttu-id="a123b-162">V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.</span><span class="sxs-lookup"><span data-stu-id="a123b-162">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|**<span data-ttu-id="a123b-163">/?</span><span class="sxs-lookup"><span data-stu-id="a123b-163">/?</span></span>**|<span data-ttu-id="a123b-164">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a123b-164">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a123b-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a123b-165">Remarks</span></span>  
 <span data-ttu-id="a123b-166">Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů.</span><span class="sxs-lookup"><span data-stu-id="a123b-166">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="a123b-167">Za normálních okolností kód, který není [ověřitelně bezpečnost typů](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) nelze spustit, nicméně můžete nastavit zásady zabezpečení umožňující spuštění důvěryhodného ale neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="a123b-167">Normally, code that is not [verifiably type safe](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="a123b-168">Pokud ani **/md** ani **/il** jsou zadány možnosti, Peverify.exe provede oba typy kontrol.</span><span class="sxs-lookup"><span data-stu-id="a123b-168">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="a123b-169">PEVerify.exe provádí **/md** nejprve.</span><span class="sxs-lookup"><span data-stu-id="a123b-169">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="a123b-170">Pokud zde nejsou žádné chyby **/il** kontroly jsou prováděny.</span><span class="sxs-lookup"><span data-stu-id="a123b-170">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="a123b-171">Pokud zadáte obě **/md** a **/il**, **/il** kontroly jsou prováděny, i když nejsou chyby v metadatech.</span><span class="sxs-lookup"><span data-stu-id="a123b-171">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="a123b-172">Proto, pokud nejsou žádné chyby metadat **peverify** *filename* je ekvivalentní **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="a123b-172">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="a123b-173">Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel.</span><span class="sxs-lookup"><span data-stu-id="a123b-173">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="a123b-174">Podrobné informace o kontrolách Peverify.exe provádí, podívejte se "specifikace ověřování metadat" a "MSIL specifikace sady instrukcí" ve složce Tools Developers Guide v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a123b-174">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="a123b-175">Všimněte si, že rozhraní .NET Framework verze 2.0 nebo novější podporuje ověřitelné `byref` zadané pomocí následujících instrukcí jazyka MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` a `unbox`.</span><span class="sxs-lookup"><span data-stu-id="a123b-175">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a123b-176">Příklady</span><span class="sxs-lookup"><span data-stu-id="a123b-176">Examples</span></span>  
 <span data-ttu-id="a123b-177">Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="a123b-177">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="a123b-178">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="a123b-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="a123b-179">Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="a123b-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="a123b-180">Nástroj zobrazí čas potřebný k provedení těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="a123b-180">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="a123b-181">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="a123b-181">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="a123b-182">Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="a123b-182">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="a123b-183">Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb.</span><span class="sxs-lookup"><span data-stu-id="a123b-183">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="a123b-184">Tento nástroj rovněž ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="a123b-184">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="a123b-185">Následující příkaz vytvoří stejný výsledek jako předchozí příklad výše, ale Určuje kódy chyb v souboru odpovědí `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="a123b-185">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="a123b-186">Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="a123b-186">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="a123b-187">Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.</span><span class="sxs-lookup"><span data-stu-id="a123b-187">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="a123b-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a123b-188">See also</span></span>

- [<span data-ttu-id="a123b-189">Nástroje</span><span class="sxs-lookup"><span data-stu-id="a123b-189">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="a123b-190">Psát kód Ověřitelně bezpečného typu</span><span class="sxs-lookup"><span data-stu-id="a123b-190">Writing Verifiably Type-Safe Code</span></span>](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="a123b-191">Bezpečnost typů a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a123b-191">Type Safety and Security</span></span>](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="a123b-192">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="a123b-192">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
