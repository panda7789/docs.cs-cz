---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441401"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="e26db-103">Možnosti konfigurace běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="e26db-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="e26db-104">Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e26db-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="e26db-105">Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="e26db-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="e26db-106">Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="e26db-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="e26db-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="e26db-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="e26db-108">Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.</span><span class="sxs-lookup"><span data-stu-id="e26db-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e26db-109">Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="e26db-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="e26db-110">Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="e26db-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="e26db-111">Tato nastavení jsou vynechána na této stránce.</span><span class="sxs-lookup"><span data-stu-id="e26db-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="e26db-112">Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig.js* pro soubor a hexadecimální zápis pro nastavení proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="e26db-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="e26db-113">U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="e26db-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="e26db-114">Charakter uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="e26db-114">Flavors of garbage collection</span></span>

<span data-ttu-id="e26db-115">Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="e26db-116">Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu věnovaném [pracovní stanici a uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="e26db-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="e26db-117">Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.</span><span class="sxs-lookup"><span data-stu-id="e26db-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="e26db-118">Pro výběr charakteru uvolňování paměti použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="e26db-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="e26db-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="e26db-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="e26db-120">Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="e26db-121">Výchozí: shromažďování paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="e26db-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="e26db-122">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="e26db-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e26db-123">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-123">Setting name</span></span> | <span data-ttu-id="e26db-124">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-124">Values</span></span> | <span data-ttu-id="e26db-125">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-126">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="e26db-127">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="e26db-127">`false` - workstation</span></span><br/><span data-ttu-id="e26db-128">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="e26db-128">`true` - server</span></span> | <span data-ttu-id="e26db-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-130">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e26db-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="e26db-131">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="e26db-131">`false` - workstation</span></span><br/><span data-ttu-id="e26db-132">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="e26db-132">`true` - server</span></span> | <span data-ttu-id="e26db-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-134">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="e26db-135">`0`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="e26db-135">`0` - workstation</span></span><br/><span data-ttu-id="e26db-136">`1`– Server</span><span class="sxs-lookup"><span data-stu-id="e26db-136">`1` - server</span></span> | <span data-ttu-id="e26db-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-138">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="e26db-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="e26db-140">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="e26db-140">`false` - workstation</span></span><br/><span data-ttu-id="e26db-141">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="e26db-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e26db-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="e26db-142">Examples</span></span>

<span data-ttu-id="e26db-143">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="e26db-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="e26db-144">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="e26db-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="e26db-145">System. GC. souběžné/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e26db-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="e26db-146">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).</span><span class="sxs-lookup"><span data-stu-id="e26db-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="e26db-147">Výchozí: použít GC na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e26db-147">Default: Use background GC.</span></span> <span data-ttu-id="e26db-148">To je ekvivalentní nastavení hodnoty na `true` .</span><span class="sxs-lookup"><span data-stu-id="e26db-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="e26db-149">Další informace najdete v tématu [uvolňování paměti na pozadí](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="e26db-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="e26db-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-150">Setting name</span></span> | <span data-ttu-id="e26db-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-151">Values</span></span> | <span data-ttu-id="e26db-152">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-153">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="e26db-154">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="e26db-154">`true` - background GC</span></span><br/><span data-ttu-id="e26db-155">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="e26db-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e26db-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-157">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e26db-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="e26db-158">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="e26db-158">`true` - background GC</span></span><br/><span data-ttu-id="e26db-159">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="e26db-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e26db-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-161">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="e26db-162">`1`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="e26db-162">`1` - background GC</span></span><br/><span data-ttu-id="e26db-163">`0`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="e26db-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="e26db-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-165">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e26db-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="e26db-167">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="e26db-167">`true` - background GC</span></span><br/><span data-ttu-id="e26db-168">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="e26db-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e26db-169">Příklady</span><span class="sxs-lookup"><span data-stu-id="e26db-169">Examples</span></span>

<span data-ttu-id="e26db-170">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="e26db-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="e26db-171">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="e26db-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="e26db-172">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="e26db-172">Manage resource usage</span></span>

