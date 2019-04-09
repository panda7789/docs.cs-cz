---
title: Ngen.exe (generátor nativních obrázků)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34fc8fb78a1dcd2637ff9ce0d0de8e7c1509bd3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116266"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="16152-102">Ngen.exe (generátor nativních obrázků)</span><span class="sxs-lookup"><span data-stu-id="16152-102">Ngen.exe (Native Image Generator)</span></span>
<span data-ttu-id="16152-103">Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="16152-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="16152-104">Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="16152-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="16152-105">Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="16152-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>  
  
 <span data-ttu-id="16152-106">Změní na Ngen.exe v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="16152-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>  
  
-   <span data-ttu-id="16152-107">Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.</span><span class="sxs-lookup"><span data-stu-id="16152-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
-   <span data-ttu-id="16152-108">Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="16152-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>  
  
 <span data-ttu-id="16152-109">Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:</span><span class="sxs-lookup"><span data-stu-id="16152-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>  
  
-   <span data-ttu-id="16152-110">Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>  
  
-   <span data-ttu-id="16152-111">Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="16152-111">Native images can now be shared across application domains.</span></span>  
  
-   <span data-ttu-id="16152-112">Nová akce `update`, znovu vytvoří bitové kopie, které byly zneplatněny.</span><span class="sxs-lookup"><span data-stu-id="16152-112">A new action, `update`, re-creates images that have been invalidated.</span></span>  
  
-   <span data-ttu-id="16152-113">Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="16152-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>  
  
