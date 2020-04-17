---
title: Nastavení konfigurace systému uvolňování paměti
description: Informace o nastavení za běhu pro konfiguraci, jak systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607807"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="b1581-103">Možnosti konfigurace za běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1581-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="b1581-104">Tato stránka obsahuje informace o nastavení systému uvolňování paměti (GC), které lze změnit za běhu.</span><span class="sxs-lookup"><span data-stu-id="b1581-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="b1581-105">Pokud se snažíte dosáhnout špičkového výkonu spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="b1581-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="b1581-106">Výchozí hodnoty však poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="b1581-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="b1581-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="b1581-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="b1581-108">Nastavení v rámci každé skupiny se běžně používají ve spojení s sebou k dosažení určitého výsledku.</span><span class="sxs-lookup"><span data-stu-id="b1581-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b1581-109">Tato nastavení může také dynamicky měnit aplikace při spuštění, takže všechna nastavení běhu, která nastavíte, mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="b1581-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="b1581-110">Některá nastavení, například [úroveň latence](../../standard/garbage-collection/latency.md), jsou obvykle nastavena pouze prostřednictvím rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b1581-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="b1581-111">Tato nastavení jsou na této stránce vynechána.</span><span class="sxs-lookup"><span data-stu-id="b1581-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="b1581-112">Pro číselné hodnoty použijte desítkovou notaci pro nastavení v souboru *runtimeconfig.json* a šestnáctkový zápis pro nastavení proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="b1581-113">Pro šestnáctkové hodnoty je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="b1581-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="b1581-114">Příchutě uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1581-114">Flavors of garbage collection</span></span>

<span data-ttu-id="b1581-115">Dvě hlavní varianty uvolňování paměti jsou pracovní stanice GC a server GC.</span><span class="sxs-lookup"><span data-stu-id="b1581-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="b1581-116">Další informace o rozdílech mezi těmito dvěma, naleznete [v tématu Základy uvolňování paměti](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="b1581-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="b1581-117">Podpříchutě uvolňování paměti jsou pozadí a non-souběžné.</span><span class="sxs-lookup"><span data-stu-id="b1581-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="b1581-118">Pomocí následujících nastavení vyberte varianty uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="b1581-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="b1581-119">Systém.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="b1581-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="b1581-120">Konfiguruje, zda aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1581-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="b1581-121">Výchozí: Uvolňování paměti`false`pracovní stanice ( ).</span><span class="sxs-lookup"><span data-stu-id="b1581-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="b1581-122">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-122">Setting name</span></span> | <span data-ttu-id="b1581-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-123">Values</span></span> | <span data-ttu-id="b1581-124">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="b1581-126">`false`- pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="b1581-126">`false` - workstation</span></span><br/><span data-ttu-id="b1581-127">`true`- server</span><span class="sxs-lookup"><span data-stu-id="b1581-127">`true` - server</span></span> | <span data-ttu-id="b1581-128">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-129">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="b1581-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="b1581-130">`false`- pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="b1581-130">`false` - workstation</span></span><br/><span data-ttu-id="b1581-131">`true`- server</span><span class="sxs-lookup"><span data-stu-id="b1581-131">`true` - server</span></span> | <span data-ttu-id="b1581-132">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-133">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="b1581-134">`0`- pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="b1581-134">`0` - workstation</span></span><br/><span data-ttu-id="b1581-135">`1`- server</span><span class="sxs-lookup"><span data-stu-id="b1581-135">`1` - server</span></span> | <span data-ttu-id="b1581-136">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-137">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-138">Server GCServer</span><span class="sxs-lookup"><span data-stu-id="b1581-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="b1581-139">`false`- pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="b1581-139">`false` - workstation</span></span><br/><span data-ttu-id="b1581-140">`true`- server</span><span class="sxs-lookup"><span data-stu-id="b1581-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="b1581-141">Příklady</span><span class="sxs-lookup"><span data-stu-id="b1581-141">Examples</span></span>