<span data-ttu-id="e26db-173">Pomocí nastavení popsaných v této části můžete spravovat paměť a využití procesoru systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="e26db-174">Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="e26db-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e26db-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="e26db-176">Omezuje počet hald vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="e26db-177">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e26db-178">Je-li povoleno [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) , což je výchozí nastavení, počet haldy spřáhne `n` haldy GC/vlákna na první `n` procesor.</span><span class="sxs-lookup"><span data-stu-id="e26db-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="e26db-179">(K určení přesně těch procesorů, které mají spřažení, použijte nastavení [Maska spřažení](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) nebo [rozsahy spřažení](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) .)</span><span class="sxs-lookup"><span data-stu-id="e26db-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="e26db-180">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, toto nastavení omezuje počet hald GC.</span><span class="sxs-lookup"><span data-stu-id="e26db-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="e26db-181">Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="e26db-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="e26db-182">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-182">Setting name</span></span> | <span data-ttu-id="e26db-183">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-183">Values</span></span> | <span data-ttu-id="e26db-184">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-185">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="e26db-186">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-186">*decimal value*</span></span> | <span data-ttu-id="e26db-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-188">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="e26db-189">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-189">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-191">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e26db-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="e26db-193">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-193">*decimal value*</span></span> | <span data-ttu-id="e26db-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e26db-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e26db-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-195">Example:</span></span>

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
> <span data-ttu-id="e26db-196">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e26db-197">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-198">Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e26db-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="e26db-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e26db-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="e26db-200">Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="e26db-201">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="e26db-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="e26db-202">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e26db-203">Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="e26db-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="e26db-204">Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="e26db-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="e26db-205">Určuje, že se má používat prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="e26db-206">Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="e26db-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="e26db-207">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-207">Setting name</span></span> | <span data-ttu-id="e26db-208">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-208">Values</span></span> | <span data-ttu-id="e26db-209">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-210">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="e26db-211">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-211">*decimal value*</span></span> | <span data-ttu-id="e26db-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-213">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="e26db-214">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-214">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-216">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e26db-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="e26db-218">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-218">*decimal value*</span></span> | <span data-ttu-id="e26db-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e26db-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e26db-220">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="e26db-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="e26db-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="e26db-222">Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="e26db-223">Toto nastavení je podobné jako [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)s tím rozdílem, že umožňuje zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="e26db-224">V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.</span><span class="sxs-lookup"><span data-stu-id="e26db-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="e26db-225">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="e26db-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="e26db-226">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e26db-227">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="e26db-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e26db-228">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-228">Setting name</span></span> | <span data-ttu-id="e26db-229">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-229">Values</span></span> | <span data-ttu-id="e26db-230">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-231">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="e26db-232">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e26db-233">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e26db-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e26db-234">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e26db-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e26db-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-236">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="e26db-237">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e26db-238">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e26db-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e26db-239">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e26db-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e26db-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-240">.NET Core 3.0</span></span> |

<span data-ttu-id="e26db-241">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="e26db-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e26db-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="e26db-243">Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.</span><span class="sxs-lookup"><span data-stu-id="e26db-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="e26db-244">Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU.</span><span class="sxs-lookup"><span data-stu-id="e26db-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="e26db-245">Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.</span><span class="sxs-lookup"><span data-stu-id="e26db-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="e26db-246">Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="e26db-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="e26db-247">Výchozí: GC se nerozšiřuje mezi skupiny PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="e26db-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="e26db-248">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="e26db-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="e26db-249">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="e26db-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e26db-250">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-250">Setting name</span></span> | <span data-ttu-id="e26db-251">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-251">Values</span></span> | <span data-ttu-id="e26db-252">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-253">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="e26db-254">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-254">N/A</span></span> | <span data-ttu-id="e26db-255">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-255">N/A</span></span> | <span data-ttu-id="e26db-256">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-256">N/A</span></span> |
| <span data-ttu-id="e26db-257">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="e26db-258">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="e26db-258">`0` - disabled</span></span><br/><span data-ttu-id="e26db-259">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="e26db-259">`1` - enabled</span></span> | <span data-ttu-id="e26db-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-261">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e26db-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="e26db-263">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="e26db-263">`false` - disabled</span></span><br/><span data-ttu-id="e26db-264">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="e26db-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="e26db-265">Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e26db-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="e26db-266">U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty `COMPlus_Thread_UseAllCpuGroups` proměnné prostředí na `1` .</span><span class="sxs-lookup"><span data-stu-id="e26db-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="e26db-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e26db-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="e26db-268">Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="e26db-269">Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru.</span><span class="sxs-lookup"><span data-stu-id="e26db-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="e26db-270">Pro každé vlákno GC se vytvoří halda.</span><span class="sxs-lookup"><span data-stu-id="e26db-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="e26db-271">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="e26db-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e26db-272">Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="e26db-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="e26db-273">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="e26db-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e26db-274">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-274">Setting name</span></span> | <span data-ttu-id="e26db-275">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-275">Values</span></span> | <span data-ttu-id="e26db-276">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-277">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="e26db-278">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-278">`false` - affinitize</span></span><br/><span data-ttu-id="e26db-279">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-279">`true` - don't affinitize</span></span> | <span data-ttu-id="e26db-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-281">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="e26db-282">`0`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-282">`0` - affinitize</span></span><br/><span data-ttu-id="e26db-283">`1`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-283">`1` - don't affinitize</span></span> | <span data-ttu-id="e26db-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-285">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e26db-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="e26db-287">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-287">`false` - affinitize</span></span><br/><span data-ttu-id="e26db-288">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="e26db-288">`true` - don't affinitize</span></span> | <span data-ttu-id="e26db-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e26db-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e26db-290">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="e26db-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="e26db-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="e26db-292">Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.</span><span class="sxs-lookup"><span data-stu-id="e26db-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="e26db-293">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="e26db-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="e26db-294">Toto nastavení se ignoruje, pokud jsou nakonfigurované [limity haldy pro jednotlivé objekty](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="e26db-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="e26db-295">Výchozí hodnota, která se vztahuje pouze na určité případy, je větší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e26db-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="e26db-296">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="e26db-296">The default value applies if:</span></span>

  - <span data-ttu-id="e26db-297">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="e26db-298">Není nastavený [System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) .</span><span class="sxs-lookup"><span data-stu-id="e26db-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="e26db-299">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-299">Setting name</span></span> | <span data-ttu-id="e26db-300">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-300">Values</span></span> | <span data-ttu-id="e26db-301">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-302">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="e26db-303">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-303">*decimal value*</span></span> | <span data-ttu-id="e26db-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-305">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="e26db-306">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-306">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-307">.NET Core 3.0</span></span> |

