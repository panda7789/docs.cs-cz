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
ms.openlocfilehash: 5079f0243faefaab6ada23cc98f5214a616c1d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044367"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="ad91c-102">Ngen.exe (generátor nativních obrázků)</span><span class="sxs-lookup"><span data-stu-id="ad91c-102">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="ad91c-103">Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="ad91c-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="ad91c-104">Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="ad91c-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="ad91c-105">Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="ad91c-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-106">Ngen. exe zkompiluje nativní bitové kopie pro sestavení, která cílí pouze na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad91c-106">Ngen.exe compiles native images for assemblies that target the .NET Framework only.</span></span> <span data-ttu-id="ad91c-107">Ekvivalentní generátor nativních bitových kopií pro .NET Core je [CrossGen](https://github.com/dotnet/coreclr/blob/master/Documentation/building/crossgen.md).</span><span class="sxs-lookup"><span data-stu-id="ad91c-107">The equivalent native image generator for .NET Core is [CrossGen](https://github.com/dotnet/coreclr/blob/master/Documentation/building/crossgen.md).</span></span> 

<span data-ttu-id="ad91c-108">Změny nástroje Ngen. exe v .NET Framework 4:</span><span class="sxs-lookup"><span data-stu-id="ad91c-108">Changes to Ngen.exe in the .NET Framework 4:</span></span>

- <span data-ttu-id="ad91c-109">Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.</span><span class="sxs-lookup"><span data-stu-id="ad91c-109">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="ad91c-110">Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="ad91c-110">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="ad91c-111">Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:</span><span class="sxs-lookup"><span data-stu-id="ad91c-111">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="ad91c-112">Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-112">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="ad91c-113">Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="ad91c-113">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="ad91c-114">Nová akce `update`způsobí, že znovu vytvoří image, jejichž platnost byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="ad91c-114">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="ad91c-115">Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-115">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="ad91c-116">Některé příčiny zneplatnění bitové kopie byly odstraněny.</span><span class="sxs-lookup"><span data-stu-id="ad91c-116">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="ad91c-117">V systému Windows 8, viz [úloha nativní bitové kopie](#native-image-task).</span><span class="sxs-lookup"><span data-stu-id="ad91c-117">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="ad91c-118">Další informace o použití nástroje Ngen. exe a služby nativních bitových kopií naleznete v tématu [nativní Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-118">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-119">Syntaxe Ngen. exe pro verze 1,0 a 1,1 .NET Framework se dá najít v [syntaxi starší verze generátoru nativních imagí (Ngen. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ad91c-119">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="ad91c-120">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad91c-120">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ad91c-121">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ad91c-121">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ad91c-122">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ad91c-122">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="ad91c-123">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="ad91c-123">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="ad91c-124">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad91c-124">Syntax</span></span>

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="ad91c-125">Akce</span><span class="sxs-lookup"><span data-stu-id="ad91c-125">Actions</span></span>

<span data-ttu-id="ad91c-126">V následující tabulce je uvedena syntaxe každého z `action`nich.</span><span class="sxs-lookup"><span data-stu-id="ad91c-126">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="ad91c-127">Popisy `action`jednotlivých částí sady najdete v tabulkách [argumenty](#ArgumentTable), [úrovně priority](#PriorityTable), [scénáře](#ScenarioTable)a [Konfigurace](#ConfigTable) .</span><span class="sxs-lookup"><span data-stu-id="ad91c-127">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="ad91c-128">V tabulce [Options](#OptionTable) jsou popsány `options` přepínače Help a.</span><span class="sxs-lookup"><span data-stu-id="ad91c-128">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="ad91c-129">Akce</span><span class="sxs-lookup"><span data-stu-id="ad91c-129">Action</span></span>|<span data-ttu-id="ad91c-130">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-130">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="ad91c-131">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="ad91c-131">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="ad91c-132">Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-132">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="ad91c-133">Je `/queue` -li parametr zadán, je akce zařazena do fronty pro službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-133">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="ad91c-134">Výchozí hodnota priority je 3.</span><span class="sxs-lookup"><span data-stu-id="ad91c-134">The default priority is 3.</span></span> <span data-ttu-id="ad91c-135">Podívejte se na tabulku [úrovně priority](#PriorityTable) .</span><span class="sxs-lookup"><span data-stu-id="ad91c-135">See the [Priority Levels](#PriorityTable) table.</span></span>|
|<span data-ttu-id="ad91c-136">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="ad91c-136">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="ad91c-137">Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-137">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="ad91c-138">Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-138">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="ad91c-139">**Poznámka:**  Počínaje .NET Framework 4 není akce `uninstall` \* nadále podporována.</span><span class="sxs-lookup"><span data-stu-id="ad91c-139">**Note:**  Starting with the .NET Framework 4, the action `uninstall` \* is no longer supported.</span></span>|
|<span data-ttu-id="ad91c-140">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="ad91c-140">`update` [`/queue`]</span></span>|<span data-ttu-id="ad91c-141">Aktualizuje nativní bitové kopie, které se staly neplatnými.</span><span class="sxs-lookup"><span data-stu-id="ad91c-141">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="ad91c-142">Pokud `/queue` je zadaný, aktualizace se zařadí do fronty pro nativní Image Service.</span><span class="sxs-lookup"><span data-stu-id="ad91c-142">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="ad91c-143">Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="ad91c-143">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|<span data-ttu-id="ad91c-144">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="ad91c-144">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="ad91c-145">Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-145">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="ad91c-146">Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-146">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|<span data-ttu-id="ad91c-147">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="ad91c-147">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="ad91c-148">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ad91c-148">-or-</span></span><br /><br /> <span data-ttu-id="ad91c-149">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="ad91c-149">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="ad91c-150">Spustí úlohy kompilace ve frontě.</span><span class="sxs-lookup"><span data-stu-id="ad91c-150">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="ad91c-151">Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou.</span><span class="sxs-lookup"><span data-stu-id="ad91c-151">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="ad91c-152">Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-152">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|<span data-ttu-id="ad91c-153">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="ad91c-153">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="ad91c-154">Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.</span><span class="sxs-lookup"><span data-stu-id="ad91c-154">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="ad91c-155">Arguments</span><span class="sxs-lookup"><span data-stu-id="ad91c-155">Arguments</span></span>

|<span data-ttu-id="ad91c-156">Argument</span><span class="sxs-lookup"><span data-stu-id="ad91c-156">Argument</span></span>|<span data-ttu-id="ad91c-157">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-157">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="ad91c-158">Plný zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-158">The full display name of the assembly.</span></span> <span data-ttu-id="ad91c-159">Například, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="ad91c-159">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="ad91c-160">**Poznámka:**  Pro akce `myAssembly` a`uninstall`můžete uvést částečný název sestavení, například. `display`</span><span class="sxs-lookup"><span data-stu-id="ad91c-160">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="ad91c-161">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-161">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="ad91c-162">Explicitní cesta k sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-162">The explicit path of the assembly.</span></span> <span data-ttu-id="ad91c-163">Lze zadat úplnou nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-163">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="ad91c-164">Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ad91c-164">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="ad91c-165">V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-165">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="ad91c-166">Úrovně priority</span><span class="sxs-lookup"><span data-stu-id="ad91c-166">Priority Levels</span></span>

|<span data-ttu-id="ad91c-167">Priority</span><span class="sxs-lookup"><span data-stu-id="ad91c-167">Priority</span></span>|<span data-ttu-id="ad91c-168">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-168">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="ad91c-169">Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.</span><span class="sxs-lookup"><span data-stu-id="ad91c-169">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="ad91c-170">Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).</span><span class="sxs-lookup"><span data-stu-id="ad91c-170">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="ad91c-171">Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="ad91c-171">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="ad91c-172">Viz [nativní Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-172">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="ad91c-173">Scénáře</span><span class="sxs-lookup"><span data-stu-id="ad91c-173">Scenarios</span></span>

|<span data-ttu-id="ad91c-174">Scénář</span><span class="sxs-lookup"><span data-stu-id="ad91c-174">Scenario</span></span>|<span data-ttu-id="ad91c-175">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-175">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="ad91c-176">Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-176">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="ad91c-177">Vygeneruje nativní bitové kopie, které lze použít v profileru.</span><span class="sxs-lookup"><span data-stu-id="ad91c-177">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="ad91c-178">Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.</span><span class="sxs-lookup"><span data-stu-id="ad91c-178">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="ad91c-179">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ad91c-179">Config</span></span>

|<span data-ttu-id="ad91c-180">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="ad91c-180">Configuration</span></span>|<span data-ttu-id="ad91c-181">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-181">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="ad91c-182">`/ExeConfig:``exePath`</span><span class="sxs-lookup"><span data-stu-id="ad91c-182">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="ad91c-183">Použije konfiguraci zadaného spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-183">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="ad91c-184">Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč.</span><span class="sxs-lookup"><span data-stu-id="ad91c-184">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="ad91c-185">Při načtení sdílené komponenty za běhu pomocí <xref:System.Reflection.Assembly.Load%2A> metody určuje konfigurační soubor aplikace závislosti, které jsou načteny pro sdílenou součást, například verzi načtené závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-185">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="ad91c-186">`/ExeConfig` Přepínač poskytuje pokyny Ngen. exe, na kterých by se měly načíst závislosti za běhu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-186">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|<span data-ttu-id="ad91c-187">`/AppBase:``directoryPath`</span><span class="sxs-lookup"><span data-stu-id="ad91c-187">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="ad91c-188">Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.</span><span class="sxs-lookup"><span data-stu-id="ad91c-188">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="ad91c-189">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ad91c-189">Options</span></span>

|<span data-ttu-id="ad91c-190">Možnost</span><span class="sxs-lookup"><span data-stu-id="ad91c-190">Option</span></span>|<span data-ttu-id="ad91c-191">Popis</span><span class="sxs-lookup"><span data-stu-id="ad91c-191">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="ad91c-192">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ad91c-192">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="ad91c-193">Potlačí zobrazování zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-193">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="ad91c-194">Zobrazí podrobné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="ad91c-194">Display detailed information for debugging.</span></span> <span data-ttu-id="ad91c-195">**Poznámka:**  V důsledku omezení operačního systému Tato možnost nezobrazuje ve Windows 98 a Windows Millennium Edition tolik dalších informací.</span><span class="sxs-lookup"><span data-stu-id="ad91c-195">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|
|<span data-ttu-id="ad91c-196">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="ad91c-196">`/help`, `/?`</span></span>|<span data-ttu-id="ad91c-197">Zobrazí syntaxi příkazu a možnosti aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="ad91c-197">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad91c-198">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad91c-198">Remarks</span></span>

<span data-ttu-id="ad91c-199">Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="ad91c-199">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="ad91c-200">Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="ad91c-200">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="ad91c-201">Počínaje .NET Framework 4, Ngen. exe zkompiluje sestavení s úplným vztahem důvěryhodnosti a zásady zabezpečení přístupu kódu (CAS) se už nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-201">Starting with the .NET Framework 4, Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="ad91c-202">Počínaje .NET Framework 4 již nelze načíst nativní bitové kopie, které jsou generovány pomocí nástroje Ngen. exe, do aplikací, které běží v částečném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-202">Starting with the .NET Framework 4, the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="ad91c-203">Namísto toho je vyvolán kompilátor za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="ad91c-203">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="ad91c-204">Ngen. exe generuje nativní bitové kopie pro sestavení určené `assemblyname` argumentem `install` pro akci a všechny její závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-204">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="ad91c-205">Závislosti se stanoví z odkazů v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-205">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="ad91c-206">Jediným scénářem, kdy je nutné nainstalovat závislost samostatně, je, když ji aplikace načte pomocí reflexe, například voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ad91c-206">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad91c-207">Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu s nativními bitovými kopiemi.</span><span class="sxs-lookup"><span data-stu-id="ad91c-207">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="ad91c-208">Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="ad91c-208">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="ad91c-209">Nástroj Ngen.exe udržuje počet odkazů na závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-209">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="ad91c-210">Předpokládejme například, že `MyAssembly.exe` a `YourAssembly.exe` jsou nainstalovány v mezipaměti nativní bitové kopie a oba mají odkazy na `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="ad91c-210">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="ad91c-211">Pokud `MyAssembly.exe` je odinstalován, `OurDependency.dll` nedojde k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="ad91c-211">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="ad91c-212">Odstraní se jenom v případě `YourAssembly.exe` , že se taky odinstaluje.</span><span class="sxs-lookup"><span data-stu-id="ad91c-212">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="ad91c-213">Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="ad91c-213">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="ad91c-214">Viz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad91c-214">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ad91c-215">Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-215">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="ad91c-216">To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-216">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="ad91c-217">Určení neutrality domény:</span><span class="sxs-lookup"><span data-stu-id="ad91c-217">To specify domain neutrality:</span></span>

- <span data-ttu-id="ad91c-218"><xref:System.LoaderOptimizationAttribute> Použijte atribut pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ad91c-218">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="ad91c-219"><xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> Nastavte vlastnost při vytváření informací o instalaci pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-219">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="ad91c-220">Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-220">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="ad91c-221">Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.</span><span class="sxs-lookup"><span data-stu-id="ad91c-221">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-222">Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.</span><span class="sxs-lookup"><span data-stu-id="ad91c-222">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="ad91c-223">V tomto oddílu Poznámky:</span><span class="sxs-lookup"><span data-stu-id="ad91c-223">In this Remarks section:</span></span>

- [<span data-ttu-id="ad91c-224">Generování imagí pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="ad91c-224">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="ad91c-225">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="ad91c-225">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="ad91c-226">Vylepšené využití paměti</span><span class="sxs-lookup"><span data-stu-id="ad91c-226">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="ad91c-227">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ad91c-227">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="ad91c-228">Souhrn důležitých informací o použití</span><span class="sxs-lookup"><span data-stu-id="ad91c-228">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="ad91c-229">Důležitost základních adres sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-229">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="ad91c-230">Pevná vazba</span><span class="sxs-lookup"><span data-stu-id="ad91c-230">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="ad91c-231">Zadání pomocného parametru vazby pro závislost</span><span class="sxs-lookup"><span data-stu-id="ad91c-231">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="ad91c-232">Určení výchozího parametru vazby pro sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-232">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="ad91c-233">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="ad91c-233">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="ad91c-234">Nativní bitové kopie a kompilace JIT</span><span class="sxs-lookup"><span data-stu-id="ad91c-234">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="ad91c-235">Neplatné obrázky</span><span class="sxs-lookup"><span data-stu-id="ad91c-235">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="ad91c-236">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="ad91c-236">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="ad91c-237">Prohlížeč protokolu vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-237">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="ad91c-238">Pomocníka spravovaného ladění jitCompilationStart –</span><span class="sxs-lookup"><span data-stu-id="ad91c-238">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="ad91c-239">Vypnutí generování nativních imagí</span><span class="sxs-lookup"><span data-stu-id="ad91c-239">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="ad91c-240">Generování imagí pro různé scénáře</span><span class="sxs-lookup"><span data-stu-id="ad91c-240">Generating images for     different scenarios</span></span>

<span data-ttu-id="ad91c-241">Po vygenerování nativní bitové kopie pro sestavení se modul runtime automaticky pokusí vyhledat a použít tuto nativní bitovou kopii při každém spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-241">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="ad91c-242">V závislosti na scénáři lze generovat více bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-242">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="ad91c-243">Například pokud spustíte sestavení ve scénáři ladění nebo profilace, modul runtime vyhledá nativní bitovou kopii, která byla vygenerována s `/Debug` možnostmi nebo. `/Profile`</span><span class="sxs-lookup"><span data-stu-id="ad91c-243">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="ad91c-244">Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ad91c-244">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="ad91c-245">Jediným způsobem, jak ladit nativní bitové kopie, je vytvořit nativní bitovou kopii `/Debug` s možností.</span><span class="sxs-lookup"><span data-stu-id="ad91c-245">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="ad91c-246">Tato `uninstall` akce také rozpoznává scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybrané scénáře.</span><span class="sxs-lookup"><span data-stu-id="ad91c-246">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="ad91c-247">Určení, kdy použít nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="ad91c-247">Determining when to Use native images</span></span>

<span data-ttu-id="ad91c-248">Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.</span><span class="sxs-lookup"><span data-stu-id="ad91c-248">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-249">Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ad91c-249">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="ad91c-250">Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-250">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="ad91c-251">Vylepšené využití paměti</span><span class="sxs-lookup"><span data-stu-id="ad91c-251">Improved memory use</span></span>

<span data-ttu-id="ad91c-252">Nativní bitové kopie mohou významně zlepšit využití paměti, je-li kód sdílen mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ad91c-252">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="ad91c-253">Nativní bitové kopie jsou soubory Windows PE, tudíž jedna kopie souboru .dll může být sdílena několika procesy. Naproti tomu nativní kód vytvořený kompilátorem JIT je uložen v soukromé paměti a nelze jej sdílet.</span><span class="sxs-lookup"><span data-stu-id="ad91c-253">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="ad91c-254">Aplikace spuštěné v rámci terminálových služeb také využívají výhod sdílených znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="ad91c-254">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="ad91c-255">Kromě toho skutečnost, že není načítán kompilátor JIT, ušetří pevně dané množství paměti pro každou instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-255">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="ad91c-256">Rychlejší spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ad91c-256">Faster application startup</span></span>

<span data-ttu-id="ad91c-257">Předkompilování sestavení programem Ngen.exe může zvýšit rychlost spuštění některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ad91c-257">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="ad91c-258">Obecně lze zvýšení výkonu dosáhnout tam, kde aplikace sdílejí sestavení komponent, protože po prvním spuštění aplikace jsou komponenty sdílené s jinými aplikacemi již načteny.</span><span class="sxs-lookup"><span data-stu-id="ad91c-258">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="ad91c-259">Úplné spuštění, při němž musí být všechna sestavení aplikace načtena z pevného disku, nevyužívají výhod nativních bitových kopií v takové míře, protože má převahu přístupová doba pevného disku.</span><span class="sxs-lookup"><span data-stu-id="ad91c-259">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="ad91c-260">Pevné vazby mohou ovlivnit rychlost spuštění, protože všechny bitové kopie pevně svázané s hlavním sestavením aplikace musí být načteny najednou.</span><span class="sxs-lookup"><span data-stu-id="ad91c-260">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-261">Před .NET Framework 3,5 aktualizace Service Pack 1 byste měli umístit sdílené a silně pojmenované komponenty do globální mezipaměti sestavení (GAC), protože zavaděč provádí dodatečné ověřování pro sestavení se silným názvem, která nejsou v globální mezipaměti sestavení (GAC), efektivně se eliminují. jakékoli zlepšení času spuštění získaného pomocí nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-261">Before the .NET Framework 3.5 Service Pack 1, you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="ad91c-262">Optimalizace, které byly představeny v .NET Framework 3,5 SP1, odebraly dodatečné ověření.</span><span class="sxs-lookup"><span data-stu-id="ad91c-262">Optimizations that were introduced in the .NET Framework 3.5 SP1 removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="ad91c-263">Souhrn důležitých informací o použití</span><span class="sxs-lookup"><span data-stu-id="ad91c-263">Summary of usage considerations</span></span>

<span data-ttu-id="ad91c-264">Následující obecné a aplikační informace vám mohou pomoci rozhodnout, zda může být vyhodnocení nativních bitových kopií pro aplikaci přínosem:</span><span class="sxs-lookup"><span data-stu-id="ad91c-264">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="ad91c-265">Nativní bitové kopie se načítají rychleji než jazyk MSIL, protože odstraňují potřebu mnoha aktivit při spouštění, například kompilaci JIT a ověření bezpečnosti typů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-265">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="ad91c-266">Nativní bitové kopie vyžadují menší počáteční pracovní sadu, protože není zapotřebí použít kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="ad91c-266">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="ad91c-267">Nativní bitové kopie umožňují sdílení kódu mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ad91c-267">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="ad91c-268">Nativní bitové kopie vyžadují více místa na disku než sestavení MSIL a jejich generování může trvat značně dlouho.</span><span class="sxs-lookup"><span data-stu-id="ad91c-268">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="ad91c-269">Nativní bitové kopie musí být udržovány.</span><span class="sxs-lookup"><span data-stu-id="ad91c-269">Native images must be maintained.</span></span>

  - <span data-ttu-id="ad91c-270">Je-li upraveno původní sestavení nebo jedna z jeho závislostí, je zapotřebí bitové kopie znovu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="ad91c-270">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="ad91c-271">Jediné sestavení může vyžadovat několik nativních bitových kopií pro použití v různých aplikacích a scénářích.</span><span class="sxs-lookup"><span data-stu-id="ad91c-271">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="ad91c-272">Například informace o konfiguraci dvou aplikací může vyústit v různá rozhodnutí o vazbách stejného závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-272">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="ad91c-273">Nativní bitové kopie musí být generovány správcem; tj. z účtu systému Windows ve skupině Administrators.</span><span class="sxs-lookup"><span data-stu-id="ad91c-273">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="ad91c-274">Spolu s těmito obecnými informacemi je zapotřebí při určování, zda mohou nativní bitové kopie poskytnout zvýšení výkonu, zvážit i povahu aplikace:</span><span class="sxs-lookup"><span data-stu-id="ad91c-274">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="ad91c-275">Je-li aplikace spouštěna v prostředí, které využívá mnoho sdílených komponent, nativní bitové kopie umožňují sdílení komponent mezi mnoha procesy.</span><span class="sxs-lookup"><span data-stu-id="ad91c-275">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="ad91c-276">Používá-li aplikace více domén aplikace, nativní bitové kopie umožňují sdílení znakových stránek mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="ad91c-276">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad91c-277">V rozhraních .NET Framework verze 1.0 a 1.1 nemohou být nativní bitové kopie sdíleny napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-277">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="ad91c-278">Verze 2.0 a novější již toto omezení nemají.</span><span class="sxs-lookup"><span data-stu-id="ad91c-278">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="ad91c-279">Bude-li aplikace spuštěna v rámci Terminálového serveru, nativní bitové kopie umožní sdílení znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="ad91c-279">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="ad91c-280">Rozsáhlé aplikace obecně těží z výhod kompilace do nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-280">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="ad91c-281">Malým aplikacím nativní bitové kopie obvykle výhody nepřinášejí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-281">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="ad91c-282">Pro dlouho běžící aplikace vykazuje kompilace JIT za běhu mírně vyšší výkon než nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-282">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="ad91c-283">(Pevné vazby mohou tento rozdíl ve výkonu do určité míry zmenšit.)</span><span class="sxs-lookup"><span data-stu-id="ad91c-283">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="ad91c-284">Důležitost základních adres sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-284">Importance of assembly base addresses</span></span>

<span data-ttu-id="ad91c-285">Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-285">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="ad91c-286">Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="ad91c-286">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="ad91c-287">Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-287">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="ad91c-288">Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-288">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-289">Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="ad91c-289">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="ad91c-290">Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.</span><span class="sxs-lookup"><span data-stu-id="ad91c-290">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="ad91c-291">Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-291">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="ad91c-292">Pevná vazba</span><span class="sxs-lookup"><span data-stu-id="ad91c-292">Hard binding</span></span>

<span data-ttu-id="ad91c-293">Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-293">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="ad91c-294">Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-294">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="ad91c-295">To u velkých aplikací může výrazně prodloužit spouštění.</span><span class="sxs-lookup"><span data-stu-id="ad91c-295">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="ad91c-296">Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-296">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="ad91c-297">Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad91c-297">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="ad91c-298">Atributy <xref:System.Runtime.CompilerServices.DependencyAttribute> a<xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> umožňují zadat pomocný parametr pro pevné vazby do nástroje Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-298">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-299">Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="ad91c-299">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="ad91c-300">Jejich použití nezaručuje pevné vazby.</span><span class="sxs-lookup"><span data-stu-id="ad91c-300">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="ad91c-301">V budoucích verzích se může změnit význam těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-301">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="ad91c-302">Zadání pomocného parametru vazby pro závislost</span><span class="sxs-lookup"><span data-stu-id="ad91c-302">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="ad91c-303"><xref:System.Runtime.CompilerServices.DependencyAttribute> Použijte pro sestavení k označení pravděpodobnosti, že se načte zadaná závislost.</span><span class="sxs-lookup"><span data-stu-id="ad91c-303">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="ad91c-304"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>označuje, že pevná vazba je vhodná <xref:System.Runtime.CompilerServices.LoadHint.Default> , indikuje, že by měla být použita výchozí hodnota závislosti, <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> a označuje, že pevná vazba není vhodná.</span><span class="sxs-lookup"><span data-stu-id="ad91c-304"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="ad91c-305">Následující kód zobrazuje atributy pro sestavení, které má dvě závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-305">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="ad91c-306">První závislost (Assembly1) je vhodným kandidátem pro pevnou vazbu, druhá závislost (Assembly2) nikoliv.</span><span class="sxs-lookup"><span data-stu-id="ad91c-306">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

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

<span data-ttu-id="ad91c-307">Název sestavení neobsahuje příponu názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="ad91c-307">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="ad91c-308">Lze použít zobrazené názvy.</span><span class="sxs-lookup"><span data-stu-id="ad91c-308">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="ad91c-309">Určení výchozího parametru vazby pro sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-309">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="ad91c-310">Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-310">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="ad91c-311"><xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> Použijte s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> u těchto sestavení k určení, že se má použít pevná vazba.</span><span class="sxs-lookup"><span data-stu-id="ad91c-311">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-312">Neexistuje žádný důvod, jak použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na sestavení knihovny DLL, která nespadají do této kategorie, protože použití atributu s jinou hodnotou než <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný efekt jako nepoužití atributu vůbec.</span><span class="sxs-lookup"><span data-stu-id="ad91c-312">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="ad91c-313">Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> k určení této pevné vazby výchozí hodnotu pro velmi malý počet sestavení v .NET Framework, jako je například mscorlib. dll.</span><span class="sxs-lookup"><span data-stu-id="ad91c-313">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="ad91c-314">Odložené zpracování</span><span class="sxs-lookup"><span data-stu-id="ad91c-314">Deferred processing</span></span>

<span data-ttu-id="ad91c-315">Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="ad91c-315">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="ad91c-316">Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-316">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="ad91c-317">Akce `install` a `update` mají`/queue` možnost, která zařadí do fronty operaci pro odložené spouštění pomocí nativní bitové kopie služby.</span><span class="sxs-lookup"><span data-stu-id="ad91c-317">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="ad91c-318">Kromě toho nástroj Ngen. exe obsahuje `queue` akce `executeQueuedItems` a, které poskytují určitou kontrolu nad službou.</span><span class="sxs-lookup"><span data-stu-id="ad91c-318">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="ad91c-319">Další informace najdete v tématu [nativní Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-319">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="ad91c-320">Nativní bitové kopie a kompilace JIT</span><span class="sxs-lookup"><span data-stu-id="ad91c-320">Native images and JIT compilation</span></span>

<span data-ttu-id="ad91c-321">Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-321">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="ad91c-322">Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="ad91c-322">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="ad91c-323">Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.</span><span class="sxs-lookup"><span data-stu-id="ad91c-323">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="ad91c-324">Neplatné obrázky</span><span class="sxs-lookup"><span data-stu-id="ad91c-324">Invalid images</span></span>

<span data-ttu-id="ad91c-325">Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače.</span><span class="sxs-lookup"><span data-stu-id="ad91c-325">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="ad91c-326">Mezi tato nastavení patří následující:</span><span class="sxs-lookup"><span data-stu-id="ad91c-326">These settings include the following:</span></span>

- <span data-ttu-id="ad91c-327">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad91c-327">The version of the .NET Framework.</span></span>

- <span data-ttu-id="ad91c-328">Verze operačního systému, pokud je změna z řady Windows 9x na řadu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="ad91c-328">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

- <span data-ttu-id="ad91c-329">Přesná identita sestavení (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="ad91c-329">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="ad91c-330">Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).</span><span class="sxs-lookup"><span data-stu-id="ad91c-330">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="ad91c-331">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="ad91c-331">Security factors.</span></span>

<span data-ttu-id="ad91c-332">Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-332">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="ad91c-333">Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače.</span><span class="sxs-lookup"><span data-stu-id="ad91c-333">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="ad91c-334">Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="ad91c-334">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="ad91c-335">Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:</span><span class="sxs-lookup"><span data-stu-id="ad91c-335">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="ad91c-336">Verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad91c-336">The version of the .NET Framework.</span></span>

     <span data-ttu-id="ad91c-337">Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní.</span><span class="sxs-lookup"><span data-stu-id="ad91c-337">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="ad91c-338">Z tohoto důvodu všechny aktualizace .NET Framework spustí `Ngen Update` příkaz, aby se zajistilo opětovné vygenerování všech nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-338">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="ad91c-339">Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.</span><span class="sxs-lookup"><span data-stu-id="ad91c-339">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="ad91c-340">Verze operačního systému, pokud je změna z řady Windows 9x na řadu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="ad91c-340">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

     <span data-ttu-id="ad91c-341">Například pokud se verze operačního systému běžícího na počítači změní z Windows 98 na Windows XP, všechny nativní bitové kopie uložené v mezipaměti nativních imagí se stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="ad91c-341">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="ad91c-342">Pokud se ale operační systém změní z Windows 2000 na Windows XP, bitové kopie se neověřují.</span><span class="sxs-lookup"><span data-stu-id="ad91c-342">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>

- <span data-ttu-id="ad91c-343">Přesná identita sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-343">The exact identity of the assembly.</span></span>

     <span data-ttu-id="ad91c-344">Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="ad91c-344">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="ad91c-345">Přesná identita všech sestavení, na která sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ad91c-345">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="ad91c-346">Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="ad91c-346">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="ad91c-347">To zahrnuje jak běžné odkazy, tak pevně vázané závislosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-347">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="ad91c-348">Pokaždé, když se použije aktualizace softwaru, instalační program by měl `Ngen Update` spustit příkaz, aby se zajistilo, že se znovu vygenerují všechny závislé nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-348">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="ad91c-349">Bezpečnostní faktory.</span><span class="sxs-lookup"><span data-stu-id="ad91c-349">Security factors.</span></span>

     <span data-ttu-id="ad91c-350">Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.</span><span class="sxs-lookup"><span data-stu-id="ad91c-350">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="ad91c-351">Podrobné informace o tom, jak modul CLR (Common Language Runtime) spravuje zabezpečení přístupu kódu a používání oprávnění, najdete v tématu [zabezpečení přístupu kódu](../misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="ad91c-351">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="ad91c-352">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="ad91c-352">Troubleshooting</span></span>

<span data-ttu-id="ad91c-353">Následující témata Poradce při potížích umožňují zjistit, které nativní bitové kopie jsou používány a které nemohou být použity vaší aplikací, k určení, kdy kompilátor JIT začne kompilovat metodu a ukazuje, jak se odhlásit ze zadaného nativního kompilování bitové kopie. způsobů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-353">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="ad91c-354">vazba sestavení – prohlížeč protokolu</span><span class="sxs-lookup"><span data-stu-id="ad91c-354">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="ad91c-355">Chcete-li potvrdit, že aplikace používá nativní bitové kopie, můžete použít [Fuslogvw. exe (Prohlížeč protokolu vazby sestavení)](fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="ad91c-355">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="ad91c-356">V okně prohlížeče protokolu vazby v poli **Kategorie protokolů** vyberte **nativní bitové kopie** .</span><span class="sxs-lookup"><span data-stu-id="ad91c-356">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="ad91c-357">Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="ad91c-357">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="ad91c-358">Pomocníka spravovaného ladění jitCompilationStart –</span><span class="sxs-lookup"><span data-stu-id="ad91c-358">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="ad91c-359">K určení, kdy kompilátor JIT začne kompilovat funkci, můžete použít pomocníka spravovaného ladění (MDA) [jitCompilationStart –](../debug-trace-profile/jitcompilationstart-mda.md) .</span><span class="sxs-lookup"><span data-stu-id="ad91c-359">You can use the [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="ad91c-360">Vypnutí generování nativních imagí</span><span class="sxs-lookup"><span data-stu-id="ad91c-360">Opting out of native image generation</span></span>

<span data-ttu-id="ad91c-361">V některých případech může NGen. exe mít potíže při generování nativní bitové kopie pro konkrétní metodu, nebo může být vhodnější, aby byla metoda JIT zkompilována, spíše zkompilována do nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-361">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="ad91c-362">V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut k zabránění generování nativní bitové kopie pro určitou metodu pomocí atributu Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-362">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="ad91c-363">Atribut musí být použit samostatně pro každou metodu, jejíž kód nechcete zahrnout do nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-363">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="ad91c-364">NGen. exe rozpoznává atribut a negeneruje kód v nativní imagi pro odpovídající metodu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-364">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="ad91c-365">Všimněte si však, že `BypassNGenAttribute` není definován jako typ v knihovně tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad91c-365">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="ad91c-366">Aby bylo možné používat atribut v kódu, je nutné nejprve definovat následující:</span><span class="sxs-lookup"><span data-stu-id="ad91c-366">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="ad91c-367">Pak můžete použít atribut na základě jednotlivých metod.</span><span class="sxs-lookup"><span data-stu-id="ad91c-367">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="ad91c-368">Následující příklad instruuje generátor nativních bitových kopií, který by neměl generovat nativní bitovou kopii `ExampleClass.ToJITCompile` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-368">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="ad91c-369">Příklady</span><span class="sxs-lookup"><span data-stu-id="ad91c-369">Examples</span></span>

<span data-ttu-id="ad91c-370">Následující příkaz vytvoří nativní bitovou kopii pro `ClientApp.exe`objekt umístěný v aktuálním adresáři a nainstaluje bitovou kopii do mezipaměti nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-370">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="ad91c-371">Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije.</span><span class="sxs-lookup"><span data-stu-id="ad91c-371">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="ad91c-372">Kromě toho jsou vygenerovány nativní bitové kopie pro všechny soubory DLL `ClientApp.exe` , které odkazují na.</span><span class="sxs-lookup"><span data-stu-id="ad91c-372">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```console
ngen install ClientApp.exe
```

<span data-ttu-id="ad91c-373">Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen.</span><span class="sxs-lookup"><span data-stu-id="ad91c-373">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="ad91c-374">Kořen může být aplikace nebo sdílená komponenta.</span><span class="sxs-lookup"><span data-stu-id="ad91c-374">A root can be an application or a shared component.</span></span>

<span data-ttu-id="ad91c-375">Následující příkaz vytvoří nativní bitovou kopii pro `MyAssembly.exe` zadanou cestu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-375">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```console
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="ad91c-376">Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ad91c-376">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="ad91c-377">Ve výchozím nastavení se adresář, který `ClientApp.exe` obsahuje, používá jako základní adresář aplikace a veškeré zjišťování sestavení začíná v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="ad91c-377">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="ad91c-378">Toto chování můžete přepsat pomocí `/AppBase` možnosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-378">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-379">Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad91c-379">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="ad91c-380">Sestavení může mít závislost bez odkazu, například pokud načte soubor DLL pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ad91c-380">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ad91c-381">Můžete vytvořit nativní bitovou kopii pro takový soubor. dll pomocí informací o konfiguraci pro sestavení aplikace s `/ExeConfig` možností.</span><span class="sxs-lookup"><span data-stu-id="ad91c-381">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="ad91c-382">Následující příkaz vytvoří nativní bitovou kopii pro `MyLib.dll,` použití informací o konfiguraci z `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad91c-382">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="ad91c-383">Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="ad91c-383">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="ad91c-384">Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="ad91c-384">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="ad91c-385">Následující příkaz odinstaluje `MyLib.dll` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-385">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="ad91c-386">Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad91c-386">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="ad91c-387">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad91c-387">For example:</span></span>

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="ad91c-388">NGen.exe vytváří samostatnou sadu bitových kopií pro každý scénář, který instalujete.</span><span class="sxs-lookup"><span data-stu-id="ad91c-388">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="ad91c-389">Například následující příkazy nainstalují kompletní sadu nativních bitových kopií pro normální provoz, jinou kompletní sadu pro ladění a třetí pro profilování:</span><span class="sxs-lookup"><span data-stu-id="ad91c-389">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="ad91c-390">Zobrazení mezipaměti nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="ad91c-390">Displaying the Native Image Cache</span></span>

<span data-ttu-id="ad91c-391">Jakmile jsou nativní bitové kopie nainstalovány v mezipaměti, lze je zobrazit pomocí nástroje Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-391">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="ad91c-392">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-392">The following command displays all native images in the native image cache.</span></span>

```console
ngen display
```

<span data-ttu-id="ad91c-393">`display` Akce nejprve Vypíše všechna kořenová sestavení a potom seznam všech nativních bitových kopií v počítači.</span><span class="sxs-lookup"><span data-stu-id="ad91c-393">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="ad91c-394">Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="ad91c-394">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="ad91c-395">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních imagí, které odpovídají částečnému `MyAssembly`názvu, jejich závislostem a všem kořenům, na `MyAssembly`kterých závisí:</span><span class="sxs-lookup"><span data-stu-id="ad91c-395">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```console
ngen display MyAssembly
```

<span data-ttu-id="ad91c-396">Znalost toho, které kořeny závisí na sestavení sdílené komponenty, je užitečné v měření dopad `update` akce po upgradu sdílené komponenty.</span><span class="sxs-lookup"><span data-stu-id="ad91c-396">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="ad91c-397">Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:</span><span class="sxs-lookup"><span data-stu-id="ad91c-397">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```console
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="ad91c-398">Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních imagí s názvem `MyAssembly` a verzí 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="ad91c-398">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="ad91c-399">Aktualizace bitových kopií</span><span class="sxs-lookup"><span data-stu-id="ad91c-399">Updating Images</span></span>

<span data-ttu-id="ad91c-400">Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty.</span><span class="sxs-lookup"><span data-stu-id="ad91c-400">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="ad91c-401">Chcete-li aktualizovat všechny nativní bitové kopie, které se změnily nebo jejichž závislosti se `update` změnily, použijte akci bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-401">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```console
ngen update
```

<span data-ttu-id="ad91c-402">Aktualizace všech bitových kopií může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="ad91c-402">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="ad91c-403">Aktualizace můžete zařadit do fronty pro spouštění pomocí služby nativních imagí pomocí `/queue` možnosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-403">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="ad91c-404">Další informace o `/queue` možnosti a prioritách instalace najdete v tématu [nativní Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-404">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```console
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="ad91c-405">Odinstalování bitových kopií</span><span class="sxs-lookup"><span data-stu-id="ad91c-405">Uninstalling Images</span></span>

<span data-ttu-id="ad91c-406">Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-406">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="ad91c-407">Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.</span><span class="sxs-lookup"><span data-stu-id="ad91c-407">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="ad91c-408">Následující příkaz odinstaluje všechny scénáře pro kořen `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="ad91c-408">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp
```

<span data-ttu-id="ad91c-409">`uninstall` Akci lze použít k odebrání konkrétních scénářů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-409">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="ad91c-410">Následující příkaz odinstaluje všechny scénáře ladění pro `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="ad91c-410">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="ad91c-411">Při `/debug` odinstalaci scénářů nedojde k odinstalování `/profile` scénáře, který zahrnuje i`/debug.`</span><span class="sxs-lookup"><span data-stu-id="ad91c-411">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>

<span data-ttu-id="ad91c-412">Následující příkaz odinstaluje všechny scénáře pro konkrétní verzi `ClientApp.exe`nástroje:</span><span class="sxs-lookup"><span data-stu-id="ad91c-412">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="ad91c-413">Následující příkazy odinstalují všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo pouze scénář ladění pro toto sestavení:</span><span class="sxs-lookup"><span data-stu-id="ad91c-413">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="ad91c-414">Stejně jako u `install` akce vyžaduje poskytnutí rozšíření buď spuštění nástroje Ngen. exe z adresáře obsahujícího sestavení, nebo zadání úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="ad91c-414">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="ad91c-415">Příklady týkající se služby nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-415">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="ad91c-416">Úloha pro nativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="ad91c-416">Native Image Task</span></span>

<span data-ttu-id="ad91c-417">Úloha nativní bitové kopie je úloha systému Windows, která generuje a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-417">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="ad91c-418">Úloha nativní bitové kopie generuje a obnoví nativní bitové kopie automaticky pro podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="ad91c-418">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="ad91c-419">Umožňuje také instalačním nástrojům použít [Ngen. exe (generátor nativních bitových kopií)](ngen-exe-native-image-generator.md) k vytváření a aktualizaci nativních imagí v odloženém čase.</span><span class="sxs-lookup"><span data-stu-id="ad91c-419">It also enables installers to use [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="ad91c-420">Úloha nativní bitové kopie je zaregistrovaná jednou pro každou architekturu procesoru podporovanou v počítači, aby se povolila kompilace pro aplikace cílené na jednotlivé architektury:</span><span class="sxs-lookup"><span data-stu-id="ad91c-420">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="ad91c-421">Název úlohy</span><span class="sxs-lookup"><span data-stu-id="ad91c-421">Task name</span></span>|<span data-ttu-id="ad91c-422">32 – bitový počítač</span><span class="sxs-lookup"><span data-stu-id="ad91c-422">32-bit computer</span></span>|<span data-ttu-id="ad91c-423">64 – bitový počítač</span><span class="sxs-lookup"><span data-stu-id="ad91c-423">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="ad91c-424">Rozhraní .NET Framework NGEN v 4.0.30319</span><span class="sxs-lookup"><span data-stu-id="ad91c-424">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="ad91c-425">Ano</span><span class="sxs-lookup"><span data-stu-id="ad91c-425">Yes</span></span>|<span data-ttu-id="ad91c-426">Ano</span><span class="sxs-lookup"><span data-stu-id="ad91c-426">Yes</span></span>|
|<span data-ttu-id="ad91c-427">Rozhraní .NET Framework NGEN v 4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="ad91c-427">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="ad91c-428">Ne</span><span class="sxs-lookup"><span data-stu-id="ad91c-428">No</span></span>|<span data-ttu-id="ad91c-429">Ano</span><span class="sxs-lookup"><span data-stu-id="ad91c-429">Yes</span></span>|

<span data-ttu-id="ad91c-430">Úloha nativní bitové kopie je k dispozici v .NET Framework 4,5 a novějších verzích při použití v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="ad91c-430">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="ad91c-431">V dřívějších verzích Windows používá .NET Framework [službu nativních bitových kopií](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="ad91c-431">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="ad91c-432">Doba života úlohy</span><span class="sxs-lookup"><span data-stu-id="ad91c-432">Task Lifetime</span></span>

<span data-ttu-id="ad91c-433">Obecně platí, že Windows Plánovač úloh spustí úlohu nativní bitové kopie každou noc, když je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="ad91c-433">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="ad91c-434">Úkol vyhledá všechny odložené práce, které jsou zařazené do fronty instalačními programy aplikací, všechny odložené požadavky na aktualizaci nativních imagí a jakékoli automatické vytváření imagí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-434">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="ad91c-435">Úkol dokončí nedokončené pracovní položky a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-435">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="ad91c-436">Pokud se počítač zastaví v nečinnosti, zatímco je úloha spuštěná, úloha se zastaví.</span><span class="sxs-lookup"><span data-stu-id="ad91c-436">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="ad91c-437">Můžete také spustit úlohu nativní bitové kopie ručně prostřednictvím uživatelského rozhraní Plánovač úloh nebo ručním voláním nástroje NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-437">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="ad91c-438">Pokud je úloha spuštěná kteroukoli z těchto metod, bude pokračovat v provozu, i když počítač přestane být nečinný.</span><span class="sxs-lookup"><span data-stu-id="ad91c-438">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="ad91c-439">Image vytvořené ručně pomocí nástroje NGen. exe jsou upřednostňovány, aby umožňovaly předvídatelné chování pro instalační programy aplikací.</span><span class="sxs-lookup"><span data-stu-id="ad91c-439">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="ad91c-440">Nativní bitová kopie služby</span><span class="sxs-lookup"><span data-stu-id="ad91c-440">Native Image Service</span></span>

<span data-ttu-id="ad91c-441">Nativní Image Service je služba systému Windows, která generuje a udržuje nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ad91c-441">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="ad91c-442">Nativní Image Service umožňuje vývojářům odložit instalaci a aktualizaci nativních imagí na období, kdy je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="ad91c-442">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="ad91c-443">Za normálních okolností je nativní Image Service inicializovaná instalačním programem (instalační program) pro aplikaci nebo aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="ad91c-443">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="ad91c-444">U akcí s prioritou 3 se služba spouští během nečinnosti počítače.</span><span class="sxs-lookup"><span data-stu-id="ad91c-444">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="ad91c-445">Služba ukládá svůj stav a v případě potřeby může pokračovat v několika restartováních.</span><span class="sxs-lookup"><span data-stu-id="ad91c-445">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="ad91c-446">Více kompilací obrázků lze zařadit do fronty.</span><span class="sxs-lookup"><span data-stu-id="ad91c-446">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="ad91c-447">Služba také komunikuje s ručním příkazem Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-447">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="ad91c-448">Ruční příkazy mají přednost před aktivitou na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-448">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="ad91c-449">V systému Windows Vista je název zobrazený pro nativní Image Service "Microsoft.NET Framework NGEN v 2.0.50727 _X86" nebo "Microsoft.NET Framework NGEN v 2.0.50727 _X64".</span><span class="sxs-lookup"><span data-stu-id="ad91c-449">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="ad91c-450">Ve všech starších verzích Microsoft Windows se jedná o název ".NET runtime Optimization Service v 2.0.50727 _X86" nebo ".NET runtime Optimization Service v 2.0.50727 _X64".</span><span class="sxs-lookup"><span data-stu-id="ad91c-450">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="ad91c-451">Spouštění odložených operací</span><span class="sxs-lookup"><span data-stu-id="ad91c-451">Launching Deferred Operations</span></span>

<span data-ttu-id="ad91c-452">Než začnete s instalací nebo upgradem, doporučujeme pozastavit službu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-452">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="ad91c-453">Tím se zajistí, že se služba nespustí, zatímco instalační program kopíruje soubory nebo umísťují sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="ad91c-453">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="ad91c-454">Následující příkazový řádek nástroje Ngen. exe pozastaví službu:</span><span class="sxs-lookup"><span data-stu-id="ad91c-454">The following Ngen.exe command line pauses the service:</span></span>

```console
ngen queue pause
```

<span data-ttu-id="ad91c-455">Když jsou všechny odložené operace zařazené do fronty, následující příkaz umožní službě obnovit:</span><span class="sxs-lookup"><span data-stu-id="ad91c-455">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```console
ngen queue continue
```

<span data-ttu-id="ad91c-456">Chcete-li při instalaci nové aplikace nebo při aktualizaci sdílené součásti odložit generování nativních imagí, `/queue` použijte možnost `install` s akcemi nebo `update` .</span><span class="sxs-lookup"><span data-stu-id="ad91c-456">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="ad91c-457">Následující příkazové řádky nástroje Ngen. exe nainstalují nativní bitovou kopii pro sdílenou součást a provedou aktualizaci všech kořenových složek, které mohly být ovlivněny:</span><span class="sxs-lookup"><span data-stu-id="ad91c-457">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```console
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="ad91c-458">Akce znovu vygeneruje všechny neověřené nativní bitové kopie, nikoli jenom ty, které používají `MyComponent`. `update`</span><span class="sxs-lookup"><span data-stu-id="ad91c-458">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="ad91c-459">Pokud se vaše aplikace skládá z mnoha kořenů, můžete řídit prioritu odložených akcí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-459">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="ad91c-460">Následující příkazy zařadí do fronty instalaci tří kořenů.</span><span class="sxs-lookup"><span data-stu-id="ad91c-460">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="ad91c-461">`Assembly1`je nainstalovaná jako první, bez čekání na dobu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="ad91c-461">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="ad91c-462">`Assembly2`je nainstalována i bez čekání na čas nečinnosti, ale po dokončení všech akcí s prioritou 1.</span><span class="sxs-lookup"><span data-stu-id="ad91c-462">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="ad91c-463">`Assembly3`se nainstaluje, když služba zjistí, že je počítač nečinný.</span><span class="sxs-lookup"><span data-stu-id="ad91c-463">`Assembly3` is installed when the service detects that the computer is idle.</span></span>

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="ad91c-464">Můžete vynutit, aby se akce zařazené do fronty probíhaly `executeQueuedItems` synchronně pomocí akce.</span><span class="sxs-lookup"><span data-stu-id="ad91c-464">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="ad91c-465">Pokud zadáte volitelnou prioritu, tato akce ovlivní pouze akce zařazené do fronty, které mají stejnou nebo nižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="ad91c-465">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="ad91c-466">Výchozí priorita je 3, takže následující příkaz Ngen. exe zpracuje všechny akce zařazené do fronty hned a nevrátí, dokud nebudou dokončeny:</span><span class="sxs-lookup"><span data-stu-id="ad91c-466">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```console
ngen executeQueuedItems
```

<span data-ttu-id="ad91c-467">Synchronní příkazy jsou spouštěny pomocí nástroje Ngen. exe a nepoužívají službu nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ad91c-467">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="ad91c-468">Můžete provést akce pomocí nástroje Ngen. exe, když je spuštěná nativní Image Service.</span><span class="sxs-lookup"><span data-stu-id="ad91c-468">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="ad91c-469">Vypnutí služby</span><span class="sxs-lookup"><span data-stu-id="ad91c-469">Service Shutdown</span></span>

<span data-ttu-id="ad91c-470">Po spuštění příkazu Ngen. exe, který obsahuje `/queue` možnost, je služba spuštěna na pozadí, dokud nebudou dokončeny všechny akce.</span><span class="sxs-lookup"><span data-stu-id="ad91c-470">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="ad91c-471">Služba ukládá svůj stav, takže v případě potřeby může pokračovat v několika restartováních.</span><span class="sxs-lookup"><span data-stu-id="ad91c-471">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="ad91c-472">Pokud služba zjistí, že žádné další akce nejsou zařazeny do fronty, obnoví její stav tak, aby se při příštím spuštění počítače nerestartoval a pak se sám ukončí.</span><span class="sxs-lookup"><span data-stu-id="ad91c-472">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="ad91c-473">Interakce služby s klienty</span><span class="sxs-lookup"><span data-stu-id="ad91c-473">Service Interaction with Clients</span></span>

<span data-ttu-id="ad91c-474">V .NET Framework verze 2,0 je jediná interakce s nativní imagí pomocí nástroje příkazového řádku Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="ad91c-474">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="ad91c-475">Použijte nástroj příkazového řádku v instalačních skriptech k zařazení akcí do fronty pro službu nativních bitových kopií a pro interakci se službou.</span><span class="sxs-lookup"><span data-stu-id="ad91c-475">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad91c-476">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad91c-476">See also</span></span>

- [<span data-ttu-id="ad91c-477">Nástroje</span><span class="sxs-lookup"><span data-stu-id="ad91c-477">Tools</span></span>](index.md)
- [<span data-ttu-id="ad91c-478">Proces spravovaného spuštění</span><span class="sxs-lookup"><span data-stu-id="ad91c-478">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="ad91c-479">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="ad91c-479">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ad91c-480">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="ad91c-480">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
