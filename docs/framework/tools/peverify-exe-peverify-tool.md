---
title: "Peverify.exe (nástroj PEVerify)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 855a1122eb4507912adca80878f78258b37d202d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="6caf9-102">Peverify.exe (nástroj PEVerify)</span><span class="sxs-lookup"><span data-stu-id="6caf9-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="6caf9-103">Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="6caf9-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="6caf9-104">Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím.</span><span class="sxs-lookup"><span data-stu-id="6caf9-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="6caf9-105">Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="6caf9-106">V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.</span><span class="sxs-lookup"><span data-stu-id="6caf9-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="6caf9-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6caf9-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6caf9-108">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="6caf9-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6caf9-109">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6caf9-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6caf9-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="6caf9-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6caf9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6caf9-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6caf9-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="6caf9-112">Parameters</span></span>  
  
|<span data-ttu-id="6caf9-113">Argument</span><span class="sxs-lookup"><span data-stu-id="6caf9-113">Argument</span></span>|<span data-ttu-id="6caf9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6caf9-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6caf9-115">*Název souboru*</span><span class="sxs-lookup"><span data-stu-id="6caf9-115">*filename*</span></span>|<span data-ttu-id="6caf9-116">Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.</span><span class="sxs-lookup"><span data-stu-id="6caf9-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="6caf9-117">Možnost</span><span class="sxs-lookup"><span data-stu-id="6caf9-117">Option</span></span>|<span data-ttu-id="6caf9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6caf9-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6caf9-119">**/ Rozdělit =** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="6caf9-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="6caf9-120">Zruší ověření po *maxErrorCount* chyby.</span><span class="sxs-lookup"><span data-stu-id="6caf9-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="6caf9-121">Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="6caf9-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="6caf9-122">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="6caf9-122">**/clock**</span></span>|<span data-ttu-id="6caf9-123">Změří a oznámí následující časy ověření v milisekundách:</span><span class="sxs-lookup"><span data-stu-id="6caf9-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="6caf9-124">**MD úč.hod cyklu**</span><span class="sxs-lookup"><span data-stu-id="6caf9-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="6caf9-125">Cyklus ověření metadat</span><span class="sxs-lookup"><span data-stu-id="6caf9-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="6caf9-126">**MD úč.hod čisté**</span><span class="sxs-lookup"><span data-stu-id="6caf9-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="6caf9-127">Čisté ověření metadat</span><span class="sxs-lookup"><span data-stu-id="6caf9-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="6caf9-128">**Cyklus IL verze**</span><span class="sxs-lookup"><span data-stu-id="6caf9-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="6caf9-129">Cyklus ověřování Microsoft Intermediate Language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="6caf9-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="6caf9-130">**Čistého IL Ver**</span><span class="sxs-lookup"><span data-stu-id="6caf9-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="6caf9-131">Čisté ověřování MSIL</span><span class="sxs-lookup"><span data-stu-id="6caf9-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="6caf9-132">**MD úč.hod cyklus** a **IL verze cyklus** časy zahrnout čas potřebný k provést nezbytné postupy spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="6caf9-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="6caf9-133">**MD úč.hod čistý** a **čistého IL Ver** časy reflektovat čas potřebné k provedení ověření nebo pouze ověření.</span><span class="sxs-lookup"><span data-stu-id="6caf9-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="6caf9-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="6caf9-134">**/help**</span></span>|<span data-ttu-id="6caf9-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="6caf9-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="6caf9-136">**/HRESULT**</span><span class="sxs-lookup"><span data-stu-id="6caf9-136">**/hresult**</span></span>|<span data-ttu-id="6caf9-137">Zobrazí kódy chyb v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="6caf9-138">**/ Ignorovat =** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="6caf9-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="6caf9-139">Ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="6caf9-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="6caf9-140">**/ Ignorovat = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="6caf9-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="6caf9-141">Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="6caf9-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="6caf9-142">**/IL**</span><span class="sxs-lookup"><span data-stu-id="6caf9-142">**/il**</span></span>|<span data-ttu-id="6caf9-143">Provádí kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení určeného *filename*.</span><span class="sxs-lookup"><span data-stu-id="6caf9-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="6caf9-144">Nástroj Vrátí podrobný popis pro jednotlivé problémy najít nezadáte **/quiet** možnost.</span><span class="sxs-lookup"><span data-stu-id="6caf9-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="6caf9-145">**/MD**</span><span class="sxs-lookup"><span data-stu-id="6caf9-145">**/md**</span></span>|<span data-ttu-id="6caf9-146">Provádí ověřovací kontroly metadata sestavení s určeného *filename*.</span><span class="sxs-lookup"><span data-stu-id="6caf9-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="6caf9-147">Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.</span><span class="sxs-lookup"><span data-stu-id="6caf9-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="6caf9-148">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="6caf9-148">**/nologo**</span></span>|<span data-ttu-id="6caf9-149">Potlačí zobrazení informací o verzi a autorských právech produktu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="6caf9-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="6caf9-150">**/nosymbols**</span></span>|<span data-ttu-id="6caf9-151">V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="6caf9-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="6caf9-152">**/ quiet**</span><span class="sxs-lookup"><span data-stu-id="6caf9-152">**/quiet**</span></span>|<span data-ttu-id="6caf9-153">Nastaví tichý režim; potlačí výstup hlášení problémů ověření.</span><span class="sxs-lookup"><span data-stu-id="6caf9-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="6caf9-154">Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="6caf9-155">Ověří pouze transparentní metody.</span><span class="sxs-lookup"><span data-stu-id="6caf9-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="6caf9-156">**/ Jedinečný**</span><span class="sxs-lookup"><span data-stu-id="6caf9-156">**/unique**</span></span>|<span data-ttu-id="6caf9-157">Ignoruje opakující se kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="6caf9-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="6caf9-158">**/ verbose**</span><span class="sxs-lookup"><span data-stu-id="6caf9-158">**/verbose**</span></span>|<span data-ttu-id="6caf9-159">V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.</span><span class="sxs-lookup"><span data-stu-id="6caf9-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="6caf9-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="6caf9-160">**/?**</span></span>|<span data-ttu-id="6caf9-161">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="6caf9-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6caf9-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6caf9-162">Remarks</span></span>  
 <span data-ttu-id="6caf9-163">Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů.</span><span class="sxs-lookup"><span data-stu-id="6caf9-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="6caf9-164">Za normálních okolností kód, který není [ověřitelný typ](http://msdn.microsoft.com/en-us/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) nelze spustit, i když můžete nastavit zásady zabezpečení pro povolení spuštění kódu důvěryhodné, ale nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="6caf9-164">Normally, code that is not [verifiably type safe](http://msdn.microsoft.com/en-us/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="6caf9-165">Pokud **/md** ani **/il** jsou zadány možnosti, Peverify.exe provede oba typy kontrol.</span><span class="sxs-lookup"><span data-stu-id="6caf9-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="6caf9-166">Provede PEVerify.exe **/md** nejprve hledá.</span><span class="sxs-lookup"><span data-stu-id="6caf9-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="6caf9-167">Pokud nejsou žádné chyby **/il** kontroly se provádějí.</span><span class="sxs-lookup"><span data-stu-id="6caf9-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="6caf9-168">Pokud zadáte oba **/md** a **/il**, **/il** kontroly se provádějí i v případě, že jsou chyby v metadatech.</span><span class="sxs-lookup"><span data-stu-id="6caf9-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="6caf9-169">Proto v případě, že nejsou žádné chyby metadat **peverify** *filename* je ekvivalentní **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="6caf9-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="6caf9-170">Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel.</span><span class="sxs-lookup"><span data-stu-id="6caf9-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="6caf9-171">Podrobné informace o kontrolách Peverify.exe provádí, najdete v části "Ověření specifikace metadat" a "MSIL instrukcí nastavit specifikace" ve složce Nástroje Příručka pro vývojáře v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6caf9-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="6caf9-172">Rozhraní .NET Framework verze 2.0 nebo novější podporuje ověřitelný `byref` vrátí zadán pomocí následujících pokynů MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` a `unbox`.</span><span class="sxs-lookup"><span data-stu-id="6caf9-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6caf9-173">Příklady</span><span class="sxs-lookup"><span data-stu-id="6caf9-173">Examples</span></span>  
 <span data-ttu-id="6caf9-174">Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="6caf9-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="6caf9-175">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="6caf9-176">Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="6caf9-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="6caf9-177">Nástroj zobrazí čas potřebný k provedení těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="6caf9-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="6caf9-178">Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="6caf9-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="6caf9-179">Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="6caf9-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="6caf9-180">Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb.</span><span class="sxs-lookup"><span data-stu-id="6caf9-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="6caf9-181">Tento nástroj rovněž ignoruje zadané kódy chyb.</span><span class="sxs-lookup"><span data-stu-id="6caf9-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="6caf9-182">Následující příkaz vytvoří stejný výsledek jako výše předchozí příklad, ale Určuje kódy chyb ignorovat v souboru odpovědí, `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="6caf9-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="6caf9-183">Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="6caf9-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="6caf9-184">Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.</span><span class="sxs-lookup"><span data-stu-id="6caf9-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="6caf9-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="6caf9-185">See Also</span></span>  
 [<span data-ttu-id="6caf9-186">Nástroje</span><span class="sxs-lookup"><span data-stu-id="6caf9-186">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="6caf9-187">NIB: Zápis typ ověřitelný kód</span><span class="sxs-lookup"><span data-stu-id="6caf9-187">NIB: Writing Verifiably Type-Safe Code</span></span>](http://msdn.microsoft.com/en-us/d18f10ef-3b48-4f47-8726-96714021547b)  
 [<span data-ttu-id="6caf9-188">Typ zabezpečení a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6caf9-188">Type Safety and Security</span></span>](http://msdn.microsoft.com/en-us/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [<span data-ttu-id="6caf9-189">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="6caf9-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