<span data-ttu-id="e26db-308">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-308">Example:</span></span>

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
> <span data-ttu-id="e26db-309">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e26db-310">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-311">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e26db-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="e26db-312">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="e26db-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="e26db-313">Určuje povolené využití haldy GC jako procento z celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="e26db-314">Pokud je nastavená taky možnost [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) , toto nastavení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e26db-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="e26db-315">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="e26db-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="e26db-316">Pokud je proces spuštěný v kontejneru, který má zadanou mez paměti, vypočítá se procento jako procento tohoto limitu paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="e26db-317">Toto nastavení se ignoruje, pokud jsou nakonfigurované [limity haldy pro jednotlivé objekty](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="e26db-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="e26db-318">Výchozí hodnota, která se vztahuje pouze na určité případy, je menší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e26db-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="e26db-319">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="e26db-319">The default value applies if:</span></span>

  - <span data-ttu-id="e26db-320">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="e26db-321">Není nastavený [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) .</span><span class="sxs-lookup"><span data-stu-id="e26db-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="e26db-322">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-322">Setting name</span></span> | <span data-ttu-id="e26db-323">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-323">Values</span></span> | <span data-ttu-id="e26db-324">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-325">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="e26db-326">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-326">*decimal value*</span></span> | <span data-ttu-id="e26db-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="e26db-328">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="e26db-329">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-329">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-330">.NET Core 3.0</span></span> |

<span data-ttu-id="e26db-331">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-331">Example:</span></span>

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
> <span data-ttu-id="e26db-332">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e26db-333">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-334">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e26db-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="e26db-335">Omezení podle objektů a haldy</span><span class="sxs-lookup"><span data-stu-id="e26db-335">Per-object-heap limits</span></span>

<span data-ttu-id="e26db-336">Můžete určit možné využití haldy GC na bázi haldy pro jednotlivé objekty.</span><span class="sxs-lookup"><span data-stu-id="e26db-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="e26db-337">Mezi různé haldy patří halda velkých objektů (LOH), halda malých objektů (SOH) a halda připnutých objektů (POH).</span><span class="sxs-lookup"><span data-stu-id="e26db-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="e26db-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="e26db-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="e26db-339">Pokud zadáte hodnotu pro jakékoli `COMPLUS_GCHeapHardLimitSOH` nastavení, nebo, `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` musíte zadat také hodnotu pro `COMPLUS_GCHeapHardLimitSOH` a `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="e26db-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="e26db-340">Pokud to neuděláte, modul runtime se nepodaří inicializovat.</span><span class="sxs-lookup"><span data-stu-id="e26db-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="e26db-341">Výchozí hodnota pro `COMPLUS_GCHeapHardLimitPOH` je 0.</span><span class="sxs-lookup"><span data-stu-id="e26db-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="e26db-342">`COMPLUS_GCHeapHardLimitSOH`a `COMPLUS_GCHeapHardLimitLOH` nemají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e26db-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="e26db-343">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-343">Setting name</span></span> | <span data-ttu-id="e26db-344">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-344">Values</span></span> | <span data-ttu-id="e26db-345">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-346">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="e26db-347">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-347">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-348">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-348">.NET 5.0</span></span> |
| <span data-ttu-id="e26db-349">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="e26db-350">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-350">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-351">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-351">.NET 5.0</span></span> |
| <span data-ttu-id="e26db-352">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="e26db-353">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-353">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-354">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="e26db-355">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-356">Například pokud chcete zadat tvrdý limit haldy 200 mebibytes (MiB), hodnota by byla 0xC800000 nebo C800000.</span><span class="sxs-lookup"><span data-stu-id="e26db-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="e26db-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="e26db-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="e26db-358">Pokud zadáte hodnotu pro jakékoli `COMPLUS_GCHeapHardLimitSOHPercent` nastavení, nebo, `COMPLUS_GCHeapHardLimitLOHPercent` `COMPLUS_GCHeapHardLimitPOHPercent` musíte zadat také hodnotu pro `COMPLUS_GCHeapHardLimitSOHPercent` a `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="e26db-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="e26db-359">Pokud to neuděláte, modul runtime se nepodaří inicializovat.</span><span class="sxs-lookup"><span data-stu-id="e26db-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="e26db-360">Tato nastavení budou ignorována `COMPLUS_GCHeapHardLimitSOH` , pokud `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` jsou zadány, a.</span><span class="sxs-lookup"><span data-stu-id="e26db-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="e26db-361">Hodnota 1 znamená, že GC používá pro haldu objektu 1% celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="e26db-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="e26db-362">Každá hodnota musí být větší než 0 a menší než 100.</span><span class="sxs-lookup"><span data-stu-id="e26db-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="e26db-363">Kromě toho součet tří procentuálních hodnot musí být menší než 100.</span><span class="sxs-lookup"><span data-stu-id="e26db-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="e26db-364">V opačném případě se inicializace modulu runtime nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e26db-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="e26db-365">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-365">Setting name</span></span> | <span data-ttu-id="e26db-366">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-366">Values</span></span> | <span data-ttu-id="e26db-367">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-368">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="e26db-369">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-369">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-370">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-370">.NET 5.0</span></span> |
| <span data-ttu-id="e26db-371">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="e26db-372">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-372">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-373">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-373">.NET 5.0</span></span> |
| <span data-ttu-id="e26db-374">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="e26db-375">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-375">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-376">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e26db-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="e26db-377">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-378">Chcete-li například omezit využití haldy na 30%, hodnota by byla 0x1E nebo 1E.</span><span class="sxs-lookup"><span data-stu-id="e26db-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="e26db-379">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="e26db-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="e26db-380">Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="e26db-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="e26db-381">Výchozí: uvolnění segmentů verze zpátky do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e26db-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="e26db-382">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="e26db-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e26db-383">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-383">Setting name</span></span> | <span data-ttu-id="e26db-384">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-384">Values</span></span> | <span data-ttu-id="e26db-385">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-386">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="e26db-387">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="e26db-387">`false` - release to OS</span></span><br/><span data-ttu-id="e26db-388">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="e26db-388">`true` - put on standby</span></span> | <span data-ttu-id="e26db-389">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-390">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e26db-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="e26db-391">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="e26db-391">`false` - release to OS</span></span><br/><span data-ttu-id="e26db-392">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="e26db-392">`true` - put on standby</span></span> | <span data-ttu-id="e26db-393">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-394">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="e26db-395">`0`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="e26db-395">`0` - release to OS</span></span><br/><span data-ttu-id="e26db-396">`1`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="e26db-396">`1` - put on standby</span></span> | <span data-ttu-id="e26db-397">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="e26db-398">Příklady</span><span class="sxs-lookup"><span data-stu-id="e26db-398">Examples</span></span>

<span data-ttu-id="e26db-399">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="e26db-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="e26db-400">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="e26db-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="e26db-401">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="e26db-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="e26db-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="e26db-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="e26db-403">Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.</span><span class="sxs-lookup"><span data-stu-id="e26db-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="e26db-404">Výchozí: Nepoužívejte velké stránky, pokud je nastaven pevný limit haldy.</span><span class="sxs-lookup"><span data-stu-id="e26db-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="e26db-405">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="e26db-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="e26db-406">Toto je experimentální nastavení.</span><span class="sxs-lookup"><span data-stu-id="e26db-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="e26db-407">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-407">Setting name</span></span> | <span data-ttu-id="e26db-408">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-408">Values</span></span> | <span data-ttu-id="e26db-409">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-410">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="e26db-411">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-411">N/A</span></span> | <span data-ttu-id="e26db-412">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-412">N/A</span></span> | <span data-ttu-id="e26db-413">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-413">N/A</span></span> |
| <span data-ttu-id="e26db-414">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="e26db-415">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="e26db-415">`0` - disabled</span></span><br/><span data-ttu-id="e26db-416">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="e26db-416">`1` - enabled</span></span> | <span data-ttu-id="e26db-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e26db-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="e26db-418">Velké objekty</span><span class="sxs-lookup"><span data-stu-id="e26db-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="e26db-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e26db-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="e26db-420">Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="e26db-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="e26db-421">Výchozí: GC podporuje pole větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="e26db-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="e26db-422">To je ekvivalentní nastavení hodnoty na `1` .</span><span class="sxs-lookup"><span data-stu-id="e26db-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="e26db-423">Tato možnost může být zastaralá v budoucí verzi .NET.</span><span class="sxs-lookup"><span data-stu-id="e26db-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="e26db-424">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-424">Setting name</span></span> | <span data-ttu-id="e26db-425">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-425">Values</span></span> | <span data-ttu-id="e26db-426">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-427">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="e26db-428">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-428">N/A</span></span> | <span data-ttu-id="e26db-429">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-429">N/A</span></span> | <span data-ttu-id="e26db-430">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-430">N/A</span></span> |
| <span data-ttu-id="e26db-431">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="e26db-432">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="e26db-432">`1` - enabled</span></span><br/> <span data-ttu-id="e26db-433">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="e26db-433">`0` - disabled</span></span> | <span data-ttu-id="e26db-434">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-435">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-436">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e26db-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="e26db-437">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="e26db-437">`1` - enabled</span></span><br/> <span data-ttu-id="e26db-438">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="e26db-438">`0` - disabled</span></span> | <span data-ttu-id="e26db-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e26db-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="e26db-440">Prahová hodnota haldy velkých objektů</span><span class="sxs-lookup"><span data-stu-id="e26db-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="e26db-441">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e26db-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="e26db-442">Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="e26db-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="e26db-443">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e26db-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="e26db-444">Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="e26db-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="e26db-445">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-445">Setting name</span></span> | <span data-ttu-id="e26db-446">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-446">Values</span></span> | <span data-ttu-id="e26db-447">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-448">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="e26db-449">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-449">*decimal value*</span></span> | <span data-ttu-id="e26db-450">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-451">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="e26db-452">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-452">*hexadecimal value*</span></span> | <span data-ttu-id="e26db-453">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e26db-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="e26db-454">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e26db-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e26db-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e26db-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="e26db-456">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="e26db-456">*decimal value*</span></span> | <span data-ttu-id="e26db-457"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="e26db-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="e26db-458">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26db-458">Example:</span></span>

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
> <span data-ttu-id="e26db-459">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e26db-460">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e26db-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e26db-461">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e26db-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="e26db-462">Samostatná GC</span><span class="sxs-lookup"><span data-stu-id="e26db-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="e26db-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="e26db-463">COMPlus_GCName</span></span>

- <span data-ttu-id="e26db-464">Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.</span><span class="sxs-lookup"><span data-stu-id="e26db-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="e26db-465">Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e26db-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="e26db-466">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e26db-466">Setting name</span></span> | <span data-ttu-id="e26db-467">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e26db-467">Values</span></span> | <span data-ttu-id="e26db-468">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e26db-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e26db-469">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e26db-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="e26db-470">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-470">N/A</span></span> | <span data-ttu-id="e26db-471">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-471">N/A</span></span> | <span data-ttu-id="e26db-472">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="e26db-472">N/A</span></span> |
| <span data-ttu-id="e26db-473">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e26db-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="e26db-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="e26db-474">*string_path*</span></span> | <span data-ttu-id="e26db-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e26db-475">.NET Core 2.0</span></span> |
