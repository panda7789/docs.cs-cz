---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: d7e3d040cd634eeb020beff806c60f834cc02585
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761977"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="57573-103">Možnosti konfigurace běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="57573-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="57573-104">Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="57573-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="57573-105">Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="57573-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="57573-106">Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="57573-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="57573-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="57573-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="57573-108">Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.</span><span class="sxs-lookup"><span data-stu-id="57573-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="57573-109">Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="57573-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="57573-110">Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="57573-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="57573-111">Tato nastavení jsou vynechána na této stránce.</span><span class="sxs-lookup"><span data-stu-id="57573-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="57573-112">Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig. JSON* a hexadecimální zápis pro nastavení proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="57573-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="57573-113">U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="57573-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="57573-114">Charakter uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="57573-114">Flavors of garbage collection</span></span>

<span data-ttu-id="57573-115">Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="57573-116">Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu věnovaném [pracovní stanici a uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="57573-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="57573-117">Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.</span><span class="sxs-lookup"><span data-stu-id="57573-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="57573-118">Pro výběr charakteru uvolňování paměti použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="57573-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="57573-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="57573-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="57573-120">Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="57573-121">Výchozí: shromažďování paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="57573-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="57573-122">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="57573-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="57573-123">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-123">Setting name</span></span> | <span data-ttu-id="57573-124">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-124">Values</span></span> | <span data-ttu-id="57573-125">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="57573-127">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="57573-127">`false` - workstation</span></span><br/><span data-ttu-id="57573-128">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="57573-128">`true` - server</span></span> | <span data-ttu-id="57573-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-130">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="57573-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="57573-131">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="57573-131">`false` - workstation</span></span><br/><span data-ttu-id="57573-132">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="57573-132">`true` - server</span></span> | <span data-ttu-id="57573-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-134">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="57573-135">`0`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="57573-135">`0` - workstation</span></span><br/><span data-ttu-id="57573-136">`1`– Server</span><span class="sxs-lookup"><span data-stu-id="57573-136">`1` - server</span></span> | <span data-ttu-id="57573-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-138">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="57573-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="57573-140">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="57573-140">`false` - workstation</span></span><br/><span data-ttu-id="57573-141">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="57573-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="57573-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="57573-142">Examples</span></span>

<span data-ttu-id="57573-143">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="57573-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="57573-144">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="57573-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="57573-145">System. GC. souběžné/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="57573-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="57573-146">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).</span><span class="sxs-lookup"><span data-stu-id="57573-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="57573-147">Výchozí: použít GC na pozadí.</span><span class="sxs-lookup"><span data-stu-id="57573-147">Default: Use background GC.</span></span> <span data-ttu-id="57573-148">To je ekvivalentní nastavení hodnoty na `true` .</span><span class="sxs-lookup"><span data-stu-id="57573-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="57573-149">Další informace najdete v tématu [uvolňování paměti na pozadí](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="57573-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="57573-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-150">Setting name</span></span> | <span data-ttu-id="57573-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-151">Values</span></span> | <span data-ttu-id="57573-152">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="57573-154">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="57573-154">`true` - background GC</span></span><br/><span data-ttu-id="57573-155">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="57573-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="57573-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-157">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="57573-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="57573-158">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="57573-158">`true` - background GC</span></span><br/><span data-ttu-id="57573-159">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="57573-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="57573-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-161">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="57573-162">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="57573-162">`true` - background GC</span></span><br/><span data-ttu-id="57573-163">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="57573-163">`false` - non-concurrent GC</span></span> | <span data-ttu-id="57573-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-165">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="57573-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="57573-167">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="57573-167">`true` - background GC</span></span><br/><span data-ttu-id="57573-168">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="57573-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="57573-169">Příklady</span><span class="sxs-lookup"><span data-stu-id="57573-169">Examples</span></span>

<span data-ttu-id="57573-170">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="57573-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="57573-171">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="57573-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="57573-172">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="57573-172">Manage resource usage</span></span>

<span data-ttu-id="57573-173">Pomocí nastavení popsaných v této části můžete spravovat paměť a využití procesoru systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="57573-174">Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="57573-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="57573-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="57573-176">Omezuje počet hald vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="57573-177">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="57573-178">Je-li povoleno [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) , což je výchozí nastavení, počet haldy spřáhne `n` haldy GC/vlákna na první `n` procesor.</span><span class="sxs-lookup"><span data-stu-id="57573-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="57573-179">(K určení přesně těch procesorů, které mají spřažení, použijte nastavení [Maska spřažení](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) nebo [rozsahy spřažení](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) .)</span><span class="sxs-lookup"><span data-stu-id="57573-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="57573-180">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, toto nastavení omezuje počet hald GC.</span><span class="sxs-lookup"><span data-stu-id="57573-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="57573-181">Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="57573-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="57573-182">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-182">Setting name</span></span> | <span data-ttu-id="57573-183">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-183">Values</span></span> | <span data-ttu-id="57573-184">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="57573-186">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-186">*decimal value*</span></span> | <span data-ttu-id="57573-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-188">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="57573-189">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-189">*hexadecimal value*</span></span> | <span data-ttu-id="57573-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-191">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="57573-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="57573-193">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-193">*decimal value*</span></span> | <span data-ttu-id="57573-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="57573-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="57573-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-195">Example:</span></span>

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
> <span data-ttu-id="57573-196">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="57573-197">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="57573-198">Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="57573-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="57573-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="57573-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="57573-200">Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="57573-201">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="57573-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="57573-202">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="57573-203">Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="57573-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="57573-204">Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="57573-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="57573-205">Určuje, že se má používat prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="57573-206">Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="57573-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="57573-207">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-207">Setting name</span></span> | <span data-ttu-id="57573-208">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-208">Values</span></span> | <span data-ttu-id="57573-209">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="57573-211">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-211">*decimal value*</span></span> | <span data-ttu-id="57573-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-213">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="57573-214">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-214">*hexadecimal value*</span></span> | <span data-ttu-id="57573-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-216">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="57573-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="57573-218">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-218">*decimal value*</span></span> | <span data-ttu-id="57573-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="57573-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="57573-220">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="57573-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="57573-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="57573-222">Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="57573-223">Toto nastavení je podobné jako [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)s tím rozdílem, že umožňuje zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="57573-224">V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.</span><span class="sxs-lookup"><span data-stu-id="57573-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="57573-225">Pokud je [spřažení procesoru GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="57573-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="57573-226">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="57573-227">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="57573-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="57573-228">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-228">Setting name</span></span> | <span data-ttu-id="57573-229">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-229">Values</span></span> | <span data-ttu-id="57573-230">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="57573-232">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="57573-233">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="57573-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="57573-234">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="57573-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="57573-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-236">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="57573-237">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="57573-238">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="57573-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="57573-239">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="57573-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="57573-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-240">.NET Core 3.0</span></span> |

<span data-ttu-id="57573-241">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="57573-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="57573-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="57573-243">Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.</span><span class="sxs-lookup"><span data-stu-id="57573-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="57573-244">Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU.</span><span class="sxs-lookup"><span data-stu-id="57573-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="57573-245">Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.</span><span class="sxs-lookup"><span data-stu-id="57573-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="57573-246">Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="57573-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="57573-247">Výchozí: GC se nerozšiřuje mezi skupiny PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="57573-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="57573-248">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="57573-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="57573-249">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="57573-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="57573-250">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-250">Setting name</span></span> | <span data-ttu-id="57573-251">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-251">Values</span></span> | <span data-ttu-id="57573-252">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="57573-254">–</span><span class="sxs-lookup"><span data-stu-id="57573-254">N/A</span></span> | <span data-ttu-id="57573-255">–</span><span class="sxs-lookup"><span data-stu-id="57573-255">N/A</span></span> | <span data-ttu-id="57573-256">–</span><span class="sxs-lookup"><span data-stu-id="57573-256">N/A</span></span> |
| <span data-ttu-id="57573-257">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="57573-258">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="57573-258">`0` - disabled</span></span><br/><span data-ttu-id="57573-259">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="57573-259">`1` - enabled</span></span> | <span data-ttu-id="57573-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-261">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="57573-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="57573-263">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="57573-263">`false` - disabled</span></span><br/><span data-ttu-id="57573-264">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="57573-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="57573-265">Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="57573-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="57573-266">U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty `COMPlus_Thread_UseAllCpuGroups` proměnné prostředí na `1` .</span><span class="sxs-lookup"><span data-stu-id="57573-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="57573-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="57573-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="57573-268">Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="57573-269">Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru.</span><span class="sxs-lookup"><span data-stu-id="57573-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="57573-270">Pro každé vlákno GC se vytvoří halda.</span><span class="sxs-lookup"><span data-stu-id="57573-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="57573-271">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="57573-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="57573-272">Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="57573-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="57573-273">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="57573-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="57573-274">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-274">Setting name</span></span> | <span data-ttu-id="57573-275">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-275">Values</span></span> | <span data-ttu-id="57573-276">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="57573-278">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-278">`false` - affinitize</span></span><br/><span data-ttu-id="57573-279">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-279">`true` - don't affinitize</span></span> | <span data-ttu-id="57573-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-281">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="57573-282">`0`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-282">`0` - affinitize</span></span><br/><span data-ttu-id="57573-283">`1`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-283">`1` - don't affinitize</span></span> | <span data-ttu-id="57573-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-285">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="57573-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="57573-287">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-287">`false` - affinitize</span></span><br/><span data-ttu-id="57573-288">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="57573-288">`true` - don't affinitize</span></span> | <span data-ttu-id="57573-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="57573-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="57573-290">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="57573-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="57573-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="57573-292">Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.</span><span class="sxs-lookup"><span data-stu-id="57573-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="57573-293">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="57573-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="57573-294">Výchozí hodnota, která se vztahuje pouze na určité případy, je větší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="57573-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="57573-295">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="57573-295">The default value applies if:</span></span>

  - <span data-ttu-id="57573-296">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="57573-297">Není nastavený [System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) .</span><span class="sxs-lookup"><span data-stu-id="57573-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="57573-298">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-298">Setting name</span></span> | <span data-ttu-id="57573-299">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-299">Values</span></span> | <span data-ttu-id="57573-300">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="57573-302">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-302">*decimal value*</span></span> | <span data-ttu-id="57573-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-304">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="57573-305">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-305">*hexadecimal value*</span></span> | <span data-ttu-id="57573-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-306">.NET Core 3.0</span></span> |

<span data-ttu-id="57573-307">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-307">Example:</span></span>

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
> <span data-ttu-id="57573-308">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="57573-309">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="57573-310">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="57573-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="57573-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="57573-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="57573-312">Určuje povolené využití haldy GC jako procento z celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="57573-313">Pokud je nastavená taky možnost [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) , toto nastavení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="57573-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="57573-314">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="57573-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="57573-315">Pokud je proces spuštěný v kontejneru, který má zadanou mez paměti, vypočítá se procento jako procento tohoto limitu paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="57573-316">Výchozí hodnota, která se vztahuje pouze na určité případy, je menší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="57573-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="57573-317">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="57573-317">The default value applies if:</span></span>

  - <span data-ttu-id="57573-318">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="57573-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="57573-319">Není nastavený [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) .</span><span class="sxs-lookup"><span data-stu-id="57573-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="57573-320">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-320">Setting name</span></span> | <span data-ttu-id="57573-321">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-321">Values</span></span> | <span data-ttu-id="57573-322">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="57573-324">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-324">*decimal value*</span></span> | <span data-ttu-id="57573-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="57573-326">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="57573-327">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-327">*hexadecimal value*</span></span> | <span data-ttu-id="57573-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-328">.NET Core 3.0</span></span> |

<span data-ttu-id="57573-329">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-329">Example:</span></span>

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
> <span data-ttu-id="57573-330">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="57573-331">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="57573-332">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="57573-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="57573-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="57573-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="57573-334">Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="57573-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="57573-335">Výchozí: uvolnění segmentů verze zpátky do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="57573-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="57573-336">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="57573-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="57573-337">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-337">Setting name</span></span> | <span data-ttu-id="57573-338">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-338">Values</span></span> | <span data-ttu-id="57573-339">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="57573-341">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="57573-341">`false` - release to OS</span></span><br/><span data-ttu-id="57573-342">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="57573-342">`true` - put on standby</span></span> | <span data-ttu-id="57573-343">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-344">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="57573-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="57573-345">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="57573-345">`false` - release to OS</span></span><br/><span data-ttu-id="57573-346">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="57573-346">`true` - put on standby</span></span> | <span data-ttu-id="57573-347">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-348">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="57573-349">`0`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="57573-349">`0` - release to OS</span></span><br/><span data-ttu-id="57573-350">`1`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="57573-350">`1` - put on standby</span></span> | <span data-ttu-id="57573-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="57573-352">Příklady</span><span class="sxs-lookup"><span data-stu-id="57573-352">Examples</span></span>

<span data-ttu-id="57573-353">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="57573-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="57573-354">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="57573-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="57573-355">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="57573-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="57573-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="57573-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="57573-357">Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.</span><span class="sxs-lookup"><span data-stu-id="57573-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="57573-358">Výchozí: Nepoužívejte velké stránky, pokud je nastaven pevný limit haldy.</span><span class="sxs-lookup"><span data-stu-id="57573-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="57573-359">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="57573-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="57573-360">Toto je experimentální nastavení.</span><span class="sxs-lookup"><span data-stu-id="57573-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="57573-361">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-361">Setting name</span></span> | <span data-ttu-id="57573-362">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-362">Values</span></span> | <span data-ttu-id="57573-363">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="57573-365">–</span><span class="sxs-lookup"><span data-stu-id="57573-365">N/A</span></span> | <span data-ttu-id="57573-366">–</span><span class="sxs-lookup"><span data-stu-id="57573-366">N/A</span></span> | <span data-ttu-id="57573-367">–</span><span class="sxs-lookup"><span data-stu-id="57573-367">N/A</span></span> |
| <span data-ttu-id="57573-368">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="57573-369">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="57573-369">`0` - disabled</span></span><br/><span data-ttu-id="57573-370">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="57573-370">`1` - enabled</span></span> | <span data-ttu-id="57573-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57573-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="57573-372">Velké objekty</span><span class="sxs-lookup"><span data-stu-id="57573-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="57573-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="57573-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="57573-374">Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="57573-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="57573-375">Výchozí: GC podporuje pole větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="57573-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="57573-376">To je ekvivalentní nastavení hodnoty na `1` .</span><span class="sxs-lookup"><span data-stu-id="57573-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="57573-377">Tato možnost může být zastaralá v budoucí verzi .NET.</span><span class="sxs-lookup"><span data-stu-id="57573-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="57573-378">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-378">Setting name</span></span> | <span data-ttu-id="57573-379">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-379">Values</span></span> | <span data-ttu-id="57573-380">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="57573-382">–</span><span class="sxs-lookup"><span data-stu-id="57573-382">N/A</span></span> | <span data-ttu-id="57573-383">–</span><span class="sxs-lookup"><span data-stu-id="57573-383">N/A</span></span> | <span data-ttu-id="57573-384">–</span><span class="sxs-lookup"><span data-stu-id="57573-384">N/A</span></span> |
| <span data-ttu-id="57573-385">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="57573-386">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="57573-386">`1` - enabled</span></span><br/> <span data-ttu-id="57573-387">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="57573-387">`0` - disabled</span></span> | <span data-ttu-id="57573-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-389">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="57573-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="57573-391">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="57573-391">`1` - enabled</span></span><br/> <span data-ttu-id="57573-392">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="57573-392">`0` - disabled</span></span> | <span data-ttu-id="57573-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="57573-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="57573-394">Prahová hodnota haldy velkých objektů</span><span class="sxs-lookup"><span data-stu-id="57573-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="57573-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="57573-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="57573-396">Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="57573-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="57573-397">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="57573-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="57573-398">Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="57573-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="57573-399">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-399">Setting name</span></span> | <span data-ttu-id="57573-400">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-400">Values</span></span> | <span data-ttu-id="57573-401">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="57573-403">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-403">*decimal value*</span></span> | <span data-ttu-id="57573-404">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-405">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="57573-406">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-406">*hexadecimal value*</span></span> | <span data-ttu-id="57573-407">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="57573-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="57573-408">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="57573-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="57573-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="57573-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="57573-410">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="57573-410">*decimal value*</span></span> | <span data-ttu-id="57573-411"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="57573-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="57573-412">Příklad:</span><span class="sxs-lookup"><span data-stu-id="57573-412">Example:</span></span>

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
> <span data-ttu-id="57573-413">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="57573-414">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57573-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="57573-415">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="57573-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="57573-416">Samostatná GC</span><span class="sxs-lookup"><span data-stu-id="57573-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="57573-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="57573-417">COMPlus_GCName</span></span>

- <span data-ttu-id="57573-418">Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.</span><span class="sxs-lookup"><span data-stu-id="57573-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="57573-419">Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="57573-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="57573-420">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="57573-420">Setting name</span></span> | <span data-ttu-id="57573-421">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="57573-421">Values</span></span> | <span data-ttu-id="57573-422">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57573-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="57573-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="57573-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="57573-424">–</span><span class="sxs-lookup"><span data-stu-id="57573-424">N/A</span></span> | <span data-ttu-id="57573-425">–</span><span class="sxs-lookup"><span data-stu-id="57573-425">N/A</span></span> | <span data-ttu-id="57573-426">–</span><span class="sxs-lookup"><span data-stu-id="57573-426">N/A</span></span> |
| <span data-ttu-id="57573-427">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="57573-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="57573-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="57573-428">*string_path*</span></span> | <span data-ttu-id="57573-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="57573-429">.NET Core 2.0</span></span> |
