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
ms.openlocfilehash: d4a5b6d490387f2da441ad95bdf369f700cf2e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400026"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="20295-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="20295-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="20295-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="20295-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="20295-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20295-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="20295-105">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="20295-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="20295-106">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="20295-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="20295-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="20295-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20295-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20295-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20295-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="20295-109">Parameters</span></span>  
  
|<span data-ttu-id="20295-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="20295-110">Required parameter</span></span>|<span data-ttu-id="20295-111">Popis</span><span class="sxs-lookup"><span data-stu-id="20295-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="20295-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="20295-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="20295-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="20295-113">Option</span></span>|<span data-ttu-id="20295-114">Popis</span><span class="sxs-lookup"><span data-stu-id="20295-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20295-115">**/ 32BITOVÉ [NO] +**</span><span class="sxs-lookup"><span data-stu-id="20295-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="20295-116">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="20295-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="20295-117">**/ 32BITOVÉ [NO]-**</span><span class="sxs-lookup"><span data-stu-id="20295-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="20295-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="20295-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="20295-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="20295-119">**/32BITPREF+**</span></span>|<span data-ttu-id="20295-120">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="20295-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="20295-121">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="20295-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="20295-122">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="20295-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="20295-123">Pokud je nastavený příznak na knihovnu DLL, knihovny DLL nepodaří načíst v 64bitové procesy a <xref:System.BadImageFormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="20295-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="20295-124">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="20295-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="20295-125">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20295-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="20295-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="20295-126">**/32BITPREF-**</span></span>|<span data-ttu-id="20295-127">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="20295-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="20295-128">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20295-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="20295-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="20295-129">**/?**</span></span>|<span data-ttu-id="20295-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="20295-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="20295-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="20295-131">**/Force**</span></span>|<span data-ttu-id="20295-132">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="20295-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="20295-133">**Důležité:** Pokud aktualizujete sestavení se silným názvem, musíte se odhlásit ho znovu před provedením jeho kód.</span><span class="sxs-lookup"><span data-stu-id="20295-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="20295-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="20295-134">**/help**</span></span>|<span data-ttu-id="20295-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="20295-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="20295-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="20295-136">**/ILONLY+**</span></span>|<span data-ttu-id="20295-137">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="20295-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="20295-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="20295-138">**/ILONLY-**</span></span>|<span data-ttu-id="20295-139">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="20295-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="20295-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="20295-140">**/nologo**</span></span>|<span data-ttu-id="20295-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="20295-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="20295-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="20295-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="20295-143">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="20295-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="20295-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="20295-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="20295-145">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="20295-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="20295-146">**Poznámka:** sestavení musí mít hlavička CLR verzi 2.5 nebo novější, abyste mohli spustit nativně.</span><span class="sxs-lookup"><span data-stu-id="20295-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20295-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20295-147">Remarks</span></span>  
 <span data-ttu-id="20295-148">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="20295-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20295-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="20295-149">See Also</span></span>  
 [<span data-ttu-id="20295-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="20295-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="20295-151">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="20295-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="20295-152">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="20295-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