-   <span data-ttu-id="16152-114">Některé příčiny zneplatnění bitové kopie byly odstraněny.</span><span class="sxs-lookup"><span data-stu-id="16152-114">Some causes of image invalidation have been eliminated.</span></span>  
  
 <span data-ttu-id="16152-115">V systému Windows 8 naleznete v tématu [Native Image Task](#native-image-task).</span><span class="sxs-lookup"><span data-stu-id="16152-115">On Windows 8, see [Native Image Task](#native-image-task).</span></span>  
  
 <span data-ttu-id="16152-116">Další informace o použití Ngen.exe a službu nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-117">Syntaxe Ngen.exe pro verze 1.0 a 1.1 rozhraní .NET Framework lze nalézt v [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="16152-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>  
  
 <span data-ttu-id="16152-118">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16152-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="16152-119">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="16152-119">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="16152-120">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="16152-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="16152-121">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="16152-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16152-122">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16152-122">Syntax</span></span>  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a><span data-ttu-id="16152-123">Akce</span><span class="sxs-lookup"><span data-stu-id="16152-123">Actions</span></span>  
 <span data-ttu-id="16152-124">Následující tabulka ukazuje syntaxi každé `action`.</span><span class="sxs-lookup"><span data-stu-id="16152-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="16152-125">Popisy jednotlivých částí `action`, najdete v článku [argumenty](#ArgumentTable), [úrovně Priority](#PriorityTable), [scénáře](#ScenarioTable), a [Config](#ConfigTable)tabulky.</span><span class="sxs-lookup"><span data-stu-id="16152-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="16152-126">[Možnosti](#OptionTable) tabulka popisuje `options` a přepínače nápovědy.</span><span class="sxs-lookup"><span data-stu-id="16152-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>  
  
|<span data-ttu-id="16152-127">Akce</span><span class="sxs-lookup"><span data-stu-id="16152-127">Action</span></span>|<span data-ttu-id="16152-128">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-128">Description</span></span>|  
|------------|-----------------|  
|`install` <span data-ttu-id="16152-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="16152-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="16152-130">Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="16152-131">Pokud `/queue` není zadána, akce je zařazena do fronty pro službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="16152-132">Výchozí hodnota priority je 3.</span><span class="sxs-lookup"><span data-stu-id="16152-132">The default priority is 3.</span></span> <span data-ttu-id="16152-133">Zobrazit [úrovně Priority](#PriorityTable) tabulky.</span><span class="sxs-lookup"><span data-stu-id="16152-133">See the [Priority Levels](#PriorityTable) table.</span></span>|  
|`uninstall` <span data-ttu-id="16152-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="16152-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="16152-135">Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="16152-136">Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="16152-137">**Poznámka:**  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], akce `uninstall` \* se už nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="16152-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` \* is no longer supported.</span></span>|  
|`update` <span data-ttu-id="16152-138">[`/queue`]</span><span class="sxs-lookup"><span data-stu-id="16152-138">[`/queue`]</span></span>|<span data-ttu-id="16152-139">Aktualizuje nativní bitové kopie, které se staly neplatnými.</span><span class="sxs-lookup"><span data-stu-id="16152-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="16152-140">Pokud `/queue` není zadána, aktualizace jsou zařazeny do fronty pro službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="16152-141">Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|  
|`display` <span data-ttu-id="16152-142">[`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="16152-142">[`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="16152-143">Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="16152-144">Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|  
|`executeQueuedItems` <span data-ttu-id="16152-145">[<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="16152-145">[<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="16152-146">-nebo-</span><span class="sxs-lookup"><span data-stu-id="16152-146">-or-</span></span><br /><br /> `eqi` <span data-ttu-id="16152-147">[1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="16152-147">[1&#124;2&#124;3]</span></span>|<span data-ttu-id="16152-148">Spustí úlohy kompilace ve frontě.</span><span class="sxs-lookup"><span data-stu-id="16152-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="16152-149">Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou.</span><span class="sxs-lookup"><span data-stu-id="16152-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="16152-150">Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.</span><span class="sxs-lookup"><span data-stu-id="16152-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|  
|`queue` <span data-ttu-id="16152-151">{`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="16152-151">{`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="16152-152">Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.</span><span class="sxs-lookup"><span data-stu-id="16152-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a><span data-ttu-id="16152-153">Arguments</span><span class="sxs-lookup"><span data-stu-id="16152-153">Arguments</span></span>  
  
|<span data-ttu-id="16152-154">Argument</span><span class="sxs-lookup"><span data-stu-id="16152-154">Argument</span></span>|<span data-ttu-id="16152-155">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-155">Description</span></span>|  
|--------------|-----------------|  
|`assemblyName`|<span data-ttu-id="16152-156">Plný zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-156">The full display name of the assembly.</span></span> <span data-ttu-id="16152-157">Například, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="16152-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="16152-158">**Poznámka:**  Lze zadat částečný název sestavení, například `myAssembly`, pro `display` a `uninstall` akce.</span><span class="sxs-lookup"><span data-stu-id="16152-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="16152-159">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
|`assemblyPath`|<span data-ttu-id="16152-160">Explicitní cesta k sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-160">The explicit path of the assembly.</span></span> <span data-ttu-id="16152-161">Lze zadat úplnou nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="16152-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="16152-162">Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="16152-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="16152-163">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a><span data-ttu-id="16152-164">Úrovně priority</span><span class="sxs-lookup"><span data-stu-id="16152-164">Priority Levels</span></span>  
  
|<span data-ttu-id="16152-165">Priorita</span><span class="sxs-lookup"><span data-stu-id="16152-165">Priority</span></span>|<span data-ttu-id="16152-166">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-166">Description</span></span>|  
|--------------|-----------------|  
|`1`|<span data-ttu-id="16152-167">Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|  
|`2`|<span data-ttu-id="16152-168">Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).</span><span class="sxs-lookup"><span data-stu-id="16152-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|  
|`3`|<span data-ttu-id="16152-169">Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="16152-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="16152-170">Zobrazit [službu nativních bitových kopií](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-170">See [Native Image Service](#native-image-service).</span></span>|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a><span data-ttu-id="16152-171">Scénáře</span><span class="sxs-lookup"><span data-stu-id="16152-171">Scenarios</span></span>  
  
|<span data-ttu-id="16152-172">Scénář</span><span class="sxs-lookup"><span data-stu-id="16152-172">Scenario</span></span>|<span data-ttu-id="16152-173">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-173">Description</span></span>|  
|--------------|-----------------|  
|`/Debug`|<span data-ttu-id="16152-174">Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="16152-174">Generate native images that can be used under a debugger.</span></span>|  
|`/Profile`|<span data-ttu-id="16152-175">Vygeneruje nativní bitové kopie, které lze použít v profileru.</span><span class="sxs-lookup"><span data-stu-id="16152-175">Generate native images that can be used under a profiler.</span></span>|  
|`/NoDependencies`|<span data-ttu-id="16152-176">Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.</span><span class="sxs-lookup"><span data-stu-id="16152-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a><span data-ttu-id="16152-177">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="16152-177">Config</span></span>  
  
|<span data-ttu-id="16152-178">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="16152-178">Configuration</span></span>|<span data-ttu-id="16152-179">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-179">Description</span></span>|  
|-------------------|-----------------|  
|`/ExeConfig:` `exePath`|<span data-ttu-id="16152-180">Použije konfiguraci zadaného spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-180">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="16152-181">Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč.</span><span class="sxs-lookup"><span data-stu-id="16152-181">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="16152-182">Pokud sdílená komponenta načtena za běhu, pomocí <xref:System.Reflection.Assembly.Load%2A> metoda, konfigurační soubor aplikace určí závislosti, která jsou načtena pro sdílenou komponentu – například verzi načtené závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-182">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="16152-183">`/ExeConfig` Přepínač poskytuje Ngen.exe pokyny, na které závislosti budou načteny za běhu.</span><span class="sxs-lookup"><span data-stu-id="16152-183">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|  
|`/AppBase:` `directoryPath`|<span data-ttu-id="16152-184">Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.</span><span class="sxs-lookup"><span data-stu-id="16152-184">When locating dependencies, use the specified directory as the application base.</span></span>|  
  
<a name="OptionTable"></a>   
## <a name="options"></a><span data-ttu-id="16152-185">Možnosti</span><span class="sxs-lookup"><span data-stu-id="16152-185">Options</span></span>  
  
|<span data-ttu-id="16152-186">Možnost</span><span class="sxs-lookup"><span data-stu-id="16152-186">Option</span></span>|<span data-ttu-id="16152-187">Popis</span><span class="sxs-lookup"><span data-stu-id="16152-187">Description</span></span>|  
|------------|-----------------|  
|`/nologo`|<span data-ttu-id="16152-188">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="16152-188">Suppress the Microsoft startup banner display.</span></span>|  
|`/silent`|<span data-ttu-id="16152-189">Potlačí zobrazování zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="16152-189">Suppress the display of success messages.</span></span>|  
|`/verbose`|<span data-ttu-id="16152-190">Zobrazí podrobné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="16152-190">Display detailed information for debugging.</span></span> <span data-ttu-id="16152-191">**Poznámka:**  Vzhledem k omezením operačního systému tato možnost nezobrazí dodatečných informací o Windows 98 a Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="16152-191">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|  
|`/help`<span data-ttu-id="16152-192">, </span><span class="sxs-lookup"><span data-stu-id="16152-192">,</span></span> `/?`|<span data-ttu-id="16152-193">Zobrazí syntaxi příkazu a možnosti aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="16152-193">Display command syntax and options for the current release.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16152-194">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16152-194">Remarks</span></span>  
 <span data-ttu-id="16152-195">Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="16152-195">To run Ngen.exe, you must have administrative privileges.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="16152-196">Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="16152-196">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="16152-197">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe kompiluje sestavení s úplným vztahem důvěryhodnosti a zásady (CAS) zabezpečení přístupu kódu už nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="16152-197">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
 <span data-ttu-id="16152-198">Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nativní bitové kopie generované nástrojem Ngen.exe již být načteny do aplikací, na kterých běží v částečném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="16152-198">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="16152-199">Namísto toho je vyvolán kompilátor za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="16152-199">Instead, the just-in-time (JIT) compiler is invoked.</span></span>  
  
 <span data-ttu-id="16152-200">Ngen.exe vytváří nativní bitové kopie pro sestavení určené parametrem `assemblyname` argument `install` akce a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-200">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="16152-201">Závislosti se stanoví z odkazů v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-201">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="16152-202">Jediný scénář, ve které je potřeba nainstalovat závislost odděleně se při načtení aplikace, například pomocí reflexe, voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="16152-202">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16152-203">Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu s nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-203">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="16152-204">Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="16152-204">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>  
  
 <span data-ttu-id="16152-205">Nástroj Ngen.exe udržuje počet odkazů na závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-205">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="16152-206">Předpokládejme například, že `MyAssembly.exe` a `YourAssembly.exe` současně nainstalovány v mezipaměti nativních bitových kopií a obě mají odkazy na `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="16152-206">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="16152-207">Pokud `MyAssembly.exe` odinstalaci `OurDependency.dll` nebude odinstalován.</span><span class="sxs-lookup"><span data-stu-id="16152-207">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="16152-208">Je jenom odebrány při `YourAssembly.exe` je odinstalována také.</span><span class="sxs-lookup"><span data-stu-id="16152-208">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>  
  
 <span data-ttu-id="16152-209">Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="16152-209">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="16152-210">Viz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16152-210">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="16152-211">Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-211">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="16152-212">To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-212">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="16152-213">Určení neutrality domény:</span><span class="sxs-lookup"><span data-stu-id="16152-213">To specify domain neutrality:</span></span>  
  
-   <span data-ttu-id="16152-214">Použít <xref:System.LoaderOptimizationAttribute> své aplikace atribut.</span><span class="sxs-lookup"><span data-stu-id="16152-214">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>  
  
-   <span data-ttu-id="16152-215">Nastavte <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> vlastnost při vytváření nastavení informace pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-215">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>  
  
 <span data-ttu-id="16152-216">Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-216">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="16152-217">Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.</span><span class="sxs-lookup"><span data-stu-id="16152-217">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-218">Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.</span><span class="sxs-lookup"><span data-stu-id="16152-218">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>  
  
 <span data-ttu-id="16152-219">V této části Poznámky:</span><span class="sxs-lookup"><span data-stu-id="16152-219">In this Remarks section:</span></span>  
  
-   [<span data-ttu-id="16152-220">Generování bitových kopií pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="16152-220">Generating images for different scenarios</span></span>](#Scenarios)  
  
-   [<span data-ttu-id="16152-221">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="16152-221">Determining when to Use native images</span></span>](#WhenToUse)  
  
    -   [<span data-ttu-id="16152-222">Lepší využití paměti</span><span class="sxs-lookup"><span data-stu-id="16152-222">Improved memory use</span></span>](#Memory)  
  
    -   [<span data-ttu-id="16152-223">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="16152-223">Faster application startup</span></span>](#Startup)  
  
    -   [<span data-ttu-id="16152-224">Souhrnné informace o použití</span><span class="sxs-lookup"><span data-stu-id="16152-224">Summary of usage considerations</span></span>](#UsageSummary)  
  
-   [<span data-ttu-id="16152-225">Důležitost základních adres sestavení</span><span class="sxs-lookup"><span data-stu-id="16152-225">Importance of assembly base addresses</span></span>](#BaseAddresses)  
  
-   [<span data-ttu-id="16152-226">Pevné vazby</span><span class="sxs-lookup"><span data-stu-id="16152-226">Hard binding</span></span>](#HardBinding)  
  
    -   [<span data-ttu-id="16152-227">Určení pokynu vazby pro závislost</span><span class="sxs-lookup"><span data-stu-id="16152-227">Specifying a binding hint for a dependency</span></span>](#DependencyHint)  
  
    -   [<span data-ttu-id="16152-228">Určení pokynu výchozí vazby pro sestavení</span><span class="sxs-lookup"><span data-stu-id="16152-228">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)  
  
-   [<span data-ttu-id="16152-229">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="16152-229">Deferred processing</span></span>](#Deferred)  
  
-   [<span data-ttu-id="16152-230">Nativní bitové kopie a JIT kompilace</span><span class="sxs-lookup"><span data-stu-id="16152-230">Native images and JIT compilation</span></span>](#JITCompilation)  
  
    -   [<span data-ttu-id="16152-231">Neplatné bitové kopie</span><span class="sxs-lookup"><span data-stu-id="16152-231">Invalid images</span></span>](#InvalidImages)  
  
-   [<span data-ttu-id="16152-232">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="16152-232">Troubleshooting</span></span>](#Troubleshooting)  
  
    -   [<span data-ttu-id="16152-233">vazba sestavení – prohlížeč protokolu</span><span class="sxs-lookup"><span data-stu-id="16152-233">Assembly Binding Log Viewer</span></span>](#Fusion)  
  
    -   [<span data-ttu-id="16152-234">JITCompilationStart Pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="16152-234">The JITCompilationStart managed debugging assistant</span></span>](#MDA)  
  
    -   [<span data-ttu-id="16152-235">Výslovné odhlášení z generování nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="16152-235">Opting out of native image generation</span></span>](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="16152-236">Generování bitových kopií pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="16152-236">Generating images for     different scenarios</span></span>  
 <span data-ttu-id="16152-237">Po vygenerování nativní bitové kopie pro sestavení, modul runtime automaticky pokusí vyhledat a použít tuto nativní bitovou kopii při každém spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-237">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="16152-238">V závislosti na scénáři lze generovat více bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-238">Multiple images can be generated, depending on usage scenarios.</span></span>  
  
 <span data-ttu-id="16152-239">Například při spuštění sestavení ve scénáři ladění nebo profilování, modul runtime vyhledá nativní bitovou kopii, která byla vygenerována s `/Debug` nebo `/Profile` možnosti.</span><span class="sxs-lookup"><span data-stu-id="16152-239">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="16152-240">Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci.</span><span class="sxs-lookup"><span data-stu-id="16152-240">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="16152-241">Vytvoření nativní bitové kopie s je jediný způsob, jak ladit nativní bitové kopie `/Debug` možnost.</span><span class="sxs-lookup"><span data-stu-id="16152-241">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>  
  
 <span data-ttu-id="16152-242">`uninstall` Akce také rozpoznává scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybrané scénáře.</span><span class="sxs-lookup"><span data-stu-id="16152-242">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="16152-243">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="16152-243">Determining when to Use native images</span></span>  
 <span data-ttu-id="16152-244">Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.</span><span class="sxs-lookup"><span data-stu-id="16152-244">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-245">Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="16152-245">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="16152-246">Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.</span><span class="sxs-lookup"><span data-stu-id="16152-246">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a><span data-ttu-id="16152-247">Lepší využití paměti</span><span class="sxs-lookup"><span data-stu-id="16152-247">Improved memory use</span></span>  
 <span data-ttu-id="16152-248">Nativní bitové kopie mohou významně zlepšit využití paměti, je-li kód sdílen mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="16152-248">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="16152-249">Nativní bitové kopie jsou soubory Windows PE, tudíž jedna kopie souboru .dll může být sdílena několika procesy. Naproti tomu nativní kód vytvořený kompilátorem JIT je uložen v soukromé paměti a nelze jej sdílet.</span><span class="sxs-lookup"><span data-stu-id="16152-249">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>  
  
 <span data-ttu-id="16152-250">Aplikace spuštěné v rámci terminálových služeb také využívají výhod sdílených znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="16152-250">Applications that are run under terminal services can also benefit from shared code pages.</span></span>  
  
 <span data-ttu-id="16152-251">Kromě toho skutečnost, že není načítán kompilátor JIT, ušetří pevně dané množství paměti pro každou instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-251">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a><span data-ttu-id="16152-252">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="16152-252">Faster application startup</span></span>  
 <span data-ttu-id="16152-253">Předkompilování sestavení programem Ngen.exe může zvýšit rychlost spuštění některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="16152-253">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="16152-254">Obecně lze zvýšení výkonu dosáhnout tam, kde aplikace sdílejí sestavení komponent, protože po prvním spuštění aplikace jsou komponenty sdílené s jinými aplikacemi již načteny.</span><span class="sxs-lookup"><span data-stu-id="16152-254">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="16152-255">Úplné spuštění, při němž musí být všechna sestavení aplikace načtena z pevného disku, nevyužívají výhod nativních bitových kopií v takové míře, protože má převahu přístupová doba pevného disku.</span><span class="sxs-lookup"><span data-stu-id="16152-255">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>  
  
 <span data-ttu-id="16152-256">Pevné vazby mohou ovlivnit rychlost spuštění, protože všechny bitové kopie pevně svázané s hlavním sestavením aplikace musí být načteny najednou.</span><span class="sxs-lookup"><span data-stu-id="16152-256">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-257">Před [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], byste měli umístit komponenty sdílené se silným názvem do globální mezipaměti sestavení, protože zavaděč provádí ověřování navíc sestavení se silným názvem, které nejsou v globální mezipaměti sestavení, čímž jsou všechna zlepšení času spuštění získaná použitím nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-257">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="16152-258">Optimalizace, které byly zavedeny v [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] tato ověřování.</span><span class="sxs-lookup"><span data-stu-id="16152-258">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a><span data-ttu-id="16152-259">Souhrnné informace o použití</span><span class="sxs-lookup"><span data-stu-id="16152-259">Summary of usage considerations</span></span>  
 <span data-ttu-id="16152-260">Následující obecné a aplikační informace vám mohou pomoci rozhodnout, zda může být vyhodnocení nativních bitových kopií pro aplikaci přínosem:</span><span class="sxs-lookup"><span data-stu-id="16152-260">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>  
  
-   <span data-ttu-id="16152-261">Nativní bitové kopie se načítají rychleji než jazyk MSIL, protože odstraňují potřebu mnoha aktivit při spouštění, například kompilaci JIT a ověření bezpečnosti typů.</span><span class="sxs-lookup"><span data-stu-id="16152-261">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>  
  
-   <span data-ttu-id="16152-262">Nativní bitové kopie vyžadují menší počáteční pracovní sadu, protože není zapotřebí použít kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="16152-262">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>  
  
-   <span data-ttu-id="16152-263">Nativní bitové kopie umožňují sdílení kódu mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="16152-263">Native images enable code sharing between processes.</span></span>  
  
-   <span data-ttu-id="16152-264">Nativní bitové kopie vyžadují více místa na disku než sestavení MSIL a jejich generování může trvat značně dlouho.</span><span class="sxs-lookup"><span data-stu-id="16152-264">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>  
  
-   <span data-ttu-id="16152-265">Nativní bitové kopie musí být udržovány.</span><span class="sxs-lookup"><span data-stu-id="16152-265">Native images must be maintained.</span></span>  
  
    -   <span data-ttu-id="16152-266">Je-li upraveno původní sestavení nebo jedna z jeho závislostí, je zapotřebí bitové kopie znovu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="16152-266">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>  
  
    -   <span data-ttu-id="16152-267">Jediné sestavení může vyžadovat několik nativních bitových kopií pro použití v různých aplikacích a scénářích.</span><span class="sxs-lookup"><span data-stu-id="16152-267">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="16152-268">Například informace o konfiguraci dvou aplikací může vyústit v různá rozhodnutí o vazbách stejného závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-268">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>  
  
    -   <span data-ttu-id="16152-269">Nativní bitové kopie musí být generovány správcem; tj. z účtu systému Windows ve skupině Administrators.</span><span class="sxs-lookup"><span data-stu-id="16152-269">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>  
  
 <span data-ttu-id="16152-270">Spolu s těmito obecnými informacemi je zapotřebí při určování, zda mohou nativní bitové kopie poskytnout zvýšení výkonu, zvážit i povahu aplikace:</span><span class="sxs-lookup"><span data-stu-id="16152-270">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>  
  
-   <span data-ttu-id="16152-271">Je-li aplikace spouštěna v prostředí, které využívá mnoho sdílených komponent, nativní bitové kopie umožňují sdílení komponent mezi mnoha procesy.</span><span class="sxs-lookup"><span data-stu-id="16152-271">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>  
  
-   <span data-ttu-id="16152-272">Používá-li aplikace více domén aplikace, nativní bitové kopie umožňují sdílení znakových stránek mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="16152-272">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16152-273">V rozhraních .NET Framework verze 1.0 a 1.1 nemohou být nativní bitové kopie sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-273">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="16152-274">Verze 2.0 a novější již toto omezení nemají.</span><span class="sxs-lookup"><span data-stu-id="16152-274">This is not the case in version 2.0 or later.</span></span>  
  
-   <span data-ttu-id="16152-275">Bude-li aplikace spuštěna v rámci Terminálového serveru, nativní bitové kopie umožní sdílení znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="16152-275">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>  
  
-   <span data-ttu-id="16152-276">Rozsáhlé aplikace obecně těží z výhod kompilace do nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-276">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="16152-277">Malým aplikacím nativní bitové kopie obvykle výhody nepřinášejí.</span><span class="sxs-lookup"><span data-stu-id="16152-277">Small applications generally do not benefit.</span></span>  
  
-   <span data-ttu-id="16152-278">Pro dlouho běžící aplikace vykazuje kompilace JIT za běhu mírně vyšší výkon než nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-278">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="16152-279">(Pevné vazby mohou tento rozdíl ve výkonu do určité míry zmenšit.)</span><span class="sxs-lookup"><span data-stu-id="16152-279">(Hard binding can mitigate this performance difference to some degree.)</span></span>  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="16152-280">Důležitost základních adres sestavení</span><span class="sxs-lookup"><span data-stu-id="16152-280">Importance of assembly base addresses</span></span>  
 <span data-ttu-id="16152-281">Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů.</span><span class="sxs-lookup"><span data-stu-id="16152-281">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="16152-282">Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="16152-282">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>  
  
 <span data-ttu-id="16152-283">Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-283">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="16152-284">Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-284">Ngen.exe uses this base address for the native image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-285">Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="16152-285">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="16152-286">Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.</span><span class="sxs-lookup"><span data-stu-id="16152-286">Base addresses must be calculated to allow for these larger sizes.</span></span>  
  
 <span data-ttu-id="16152-287">Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-287">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a><span data-ttu-id="16152-288">Pevné vazby</span><span class="sxs-lookup"><span data-stu-id="16152-288">Hard binding</span></span>  
 <span data-ttu-id="16152-289">Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-289">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="16152-290">Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-290">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="16152-291">To u velkých aplikací může výrazně prodloužit spouštění.</span><span class="sxs-lookup"><span data-stu-id="16152-291">This can significantly increase startup time for a large application.</span></span>  
  
 <span data-ttu-id="16152-292">Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu.</span><span class="sxs-lookup"><span data-stu-id="16152-292">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="16152-293">Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="16152-293">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>  
  
 <span data-ttu-id="16152-294"><xref:System.Runtime.CompilerServices.DependencyAttribute> a <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atributy umožňují poskytovat Ngen.exe pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="16152-294">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-295">Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="16152-295">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="16152-296">Jejich použití nezaručuje pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="16152-296">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="16152-297">V budoucích verzích se může změnit význam těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="16152-297">The meaning of these attributes may change in future releases.</span></span>  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="16152-298">Určení pokynu vazby pro závislost</span><span class="sxs-lookup"><span data-stu-id="16152-298">Specifying a binding hint for a dependency</span></span>  
 <span data-ttu-id="16152-299">Použít <xref:System.Runtime.CompilerServices.DependencyAttribute> sestavení k označení pravděpodobnost, že určená závislost bude načtena.</span><span class="sxs-lookup"><span data-stu-id="16152-299">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> <span data-ttu-id="16152-300">Označuje, že pevná vazba je vhodná, <xref:System.Runtime.CompilerServices.LoadHint.Default> označuje, že má být použita výchozí hodnota pro závislost, a <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> označuje, že pevná vazba není vhodná.</span><span class="sxs-lookup"><span data-stu-id="16152-300">indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>  
  
 <span data-ttu-id="16152-301">Následující kód zobrazuje atributy pro sestavení, které má dvě závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-301">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="16152-302">První závislost (Assembly1) je vhodným kandidátem pro pevnou vazbu, druhá závislost (Assembly2) nikoliv.</span><span class="sxs-lookup"><span data-stu-id="16152-302">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 <span data-ttu-id="16152-303">Název sestavení neobsahuje příponu názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="16152-303">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="16152-304">Lze použít zobrazené názvy.</span><span class="sxs-lookup"><span data-stu-id="16152-304">Display names can be used.</span></span>  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="16152-305">Určení pokynu výchozí vazby pro sestavení</span><span class="sxs-lookup"><span data-stu-id="16152-305">Specifying a default binding hint for an assembly</span></span>  
 <span data-ttu-id="16152-306">Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="16152-306">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="16152-307">Použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> na taková sestavení k určení, že má být použit pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="16152-307">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-308">Neexistuje žádný důvod použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na .dll sestavení, které nespadají do této kategorie, protože použití atributu s jinou hodnotou než <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný účinek jako vynechání atributu vůbec.</span><span class="sxs-lookup"><span data-stu-id="16152-308">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>  
  
 <span data-ttu-id="16152-309">Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> k určení, že pevná vazba je výchozí nastavení pro velmi malý počet sestavení v rozhraní .NET Framework, jako například mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="16152-309">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a><span data-ttu-id="16152-310">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="16152-310">Deferred processing</span></span>  
 <span data-ttu-id="16152-311">Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="16152-311">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="16152-312">Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-312">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="16152-313">`install` a `update` mají akce `/queue` možnost, která se zařadí do fronty operace k odloženému spuštění službou nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-313">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="16152-314">Kromě toho má Ngen.exe `queue` a `executeQueuedItems` akce, které poskytuje určitou kontrolu nad službu.</span><span class="sxs-lookup"><span data-stu-id="16152-314">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="16152-315">Další informace najdete v tématu [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-315">For more information, see [Native Image Service](#native-image-service).</span></span>  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="16152-316">Nativní bitové kopie a JIT kompilace</span><span class="sxs-lookup"><span data-stu-id="16152-316">Native images and JIT compilation</span></span>  
 <span data-ttu-id="16152-317">Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-317">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="16152-318">Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="16152-318">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>  
  
 <span data-ttu-id="16152-319">Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.</span><span class="sxs-lookup"><span data-stu-id="16152-319">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a><span data-ttu-id="16152-320">Neplatné bitové kopie</span><span class="sxs-lookup"><span data-stu-id="16152-320">Invalid images</span></span>  
 <span data-ttu-id="16152-321">Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-321">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="16152-322">Mezi tato nastavení patří následující:</span><span class="sxs-lookup"><span data-stu-id="16152-322">These settings include the following:</span></span>  
  
-   <span data-ttu-id="16152-323">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16152-323">The version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="16152-324">Verze operačního systému, pokud je změna z řady Windows 9 x na řadu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="16152-324">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
-   <span data-ttu-id="16152-325">Přesná identita sestavení (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="16152-325">The exact identity of the assembly (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="16152-326">Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="16152-326">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="16152-327">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="16152-327">Security factors.</span></span>  
  
 <span data-ttu-id="16152-328">Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-328">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="16152-329">Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-329">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="16152-330">Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="16152-330">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="16152-331">Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:</span><span class="sxs-lookup"><span data-stu-id="16152-331">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>  
  
-   <span data-ttu-id="16152-332">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16152-332">The version of the .NET Framework.</span></span>  
  
     <span data-ttu-id="16152-333">Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní.</span><span class="sxs-lookup"><span data-stu-id="16152-333">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="16152-334">Z tohoto důvodu všechny aktualizace rozhraní .NET Framework spustit `Ngen Update` příkazu, ujistěte se, že všechny nativní bitové kopie budou znovu vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="16152-334">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="16152-335">Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.</span><span class="sxs-lookup"><span data-stu-id="16152-335">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>  
  
-   <span data-ttu-id="16152-336">Verze operačního systému, pokud je změna z řady Windows 9 x na řadu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="16152-336">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
     <span data-ttu-id="16152-337">Například pokud verze operačního systému spuštěného na počítači změní z Windows 98 na Windows XP, všechny nativní bitové kopie, které jsou uložené v mezipaměti nativní bitové kopie se zneplatní.</span><span class="sxs-lookup"><span data-stu-id="16152-337">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="16152-338">Nicméně pokud operační systém změní z Windows 2000 na Windows XP, bitové kopie nejsou zneplatněny.</span><span class="sxs-lookup"><span data-stu-id="16152-338">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>  
  
-   <span data-ttu-id="16152-339">Přesná identita sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-339">The exact identity of the assembly.</span></span>  
  
     <span data-ttu-id="16152-340">Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="16152-340">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>  
  
-   <span data-ttu-id="16152-341">Přesná identita všech sestavení, na která sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="16152-341">The exact identity of any assemblies the assembly references.</span></span>  
  
     <span data-ttu-id="16152-342">Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="16152-342">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="16152-343">To zahrnuje jak běžné odkazy, tak pevně vázané závislosti.</span><span class="sxs-lookup"><span data-stu-id="16152-343">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="16152-344">Pokaždé, když je aplikována aktualizace softwaru, by se měl spustit instalační program `Ngen Update` příkaz, kterým zajistíte, že všechny závislé nativní bitové kopie budou znovu vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="16152-344">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>  
  
-   <span data-ttu-id="16152-345">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="16152-345">Security factors.</span></span>  
  
     <span data-ttu-id="16152-346">Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="16152-346">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>  
  
     <span data-ttu-id="16152-347">Podrobné informace o tom, jak modul CLR spravuje bezpečnost přístupu kódu a jak použít oprávnění najdete v tématu [zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="16152-347">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="16152-348">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="16152-348">Troubleshooting</span></span>  
 <span data-ttu-id="16152-349">Následující témata odstraňování problémů umožňují zobrazit, které nativní bitové kopie se používají a které nelze použít v aplikaci, můžete určit, kdy začne ke kompilaci metody kompilátor JIT a ukazuje, jak se odhlásit ze sestavování nativních bitových kopií zadaný metody.</span><span class="sxs-lookup"><span data-stu-id="16152-349">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="16152-350">vazba sestavení – prohlížeč protokolu</span><span class="sxs-lookup"><span data-stu-id="16152-350">Assembly Binding Log Viewer</span></span>  
 <span data-ttu-id="16152-351">Potvrďte, že se nativní bitové kopie slouží v aplikaci, můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="16152-351">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="16152-352">Vyberte **nativní bitové kopie** v **kategorie protokolu** pole v okně prohlížeče protokolu vazeb.</span><span class="sxs-lookup"><span data-stu-id="16152-352">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="16152-353">Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="16152-353">Fuslogvw.exe provides information about why a native image was rejected.</span></span>  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="16152-354">JITCompilationStart Pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="16152-354">The JITCompilationStart managed debugging assistant</span></span>  
 <span data-ttu-id="16152-355">Můžete použít [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) pomocníka spravovaného ladění (MDA) k určení, kdy začne kompilátor JIT kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="16152-355">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="16152-356">Výslovné odhlášení z generování nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="16152-356">Opting out of native image generation</span></span>  
 <span data-ttu-id="16152-357">NGen.exe v některých případech může mít potíže při generování, které nativních bitových kopií pro konkrétní metody, ale možná dáte přednost, že metoda být kompilována JIT místo toho potom zkompiluje nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-357">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="16152-358">V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut zabránit NGen.exe generuje nativní bitové kopie pro konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="16152-358">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="16152-359">Atribut musí být použit jednotlivě pro každou metodu, jejíž kód nechcete zahrnout do nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-359">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="16152-360">NGen.exe rozpozná atribut a nevygeneruje žádný kód v nativních bitových kopií pro odpovídající metody.</span><span class="sxs-lookup"><span data-stu-id="16152-360">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>  
  
 <span data-ttu-id="16152-361">Upozorňujeme, že `BypassNGenAttribute` není definován jako typ v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16152-361">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="16152-362">Aby bylo možné využívat atribut ve vašem kódu, je nutné definovat ho následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="16152-362">In order to consume the attribute in your code, you must first define it as follows:</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 <span data-ttu-id="16152-363">Atribut lze následně použít na základě-method.</span><span class="sxs-lookup"><span data-stu-id="16152-363">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="16152-364">Následující příklad nastaví Native Image Generator, že by neměla generovat nativních bitových kopií pro `ExampleClass.ToJITCompile` metody.</span><span class="sxs-lookup"><span data-stu-id="16152-364">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a><span data-ttu-id="16152-365">Příklady</span><span class="sxs-lookup"><span data-stu-id="16152-365">Examples</span></span>  
 <span data-ttu-id="16152-366">Následující příkaz vytvoří nativní bitovou kopii pro `ClientApp.exe`nachází v aktuálním adresáři a nainstaluje bitovou kopii v mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-366">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="16152-367">Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije.</span><span class="sxs-lookup"><span data-stu-id="16152-367">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="16152-368">Kromě toho nativní bitové kopie jsou generovány pro všechny soubory .dll, který `ClientApp.exe` odkazy.</span><span class="sxs-lookup"><span data-stu-id="16152-368">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>  
  
```  
ngen install ClientApp.exe  
```  
  
 <span data-ttu-id="16152-369">Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen.</span><span class="sxs-lookup"><span data-stu-id="16152-369">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="16152-370">Kořen může být aplikace nebo sdílená komponenta.</span><span class="sxs-lookup"><span data-stu-id="16152-370">A root can be an application or a shared component.</span></span>  
  
 <span data-ttu-id="16152-371">Následující příkaz vytvoří nativní bitovou kopii pro `MyAssembly.exe` se zadanou cestou.</span><span class="sxs-lookup"><span data-stu-id="16152-371">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 <span data-ttu-id="16152-372">Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="16152-372">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="16152-373">Ve výchozím adresáři, který obsahuje `ClientApp.exe` slouží jako základní adresář aplikace a veškeré zjišťování sestavení začíná v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="16152-373">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="16152-374">Toto chování můžete přepsat pomocí `/AppBase` možnost.</span><span class="sxs-lookup"><span data-stu-id="16152-374">You can override this behavior by using the `/AppBase` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-375">Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="16152-375">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>  
  
 <span data-ttu-id="16152-376">Sestavení může mít závislost bez odkazu, například pokud načte soubor .dll pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="16152-376">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="16152-377">Můžete vytvořit nativní bitovou kopii pro takový soubor .dll pomocí konfigurační informace pro sestavení aplikace s `/ExeConfig` možnost.</span><span class="sxs-lookup"><span data-stu-id="16152-377">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="16152-378">Následující příkaz vytvoří nativní bitovou kopii pro `MyLib.dll,` pomocí konfiguračních informací z `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="16152-378">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="16152-379">Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="16152-379">Assemblies installed in this way are not removed when the application is removed.</span></span>  
  
 <span data-ttu-id="16152-380">Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="16152-380">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="16152-381">Následující příkaz odinstaluje `MyLib.dll` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="16152-381">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="16152-382">Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-382">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="16152-383">Příklad:</span><span class="sxs-lookup"><span data-stu-id="16152-383">For example:</span></span>  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 <span data-ttu-id="16152-384">NGen.exe vytváří samostatnou sadu bitových kopií pro každý scénář, který instalujete.</span><span class="sxs-lookup"><span data-stu-id="16152-384">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="16152-385">Například následující příkazy nainstalují kompletní sadu nativních bitových kopií pro normální provoz, jinou kompletní sadu pro ladění a třetí pro profilování:</span><span class="sxs-lookup"><span data-stu-id="16152-385">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="16152-386">Zobrazení mezipaměti nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="16152-386">Displaying the Native Image Cache</span></span>  
 <span data-ttu-id="16152-387">Jakmile jsou nativní bitové kopie nainstalovány v mezipaměti, lze je zobrazit pomocí nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-387">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="16152-388">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-388">The following command displays all native images in the native image cache.</span></span>  
  
```  
ngen display  
```  
  
 <span data-ttu-id="16152-389">`display` Seznamy akcí všechna kořenová sestavení nejprve následovaný seznamem všech nativních bitových kopií v počítači.</span><span class="sxs-lookup"><span data-stu-id="16152-389">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>  
  
 <span data-ttu-id="16152-390">Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="16152-390">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="16152-391">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií, které se shodují v částečném názvu `MyAssembly`, jejich závislostech a všech kořenech majících závislost na `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="16152-391">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>  
  
```  
ngen display MyAssembly  
```  
  
 <span data-ttu-id="16152-392">Znalost, které kořeny závisí na sdíleném sestavení komponenty je užitečná při měření dopadu `update` akce po upgradu sdílené komponenty.</span><span class="sxs-lookup"><span data-stu-id="16152-392">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>  
  
 <span data-ttu-id="16152-393">Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:</span><span class="sxs-lookup"><span data-stu-id="16152-393">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 <span data-ttu-id="16152-394">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií s názvem `MyAssembly` a verzi 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="16152-394">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a><span data-ttu-id="16152-395">Aktualizace bitových kopií</span><span class="sxs-lookup"><span data-stu-id="16152-395">Updating Images</span></span>  
 <span data-ttu-id="16152-396">Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty.</span><span class="sxs-lookup"><span data-stu-id="16152-396">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="16152-397">Chcete-li aktualizovat všechny nativní bitové kopie, které se změnily, nebo se změnily jejich závislosti, použijte `update` akce bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="16152-397">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>  
  
```  
ngen update  
```  
  
 <span data-ttu-id="16152-398">Aktualizace všech bitových kopií může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="16152-398">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="16152-399">Aktualizace pro spuštění službou nativních bitových kopií může fronty pomocí `/queue` možnost.</span><span class="sxs-lookup"><span data-stu-id="16152-399">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="16152-400">Další informace o `/queue` možnost a instalačních prioritách naleznete v tématu [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-400">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a><span data-ttu-id="16152-401">Odinstalování bitových kopií</span><span class="sxs-lookup"><span data-stu-id="16152-401">Uninstalling Images</span></span>  
 <span data-ttu-id="16152-402">Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="16152-402">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="16152-403">Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.</span><span class="sxs-lookup"><span data-stu-id="16152-403">In addition, a shared component is not removed if it has been installed as a root.</span></span>  
  
 <span data-ttu-id="16152-404">Následující příkaz odinstaluje všechny scénáře kořenu `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="16152-404">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp  
```  
  
 <span data-ttu-id="16152-405">`uninstall` Akce slouží k odebrání konkrétních scénářů.</span><span class="sxs-lookup"><span data-stu-id="16152-405">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="16152-406">Následující příkaz odinstaluje všechny ladicí scénáře pro `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="16152-406">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  <span data-ttu-id="16152-407">Odinstalace `/debug` scénáře neodinstaluje scénáře zahrnující současně obě `/profile` a</span><span class="sxs-lookup"><span data-stu-id="16152-407">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and</span></span> `/debug.`  
  
 <span data-ttu-id="16152-408">Následující příkaz odinstaluje všechny scénáře pro konkrétní verzi `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="16152-408">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 <span data-ttu-id="16152-409">Následující příkaz odinstaluje všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo pouze jeho ladicí scénář pro toto sestavení:</span><span class="sxs-lookup"><span data-stu-id="16152-409">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 <span data-ttu-id="16152-410">Stejně jako u `install` akce zadání přípony zapotřebí buď spuštění Ngen.exe z adresáře obsahujícího sestavení, nebo zadání úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="16152-410">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>  
  
 <span data-ttu-id="16152-411">Příklady pro službu nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-411">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>  
  
## <a name="native-image-task"></a><span data-ttu-id="16152-412">Úloha pro nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="16152-412">Native Image Task</span></span>  
 <span data-ttu-id="16152-413">Úloha pro nativní bitové kopie je Windows úlohu, která vytváří a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-413">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="16152-414">Úloha pro nativní bitové kopie vygeneruje a uvolní nativních bitových kopií automaticky pro podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="16152-414">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="16152-415">Umožňuje také instalační programy používat [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) vytvářet a aktualizovat nativní bitové kopie odložené najednou.</span><span class="sxs-lookup"><span data-stu-id="16152-415">It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>  
  
 <span data-ttu-id="16152-416">Úloha pro nativní bitové kopie je zaregistrovaný jednou pro každý procesor architektury podporována v počítači, aby kompilace pro aplikace, které se zaměřují každou architekturu:</span><span class="sxs-lookup"><span data-stu-id="16152-416">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>  
  
|<span data-ttu-id="16152-417">Název úlohy</span><span class="sxs-lookup"><span data-stu-id="16152-417">Task name</span></span>|<span data-ttu-id="16152-418">32bitový počítač</span><span class="sxs-lookup"><span data-stu-id="16152-418">32-bit computer</span></span>|<span data-ttu-id="16152-419">64bitový počítač</span><span class="sxs-lookup"><span data-stu-id="16152-419">64-bit computer</span></span>|  
|---------------|----------------------|----------------------|  
|<span data-ttu-id="16152-420">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="16152-420">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="16152-421">Ano</span><span class="sxs-lookup"><span data-stu-id="16152-421">Yes</span></span>|<span data-ttu-id="16152-422">Ano</span><span class="sxs-lookup"><span data-stu-id="16152-422">Yes</span></span>|  
|<span data-ttu-id="16152-423">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="16152-423">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="16152-424">Ne</span><span class="sxs-lookup"><span data-stu-id="16152-424">No</span></span>|<span data-ttu-id="16152-425">Ano</span><span class="sxs-lookup"><span data-stu-id="16152-425">Yes</span></span>|  
  
 <span data-ttu-id="16152-426">Úloha pro nativní bitové kopie je k dispozici v rozhraní .NET Framework 4.5 a novější verze, při spouštění v systému Windows 8 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="16152-426">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="16152-427">Ve starších verzích Windows rozhraní .NET Framework používá [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="16152-427">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>  
  
### <a name="task-lifetime"></a><span data-ttu-id="16152-428">Doba života úkolu</span><span class="sxs-lookup"><span data-stu-id="16152-428">Task Lifetime</span></span>  
 <span data-ttu-id="16152-429">Obecně platí Plánovač úloh Windows spustí úloha pro nativní bitové kopie každou noc, pokud je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="16152-429">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="16152-430">Úloha zkontroluje odložená práce, zařazených do fronty tak, že instalační programy aplikací, všechny žádosti o aktualizaci odložené nativních bitových kopií a vytvoření jakékoli automatické bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-430">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="16152-431">Úloha dokončení nevyřízených pracovních položek a potom vypne.</span><span class="sxs-lookup"><span data-stu-id="16152-431">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="16152-432">Pokud počítač přestane nečinnosti, zatímco úloha běží, zastaví úlohu.</span><span class="sxs-lookup"><span data-stu-id="16152-432">If the computer stops being idle while the task is running, the task stops.</span></span>  
  
 <span data-ttu-id="16152-433">Můžete spustit také úkol nativní bitové kopie ručně prostřednictvím uživatelského rozhraní plánovače úloh nebo ruční volání NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-433">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="16152-434">Pokud úloha je spuštěna pomocí některé z těchto metod, budou spuštěny při nečinnosti počítače už.</span><span class="sxs-lookup"><span data-stu-id="16152-434">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="16152-435">Bitové kopie ručně vytvořené pomocí NGen.exe budou mít vyšší prioritu, abyste umožnili předvídatelný chování pro instalační programy aplikací.</span><span class="sxs-lookup"><span data-stu-id="16152-435">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>  
  
## <a name="native-image-service"></a><span data-ttu-id="16152-436">Nativní bitová kopie služby</span><span class="sxs-lookup"><span data-stu-id="16152-436">Native Image Service</span></span>  
 <span data-ttu-id="16152-437">Službu nativních bitových kopií je služba Windows, která vytváří a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="16152-437">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="16152-438">Službu nativních bitových kopií umožňuje vývojářům odložení instalace a aktualizace nativní bitové kopie do období při nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-438">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>  
  
 <span data-ttu-id="16152-439">Za normálních okolností instalačního programu (Instalační program) pro aplikace nebo aktualizace Inicializuje službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-439">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="16152-440">Pro akce prioritou 3 služba prováděla během doby nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="16152-440">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="16152-441">Služba ukládá svůj stav a je schopný pokračováním prostřednictvím více restartování v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="16152-441">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="16152-442">Více kompilace image můžete zařadit do fronty.</span><span class="sxs-lookup"><span data-stu-id="16152-442">Multiple image compilations can be queued.</span></span>  
  
 <span data-ttu-id="16152-443">Služba také pracuje s ruční příkaz Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-443">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="16152-444">Ruční příkazy mají přednost před aktivitu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="16152-444">Manual commands take precedence over background activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16152-445">V systému Windows Vista je název zobrazený pro službu nativních bitových kopií "v2.0.50727_X86 NGEN Microsoft.NET Framework" nebo "Microsoft.NET Framework NGEN v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="16152-445">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="16152-446">Všechny starší verze systému Microsoft Windows název je "Služby .NET Runtime optimalizace v2.0.50727_X86" nebo "Služby .NET Runtime optimalizace v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="16152-446">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>  
  
### <a name="launching-deferred-operations"></a><span data-ttu-id="16152-447">Spouští se operace odložené</span><span class="sxs-lookup"><span data-stu-id="16152-447">Launching Deferred Operations</span></span>  
 <span data-ttu-id="16152-448">Před zahájením instalace nebo upgradu, se doporučuje pozastavení služby.</span><span class="sxs-lookup"><span data-stu-id="16152-448">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="16152-449">Tím se zajistí, že služba nespustí při kopírování souborů instalačního programu nebo vložení sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="16152-449">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="16152-450">Následující příkazový řádek Ngen.exe pozastaví službu:</span><span class="sxs-lookup"><span data-stu-id="16152-450">The following Ngen.exe command line pauses the service:</span></span>  
  
```  
ngen queue pause  
```  
  
 <span data-ttu-id="16152-451">Pokud všechny operace odložené byl zařazen do fronty, umožňuje následující příkaz na obnovení služby:</span><span class="sxs-lookup"><span data-stu-id="16152-451">When all deferred operations have been queued, the following command allows the service to resume:</span></span>  
  
```  
ngen queue continue  
```  
  
 <span data-ttu-id="16152-452">Chcete-li odložit generování nativních bitových kopií při instalaci nové aplikace nebo při aktualizaci sdílené komponenty, použijte `/queue` spolu s možností `install` nebo `update` akce.</span><span class="sxs-lookup"><span data-stu-id="16152-452">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="16152-453">Následujících příkazových řádků Ngen.exe instalaci nativních bitových kopií pro sdílené komponenty a proveďte aktualizaci všechny kořenové adresáře, které může mít dopad:</span><span class="sxs-lookup"><span data-stu-id="16152-453">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 <span data-ttu-id="16152-454">`update` Akce obnoví všechny nativní bitové kopie, které byly zneplatněny, nejen ty, které používají `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="16152-454">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>  
  
 <span data-ttu-id="16152-455">Pokud vaše aplikace se skládá z mnoha kořeny, můžete určit prioritu odložené akce.</span><span class="sxs-lookup"><span data-stu-id="16152-455">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="16152-456">Následující příkazy fronty instalace tři kořenové adresáře.</span><span class="sxs-lookup"><span data-stu-id="16152-456">The following commands queue the installation of three roots.</span></span> `Assembly1` <span data-ttu-id="16152-457">je nainstalována jako první, bez čekání na nečinnost.</span><span class="sxs-lookup"><span data-stu-id="16152-457">is installed first, without waiting for idle time.</span></span> `Assembly2` <span data-ttu-id="16152-458">je také nainstalovat bez čekací dobu nečinnosti, ale po dokončení všech akcí s prioritou 1.</span><span class="sxs-lookup"><span data-stu-id="16152-458">is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> `Assembly3` <span data-ttu-id="16152-459">je nainstalována, když služba zjistí, že je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="16152-459">is installed when the service detects that the computer is idle.</span></span>  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 <span data-ttu-id="16152-460">Můžete vynutit zařazených do fronty akce neproběhne synchronně pomocí `executeQueuedItems` akce.</span><span class="sxs-lookup"><span data-stu-id="16152-460">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="16152-461">Pokud zadáte volitelné prioritu, tato akce ovlivní pouze zařazených do fronty akce, které mají stejné nebo nižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="16152-461">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="16152-462">Výchozí hodnota priority je 3, tak příkaz Ngen.exe okamžitě zpracovává všechny akce ve frontě a nevrací až skončí:</span><span class="sxs-lookup"><span data-stu-id="16152-462">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>  
  
```  
ngen executeQueuedItems  
```  
  
 <span data-ttu-id="16152-463">Synchronní příkazy jsou spouštěny příkazem Ngen.exe a nepoužívejte službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-463">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="16152-464">Můžete provést akce pomocí Ngen.exe, zatímco se službou nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="16152-464">You can execute actions using Ngen.exe while the native image service is running.</span></span>  
  
### <a name="service-shutdown"></a><span data-ttu-id="16152-465">Vypnutí služby</span><span class="sxs-lookup"><span data-stu-id="16152-465">Service Shutdown</span></span>  
 <span data-ttu-id="16152-466">Po iniciováno prováděním příkazu Ngen.exe, která zahrnuje `/queue` možnost, služba běží na pozadí dokud nejsou dokončeny všechny akce.</span><span class="sxs-lookup"><span data-stu-id="16152-466">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="16152-467">Služba ukládá svůj stav tak, že můžete pokračovat až do více restartování v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="16152-467">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="16152-468">Když služba zjistí, že neexistují žádné další akce ve frontě, obnoví svůj stav tak, aby nerestartuje při příštím spuštění počítače a pak ji vypne samotný.</span><span class="sxs-lookup"><span data-stu-id="16152-468">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>  
  
### <a name="service-interaction-with-clients"></a><span data-ttu-id="16152-469">Služba interakci s klienty</span><span class="sxs-lookup"><span data-stu-id="16152-469">Service Interaction with Clients</span></span>  
 <span data-ttu-id="16152-470">V rozhraní .NET Framework verze 2.0 je pouze interakci se službou nativních bitových kopií pomocí příkazového řádku nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="16152-470">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="16152-471">Pomocí nástroje příkazového řádku ve skriptů instalace pro akce fronty pro službu nativních bitových kopií a k interakci se službou.</span><span class="sxs-lookup"><span data-stu-id="16152-471">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16152-472">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16152-472">See also</span></span>

- [<span data-ttu-id="16152-473">Nástroje</span><span class="sxs-lookup"><span data-stu-id="16152-473">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="16152-474">Proces spravovaného spouštění</span><span class="sxs-lookup"><span data-stu-id="16152-474">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)
- [<span data-ttu-id="16152-475">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="16152-475">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="16152-476">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="16152-476">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
