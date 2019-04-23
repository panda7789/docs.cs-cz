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
ms.openlocfilehash: 7ee801a5af214e2306e6f1667b5e4ee067683fdb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093108"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="3ceb6-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="3ceb6-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="3ceb6-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="3ceb6-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="3ceb6-105">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="3ceb6-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="3ceb6-106">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3ceb6-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="3ceb6-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="3ceb6-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ceb6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ceb6-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ceb6-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ceb6-109">Parameters</span></span>  
  
|<span data-ttu-id="3ceb6-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="3ceb6-110">Required parameter</span></span>|<span data-ttu-id="3ceb6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3ceb6-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="3ceb6-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="3ceb6-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="3ceb6-113">Option</span></span>|<span data-ttu-id="3ceb6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ceb6-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3ceb6-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="3ceb6-116">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="3ceb6-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="3ceb6-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="3ceb6-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-119">**/32BITPREF+**</span></span>|<span data-ttu-id="3ceb6-120">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="3ceb6-121">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="3ceb6-122">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="3ceb6-123">Pokud je příznak nastaven na knihovnu DLL, knihovnu DLL se nepodaří načíst v 64bitových procesů a <xref:System.BadImageFormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="3ceb6-124">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="3ceb6-125">Novinkou [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ceb6-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="3ceb6-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-126">**/32BITPREF-**</span></span>|<span data-ttu-id="3ceb6-127">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="3ceb6-128">Novinkou [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ceb6-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="3ceb6-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-129">**/?**</span></span>|<span data-ttu-id="3ceb6-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="3ceb6-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-131">**/Force**</span></span>|<span data-ttu-id="3ceb6-132">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="3ceb6-133">**Důležité:**  Při aktualizaci sestavení se silným názvem je nutné toto sestavení před spuštěním jeho kódu znovu podepsat.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="3ceb6-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-134">**/help**</span></span>|<span data-ttu-id="3ceb6-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="3ceb6-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-136">**/ILONLY+**</span></span>|<span data-ttu-id="3ceb6-137">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="3ceb6-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-138">**/ILONLY-**</span></span>|<span data-ttu-id="3ceb6-139">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="3ceb6-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-140">**/nologo**</span></span>|<span data-ttu-id="3ceb6-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="3ceb6-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="3ceb6-143">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="3ceb6-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="3ceb6-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="3ceb6-145">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="3ceb6-146">**Poznámka:**  Pro nativní spuštění musí mít sestavení hlavičku modulu CLR verze 2.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ceb6-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ceb6-147">Remarks</span></span>  
 <span data-ttu-id="3ceb6-148">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ceb6-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ceb6-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ceb6-149">See also</span></span>

- [<span data-ttu-id="3ceb6-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="3ceb6-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="3ceb6-151">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="3ceb6-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)
- [<span data-ttu-id="3ceb6-152">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="3ceb6-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
