---
title: "CorFlags.exe (CorFlags – převodní nástroj)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111c697d4d62cd52cd7913039e3c17e8a25ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="f15c9-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="f15c9-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="f15c9-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="f15c9-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="f15c9-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f15c9-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f15c9-105">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f15c9-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f15c9-106">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f15c9-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="f15c9-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="f15c9-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15c9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f15c9-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f15c9-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="f15c9-109">Parameters</span></span>  
  
|<span data-ttu-id="f15c9-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="f15c9-110">Required parameter</span></span>|<span data-ttu-id="f15c9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f15c9-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="f15c9-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="f15c9-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="f15c9-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="f15c9-113">Option</span></span>|<span data-ttu-id="f15c9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f15c9-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f15c9-115">**/ 32BITOVÉ [NO] +**</span><span class="sxs-lookup"><span data-stu-id="f15c9-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="f15c9-116">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="f15c9-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="f15c9-117">**/ 32BITOVÉ [NO]-**</span><span class="sxs-lookup"><span data-stu-id="f15c9-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="f15c9-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="f15c9-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="f15c9-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="f15c9-119">**/32BITPREF+**</span></span>|<span data-ttu-id="f15c9-120">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="f15c9-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="f15c9-121">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="f15c9-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="f15c9-122">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="f15c9-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="f15c9-123">Pokud je nastavený příznak na knihovnu DLL, knihovny DLL nepodaří načíst v 64bitové procesy a <xref:System.BadImageFormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f15c9-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="f15c9-124">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="f15c9-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="f15c9-125">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f15c9-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="f15c9-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="f15c9-126">**/32BITPREF-**</span></span>|<span data-ttu-id="f15c9-127">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="f15c9-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="f15c9-128">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f15c9-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="f15c9-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="f15c9-129">**/?**</span></span>|<span data-ttu-id="f15c9-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="f15c9-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f15c9-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="f15c9-131">**/Force**</span></span>|<span data-ttu-id="f15c9-132">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f15c9-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="f15c9-133">**Důležité:** Pokud aktualizujete sestavení se silným názvem, musíte se odhlásit ho znovu před provedením jeho kód.</span><span class="sxs-lookup"><span data-stu-id="f15c9-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="f15c9-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="f15c9-134">**/help**</span></span>|<span data-ttu-id="f15c9-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="f15c9-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f15c9-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="f15c9-136">**/ILONLY+**</span></span>|<span data-ttu-id="f15c9-137">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="f15c9-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="f15c9-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="f15c9-138">**/ILONLY-**</span></span>|<span data-ttu-id="f15c9-139">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="f15c9-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="f15c9-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="f15c9-140">**/nologo**</span></span>|<span data-ttu-id="f15c9-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f15c9-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="f15c9-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="f15c9-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="f15c9-143">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="f15c9-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="f15c9-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="f15c9-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="f15c9-145">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="f15c9-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="f15c9-146">**Poznámka:** sestavení musí mít hlavička CLR verzi 2.5 nebo novější, abyste mohli spustit nativně.</span><span class="sxs-lookup"><span data-stu-id="f15c9-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f15c9-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f15c9-147">Remarks</span></span>  
 <span data-ttu-id="f15c9-148">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="f15c9-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15c9-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="f15c9-149">See Also</span></span>  
 [<span data-ttu-id="f15c9-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="f15c9-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="f15c9-151">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="f15c9-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="f15c9-152">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="f15c9-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