<span data-ttu-id="b1581-142">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="b1581-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="b1581-143">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="b1581-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="b1581-144">System.GC.Concurrent/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="b1581-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="b1581-145">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžné).</span><span class="sxs-lookup"><span data-stu-id="b1581-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="b1581-146">Výchozí hodnota:`true`Povoleno ( ).</span><span class="sxs-lookup"><span data-stu-id="b1581-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="b1581-147">Další informace naleznete v [tématu Uvolňování paměti na pozadí](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) a uvolňování paměti serveru na [pozadí](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="b1581-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="b1581-148">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-148">Setting name</span></span> | <span data-ttu-id="b1581-149">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-149">Values</span></span> | <span data-ttu-id="b1581-150">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="b1581-152">`true`- pozadí GC</span><span class="sxs-lookup"><span data-stu-id="b1581-152">`true` - background GC</span></span><br/><span data-ttu-id="b1581-153">`false`- nesouběžné GC</span><span class="sxs-lookup"><span data-stu-id="b1581-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="b1581-154">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-155">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="b1581-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="b1581-156">`true`- pozadí GC</span><span class="sxs-lookup"><span data-stu-id="b1581-156">`true` - background GC</span></span><br/><span data-ttu-id="b1581-157">`false`- nesouběžné GC</span><span class="sxs-lookup"><span data-stu-id="b1581-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="b1581-158">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-159">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="b1581-160">`true`- pozadí GC</span><span class="sxs-lookup"><span data-stu-id="b1581-160">`true` - background GC</span></span><br/><span data-ttu-id="b1581-161">`false`- nesouběžné GC</span><span class="sxs-lookup"><span data-stu-id="b1581-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="b1581-162">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-163">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="b1581-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="b1581-165">`true`- pozadí GC</span><span class="sxs-lookup"><span data-stu-id="b1581-165">`true` - background GC</span></span><br/><span data-ttu-id="b1581-166">`false`- nesouběžné GC</span><span class="sxs-lookup"><span data-stu-id="b1581-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="b1581-167">Příklady</span><span class="sxs-lookup"><span data-stu-id="b1581-167">Examples</span></span>

<span data-ttu-id="b1581-168">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="b1581-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="b1581-169">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="b1581-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="b1581-170">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="b1581-170">Manage resource usage</span></span>

<span data-ttu-id="b1581-171">Pomocí nastavení popsaných v této části můžete spravovat využití paměti a procesoru systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="b1581-172">Další informace o některých z těchto nastavení naleznete v [tématu Middle ground mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu server GC.</span><span class="sxs-lookup"><span data-stu-id="b1581-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="b1581-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="b1581-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="b1581-174">Omezuje počet hromad vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="b1581-175">Platí pouze pro uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1581-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b1581-176">Pokud je [povolena spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) což je výchozí, nastavení `n` spřažení haldy `n` GC haldy/vlákna na první procesory.</span><span class="sxs-lookup"><span data-stu-id="b1581-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="b1581-177">(Pomocí nastavení [spřažení nebo](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) [spřažení rozsahů určete](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) přesně, které procesory chcete spárovat.)</span><span class="sxs-lookup"><span data-stu-id="b1581-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="b1581-178">Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) toto nastavení omezuje počet hromad GC.</span><span class="sxs-lookup"><span data-stu-id="b1581-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="b1581-179">Další informace naleznete v [poznámkách GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="b1581-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="b1581-180">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-180">Setting name</span></span> | <span data-ttu-id="b1581-181">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-181">Values</span></span> | <span data-ttu-id="b1581-182">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="b1581-184">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-184">*decimal value*</span></span> | <span data-ttu-id="b1581-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-186">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="b1581-187">*šestnáctková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-187">*hexadecimal value*</span></span> | <span data-ttu-id="b1581-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-189">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-190">Počet gcheapcount</span><span class="sxs-lookup"><span data-stu-id="b1581-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="b1581-191">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-191">*decimal value*</span></span> | <span data-ttu-id="b1581-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b1581-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b1581-193">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-193">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="b1581-194">Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b1581-195">Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b1581-196">Chcete-li například omezit počet hromad na 16, hodnoty by 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="b1581-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="b1581-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="b1581-198">Určuje přesné procesory, které by měly používat vlákna systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="b1581-199">Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="b1581-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="b1581-200">Platí pouze pro uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1581-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b1581-201">Hodnota je bitová maska, která definuje procesory, které jsou k dispozici pro proces.</span><span class="sxs-lookup"><span data-stu-id="b1581-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="b1581-202">Například desetinná hodnota 1023 (nebo šestnáctkové hodnoty 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="b1581-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="b1581-203">To určuje, že má být použito prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="b1581-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="b1581-204">Chcete-li zadat dalších 10 procesorů, tedy procesorů 10-19, zadejte desetinnou hodnotu 1047552 (nebo šestnáctkovou hodnotu 0xFFC00 nebo FFC00), což odpovídá binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="b1581-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="b1581-205">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-205">Setting name</span></span> | <span data-ttu-id="b1581-206">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-206">Values</span></span> | <span data-ttu-id="b1581-207">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="b1581-209">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-209">*decimal value*</span></span> | <span data-ttu-id="b1581-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-211">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="b1581-212">*šestnáctková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-212">*hexadecimal value*</span></span> | <span data-ttu-id="b1581-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-214">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="b1581-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="b1581-216">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-216">*decimal value*</span></span> | <span data-ttu-id="b1581-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b1581-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b1581-218">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="b1581-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="b1581-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="b1581-220">Určuje seznam procesorů, které mají být používány pro vlákna systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="b1581-221">Toto nastavení je podobné [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), kromě toho umožňuje zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="b1581-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="b1581-222">Pro operační systémy Windows předponu číslo procesoru nebo rozsah s odpovídající [skupinou procesoru](/windows/win32/procthread/processor-groups), například "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="b1581-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="b1581-223">Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="b1581-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="b1581-224">Platí pouze pro uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1581-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b1581-225">Další informace najdete [v tématu Lepší konfigurace procesoru pro GC na počítačích s procesory > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="b1581-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="b1581-226">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-226">Setting name</span></span> | <span data-ttu-id="b1581-227">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-227">Values</span></span> | <span data-ttu-id="b1581-228">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="b1581-230">Seznam procesorů oddělených čárkami nebo rozsahy procesorových čísel.</span><span class="sxs-lookup"><span data-stu-id="b1581-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="b1581-231">Unix příklad: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="b1581-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="b1581-232">Příklad systému Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="b1581-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="b1581-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-234">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="b1581-235">Seznam procesorů oddělených čárkami nebo rozsahy procesorových čísel.</span><span class="sxs-lookup"><span data-stu-id="b1581-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="b1581-236">Unix příklad: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="b1581-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="b1581-237">Příklad systému Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="b1581-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="b1581-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-238">.NET Core 3.0</span></span> |

