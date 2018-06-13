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
ms.openlocfilehash: f0811e32a9483238d1cd15084c19951075c8a36a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399539"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="b2923-102">Ngen.exe (generátor nativních obrázků)</span><span class="sxs-lookup"><span data-stu-id="b2923-102">Ngen.exe (Native Image Generator)</span></span>
<span data-ttu-id="b2923-103">Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="b2923-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="b2923-104">Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b2923-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="b2923-105">Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="b2923-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>  
  
 <span data-ttu-id="b2923-106">Změny Ngen.exe v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b2923-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>  
  
-   <span data-ttu-id="b2923-107">Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.</span><span class="sxs-lookup"><span data-stu-id="b2923-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
-   <span data-ttu-id="b2923-108">Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="b2923-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>  
  
 <span data-ttu-id="b2923-109">Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:</span><span class="sxs-lookup"><span data-stu-id="b2923-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>  
  
-   <span data-ttu-id="b2923-110">Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>  
  
-   <span data-ttu-id="b2923-111">Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="b2923-111">Native images can now be shared across application domains.</span></span>  
  
-   <span data-ttu-id="b2923-112">Nová akce `update`, znovu vytvoří bitové kopie, které se zrušila platnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-112">A new action, `update`, re-creates images that have been invalidated.</span></span>  
  
-   <span data-ttu-id="b2923-113">Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>  
  
