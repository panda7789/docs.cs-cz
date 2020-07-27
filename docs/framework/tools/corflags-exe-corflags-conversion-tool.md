---
title: CorFlags.exe (CorFlags – převodní nástroj)
description: Pochopení CorFlags.exe nástroje pro konverzi CorFlags Tento nástroj umožňuje nakonfigurovat část CorFlags hlavičky přenosné spustitelné image.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: da5efadd63cc03f6f6e4eecf3115865ca3643b39
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167228"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="8bebe-104">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="8bebe-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="8bebe-105">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="8bebe-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="8bebe-106">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bebe-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8bebe-107">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="8bebe-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8bebe-108">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8bebe-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8bebe-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="8bebe-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bebe-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bebe-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bebe-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bebe-111">Parameters</span></span>  
  
|<span data-ttu-id="8bebe-112">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="8bebe-112">Required parameter</span></span>|<span data-ttu-id="8bebe-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8bebe-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="8bebe-114">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="8bebe-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="8bebe-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="8bebe-115">Option</span></span>|<span data-ttu-id="8bebe-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8bebe-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="8bebe-117">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="8bebe-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="8bebe-118">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="8bebe-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="8bebe-119">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="8bebe-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="8bebe-120">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="8bebe-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="8bebe-121">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="8bebe-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="8bebe-122">Pokud je příznak nastaven na knihovnu DLL, knihovna DLL se nenačte v 64ch procesech a <xref:System.BadImageFormatException> vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="8bebe-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="8bebe-123">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="8bebe-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="8bebe-124">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="8bebe-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="8bebe-125">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="8bebe-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="8bebe-126">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="8bebe-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="8bebe-127">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="8bebe-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="8bebe-128">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="8bebe-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="8bebe-129">**Důležité informace:**  Pokud aktualizujete sestavení se silným názvem, je nutné jej před spuštěním kódu znovu podepsat.</span><span class="sxs-lookup"><span data-stu-id="8bebe-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="8bebe-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="8bebe-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="8bebe-131">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="8bebe-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="8bebe-132">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="8bebe-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="8bebe-133">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8bebe-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="8bebe-134">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="8bebe-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="8bebe-135">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="8bebe-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="8bebe-136">**Poznámka:**  Sestavení musí mít verzi hlavičky CLR 2,5 nebo vyšší, aby bylo možné spustit nativně.</span><span class="sxs-lookup"><span data-stu-id="8bebe-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bebe-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bebe-137">Remarks</span></span>  
 <span data-ttu-id="8bebe-138">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="8bebe-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bebe-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bebe-139">See also</span></span>

- [<span data-ttu-id="8bebe-140">Nástroje</span><span class="sxs-lookup"><span data-stu-id="8bebe-140">Tools</span></span>](index.md)
- [<span data-ttu-id="8bebe-141">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="8bebe-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="8bebe-142">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8bebe-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
