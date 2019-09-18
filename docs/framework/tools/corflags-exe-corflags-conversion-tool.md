---
title: CorFlags.exe (CorFlags – převodní nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b420fb451bf1bb2078a4419a648a1407c39ad178
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044744"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="9355e-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="9355e-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="9355e-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="9355e-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="9355e-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9355e-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9355e-105">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="9355e-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="9355e-106">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9355e-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="9355e-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="9355e-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9355e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9355e-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="9355e-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="9355e-109">Parameters</span></span>  
  
|<span data-ttu-id="9355e-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="9355e-110">Required parameter</span></span>|<span data-ttu-id="9355e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9355e-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="9355e-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="9355e-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="9355e-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="9355e-113">Option</span></span>|<span data-ttu-id="9355e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9355e-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9355e-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="9355e-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="9355e-116">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="9355e-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="9355e-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="9355e-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="9355e-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="9355e-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="9355e-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="9355e-119">**/32BITPREF+**</span></span>|<span data-ttu-id="9355e-120">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="9355e-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="9355e-121">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="9355e-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="9355e-122">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="9355e-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="9355e-123">Pokud je příznak nastaven na knihovnu DLL, knihovna DLL se nenačte v 64ch procesech a <xref:System.BadImageFormatException> vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="9355e-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="9355e-124">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="9355e-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="9355e-125">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="9355e-125">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="9355e-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="9355e-126">**/32BITPREF-**</span></span>|<span data-ttu-id="9355e-127">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="9355e-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="9355e-128">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="9355e-128">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="9355e-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="9355e-129">**/?**</span></span>|<span data-ttu-id="9355e-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="9355e-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9355e-131">**/Force.**</span><span class="sxs-lookup"><span data-stu-id="9355e-131">**/Force**</span></span>|<span data-ttu-id="9355e-132">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9355e-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="9355e-133">**Důležité:**  Při aktualizaci sestavení se silným názvem je nutné toto sestavení před spuštěním jeho kódu znovu podepsat.</span><span class="sxs-lookup"><span data-stu-id="9355e-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="9355e-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="9355e-134">**/help**</span></span>|<span data-ttu-id="9355e-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="9355e-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9355e-136">**/ILONLY +**</span><span class="sxs-lookup"><span data-stu-id="9355e-136">**/ILONLY+**</span></span>|<span data-ttu-id="9355e-137">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="9355e-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="9355e-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="9355e-138">**/ILONLY-**</span></span>|<span data-ttu-id="9355e-139">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="9355e-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="9355e-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="9355e-140">**/nologo**</span></span>|<span data-ttu-id="9355e-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9355e-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="9355e-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="9355e-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="9355e-143">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="9355e-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="9355e-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="9355e-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="9355e-145">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="9355e-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="9355e-146">**Poznámka:**  Pro nativní spuštění musí mít sestavení hlavičku modulu CLR verze 2.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9355e-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9355e-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9355e-147">Remarks</span></span>  
 <span data-ttu-id="9355e-148">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="9355e-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9355e-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9355e-149">See also</span></span>

- [<span data-ttu-id="9355e-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="9355e-150">Tools</span></span>](index.md)
- [<span data-ttu-id="9355e-151">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="9355e-151">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="9355e-152">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="9355e-152">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