-   <span data-ttu-id="b2923-114">Některé příčiny zneplatnění bitové kopie byly odstraněny.</span><span class="sxs-lookup"><span data-stu-id="b2923-114">Some causes of image invalidation have been eliminated.</span></span>  
  
 <span data-ttu-id="b2923-115">V systému Windows 8, najdete v části [nativní bitové kopie úloh](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span><span class="sxs-lookup"><span data-stu-id="b2923-115">On Windows 8, see [Native Image Task](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span></span>  
  
 <span data-ttu-id="b2923-116">Další informace o používání Ngen.exe a služba nativních bitových kopií naleznete v části [nativní bitové kopie služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service][Native Image Service].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-117">Ngen.exe syntaxi pro verze 1.0 a 1.1 rozhraní .NET Framework naleznete v [generátor (Ngen.exe) zastaralé syntaxe](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span><span class="sxs-lookup"><span data-stu-id="b2923-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span></span>  
  
 <span data-ttu-id="b2923-118">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2923-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b2923-119">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b2923-119">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b2923-120">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b2923-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b2923-121">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="b2923-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2923-122">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2923-122">Syntax</span></span>  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a><span data-ttu-id="b2923-123">Akce</span><span class="sxs-lookup"><span data-stu-id="b2923-123">Actions</span></span>  
 <span data-ttu-id="b2923-124">Následující tabulka ukazuje syntaxi jednotlivých `action`.</span><span class="sxs-lookup"><span data-stu-id="b2923-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="b2923-125">Popis jednotlivých částí `action`, najdete v článku [argumenty](#ArgumentTable), [úroveň Priority](#PriorityTable), [scénáře](#ScenarioTable), a [konfigurace](#ConfigTable)tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2923-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="b2923-126">[Možnosti](#OptionTable) tabulce jsou popsány `options` a přepínače nápovědy.</span><span class="sxs-lookup"><span data-stu-id="b2923-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>  
  
|<span data-ttu-id="b2923-127">Akce</span><span class="sxs-lookup"><span data-stu-id="b2923-127">Action</span></span>|<span data-ttu-id="b2923-128">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b2923-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="b2923-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="b2923-130">Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="b2923-131">Pokud `/queue` je zadána akce ve frontě pro službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="b2923-132">Výchozí hodnota priority je 3.</span><span class="sxs-lookup"><span data-stu-id="b2923-132">The default priority is 3.</span></span> <span data-ttu-id="b2923-133">Najdete v článku [úroveň Priority](#PriorityTable) tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2923-133">See the [Priority Levels](#PriorityTable) table.</span></span>|  
|<span data-ttu-id="b2923-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="b2923-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="b2923-135">Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="b2923-136">Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="b2923-137">**Poznámka:** začínající [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], akce `uninstall` \* již není podporována.</span><span class="sxs-lookup"><span data-stu-id="b2923-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` \* is no longer supported.</span></span>|  
|<span data-ttu-id="b2923-138">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="b2923-138">`update` [`/queue`]</span></span>|<span data-ttu-id="b2923-139">Aktualizuje nativní bitové kopie, které se staly neplatnými.</span><span class="sxs-lookup"><span data-stu-id="b2923-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="b2923-140">Pokud `/queue` není zadaný, aktualizace jsou zařazeny do fronty pro službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="b2923-141">Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="b2923-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|  
|<span data-ttu-id="b2923-142">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="b2923-142">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="b2923-143">Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="b2923-144">Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|  
|<span data-ttu-id="b2923-145">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="b2923-145">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="b2923-146">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b2923-146">-or-</span></span><br /><br /> <span data-ttu-id="b2923-147">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="b2923-147">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="b2923-148">Spustí úlohy kompilace ve frontě.</span><span class="sxs-lookup"><span data-stu-id="b2923-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="b2923-149">Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou.</span><span class="sxs-lookup"><span data-stu-id="b2923-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="b2923-150">Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.</span><span class="sxs-lookup"><span data-stu-id="b2923-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|  
|<span data-ttu-id="b2923-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="b2923-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="b2923-152">Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.</span><span class="sxs-lookup"><span data-stu-id="b2923-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a><span data-ttu-id="b2923-153">Arguments</span><span class="sxs-lookup"><span data-stu-id="b2923-153">Arguments</span></span>  
  
|<span data-ttu-id="b2923-154">Argument</span><span class="sxs-lookup"><span data-stu-id="b2923-154">Argument</span></span>|<span data-ttu-id="b2923-155">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-155">Description</span></span>|  
|--------------|-----------------|  
|`assemblyName`|<span data-ttu-id="b2923-156">Plný zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-156">The full display name of the assembly.</span></span> <span data-ttu-id="b2923-157">Například `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="b2923-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="b2923-158">**Poznámka:** můžete například zadat název částečného sestavení, `myAssembly`, pro `display` a `uninstall` akce.</span><span class="sxs-lookup"><span data-stu-id="b2923-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="b2923-159">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
|`assemblyPath`|<span data-ttu-id="b2923-160">Explicitní cesta k sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-160">The explicit path of the assembly.</span></span> <span data-ttu-id="b2923-161">Lze zadat úplnou nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="b2923-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="b2923-162">Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="b2923-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="b2923-163">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a><span data-ttu-id="b2923-164">Úrovně priority</span><span class="sxs-lookup"><span data-stu-id="b2923-164">Priority Levels</span></span>  
  
|<span data-ttu-id="b2923-165">Priorita</span><span class="sxs-lookup"><span data-stu-id="b2923-165">Priority</span></span>|<span data-ttu-id="b2923-166">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-166">Description</span></span>|  
|--------------|-----------------|  
|`1`|<span data-ttu-id="b2923-167">Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.</span><span class="sxs-lookup"><span data-stu-id="b2923-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|  
|`2`|<span data-ttu-id="b2923-168">Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).</span><span class="sxs-lookup"><span data-stu-id="b2923-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|  
|`3`|<span data-ttu-id="b2923-169">Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="b2923-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="b2923-170">V tématu [nativních bitových kopií služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-170">See [Native Image Service][Native Image Service].</span></span>|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a><span data-ttu-id="b2923-171">Scénáře</span><span class="sxs-lookup"><span data-stu-id="b2923-171">Scenarios</span></span>  
  
|<span data-ttu-id="b2923-172">Scénář</span><span class="sxs-lookup"><span data-stu-id="b2923-172">Scenario</span></span>|<span data-ttu-id="b2923-173">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-173">Description</span></span>|  
|--------------|-----------------|  
|`/Debug`|<span data-ttu-id="b2923-174">Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="b2923-174">Generate native images that can be used under a debugger.</span></span>|  
|`/Profile`|<span data-ttu-id="b2923-175">Vygeneruje nativní bitové kopie, které lze použít v profileru.</span><span class="sxs-lookup"><span data-stu-id="b2923-175">Generate native images that can be used under a profiler.</span></span>|  
|`/NoDependencies`|<span data-ttu-id="b2923-176">Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.</span><span class="sxs-lookup"><span data-stu-id="b2923-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a><span data-ttu-id="b2923-177">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b2923-177">Config</span></span>  
  
|<span data-ttu-id="b2923-178">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b2923-178">Configuration</span></span>|<span data-ttu-id="b2923-179">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-179">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="b2923-180">`/ExeConfig:``exePath`</span><span class="sxs-lookup"><span data-stu-id="b2923-180">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="b2923-181">Použije konfiguraci zadaného spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-181">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="b2923-182">Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč.</span><span class="sxs-lookup"><span data-stu-id="b2923-182">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="b2923-183">Po načtení sdílená součást v době běhu pomocí <xref:System.Reflection.Assembly.Load%2A> metoda, konfigurační soubor aplikace určuje závislosti, které jsou načteny sdílená součást – například verzi závislostí, který je načten.</span><span class="sxs-lookup"><span data-stu-id="b2923-183">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="b2923-184">`/ExeConfig` Přepínač poskytuje pokyny Ngen.exe, na kterém by závislosti načíst za běhu.</span><span class="sxs-lookup"><span data-stu-id="b2923-184">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|  
|<span data-ttu-id="b2923-185">`/AppBase:``directoryPath`</span><span class="sxs-lookup"><span data-stu-id="b2923-185">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="b2923-186">Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.</span><span class="sxs-lookup"><span data-stu-id="b2923-186">When locating dependencies, use the specified directory as the application base.</span></span>|  
  
<a name="OptionTable"></a>   
## <a name="options"></a><span data-ttu-id="b2923-187">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b2923-187">Options</span></span>  
  
|<span data-ttu-id="b2923-188">Možnost</span><span class="sxs-lookup"><span data-stu-id="b2923-188">Option</span></span>|<span data-ttu-id="b2923-189">Popis</span><span class="sxs-lookup"><span data-stu-id="b2923-189">Description</span></span>|  
|------------|-----------------|  
|`/nologo`|<span data-ttu-id="b2923-190">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b2923-190">Suppress the Microsoft startup banner display.</span></span>|  
|`/silent`|<span data-ttu-id="b2923-191">Potlačí zobrazování zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="b2923-191">Suppress the display of success messages.</span></span>|  
|`/verbose`|<span data-ttu-id="b2923-192">Zobrazí podrobné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="b2923-192">Display detailed information for debugging.</span></span> <span data-ttu-id="b2923-193">**Poznámka:** z důvodu omezení operačního systému, tato možnost nezobrazí tolik Další informace v systému Windows 98 a Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="b2923-193">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|  
|<span data-ttu-id="b2923-194">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="b2923-194">`/help`, `/?`</span></span>|<span data-ttu-id="b2923-195">Zobrazí syntaxi příkazu a možnosti aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="b2923-195">Display command syntax and options for the current release.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2923-196">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2923-196">Remarks</span></span>  
 <span data-ttu-id="b2923-197">Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b2923-197">To run Ngen.exe, you must have administrative privileges.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b2923-198">Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-198">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="b2923-199">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe zkompiluje sestavení s úplným vztahem důvěryhodnosti a zásady (CAS) zabezpečení přístupu kódu už nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="b2923-199">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
 <span data-ttu-id="b2923-200">Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nativní bitové kopie, které se generují s Ngen.exe již nebude možné načíst do aplikace, které jsou spuštěny v částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-200">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="b2923-201">Namísto toho je vyvolán kompilátor za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="b2923-201">Instead, the just-in-time (JIT) compiler is invoked.</span></span>  
  
 <span data-ttu-id="b2923-202">Ngen.exe generuje nativní bitové kopie pro sestavení určeného `assemblyname` argument `install` akce a všechny jeho závislé součásti.</span><span class="sxs-lookup"><span data-stu-id="b2923-202">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="b2923-203">Závislosti se stanoví z odkazů v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-203">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="b2923-204">Jediný scénář, ve kterém je potřeba instalovat samostatně závislost je při načtení aplikace pomocí reflexe, například voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b2923-204">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2923-205">Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda s nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-205">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="b2923-206">Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="b2923-206">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>  
  
 <span data-ttu-id="b2923-207">Nástroj Ngen.exe udržuje počet odkazů na závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-207">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="b2923-208">Předpokládejme například, `MyAssembly.exe` a `YourAssembly.exe` jsou nainstalovány v mezipaměť nativních bitových kopií a mohou mít odkazy na `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="b2923-208">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="b2923-209">Pokud `MyAssembly.exe` odinstalaci `OurDependency.dll` není odinstalována.</span><span class="sxs-lookup"><span data-stu-id="b2923-209">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="b2923-210">Je jenom odebrány při `YourAssembly.exe` je také odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2923-210">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>  
  
 <span data-ttu-id="b2923-211">Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="b2923-211">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="b2923-212">V tématu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2923-212">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b2923-213">Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-213">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="b2923-214">To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-214">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="b2923-215">Určení neutrality domény:</span><span class="sxs-lookup"><span data-stu-id="b2923-215">To specify domain neutrality:</span></span>  
  
-   <span data-ttu-id="b2923-216">Použít <xref:System.LoaderOptimizationAttribute> atributu do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-216">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>  
  
-   <span data-ttu-id="b2923-217">Nastavte <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> vlastnost při vytváření informace o instalaci pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-217">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>  
  
 <span data-ttu-id="b2923-218">Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-218">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="b2923-219">Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.</span><span class="sxs-lookup"><span data-stu-id="b2923-219">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-220">Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.</span><span class="sxs-lookup"><span data-stu-id="b2923-220">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>  
  
 <span data-ttu-id="b2923-221">V této části Poznámky:</span><span class="sxs-lookup"><span data-stu-id="b2923-221">In this Remarks section:</span></span>  
  
-   [<span data-ttu-id="b2923-222">Generování bitových kopií pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="b2923-222">Generating images for different scenarios</span></span>](#Scenarios)  
  
-   [<span data-ttu-id="b2923-223">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="b2923-223">Determining when to Use native images</span></span>](#WhenToUse)  
  
    -   [<span data-ttu-id="b2923-224">Vylepšené využití paměti</span><span class="sxs-lookup"><span data-stu-id="b2923-224">Improved memory use</span></span>](#Memory)  
  
    -   [<span data-ttu-id="b2923-225">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="b2923-225">Faster application startup</span></span>](#Startup)  
  
    -   [<span data-ttu-id="b2923-226">Souhrn využití aspekty</span><span class="sxs-lookup"><span data-stu-id="b2923-226">Summary of usage considerations</span></span>](#UsageSummary)  
  
-   [<span data-ttu-id="b2923-227">Důležitost základní adresy sestavení</span><span class="sxs-lookup"><span data-stu-id="b2923-227">Importance of assembly base addresses</span></span>](#BaseAddresses)  
  
-   [<span data-ttu-id="b2923-228">Pevné vazby</span><span class="sxs-lookup"><span data-stu-id="b2923-228">Hard binding</span></span>](#HardBinding)  
  
    -   [<span data-ttu-id="b2923-229">Určení vazby nápovědu pro závislosti</span><span class="sxs-lookup"><span data-stu-id="b2923-229">Specifying a binding hint for a dependency</span></span>](#DependencyHint)  
  
    -   [<span data-ttu-id="b2923-230">Určení výchozí vazby nápovědu pro sestavení</span><span class="sxs-lookup"><span data-stu-id="b2923-230">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)  
  
-   [<span data-ttu-id="b2923-231">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="b2923-231">Deferred processing</span></span>](#Deferred)  
  
-   [<span data-ttu-id="b2923-232">Nativní bitové kopie a JIT – kompilace</span><span class="sxs-lookup"><span data-stu-id="b2923-232">Native images and JIT compilation</span></span>](#JITCompilation)  
  
    -   [<span data-ttu-id="b2923-233">Neplatné obrázky</span><span class="sxs-lookup"><span data-stu-id="b2923-233">Invalid images</span></span>](#InvalidImages)  
  
-   [<span data-ttu-id="b2923-234">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="b2923-234">Troubleshooting</span></span>](#Troubleshooting)  
  
    -   [<span data-ttu-id="b2923-235">Vazba sestavení – Prohlížeč protokolu</span><span class="sxs-lookup"><span data-stu-id="b2923-235">Assembly Binding Log Viewer</span></span>](#Fusion)  
  
    -   [<span data-ttu-id="b2923-236">JITCompilationStart spravované ladění pomocníka</span><span class="sxs-lookup"><span data-stu-id="b2923-236">The JITCompilationStart managed debugging assistant</span></span>](#MDA)  
  
    -   [<span data-ttu-id="b2923-237">Zrušení generování nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="b2923-237">Opting out of native image generation</span></span>](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="b2923-238">Generování bitových kopií pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="b2923-238">Generating images for     different scenarios</span></span>  
 <span data-ttu-id="b2923-239">Po vygenerování nativních bitových kopií pro sestavení modulu runtime automaticky pokusí vyhledat a použít tento nativních bitových kopií pokaždé, když ji spustí sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-239">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="b2923-240">V závislosti na scénáři lze generovat více bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-240">Multiple images can be generated, depending on usage scenarios.</span></span>  
  
 <span data-ttu-id="b2923-241">Například pokud spustíte sestavení ladění nebo profilace scénář, modul runtime hledá nativních bitových kopií, který se vygeneroval s `/Debug` nebo `/Profile` možnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-241">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="b2923-242">Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b2923-242">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="b2923-243">Jediný způsob, jak ladit nativní bitové kopie je vytvoření nativní bitové kopie s `/Debug` možnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-243">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>  
  
 <span data-ttu-id="b2923-244">`uninstall` Akce také rozpoznat scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybraného scénáře.</span><span class="sxs-lookup"><span data-stu-id="b2923-244">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="b2923-245">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="b2923-245">Determining when to Use native images</span></span>  
 <span data-ttu-id="b2923-246">Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.</span><span class="sxs-lookup"><span data-stu-id="b2923-246">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-247">Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="b2923-247">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="b2923-248">Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.</span><span class="sxs-lookup"><span data-stu-id="b2923-248">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a><span data-ttu-id="b2923-249">Vylepšené využití paměti</span><span class="sxs-lookup"><span data-stu-id="b2923-249">Improved memory use</span></span>  
 <span data-ttu-id="b2923-250">Nativní bitové kopie mohou významně zlepšit využití paměti, je-li kód sdílen mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b2923-250">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="b2923-251">Nativní bitové kopie jsou soubory Windows PE, tudíž jedna kopie souboru .dll může být sdílena několika procesy. Naproti tomu nativní kód vytvořený kompilátorem JIT je uložen v soukromé paměti a nelze jej sdílet.</span><span class="sxs-lookup"><span data-stu-id="b2923-251">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>  
  
 <span data-ttu-id="b2923-252">Aplikace spuštěné v rámci terminálových služeb také využívají výhod sdílených znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="b2923-252">Applications that are run under terminal services can also benefit from shared code pages.</span></span>  
  
 <span data-ttu-id="b2923-253">Kromě toho skutečnost, že není načítán kompilátor JIT, ušetří pevně dané množství paměti pro každou instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-253">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a><span data-ttu-id="b2923-254">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="b2923-254">Faster application startup</span></span>  
 <span data-ttu-id="b2923-255">Předkompilování sestavení programem Ngen.exe může zvýšit rychlost spuštění některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="b2923-255">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="b2923-256">Obecně lze zvýšení výkonu dosáhnout tam, kde aplikace sdílejí sestavení komponent, protože po prvním spuštění aplikace jsou komponenty sdílené s jinými aplikacemi již načteny.</span><span class="sxs-lookup"><span data-stu-id="b2923-256">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="b2923-257">Úplné spuštění, při němž musí být všechna sestavení aplikace načtena z pevného disku, nevyužívají výhod nativních bitových kopií v takové míře, protože má převahu přístupová doba pevného disku.</span><span class="sxs-lookup"><span data-stu-id="b2923-257">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>  
  
 <span data-ttu-id="b2923-258">Pevné vazby mohou ovlivnit rychlost spuštění, protože všechny bitové kopie pevně svázané s hlavním sestavením aplikace musí být načteny najednou.</span><span class="sxs-lookup"><span data-stu-id="b2923-258">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-259">Před [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], byste měli umístit sdílené, silným názvem součásti v globální mezipaměti sestavení, protože zavaděč provádí sestavení se silným názvem, které nejsou v globální mezipaměti sestavení, což eliminuje efektivně zlepšení doplňující ověření v čase spuštění získaných pomocí nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-259">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="b2923-260">Optimalizace, které byly zavedeny v [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] odebrat doplňující ověření.</span><span class="sxs-lookup"><span data-stu-id="b2923-260">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a><span data-ttu-id="b2923-261">Souhrn využití aspekty</span><span class="sxs-lookup"><span data-stu-id="b2923-261">Summary of usage considerations</span></span>  
 <span data-ttu-id="b2923-262">Následující obecné a aplikační informace vám mohou pomoci rozhodnout, zda může být vyhodnocení nativních bitových kopií pro aplikaci přínosem:</span><span class="sxs-lookup"><span data-stu-id="b2923-262">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>  
  
-   <span data-ttu-id="b2923-263">Nativní bitové kopie se načítají rychleji než jazyk MSIL, protože odstraňují potřebu mnoha aktivit při spouštění, například kompilaci JIT a ověření bezpečnosti typů.</span><span class="sxs-lookup"><span data-stu-id="b2923-263">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>  
  
-   <span data-ttu-id="b2923-264">Nativní bitové kopie vyžadují menší počáteční pracovní sadu, protože není zapotřebí použít kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="b2923-264">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>  
  
-   <span data-ttu-id="b2923-265">Nativní bitové kopie umožňují sdílení kódu mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b2923-265">Native images enable code sharing between processes.</span></span>  
  
-   <span data-ttu-id="b2923-266">Nativní bitové kopie vyžadují více místa na disku než sestavení MSIL a jejich generování může trvat značně dlouho.</span><span class="sxs-lookup"><span data-stu-id="b2923-266">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>  
  
-   <span data-ttu-id="b2923-267">Nativní bitové kopie musí být udržovány.</span><span class="sxs-lookup"><span data-stu-id="b2923-267">Native images must be maintained.</span></span>  
  
    -   <span data-ttu-id="b2923-268">Je-li upraveno původní sestavení nebo jedna z jeho závislostí, je zapotřebí bitové kopie znovu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="b2923-268">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>  
  
    -   <span data-ttu-id="b2923-269">Jediné sestavení může vyžadovat několik nativních bitových kopií pro použití v různých aplikacích a scénářích.</span><span class="sxs-lookup"><span data-stu-id="b2923-269">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="b2923-270">Například informace o konfiguraci dvou aplikací může vyústit v různá rozhodnutí o vazbách stejného závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-270">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>  
  
    -   <span data-ttu-id="b2923-271">Nativní bitové kopie musí být generovány správcem; tj. z účtu systému Windows ve skupině Administrators.</span><span class="sxs-lookup"><span data-stu-id="b2923-271">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>  
  
 <span data-ttu-id="b2923-272">Spolu s těmito obecnými informacemi je zapotřebí při určování, zda mohou nativní bitové kopie poskytnout zvýšení výkonu, zvážit i povahu aplikace:</span><span class="sxs-lookup"><span data-stu-id="b2923-272">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>  
  
-   <span data-ttu-id="b2923-273">Je-li aplikace spouštěna v prostředí, které využívá mnoho sdílených komponent, nativní bitové kopie umožňují sdílení komponent mezi mnoha procesy.</span><span class="sxs-lookup"><span data-stu-id="b2923-273">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>  
  
-   <span data-ttu-id="b2923-274">Používá-li aplikace více domén aplikace, nativní bitové kopie umožňují sdílení znakových stránek mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="b2923-274">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2923-275">V rozhraních .NET Framework verze 1.0 a 1.1 nemohou být nativní bitové kopie sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-275">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="b2923-276">Verze 2.0 a novější již toto omezení nemají.</span><span class="sxs-lookup"><span data-stu-id="b2923-276">This is not the case in version 2.0 or later.</span></span>  
  
-   <span data-ttu-id="b2923-277">Bude-li aplikace spuštěna v rámci Terminálového serveru, nativní bitové kopie umožní sdílení znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="b2923-277">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>  
  
-   <span data-ttu-id="b2923-278">Rozsáhlé aplikace obecně těží z výhod kompilace do nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-278">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="b2923-279">Malým aplikacím nativní bitové kopie obvykle výhody nepřinášejí.</span><span class="sxs-lookup"><span data-stu-id="b2923-279">Small applications generally do not benefit.</span></span>  
  
-   <span data-ttu-id="b2923-280">Pro dlouho běžící aplikace vykazuje kompilace JIT za běhu mírně vyšší výkon než nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-280">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="b2923-281">(Pevné vazby mohou tento rozdíl ve výkonu do určité míry zmenšit.)</span><span class="sxs-lookup"><span data-stu-id="b2923-281">(Hard binding can mitigate this performance difference to some degree.)</span></span>  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="b2923-282">Důležitost základní adresy sestavení</span><span class="sxs-lookup"><span data-stu-id="b2923-282">Importance of assembly base addresses</span></span>  
 <span data-ttu-id="b2923-283">Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů.</span><span class="sxs-lookup"><span data-stu-id="b2923-283">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="b2923-284">Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="b2923-284">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>  
  
 <span data-ttu-id="b2923-285">Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-285">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="b2923-286">Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-286">Ngen.exe uses this base address for the native image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-287">Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="b2923-287">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="b2923-288">Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.</span><span class="sxs-lookup"><span data-stu-id="b2923-288">Base addresses must be calculated to allow for these larger sizes.</span></span>  
  
 <span data-ttu-id="b2923-289">Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-289">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a><span data-ttu-id="b2923-290">Pevné vazby</span><span class="sxs-lookup"><span data-stu-id="b2923-290">Hard binding</span></span>  
 <span data-ttu-id="b2923-291">Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-291">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="b2923-292">Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-292">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="b2923-293">To u velkých aplikací může výrazně prodloužit spouštění.</span><span class="sxs-lookup"><span data-stu-id="b2923-293">This can significantly increase startup time for a large application.</span></span>  
  
 <span data-ttu-id="b2923-294">Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu.</span><span class="sxs-lookup"><span data-stu-id="b2923-294">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="b2923-295">Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2923-295">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>  
  
 <span data-ttu-id="b2923-296"><xref:System.Runtime.CompilerServices.DependencyAttribute> a <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atributů umožňují poskytovat pevný vazby k Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-296">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-297">Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="b2923-297">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="b2923-298">Jejich použití nezaručuje pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="b2923-298">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="b2923-299">V budoucích verzích se může změnit význam těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="b2923-299">The meaning of these attributes may change in future releases.</span></span>  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="b2923-300">Určení vazby nápovědu pro závislosti</span><span class="sxs-lookup"><span data-stu-id="b2923-300">Specifying a binding hint for a dependency</span></span>  
 <span data-ttu-id="b2923-301">Použít <xref:System.Runtime.CompilerServices.DependencyAttribute> k sestavení udávajících pravděpodobnost, že zadaná závislost budou načteny.</span><span class="sxs-lookup"><span data-stu-id="b2923-301">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="b2923-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> Označuje, že je vhodné, pevné vazby <xref:System.Runtime.CompilerServices.LoadHint.Default> označuje, že má být použita výchozí hodnota pro závislost, a <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> označuje, že pevné vazba není vhodná.</span><span class="sxs-lookup"><span data-stu-id="b2923-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>  
  
 <span data-ttu-id="b2923-303">Následující kód zobrazuje atributy pro sestavení, které má dvě závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-303">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="b2923-304">První závislost (Assembly1) je vhodným kandidátem pro pevnou vazbu, druhá závislost (Assembly2) nikoliv.</span><span class="sxs-lookup"><span data-stu-id="b2923-304">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>  
  
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
  
 <span data-ttu-id="b2923-305">Název sestavení neobsahuje příponu názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="b2923-305">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="b2923-306">Lze použít zobrazené názvy.</span><span class="sxs-lookup"><span data-stu-id="b2923-306">Display names can be used.</span></span>  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="b2923-307">Určení výchozí vazby nápovědu pro sestavení</span><span class="sxs-lookup"><span data-stu-id="b2923-307">Specifying a default binding hint for an assembly</span></span>  
 <span data-ttu-id="b2923-308">Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="b2923-308">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="b2923-309">Použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> na takové sestavení k určení, že má být použita pevný vazby.</span><span class="sxs-lookup"><span data-stu-id="b2923-309">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-310">Neexistuje žádný důvod pro použití <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na sestavení .dll, které nepatří do této kategorie patří, protože jiné než použití atributu s hodnotou <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný účinek jako nejsou vůbec použití atributu.</span><span class="sxs-lookup"><span data-stu-id="b2923-310">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>  
  
 <span data-ttu-id="b2923-311">Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> pevný vazba je výchozí nastavení pro velmi malý počet sestavení v rozhraní .NET Framework, jako je například mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="b2923-311">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a><span data-ttu-id="b2923-312">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="b2923-312">Deferred processing</span></span>  
 <span data-ttu-id="b2923-313">Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="b2923-313">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="b2923-314">Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-314">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="b2923-315">`install` a `update` mají akce `/queue` možnost, která fronty operaci pro odložené provedení službou nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-315">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="b2923-316">Kromě toho má Ngen.exe `queue` a `executeQueuedItems` akce, které poskytuje určitou kontrolu nad službu.</span><span class="sxs-lookup"><span data-stu-id="b2923-316">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="b2923-317">Další informace najdete v tématu [nativní bitové kopie služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-317">For more information, see [Native Image Service][Native Image Service].</span></span>  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="b2923-318">Nativní bitové kopie a JIT – kompilace</span><span class="sxs-lookup"><span data-stu-id="b2923-318">Native images and JIT compilation</span></span>  
 <span data-ttu-id="b2923-319">Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-319">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="b2923-320">Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="b2923-320">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>  
  
 <span data-ttu-id="b2923-321">Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.</span><span class="sxs-lookup"><span data-stu-id="b2923-321">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a><span data-ttu-id="b2923-322">Neplatné obrázky</span><span class="sxs-lookup"><span data-stu-id="b2923-322">Invalid images</span></span>  
 <span data-ttu-id="b2923-323">Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače.</span><span class="sxs-lookup"><span data-stu-id="b2923-323">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="b2923-324">Mezi tato nastavení patří následující:</span><span class="sxs-lookup"><span data-stu-id="b2923-324">These settings include the following:</span></span>  
  
-   <span data-ttu-id="b2923-325">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2923-325">The version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="b2923-326">Verze operačního systému, pokud se změna týká ze systémů řady Windows 9 x řady systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="b2923-326">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
-   <span data-ttu-id="b2923-327">Přesná identita sestavení (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="b2923-327">The exact identity of the assembly (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="b2923-328">Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="b2923-328">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="b2923-329">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="b2923-329">Security factors.</span></span>  
  
 <span data-ttu-id="b2923-330">Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-330">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="b2923-331">Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače.</span><span class="sxs-lookup"><span data-stu-id="b2923-331">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="b2923-332">Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="b2923-332">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="b2923-333">Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:</span><span class="sxs-lookup"><span data-stu-id="b2923-333">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>  
  
-   <span data-ttu-id="b2923-334">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2923-334">The version of the .NET Framework.</span></span>  
  
     <span data-ttu-id="b2923-335">Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní.</span><span class="sxs-lookup"><span data-stu-id="b2923-335">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="b2923-336">Z tohoto důvodu všechny aktualizace rozhraní .NET Framework provést `Ngen Update` příkazu, ujistěte se, že se znova vygeneroval všechny nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-336">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="b2923-337">Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.</span><span class="sxs-lookup"><span data-stu-id="b2923-337">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>  
  
-   <span data-ttu-id="b2923-338">Verze operačního systému, pokud se změna týká ze systémů řady Windows 9 x řady systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="b2923-338">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
     <span data-ttu-id="b2923-339">Například, pokud verze operačního systému na počítač se změní ze systému Windows 98 do systému Windows XP, budou všechny nativní bitové kopie, které jsou uložené v mezipaměti nativních bitových kopií neplatné.</span><span class="sxs-lookup"><span data-stu-id="b2923-339">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="b2923-340">Pokud se operační systém se změní ze systému Windows 2000 na systém Windows XP, nejsou zrušena bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-340">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>  
  
-   <span data-ttu-id="b2923-341">Přesná identita sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-341">The exact identity of the assembly.</span></span>  
  
     <span data-ttu-id="b2923-342">Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="b2923-342">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>  
  
-   <span data-ttu-id="b2923-343">Přesná identita všech sestavení, na která sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="b2923-343">The exact identity of any assemblies the assembly references.</span></span>  
  
     <span data-ttu-id="b2923-344">Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="b2923-344">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="b2923-345">To zahrnuje jak běžné odkazy, tak pevně vázané závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-345">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="b2923-346">Vždy, když se použije aktualizace softwaru, by měla spustit instalační program `Ngen Update` zajistěte, aby všechny závislé nativní bitové kopie jsou obnovovaly.</span><span class="sxs-lookup"><span data-stu-id="b2923-346">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>  
  
-   <span data-ttu-id="b2923-347">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="b2923-347">Security factors.</span></span>  
  
     <span data-ttu-id="b2923-348">Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="b2923-348">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>  
  
     <span data-ttu-id="b2923-349">Podrobné informace o tom, jak modul common language runtime spravuje zabezpečení přístupu kódu a jak používat oprávnění najdete v tématu [zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="b2923-349">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="b2923-350">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="b2923-350">Troubleshooting</span></span>  
 <span data-ttu-id="b2923-351">V následujících tématech řešení potíží umožňují zobrazit které nativní bitové kopie se používají a které nelze použít v aplikaci, pro určení, kdy JIT kompilátoru spustí zkompilovat metodu a ukazuje, jak pro vyjádření výslovného nesouhlasu kompilaci nativních bitových kopií zadat metody.</span><span class="sxs-lookup"><span data-stu-id="b2923-351">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="b2923-352">vazba sestavení – prohlížeč protokolu</span><span class="sxs-lookup"><span data-stu-id="b2923-352">Assembly Binding Log Viewer</span></span>  
 <span data-ttu-id="b2923-353">Pokud chcete potvrdit, že nativní bitové kopie jsou používány aplikací, můžete použít [Fuslogvw.exe (sestavení vazby Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="b2923-353">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="b2923-354">Vyberte **nativní bitové kopie** v **kategorií protokolu** pole v okně Prohlížeč protokolu vazby.</span><span class="sxs-lookup"><span data-stu-id="b2923-354">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="b2923-355">Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="b2923-355">Fuslogvw.exe provides information about why a native image was rejected.</span></span>  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="b2923-356">JITCompilationStart spravované ladění pomocníka</span><span class="sxs-lookup"><span data-stu-id="b2923-356">The JITCompilationStart managed debugging assistant</span></span>  
 <span data-ttu-id="b2923-357">Můžete použít [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) pomocníka spravovaného ladění (MDA) k určení, kdy začne JIT kompilátoru zkompilovat funkce.</span><span class="sxs-lookup"><span data-stu-id="b2923-357">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="b2923-358">Zrušení generování nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="b2923-358">Opting out of native image generation</span></span>  
 <span data-ttu-id="b2923-359">V některých případech může mít NGen.exe generování potíže, které nativních bitových kopií pro konkrétní metody, nebo můžete můžou upřednostňovat, že metoda být JIT zkompilovat místo poté zkompilovány do nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-359">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="b2923-360">V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut zabránit NGen.exe generování nativních bitových kopií pro konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="b2923-360">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="b2923-361">Atribut se musí použít jednotlivě u jednotlivých metod, jejichž kód není chcete zahrnout do nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-361">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="b2923-362">NGen.exe rozpozná atribut a nevygeneruje žádný kód v nativních bitových kopií pro odpovídající metodu.</span><span class="sxs-lookup"><span data-stu-id="b2923-362">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>  
  
 <span data-ttu-id="b2923-363">Upozorňujeme však, který `BypassNGenAttribute` není definován jako typ v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2923-363">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="b2923-364">Aby bylo možné využívat atribut ve vašem kódu, je nutné nejprve definovat ho následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b2923-364">In order to consume the attribute in your code, you must first define it as follows:</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 <span data-ttu-id="b2923-365">Atribut lze následně použít na základě-method.</span><span class="sxs-lookup"><span data-stu-id="b2923-365">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="b2923-366">Následující příklad dá pokyn, generátor, to by nemělo generovat nativních bitových kopií pro `ExampleClass.ToJITCompile` metoda.</span><span class="sxs-lookup"><span data-stu-id="b2923-366">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a><span data-ttu-id="b2923-367">Příklady</span><span class="sxs-lookup"><span data-stu-id="b2923-367">Examples</span></span>  
 <span data-ttu-id="b2923-368">Následující příkaz vytvoří nativních bitových kopií pro `ClientApp.exe`, umístěný v aktuálním adresáři a nainstaluje bitovou kopii do mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-368">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="b2923-369">Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije.</span><span class="sxs-lookup"><span data-stu-id="b2923-369">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="b2923-370">Kromě toho jsou generována nativní bitové kopie, pro žádné DLL, soubory, které `ClientApp.exe` odkazy.</span><span class="sxs-lookup"><span data-stu-id="b2923-370">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>  
  
```  
ngen install ClientApp.exe  
```  
  
 <span data-ttu-id="b2923-371">Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen.</span><span class="sxs-lookup"><span data-stu-id="b2923-371">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="b2923-372">Kořen může být aplikace nebo sdílená komponenta.</span><span class="sxs-lookup"><span data-stu-id="b2923-372">A root can be an application or a shared component.</span></span>  
  
 <span data-ttu-id="b2923-373">Následující příkaz vytvoří nativních bitových kopií pro `MyAssembly.exe` se zadanou cestou.</span><span class="sxs-lookup"><span data-stu-id="b2923-373">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 <span data-ttu-id="b2923-374">Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b2923-374">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="b2923-375">Ve výchozím adresáři, který obsahuje `ClientApp.exe` slouží jako základní adresář aplikace a začne zjišťování všechna sestavení v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="b2923-375">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="b2923-376">Toto chování můžete přepsat pomocí `/AppBase` možnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-376">You can override this behavior by using the `/AppBase` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-377">Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b2923-377">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>  
  
 <span data-ttu-id="b2923-378">Sestavení mohou mít závislosti bez odkazu, například pokud načte soubor s příponou DLL pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b2923-378">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b2923-379">Nativních bitových kopií pro soubor .dll můžete vytvořit pomocí konfigurační informace pro sestavení aplikace pomocí `/ExeConfig` možnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-379">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="b2923-380">Následující příkaz vytvoří nativních bitových kopií pro `MyLib.dll,` pomocí konfiguračních informací z `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="b2923-380">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="b2923-381">Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="b2923-381">Assemblies installed in this way are not removed when the application is removed.</span></span>  
  
 <span data-ttu-id="b2923-382">Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="b2923-382">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="b2923-383">Příkaz odinstaluje `MyLib.dll` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="b2923-383">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="b2923-384">Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2923-384">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="b2923-385">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b2923-385">For example:</span></span>  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 <span data-ttu-id="b2923-386">NGen.exe vytváří samostatnou sadu bitových kopií pro každý scénář, který instalujete.</span><span class="sxs-lookup"><span data-stu-id="b2923-386">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="b2923-387">Například následující příkazy nainstalují kompletní sadu nativních bitových kopií pro normální provoz, jinou kompletní sadu pro ladění a třetí pro profilování:</span><span class="sxs-lookup"><span data-stu-id="b2923-387">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="b2923-388">Zobrazení mezipaměti nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="b2923-388">Displaying the Native Image Cache</span></span>  
 <span data-ttu-id="b2923-389">Jakmile jsou nativní bitové kopie nainstalovány v mezipaměti, lze je zobrazit pomocí nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-389">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="b2923-390">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-390">The following command displays all native images in the native image cache.</span></span>  
  
```  
ngen display  
```  
  
 <span data-ttu-id="b2923-391">`display` Akce jsou uvedeny všechny kořenové sestavení nejprve následuje seznam nativní bitové kopie na počítače.</span><span class="sxs-lookup"><span data-stu-id="b2923-391">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>  
  
 <span data-ttu-id="b2923-392">Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="b2923-392">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="b2923-393">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií, které odpovídají částečný název `MyAssembly`, jejich závislosti a všechny kořenové adresáře, které jsou závislé na `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="b2923-393">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>  
  
```  
ngen display MyAssembly  
```  
  
 <span data-ttu-id="b2923-394">Zároveň budete vědět, jaké kořeny závisí na sestavení sdílená součást je užitečný při měření dopad `update` akce po upgradu sdílená součást.</span><span class="sxs-lookup"><span data-stu-id="b2923-394">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>  
  
 <span data-ttu-id="b2923-395">Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:</span><span class="sxs-lookup"><span data-stu-id="b2923-395">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 <span data-ttu-id="b2923-396">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativní bitové kopie s názvem `MyAssembly` a verzi 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="b2923-396">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a><span data-ttu-id="b2923-397">Aktualizace bitových kopií</span><span class="sxs-lookup"><span data-stu-id="b2923-397">Updating Images</span></span>  
 <span data-ttu-id="b2923-398">Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty.</span><span class="sxs-lookup"><span data-stu-id="b2923-398">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="b2923-399">Chcete-li aktualizovat všechny nativní bitové kopie, které změnily, nebo se změnily jehož závislosti, použijte `update` akce bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="b2923-399">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>  
  
```  
ngen update  
```  
  
 <span data-ttu-id="b2923-400">Aktualizace všech bitových kopií může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="b2923-400">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="b2923-401">Aktualizace pro spuštění pomocí služby nativních bitových kopií můžete fronty pomocí `/queue` možnost.</span><span class="sxs-lookup"><span data-stu-id="b2923-401">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="b2923-402">Další informace o `/queue` možnost a instalace priority, najdete v části [nativní bitové kopie služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-402">For more information on the `/queue` option and installation priorities, see [Native Image Service][Native Image Service].</span></span>  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a><span data-ttu-id="b2923-403">Odinstalování bitových kopií</span><span class="sxs-lookup"><span data-stu-id="b2923-403">Uninstalling Images</span></span>  
 <span data-ttu-id="b2923-404">Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="b2923-404">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="b2923-405">Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.</span><span class="sxs-lookup"><span data-stu-id="b2923-405">In addition, a shared component is not removed if it has been installed as a root.</span></span>  
  
 <span data-ttu-id="b2923-406">Příkaz odinstaluje všechny scénáře pro kořenovou `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="b2923-406">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp  
```  
  
 <span data-ttu-id="b2923-407">`uninstall` Akci lze použít k odebrání konkrétních scénářů.</span><span class="sxs-lookup"><span data-stu-id="b2923-407">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="b2923-408">Příkaz odinstaluje všechny scénáře ladění pro `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="b2923-408">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  <span data-ttu-id="b2923-409">Odinstalace `/debug` scénáře neodinstaluje scénáře, který zahrnuje obě `/profile` a `/debug.`</span><span class="sxs-lookup"><span data-stu-id="b2923-409">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>  
  
 <span data-ttu-id="b2923-410">Příkaz odinstaluje všechny scénáře pro určitou verzi `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="b2923-410">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 <span data-ttu-id="b2923-411">Následující příkazy odinstalovat všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo právě tento scénář ladění pro toto sestavení:</span><span class="sxs-lookup"><span data-stu-id="b2923-411">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 <span data-ttu-id="b2923-412">Stejně jako u `install` akce, poskytuje rozšíření vyžaduje buď provádění Ngen.exe z adresáře, který obsahuje sestavení nebo zadat úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="b2923-412">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>  
  
 <span data-ttu-id="b2923-413">Příklady týkající se služby nativních bitových kopií naleznete v tématu [nativní bitové kopie služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-413">For examples relating to the native image service, see [Native Image Service][Native Image Service].</span></span>  
  
## <a name="native-image-task"></a><span data-ttu-id="b2923-414">Úloha pro nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="b2923-414">Native Image Task</span></span>  
 <span data-ttu-id="b2923-415">Úloha nativních bitových kopií je úloh systému Windows, která vytváří a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-415">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="b2923-416">Úloha nativních bitových kopií generuje a získá nativní bitové kopie automaticky pro podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="b2923-416">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="b2923-417">(Viz [vytváření nativní bitové kopie](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Umožňuje také instalační programy používat [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) k vytváření a aktualizaci nativní bitové kopie odložené najednou.</span><span class="sxs-lookup"><span data-stu-id="b2923-417">(See [Creating Native Images](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>  
  
 <span data-ttu-id="b2923-418">Jakmile pro každý procesor architektura podporovaný na počítači, aby kompilace pro aplikace, že cíl každou architekturu registraci nativních bitových kopií úlohy:</span><span class="sxs-lookup"><span data-stu-id="b2923-418">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>  
  
|<span data-ttu-id="b2923-419">Název úlohy</span><span class="sxs-lookup"><span data-stu-id="b2923-419">Task name</span></span>|<span data-ttu-id="b2923-420">32bitový počítač</span><span class="sxs-lookup"><span data-stu-id="b2923-420">32-bit computer</span></span>|<span data-ttu-id="b2923-421">64bitový počítač</span><span class="sxs-lookup"><span data-stu-id="b2923-421">64-bit computer</span></span>|  
|---------------|----------------------|----------------------|  
|<span data-ttu-id="b2923-422">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="b2923-422">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="b2923-423">Ano</span><span class="sxs-lookup"><span data-stu-id="b2923-423">Yes</span></span>|<span data-ttu-id="b2923-424">Ano</span><span class="sxs-lookup"><span data-stu-id="b2923-424">Yes</span></span>|  
|<span data-ttu-id="b2923-425">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="b2923-425">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="b2923-426">Ne</span><span class="sxs-lookup"><span data-stu-id="b2923-426">No</span></span>|<span data-ttu-id="b2923-427">Ano</span><span class="sxs-lookup"><span data-stu-id="b2923-427">Yes</span></span>|  
  
 <span data-ttu-id="b2923-428">Tato úloha nativních bitových kopií je je k dispozici v rozhraní .NET Framework 4.5 a novějších verzích, při spuštění v systému Windows 8 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b2923-428">The native image task is is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="b2923-429">V dřívějších verzích systému Windows, používá rozhraní .NET Framework [nativní bitové kopie služby][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="b2923-429">On earlier versions of Windows, the .NET Framework uses the [Native Image Service][Native Image Service].</span></span>  
  
### <a name="task-lifetime"></a><span data-ttu-id="b2923-430">Doba platnosti úloh</span><span class="sxs-lookup"><span data-stu-id="b2923-430">Task Lifetime</span></span>  
 <span data-ttu-id="b2923-431">Obecně platí plánovače úloh systému Windows spustí úlohu nativních bitových kopií každou noc, když je počítač v nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-431">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="b2923-432">Úloha zkontroluje všechny odložené práci, kterou je zařazena ve frontě instalační programy aplikací, všechny žádosti o aktualizaci odložené nativních bitových kopií a vytvoření všechny automatické bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-432">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="b2923-433">Úloha dokončení zbývajících pracovní položky a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="b2923-433">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="b2923-434">Pokud se počítač zastaví nečinnosti, když je spuštěn úkol, zastaví úlohu.</span><span class="sxs-lookup"><span data-stu-id="b2923-434">If the computer stops being idle while the task is running, the task stops.</span></span>  
  
 <span data-ttu-id="b2923-435">Můžete také spustit úlohu nativních bitových kopií ručně prostřednictvím uživatelského rozhraní plánovače úloh nebo ruční volání NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-435">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="b2923-436">Pokud úloha se spustí pomocí jedné z těchto metod, bude spuštěn, když se počítač již není nečinný.</span><span class="sxs-lookup"><span data-stu-id="b2923-436">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="b2923-437">Bitové kopie ručně vytvořené pomocí NGen.exe budou mít vyšší prioritu, chcete-li povolit předvídatelné chování pro instalační programy aplikací.</span><span class="sxs-lookup"><span data-stu-id="b2923-437">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>  
  
## <a name="native-image-service"></a><span data-ttu-id="b2923-438">Nativní bitová kopie služby</span><span class="sxs-lookup"><span data-stu-id="b2923-438">Native Image Service</span></span>  
 <span data-ttu-id="b2923-439">Služba nativních bitových kopií je služba systému Windows, která vytváří a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="b2923-439">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="b2923-440">Službu nativních bitových kopií umožňuje vývojáři odložení instalace a aktualizace nativních bitových kopií do doby, kdy počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="b2923-440">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>  
  
 <span data-ttu-id="b2923-441">Za normálních okolností službu nativních bitových kopií inicializuje instalačního programu (Instalační program) pro aplikace nebo aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b2923-441">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="b2923-442">Pro akce s prioritou 3 služba provede během doby nečinnosti v počítači.</span><span class="sxs-lookup"><span data-stu-id="b2923-442">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="b2923-443">Služba uloží stav a se může nadále prostřednictvím více restartování v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="b2923-443">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="b2923-444">Více kompilace bitové kopie můžete zařadit do fronty.</span><span class="sxs-lookup"><span data-stu-id="b2923-444">Multiple image compilations can be queued.</span></span>  
  
 <span data-ttu-id="b2923-445">Službu taky komunikuje s ruční Ngen.exe příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2923-445">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="b2923-446">Ruční příkazy mají přednost před aktivita na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b2923-446">Manual commands take precedence over background activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2923-447">V systému Windows Vista je název zobrazený pro službu nativních bitových kopií "Microsoft.NET Framework NGEN v2.0.50727_X86" nebo "Microsoft.NET Framework NGEN v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="b2923-447">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="b2923-448">Na všechny starší verze systému Microsoft Windows je název "Služba optimalizace modulu Runtime .NET v2.0.50727_X86" nebo "Služba optimalizace modulu Runtime .NET v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="b2923-448">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>  
  
### <a name="launching-deferred-operations"></a><span data-ttu-id="b2923-449">Spuštění operace odložené</span><span class="sxs-lookup"><span data-stu-id="b2923-449">Launching Deferred Operations</span></span>  
 <span data-ttu-id="b2923-450">Před zahájením instalace nebo upgradu, se doporučuje pozastavení služby.</span><span class="sxs-lookup"><span data-stu-id="b2923-450">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="b2923-451">Tím se zajistí, že služba nespustí při kopírování souborů nebo uvedení sestavení v globální mezipaměti sestavení Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="b2923-451">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="b2923-452">Následující příkazový řádek Ngen.exe pozastaví službu:</span><span class="sxs-lookup"><span data-stu-id="b2923-452">The following Ngen.exe command line pauses the service:</span></span>  
  
```  
ngen queue pause  
```  
  
 <span data-ttu-id="b2923-453">Pokud všechny odložené operace byla zařazena do fronty, následující příkaz umožňuje službu, kterou chcete obnovit:</span><span class="sxs-lookup"><span data-stu-id="b2923-453">When all deferred operations have been queued, the following command allows the service to resume:</span></span>  
  
```  
ngen queue continue  
```  
  
 <span data-ttu-id="b2923-454">Chcete-li při instalaci nové aplikace, nebo při aktualizaci sdílené součásti, odložení generování nativních bitových kopií, použijte `/queue` možnost s `install` nebo `update` akce.</span><span class="sxs-lookup"><span data-stu-id="b2923-454">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="b2923-455">Na příkazovém řádku následující Ngen.exe instalace nativních bitových kopií pro sdílené součást a proveďte aktualizaci všechny kořenové adresáře, které byly:</span><span class="sxs-lookup"><span data-stu-id="b2923-455">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 <span data-ttu-id="b2923-456">`update` Akce regeneruje všechny nativní bitové kopie, které se zrušila platnost, nikoli pouze ty, které používají `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="b2923-456">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>  
  
 <span data-ttu-id="b2923-457">Pokud vaše aplikace obsahuje mnoho kořeny, můžete řídit prioritu odložené akce.</span><span class="sxs-lookup"><span data-stu-id="b2923-457">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="b2923-458">Následující příkazy ve frontě pro instalaci tři kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="b2923-458">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="b2923-459">`Assembly1` je nainstalována jako první, bez čekání na čas nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-459">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="b2923-460">`Assembly2` je také nainstalován bez čekání na dobu nečinnosti, ale po dokončení všech akcí priority 1.</span><span class="sxs-lookup"><span data-stu-id="b2923-460">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="b2923-461">`Assembly3` nainstaluje se při službu zjistí, že je počítač v nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="b2923-461">`Assembly3` is installed when the service detects that the computer is idle.</span></span>  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 <span data-ttu-id="b2923-462">Můžete vynutit akce ve frontě proběhnout synchronně pomocí `executeQueuedItems` akce.</span><span class="sxs-lookup"><span data-stu-id="b2923-462">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="b2923-463">Pokud zadáte volitelné prioritu, tato akce ovlivní pouze zařazených do fronty akce, které mají stejné nebo nižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="b2923-463">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="b2923-464">Výchozí priorita je 3, takže příkaz Ngen.exe okamžitě zpracovává všechny akce ve frontě a nevrací až skončí:</span><span class="sxs-lookup"><span data-stu-id="b2923-464">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>  
  
```  
ngen executeQueuedItems  
```  
  
 <span data-ttu-id="b2923-465">Synchronní příkazy jsou provedený Ngen.exe a nepoužívejte službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-465">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="b2923-466">Můžete provést akce s použitím Ngen.exe během spuštěné služby nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="b2923-466">You can execute actions using Ngen.exe while the native image service is running.</span></span>  
  
### <a name="service-shutdown"></a><span data-ttu-id="b2923-467">Vypnutí služby</span><span class="sxs-lookup"><span data-stu-id="b2923-467">Service Shutdown</span></span>  
 <span data-ttu-id="b2923-468">Po se iniciovat provádění příkaz Ngen.exe, která zahrnuje `/queue` možnost, služba bude spuštěna na pozadí dokud všechny akce byly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="b2923-468">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="b2923-469">Služba uloží stav, aby mohl pokračovat prostřednictvím více restartování v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="b2923-469">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="b2923-470">Když službu zjistí, že neexistují žádné další akce ve frontě, obnoví stav tak, že ji nebude restartování při příštím spuštění počítače a pak se ukončí sám.</span><span class="sxs-lookup"><span data-stu-id="b2923-470">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>  
  
### <a name="service-interaction-with-clients"></a><span data-ttu-id="b2923-471">Služba interakci s klienty</span><span class="sxs-lookup"><span data-stu-id="b2923-471">Service Interaction with Clients</span></span>  
 <span data-ttu-id="b2923-472">V rozhraní .NET Framework verze 2.0 je jediná interakce s nativních bitových kopií služby pomocí nástroje příkazového řádku Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b2923-472">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="b2923-473">Pomocí nástroje příkazového řádku ve skriptech instalace do fronty akce pro službu nativních bitových kopií a komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="b2923-473">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2923-474">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2923-474">See Also</span></span>  
 [<span data-ttu-id="b2923-475">Nástroje</span><span class="sxs-lookup"><span data-stu-id="b2923-475">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="b2923-476">Proces spravovaného spuštění</span><span class="sxs-lookup"><span data-stu-id="b2923-476">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)  
 [<span data-ttu-id="b2923-477">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b2923-477">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="b2923-478">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="b2923-478">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

[Native Image Service]: #native-image-service
