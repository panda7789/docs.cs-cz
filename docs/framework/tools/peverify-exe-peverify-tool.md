---
title: Peverify.exe (nástroj PEVerify)
description: Pomocí Peverify.exe (přenosné spustitelné soubory) můžete určit, jestli kód jazyka MSIL (Microsoft Intermediate Language) & metadata splňují standardy zabezpečení typu v .NET.
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
ms.openlocfilehash: d7962bc91d89d3bd183697011aed1afca0fb0fc1
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904205"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="eaa13-103">Peverify.exe (nástroj PEVerify)</span><span class="sxs-lookup"><span data-stu-id="eaa13-103">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="eaa13-104">Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="eaa13-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="eaa13-105">Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím.</span><span class="sxs-lookup"><span data-stu-id="eaa13-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="eaa13-106">Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-106">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="eaa13-107">V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.</span><span class="sxs-lookup"><span data-stu-id="eaa13-107">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="eaa13-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eaa13-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="eaa13-109">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="eaa13-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="eaa13-110">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="eaa13-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="eaa13-111">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="eaa13-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa13-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaa13-112">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa13-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaa13-113">Parameters</span></span>  
  
|<span data-ttu-id="eaa13-114">Argument</span><span class="sxs-lookup"><span data-stu-id="eaa13-114">Argument</span></span>|<span data-ttu-id="eaa13-115">Description</span><span class="sxs-lookup"><span data-stu-id="eaa13-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="eaa13-116">*Bitmap*</span><span class="sxs-lookup"><span data-stu-id="eaa13-116">*filename*</span></span>|<span data-ttu-id="eaa13-117">Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.</span><span class="sxs-lookup"><span data-stu-id="eaa13-117">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="eaa13-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="eaa13-118">Option</span></span>|<span data-ttu-id="eaa13-119">Description</span><span class="sxs-lookup"><span data-stu-id="eaa13-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eaa13-120">**/Break =** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="eaa13-120">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="eaa13-121">Po *maxErrorCount* chybách zruší ověření.</span><span class="sxs-lookup"><span data-stu-id="eaa13-121">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="eaa13-122">Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="eaa13-122">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="eaa13-123">**/clock**</span><span class="sxs-lookup"><span data-stu-id="eaa13-123">**/clock**</span></span>|<span data-ttu-id="eaa13-124">Změří a oznámí následující časy ověření v milisekundách:</span><span class="sxs-lookup"><span data-stu-id="eaa13-124">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="eaa13-125">**MD Val. koloběh**</span><span class="sxs-lookup"><span data-stu-id="eaa13-125">**MD Val. cycle**</span></span><br /> <span data-ttu-id="eaa13-126">Cyklus ověření metadat</span><span class="sxs-lookup"><span data-stu-id="eaa13-126">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="eaa13-127">**MD Val. Pure**</span><span class="sxs-lookup"><span data-stu-id="eaa13-127">**MD Val. pure**</span></span><br /> <span data-ttu-id="eaa13-128">Čisté ověření metadat</span><span class="sxs-lookup"><span data-stu-id="eaa13-128">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="eaa13-129">**IL – ver. koloběh**</span><span class="sxs-lookup"><span data-stu-id="eaa13-129">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="eaa13-130">Cyklus ověřování Microsoft Intermediate Language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="eaa13-130">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="eaa13-131">**IL – ver – čistá**</span><span class="sxs-lookup"><span data-stu-id="eaa13-131">**IL Ver pure**</span></span><br /> <span data-ttu-id="eaa13-132">Čisté ověřování MSIL</span><span class="sxs-lookup"><span data-stu-id="eaa13-132">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="eaa13-133">Časy **MD Val. Cycle** a **Il ver. Cycle** zahrnují dobu potřebnou k provedení nezbytných postupů spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="eaa13-133">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="eaa13-134">Časy **MD Val. Pure** a **Il verze Pure** odrážejí dobu potřebnou k provedení ověřování nebo ověření.</span><span class="sxs-lookup"><span data-stu-id="eaa13-134">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="eaa13-135">**/Help**</span><span class="sxs-lookup"><span data-stu-id="eaa13-135">**/help**</span></span>|<span data-ttu-id="eaa13-136">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="eaa13-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="eaa13-137">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="eaa13-137">**/hresult**</span></span>|<span data-ttu-id="eaa13-138">Zobrazí kódy chyb v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-138">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="eaa13-139">**/Ignore =** *Hex. Code* [, *Hex. Code*]</span><span class="sxs-lookup"><span data-stu-id="eaa13-139">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="eaa13-140">Ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="eaa13-140">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="eaa13-141">**/Ignore = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="eaa13-141">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="eaa13-142">Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="eaa13-142">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="eaa13-143">**/Il**</span><span class="sxs-lookup"><span data-stu-id="eaa13-143">**/il**</span></span>|<span data-ttu-id="eaa13-144">Provede kontroly ověřování bezpečnosti typů jazyka MSIL pro metody implementované v sestavení určeném parametrem *filename*.</span><span class="sxs-lookup"><span data-stu-id="eaa13-144">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="eaa13-145">Nástroj vrátí podrobné popisy jednotlivých nalezených problémů, pokud nezadáte možnost **/quiet** .</span><span class="sxs-lookup"><span data-stu-id="eaa13-145">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="eaa13-146">**/MD**</span><span class="sxs-lookup"><span data-stu-id="eaa13-146">**/md**</span></span>|<span data-ttu-id="eaa13-147">Provádí kontroly ověřování metadat u sestavení určeného parametrem *filename*.</span><span class="sxs-lookup"><span data-stu-id="eaa13-147">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="eaa13-148">Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.</span><span class="sxs-lookup"><span data-stu-id="eaa13-148">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="eaa13-149">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="eaa13-149">**/nologo**</span></span>|<span data-ttu-id="eaa13-150">Potlačí zobrazení informací o verzi a autorských právech produktu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-150">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="eaa13-151">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="eaa13-151">**/nosymbols**</span></span>|<span data-ttu-id="eaa13-152">V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="eaa13-152">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="eaa13-153">**parametr**</span><span class="sxs-lookup"><span data-stu-id="eaa13-153">**/quiet**</span></span>|<span data-ttu-id="eaa13-154">Nastaví tichý režim; potlačí výstup hlášení problémů ověření.</span><span class="sxs-lookup"><span data-stu-id="eaa13-154">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="eaa13-155">Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-155">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="eaa13-156">Ověří pouze transparentní metody.</span><span class="sxs-lookup"><span data-stu-id="eaa13-156">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="eaa13-157">**/Unique**</span><span class="sxs-lookup"><span data-stu-id="eaa13-157">**/unique**</span></span>|<span data-ttu-id="eaa13-158">Ignoruje opakující se kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="eaa13-158">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="eaa13-159">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="eaa13-159">**/verbose**</span></span>|<span data-ttu-id="eaa13-160">V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.</span><span class="sxs-lookup"><span data-stu-id="eaa13-160">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="eaa13-161">**/?**</span><span class="sxs-lookup"><span data-stu-id="eaa13-161">**/?**</span></span>|<span data-ttu-id="eaa13-162">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="eaa13-162">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa13-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaa13-163">Remarks</span></span>  
 <span data-ttu-id="eaa13-164">Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů.</span><span class="sxs-lookup"><span data-stu-id="eaa13-164">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="eaa13-165">Kód, který není [ověřovatelně typově bezpečný](../../standard/security/key-security-concepts.md#type-safety-and-security) , se normálně nedá spustit, i když můžete nastavit zásady zabezpečení, které umožňují spuštění důvěryhodného, ale neověřitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-165">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="eaa13-166">Pokud nejsou zadány žádné možnosti **/MD** ani **/Il** , Peverify.exe provádí oba typy kontrol.</span><span class="sxs-lookup"><span data-stu-id="eaa13-166">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="eaa13-167">Peverify.exe nejprve provádí kontroly **/MD** .</span><span class="sxs-lookup"><span data-stu-id="eaa13-167">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="eaa13-168">V případě, že nejsou k dispozici žádné chyby, provedou se kontroly **/Il** .</span><span class="sxs-lookup"><span data-stu-id="eaa13-168">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="eaa13-169">Pokud zadáte obě **/MD** i **/Il**, kontroly **/Il** se provedou, i když v metadatech dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="eaa13-169">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="eaa13-170">Proto pokud nejsou k dispozici žádné chyby metadat, *název souboru* **Nástroj PEVerify** je ekvivalentní **Nástroj PEVerify** *název_souboru* **/MD** **/Il**.</span><span class="sxs-lookup"><span data-stu-id="eaa13-170">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="eaa13-171">Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel.</span><span class="sxs-lookup"><span data-stu-id="eaa13-171">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="eaa13-172">Podrobné informace o kontrolách, které Peverify.exe provádí, naleznete v části specifikace ověření metadat a specifikace sady MSIL instrukcí ve složce průvodce pro vývojáře v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="eaa13-172">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="eaa13-173">Všimněte si, že .NET Framework verze 2,0 nebo novější podporuje ověřitelné `byref` návraty zadané pomocí následujících instrukcí jazyka MSIL: `dup` , `ldsflda` ,, `ldflda` `ldelema` `call` a `unbox` .</span><span class="sxs-lookup"><span data-stu-id="eaa13-173">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="eaa13-174">Příklady</span><span class="sxs-lookup"><span data-stu-id="eaa13-174">Examples</span></span>  
 <span data-ttu-id="eaa13-175">Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="eaa13-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="eaa13-176">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-176">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="eaa13-177">Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="eaa13-177">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="eaa13-178">Nástroj zobrazí čas potřebný k provedení těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="eaa13-178">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="eaa13-179">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="eaa13-179">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="eaa13-180">Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="eaa13-180">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="eaa13-181">Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb.</span><span class="sxs-lookup"><span data-stu-id="eaa13-181">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="eaa13-182">Tento nástroj rovněž ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="eaa13-182">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="eaa13-183">Následující příkaz vytvoří stejný výsledek jako výše předchozí příklad, ale Určuje kódy chyb, které se mají v souboru odpovědí ignorovat `ignoreErrors.rsp` .</span><span class="sxs-lookup"><span data-stu-id="eaa13-183">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="eaa13-184">Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="eaa13-184">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="eaa13-185">Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.</span><span class="sxs-lookup"><span data-stu-id="eaa13-185">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaa13-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaa13-186">See also</span></span>

- [<span data-ttu-id="eaa13-187">Nástroje</span><span class="sxs-lookup"><span data-stu-id="eaa13-187">Tools</span></span>](index.md)
- [<span data-ttu-id="eaa13-188">Zápis ověřitelného kódu bezpečného typu</span><span class="sxs-lookup"><span data-stu-id="eaa13-188">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="eaa13-189">Bezpečnost typů a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eaa13-189">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="eaa13-190">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="eaa13-190">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
