---
title: CorFlags.exe (CorFlags – převodní nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129866"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="af20a-102">CorFlags.exe (CorFlags – převodní nástroj)</span><span class="sxs-lookup"><span data-stu-id="af20a-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="af20a-103">Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="af20a-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="af20a-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af20a-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="af20a-105">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="af20a-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="af20a-106">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="af20a-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="af20a-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="af20a-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af20a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af20a-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="af20a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="af20a-109">Parameters</span></span>  
  
|<span data-ttu-id="af20a-110">Povinný parametr</span><span class="sxs-lookup"><span data-stu-id="af20a-110">Required parameter</span></span>|<span data-ttu-id="af20a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="af20a-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="af20a-112">Název sestavení, pro které chcete konfigurovat CorFlags.</span><span class="sxs-lookup"><span data-stu-id="af20a-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="af20a-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="af20a-113">Option</span></span>|<span data-ttu-id="af20a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="af20a-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="af20a-115">Nastaví příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="af20a-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="af20a-116">Odstraní příznak 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="af20a-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="af20a-117">Nastaví příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="af20a-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="af20a-118">Aplikace běží jako 32bitový proces i na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="af20a-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="af20a-119">Tento příznak je třeba nastavit pouze u souborů EXE.</span><span class="sxs-lookup"><span data-stu-id="af20a-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="af20a-120">Pokud je příznak nastaven na knihovnu DLL, knihovna DLL se nenačte v 64ch procesech a vyvolá se výjimka <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="af20a-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="af20a-121">Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.</span><span class="sxs-lookup"><span data-stu-id="af20a-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="af20a-122">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="af20a-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="af20a-123">Odstraní příznak 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="af20a-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="af20a-124">Novinka v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="af20a-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="af20a-125">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="af20a-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="af20a-126">Vynutí aktualizaci i v případě sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="af20a-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="af20a-127">**Důležité informace:**  Pokud aktualizujete sestavení se silným názvem, je nutné jej před spuštěním kódu znovu podepsat.</span><span class="sxs-lookup"><span data-stu-id="af20a-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="af20a-128">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="af20a-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="af20a-129">Nastaví příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="af20a-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="af20a-130">Odstraní příznak ILONLY.</span><span class="sxs-lookup"><span data-stu-id="af20a-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="af20a-131">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="af20a-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="af20a-132">Vrátí verzi hlavičky CLR na 2.0.</span><span class="sxs-lookup"><span data-stu-id="af20a-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="af20a-133">Aktualizuje verzi hlavičky CLR na 2.5.</span><span class="sxs-lookup"><span data-stu-id="af20a-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="af20a-134">**Poznámka:**  Sestavení musí mít verzi hlavičky CLR 2,5 nebo vyšší, aby bylo možné spustit nativně.</span><span class="sxs-lookup"><span data-stu-id="af20a-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af20a-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af20a-135">Remarks</span></span>  
 <span data-ttu-id="af20a-136">Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="af20a-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af20a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af20a-137">See also</span></span>

- [<span data-ttu-id="af20a-138">Nástroje</span><span class="sxs-lookup"><span data-stu-id="af20a-138">Tools</span></span>](index.md)
- [<span data-ttu-id="af20a-139">64bitové aplikace</span><span class="sxs-lookup"><span data-stu-id="af20a-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="af20a-140">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="af20a-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