<span data-ttu-id="b1581-239">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="b1581-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="b1581-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="b1581-241">Konfiguruje, zda systém uvolňování paměti používá [skupiny procesoru](/windows/win32/procthread/processor-groups) nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b1581-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="b1581-242">Pokud 64bitový počítač se systémem Windows obsahuje více skupin procesorů, to znamená, že existuje více než 64 procesorů, povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="b1581-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="b1581-243">Systém uvolňování paměti používá všechna jádra k vytvoření a vyvážení hald.</span><span class="sxs-lookup"><span data-stu-id="b1581-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="b1581-244">Platí pouze pro uvolňování paměti serveru v 64bitových operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="b1581-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="b1581-245">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="b1581-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="b1581-246">Další informace najdete [v tématu Lepší konfigurace procesoru pro GC na počítačích s procesory > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="b1581-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="b1581-247">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-247">Setting name</span></span> | <span data-ttu-id="b1581-248">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-248">Values</span></span> | <span data-ttu-id="b1581-249">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="b1581-251">–</span><span class="sxs-lookup"><span data-stu-id="b1581-251">N/A</span></span> | <span data-ttu-id="b1581-252">–</span><span class="sxs-lookup"><span data-stu-id="b1581-252">N/A</span></span> | <span data-ttu-id="b1581-253">–</span><span class="sxs-lookup"><span data-stu-id="b1581-253">N/A</span></span> |
| <span data-ttu-id="b1581-254">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="b1581-255">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="b1581-255">`0` - disabled</span></span><br/><span data-ttu-id="b1581-256">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="b1581-256">`1` - enabled</span></span> | <span data-ttu-id="b1581-257">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-258">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-259">Skupina GCCpu</span><span class="sxs-lookup"><span data-stu-id="b1581-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="b1581-260">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="b1581-260">`false` - disabled</span></span><br/><span data-ttu-id="b1581-261">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="b1581-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="b1581-262">Chcete-li nakonfigurovat běžný jazyk runtime (CLR) také distribuovat podprocesy z fondu vláken ve všech skupinách procesoru, povolte [možnost Thread_UseAllCpuGroups prvek.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1581-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="b1581-263">Pro aplikace .NET Core můžete tuto možnost povolit `COMPlus_Thread_UseAllCpuGroups` nastavením `1`hodnoty proměnné prostředí na .</span><span class="sxs-lookup"><span data-stu-id="b1581-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="b1581-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="b1581-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="b1581-265">Určuje, zda chcete *spárovat* vlákna uvolňování paměti s procesory.</span><span class="sxs-lookup"><span data-stu-id="b1581-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="b1581-266">Chcete-li spřažení podprocesu GC znamená, že jej lze spustit pouze na jeho konkrétní procesor.</span><span class="sxs-lookup"><span data-stu-id="b1581-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="b1581-267">Haldy je vytvořen pro každý podproces GC.</span><span class="sxs-lookup"><span data-stu-id="b1581-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="b1581-268">Platí pouze pro uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1581-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b1581-269">Výchozí: Spřažení podprocesů uvolňování paměti`false`s procesory ( ).</span><span class="sxs-lookup"><span data-stu-id="b1581-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="b1581-270">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-270">Setting name</span></span> | <span data-ttu-id="b1581-271">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-271">Values</span></span> | <span data-ttu-id="b1581-272">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="b1581-274">`false`- afinitizovat</span><span class="sxs-lookup"><span data-stu-id="b1581-274">`false` - affinitize</span></span><br/><span data-ttu-id="b1581-275">`true`- nesoužejte</span><span class="sxs-lookup"><span data-stu-id="b1581-275">`true` - don't affinitize</span></span> | <span data-ttu-id="b1581-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-277">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="b1581-278">`0`- afinitizovat</span><span class="sxs-lookup"><span data-stu-id="b1581-278">`0` - affinitize</span></span><br/><span data-ttu-id="b1581-279">`1`- nesoužejte</span><span class="sxs-lookup"><span data-stu-id="b1581-279">`1` - don't affinitize</span></span> | <span data-ttu-id="b1581-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-281">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="b1581-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="b1581-283">`false`- afinitizovat</span><span class="sxs-lookup"><span data-stu-id="b1581-283">`false` - affinitize</span></span><br/><span data-ttu-id="b1581-284">`true`- nesoužejte</span><span class="sxs-lookup"><span data-stu-id="b1581-284">`true` - don't affinitize</span></span> | <span data-ttu-id="b1581-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b1581-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b1581-286">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="b1581-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="b1581-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="b1581-288">Určuje maximální velikost potvrzení v bajtech pro hromadu GC a účetnictví gc.</span><span class="sxs-lookup"><span data-stu-id="b1581-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="b1581-289">Toto nastavení platí pouze pro 64bitové počítače.</span><span class="sxs-lookup"><span data-stu-id="b1581-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="b1581-290">Výchozí hodnota, která platí pouze v určitých případech, je menší 20 MB nebo 75 % limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b1581-290">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="b1581-291">Výchozí hodnota se použije v případě, že:</span><span class="sxs-lookup"><span data-stu-id="b1581-291">The default value applies if:</span></span>

  - <span data-ttu-id="b1581-292">Proces je spuštěn uvnitř kontejneru, který má zadaný limit paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="b1581-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) není nastavena.</span><span class="sxs-lookup"><span data-stu-id="b1581-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="b1581-294">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-294">Setting name</span></span> | <span data-ttu-id="b1581-295">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-295">Values</span></span> | <span data-ttu-id="b1581-296">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="b1581-298">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-298">*decimal value*</span></span> | <span data-ttu-id="b1581-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-300">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="b1581-301">*šestnáctková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-301">*hexadecimal value*</span></span> | <span data-ttu-id="b1581-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-302">.NET Core 3.0</span></span> |

<span data-ttu-id="b1581-303">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="b1581-304">Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b1581-305">Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b1581-306">Chcete-li například zadat pevný limit haldy 200 mebibytes (MiB), hodnoty by 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="b1581-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="b1581-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="b1581-308">Určuje povolené využití haldy GC jako procento celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="b1581-309">Pokud [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) je také nastavena, toto nastavení je ignorována.</span><span class="sxs-lookup"><span data-stu-id="b1581-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="b1581-310">Toto nastavení platí pouze pro 64bitové počítače.</span><span class="sxs-lookup"><span data-stu-id="b1581-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="b1581-311">Pokud je proces spuštěn uvnitř kontejneru, který má zadaný limit paměti, procento se vypočítá jako procento tohoto limitu paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="b1581-312">Výchozí hodnota, která platí pouze v určitých případech, je menší 20 MB nebo 75 % limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b1581-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="b1581-313">Výchozí hodnota se použije v případě, že:</span><span class="sxs-lookup"><span data-stu-id="b1581-313">The default value applies if:</span></span>

  - <span data-ttu-id="b1581-314">Proces je spuštěn uvnitř kontejneru, který má zadaný limit paměti.</span><span class="sxs-lookup"><span data-stu-id="b1581-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="b1581-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) není nastaven.</span><span class="sxs-lookup"><span data-stu-id="b1581-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="b1581-316">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-316">Setting name</span></span> | <span data-ttu-id="b1581-317">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-317">Values</span></span> | <span data-ttu-id="b1581-318">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="b1581-320">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-320">*decimal value*</span></span> | <span data-ttu-id="b1581-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="b1581-322">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="b1581-323">*šestnáctková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-323">*hexadecimal value*</span></span> | <span data-ttu-id="b1581-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-324">.NET Core 3.0</span></span> |

<span data-ttu-id="b1581-325">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-325">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="b1581-326">Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b1581-327">Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b1581-328">Chcete-li například omezit využití haldy na 30 %, hodnoty by byly 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="b1581-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="b1581-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="b1581-330">Konfiguruje, zda segmenty, které mají být odstraněny jsou uvedeny do pohotovostního seznamu pro budoucí použití nebo jsou uvolněny zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="b1581-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="b1581-331">Výchozí: Uvolnění segmentů zpět do`false`operačního systému ( ).</span><span class="sxs-lookup"><span data-stu-id="b1581-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="b1581-332">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-332">Setting name</span></span> | <span data-ttu-id="b1581-333">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-333">Values</span></span> | <span data-ttu-id="b1581-334">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="b1581-336">`false`- uvolnění do OS</span><span class="sxs-lookup"><span data-stu-id="b1581-336">`false` - release to OS</span></span><br/><span data-ttu-id="b1581-337">`true`- v pohotovostním režimu</span><span class="sxs-lookup"><span data-stu-id="b1581-337">`true` - put on standby</span></span> | <span data-ttu-id="b1581-338">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-339">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="b1581-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="b1581-340">`false`- uvolnění do OS</span><span class="sxs-lookup"><span data-stu-id="b1581-340">`false` - release to OS</span></span><br/><span data-ttu-id="b1581-341">`true`- v pohotovostním režimu</span><span class="sxs-lookup"><span data-stu-id="b1581-341">`true` - put on standby</span></span> | <span data-ttu-id="b1581-342">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-343">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="b1581-344">`0`- uvolnění do OS</span><span class="sxs-lookup"><span data-stu-id="b1581-344">`0` - release to OS</span></span><br/><span data-ttu-id="b1581-345">`1`- v pohotovostním režimu</span><span class="sxs-lookup"><span data-stu-id="b1581-345">`1` - put on standby</span></span> | <span data-ttu-id="b1581-346">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="b1581-347">Příklady</span><span class="sxs-lookup"><span data-stu-id="b1581-347">Examples</span></span>

<span data-ttu-id="b1581-348">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="b1581-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="b1581-349">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="b1581-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="b1581-350">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="b1581-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="b1581-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="b1581-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="b1581-352">Určuje, zda mají být velké stránky použity při nastavení pevného limitu haldy.</span><span class="sxs-lookup"><span data-stu-id="b1581-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="b1581-353">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="b1581-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="b1581-354">Toto je experimentální prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="b1581-355">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-355">Setting name</span></span> | <span data-ttu-id="b1581-356">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-356">Values</span></span> | <span data-ttu-id="b1581-357">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="b1581-359">–</span><span class="sxs-lookup"><span data-stu-id="b1581-359">N/A</span></span> | <span data-ttu-id="b1581-360">–</span><span class="sxs-lookup"><span data-stu-id="b1581-360">N/A</span></span> | <span data-ttu-id="b1581-361">–</span><span class="sxs-lookup"><span data-stu-id="b1581-361">N/A</span></span> |
| <span data-ttu-id="b1581-362">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="b1581-363">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="b1581-363">`0` - disabled</span></span><br/><span data-ttu-id="b1581-364">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="b1581-364">`1` - enabled</span></span> | <span data-ttu-id="b1581-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1581-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="b1581-366">Velké objekty</span><span class="sxs-lookup"><span data-stu-id="b1581-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="b1581-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="b1581-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="b1581-368">Konfiguruje podporu systému uvolňování paměti na 64bitových platformách pro pole větší než 2 gigabajty (GB) v celkové velikosti.</span><span class="sxs-lookup"><span data-stu-id="b1581-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="b1581-369">Výchozí hodnota:`1`Povoleno ( ).</span><span class="sxs-lookup"><span data-stu-id="b1581-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="b1581-370">Tato možnost může být v budoucí verzi rozhraní .NET zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b1581-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="b1581-371">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-371">Setting name</span></span> | <span data-ttu-id="b1581-372">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-372">Values</span></span> | <span data-ttu-id="b1581-373">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="b1581-375">–</span><span class="sxs-lookup"><span data-stu-id="b1581-375">N/A</span></span> | <span data-ttu-id="b1581-376">–</span><span class="sxs-lookup"><span data-stu-id="b1581-376">N/A</span></span> | <span data-ttu-id="b1581-377">–</span><span class="sxs-lookup"><span data-stu-id="b1581-377">N/A</span></span> |
| <span data-ttu-id="b1581-378">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="b1581-379">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="b1581-379">`1` - enabled</span></span><br/> <span data-ttu-id="b1581-380">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="b1581-380">`0` - disabled</span></span> | <span data-ttu-id="b1581-381">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-382">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-383">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="b1581-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="b1581-384">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="b1581-384">`1` - enabled</span></span><br/> <span data-ttu-id="b1581-385">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="b1581-385">`0` - disabled</span></span> | <span data-ttu-id="b1581-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b1581-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="b1581-387">Prahová hodnota haldy velkého objektu</span><span class="sxs-lookup"><span data-stu-id="b1581-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="b1581-388">System.GC.LOHPrahová hodnota/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="b1581-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="b1581-389">Určuje velikost prahu v bajtů, která způsobí, že objekty přejít na haldy velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="b1581-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="b1581-390">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b1581-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="b1581-391">Zadaná hodnota musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="b1581-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="b1581-392">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-392">Setting name</span></span> | <span data-ttu-id="b1581-393">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-393">Values</span></span> | <span data-ttu-id="b1581-394">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="b1581-396">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-396">*decimal value*</span></span> | <span data-ttu-id="b1581-397">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-398">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="b1581-399">*šestnáctková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-399">*hexadecimal value*</span></span> | <span data-ttu-id="b1581-400">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b1581-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="b1581-401">**app.config pro rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b1581-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b1581-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="b1581-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="b1581-403">*desítková hodnota*</span><span class="sxs-lookup"><span data-stu-id="b1581-403">*decimal value*</span></span> | <span data-ttu-id="b1581-404"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b1581-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="b1581-405">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1581-405">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="b1581-406">Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b1581-407">Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1581-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b1581-408">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="b1581-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="b1581-409">Samostatný GC</span><span class="sxs-lookup"><span data-stu-id="b1581-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="b1581-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="b1581-410">COMPlus_GCName</span></span>

- <span data-ttu-id="b1581-411">Určuje cestu ke knihovně obsahující systém uvolňování paměti, který má za můe být načíst.</span><span class="sxs-lookup"><span data-stu-id="b1581-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="b1581-412">Další informace naleznete [v tématu Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="b1581-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="b1581-413">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="b1581-413">Setting name</span></span> | <span data-ttu-id="b1581-414">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="b1581-414">Values</span></span> | <span data-ttu-id="b1581-415">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b1581-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b1581-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b1581-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="b1581-417">–</span><span class="sxs-lookup"><span data-stu-id="b1581-417">N/A</span></span> | <span data-ttu-id="b1581-418">–</span><span class="sxs-lookup"><span data-stu-id="b1581-418">N/A</span></span> | <span data-ttu-id="b1581-419">–</span><span class="sxs-lookup"><span data-stu-id="b1581-419">N/A</span></span> |
| <span data-ttu-id="b1581-420">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="b1581-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="b1581-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="b1581-421">*string_path*</span></span> | <span data-ttu-id="b1581-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b1581-422">.NET Core 2.0</span></span> |
