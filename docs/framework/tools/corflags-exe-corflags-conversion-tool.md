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
ms.openlocfilehash: ca3e9dbe5578623ccc67898c6f08213c31ad8e23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="76c65-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="76c65-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="76c65-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="76c65-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="76c65-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76c65-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="76c65-105">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="76c65-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="76c65-106">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="76c65-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="76c65-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="76c65-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c65-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76c65-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76c65-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="76c65-109">Parameters</span></span>  
  
|<span data-ttu-id="76c65-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="76c65-110">Required parameter</span></span>|<span data-ttu-id="76c65-111">Popis</span><span class="sxs-lookup"><span data-stu-id="76c65-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="76c65-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="76c65-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="76c65-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="76c65-113">Option</span></span>|<span data-ttu-id="76c65-114">Popis</span><span class="sxs-lookup"><span data-stu-id="76c65-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="76c65-115">**/ 32BITOVÉ [NO] +**</span><span class="sxs-lookup"><span data-stu-id="76c65-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="76c65-116">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="76c65-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="76c65-117">**/ 32BITOVÉ [NO]-**</span><span class="sxs-lookup"><span data-stu-id="76c65-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="76c65-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="76c65-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="76c65-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="76c65-119">**/32BITPREF+**</span></span>|<span data-ttu-id="76c65-120">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="76c65-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="76c65-121">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="76c65-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="76c65-122">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="76c65-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="76c65-123">Pokud je nastavený příznak na knihovnu DLL, knihovny DLL nepodaří načíst v 64bitové procesy a <xref:System.BadImageFormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="76c65-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="76c65-124">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="76c65-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="76c65-125">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76c65-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="76c65-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="76c65-126">**/32BITPREF-**</span></span>|<span data-ttu-id="76c65-127">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="76c65-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="76c65-128">Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76c65-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="76c65-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="76c65-129">**/?**</span></span>|<span data-ttu-id="76c65-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="76c65-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="76c65-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="76c65-131">**/Force**</span></span>|<span data-ttu-id="76c65-132">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="76c65-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="76c65-133">**Důležité:** Pokud aktualizujete sestavení se silným názvem, musíte se odhlásit ho znovu před provedením jeho kód.</span><span class="sxs-lookup"><span data-stu-id="76c65-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="76c65-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="76c65-134">**/help**</span></span>|<span data-ttu-id="76c65-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="76c65-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="76c65-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="76c65-136">**/ILONLY+**</span></span>|<span data-ttu-id="76c65-137">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="76c65-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="76c65-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="76c65-138">**/ILONLY-**</span></span>|<span data-ttu-id="76c65-139">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="76c65-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="76c65-140">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="76c65-140">**/nologo**</span></span>|<span data-ttu-id="76c65-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="76c65-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="76c65-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="76c65-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="76c65-143">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="76c65-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="76c65-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="76c65-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="76c65-145">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="76c65-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="76c65-146">**Poznámka:** sestavení musí mít hlavička CLR verzi 2.5 nebo novější, abyste mohli spustit nativně.</span><span class="sxs-lookup"><span data-stu-id="76c65-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c65-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76c65-147">Remarks</span></span>  
 <span data-ttu-id="76c65-148">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="76c65-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c65-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="76c65-149">See Also</span></span>  
 [<span data-ttu-id="76c65-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="76c65-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="76c65-151">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="76c65-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="76c65-152">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="76c65-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
