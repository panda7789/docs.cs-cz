---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 91d155b638c7e69b3d2c0216266a7c0c0410db4c
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915985"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="5418b-103">Možnosti konfigurace běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="5418b-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="5418b-104">Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5418b-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="5418b-105">Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="5418b-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="5418b-106">Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="5418b-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="5418b-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="5418b-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="5418b-108">Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.</span><span class="sxs-lookup"><span data-stu-id="5418b-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5418b-109">Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="5418b-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="5418b-110">Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="5418b-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="5418b-111">Tato nastavení jsou vynechána na této stránce.</span><span class="sxs-lookup"><span data-stu-id="5418b-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="5418b-112">Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig.js* pro soubor a hexadecimální zápis pro nastavení proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="5418b-113">U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="5418b-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="5418b-114">Charakter uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="5418b-114">Flavors of garbage collection</span></span>

<span data-ttu-id="5418b-115">Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="5418b-116">Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu věnovaném [pracovní stanici a uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5418b-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="5418b-117">Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.</span><span class="sxs-lookup"><span data-stu-id="5418b-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="5418b-118">Pro výběr charakteru uvolňování paměti použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="5418b-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="5418b-119">Pracovní stanice vs. uvolňování paměti serveru</span><span class="sxs-lookup"><span data-stu-id="5418b-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="5418b-120">Uvolňování paměti pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="5418b-121">Pracovní stanice vs. Server</span><span class="sxs-lookup"><span data-stu-id="5418b-121">Workstation vs. server</span></span>

- <span data-ttu-id="5418b-122">Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="5418b-123">Výchozí: shromažďování paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="5418b-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="5418b-124">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="5418b-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5418b-125">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-125">Setting name</span></span> | <span data-ttu-id="5418b-126">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-126">Values</span></span> | <span data-ttu-id="5418b-127">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-128">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="5418b-129">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="5418b-129">`false` - workstation</span></span><br/><span data-ttu-id="5418b-130">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="5418b-130">`true` - server</span></span> | <span data-ttu-id="5418b-131">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-132">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5418b-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="5418b-133">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="5418b-133">`false` - workstation</span></span><br/><span data-ttu-id="5418b-134">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="5418b-134">`true` - server</span></span> | <span data-ttu-id="5418b-135">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-136">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="5418b-137">`0`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="5418b-137">`0` - workstation</span></span><br/><span data-ttu-id="5418b-138">`1`– Server</span><span class="sxs-lookup"><span data-stu-id="5418b-138">`1` - server</span></span> | <span data-ttu-id="5418b-139">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-140">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="5418b-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="5418b-142">`false`– pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="5418b-142">`false` - workstation</span></span><br/><span data-ttu-id="5418b-143">`true`– Server</span><span class="sxs-lookup"><span data-stu-id="5418b-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="5418b-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="5418b-144">Examples</span></span>

<span data-ttu-id="5418b-145">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="5418b-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="5418b-146">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="5418b-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="5418b-147">Uvolňování paměti pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-147">Background GC</span></span>

- <span data-ttu-id="5418b-148">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).</span><span class="sxs-lookup"><span data-stu-id="5418b-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="5418b-149">Výchozí: použít GC na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5418b-149">Default: Use background GC.</span></span> <span data-ttu-id="5418b-150">To je ekvivalentní nastavení hodnoty na `true` .</span><span class="sxs-lookup"><span data-stu-id="5418b-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="5418b-151">Další informace najdete v tématu [uvolňování paměti na pozadí](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5418b-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="5418b-152">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-152">Setting name</span></span> | <span data-ttu-id="5418b-153">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-153">Values</span></span> | <span data-ttu-id="5418b-154">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-155">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="5418b-156">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-156">`true` - background GC</span></span><br/><span data-ttu-id="5418b-157">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="5418b-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5418b-158">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-159">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5418b-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="5418b-160">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-160">`true` - background GC</span></span><br/><span data-ttu-id="5418b-161">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="5418b-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5418b-162">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-163">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="5418b-164">`1`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-164">`1` - background GC</span></span><br/><span data-ttu-id="5418b-165">`0`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="5418b-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="5418b-166">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-167">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5418b-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="5418b-169">`true`– GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="5418b-169">`true` - background GC</span></span><br/><span data-ttu-id="5418b-170">`false`– nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="5418b-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="5418b-171">Příklady</span><span class="sxs-lookup"><span data-stu-id="5418b-171">Examples</span></span>

<span data-ttu-id="5418b-172">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="5418b-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="5418b-173">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="5418b-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="5418b-174">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="5418b-174">Manage resource usage</span></span>

<span data-ttu-id="5418b-175">Pomocí následujících nastavení můžete spravovat paměť a využití procesoru systémem uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="5418b-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="5418b-176">Spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="5418b-177">Spřažení – maska</span><span class="sxs-lookup"><span data-stu-id="5418b-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="5418b-178">Spřažení rozsahy</span><span class="sxs-lookup"><span data-stu-id="5418b-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="5418b-179">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="5418b-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="5418b-180">Počet hald</span><span class="sxs-lookup"><span data-stu-id="5418b-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="5418b-181">Omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="5418b-182">Procento omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="5418b-183">Procentuální hodnota vysoké paměti</span><span class="sxs-lookup"><span data-stu-id="5418b-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="5418b-184">Omezení podle objektů a haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="5418b-185">Per – Object – počet procent omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="5418b-186">Zachovat virtuální počítač</span><span class="sxs-lookup"><span data-stu-id="5418b-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="5418b-187">Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="5418b-188">Počet hald</span><span class="sxs-lookup"><span data-stu-id="5418b-188">Heap count</span></span>

- <span data-ttu-id="5418b-189">Omezuje počet hald vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="5418b-190">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5418b-191">Je-li povoleno [spřažení procesoru GC](#affinitize) , což je výchozí nastavení, počet haldy spřáhne `n` haldy GC/vlákna na první `n` procesor.</span><span class="sxs-lookup"><span data-stu-id="5418b-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="5418b-192">(K určení přesně těch procesorů, které mají spřažení, použijte nastavení [Maska spřažení](#affinitize-mask) nebo [rozsahy spřažení](#affinitize-ranges) .)</span><span class="sxs-lookup"><span data-stu-id="5418b-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="5418b-193">Pokud je [spřažení procesoru GC](#affinitize) zakázané, toto nastavení omezuje počet hald GC.</span><span class="sxs-lookup"><span data-stu-id="5418b-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="5418b-194">Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="5418b-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="5418b-195">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-195">Setting name</span></span> | <span data-ttu-id="5418b-196">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-196">Values</span></span> | <span data-ttu-id="5418b-197">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-198">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="5418b-199">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-199">*decimal value*</span></span> | <span data-ttu-id="5418b-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-201">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="5418b-202">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-202">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-204">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="5418b-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="5418b-206">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-206">*decimal value*</span></span> | <span data-ttu-id="5418b-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5418b-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5418b-208">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-208">Example:</span></span>

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
> <span data-ttu-id="5418b-209">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-210">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-211">Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="5418b-212">Spřažení – maska</span><span class="sxs-lookup"><span data-stu-id="5418b-212">Affinitize mask</span></span>

- <span data-ttu-id="5418b-213">Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="5418b-214">Pokud je [spřažení procesoru GC](#affinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="5418b-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5418b-215">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5418b-216">Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="5418b-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="5418b-217">Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="5418b-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="5418b-218">Určuje, že se má používat prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="5418b-219">Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="5418b-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="5418b-220">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-220">Setting name</span></span> | <span data-ttu-id="5418b-221">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-221">Values</span></span> | <span data-ttu-id="5418b-222">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-223">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="5418b-224">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-224">*decimal value*</span></span> | <span data-ttu-id="5418b-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-226">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="5418b-227">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-227">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-229">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5418b-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="5418b-231">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-231">*decimal value*</span></span> | <span data-ttu-id="5418b-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5418b-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5418b-233">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="5418b-234">Spřažení rozsahy</span><span class="sxs-lookup"><span data-stu-id="5418b-234">Affinitize ranges</span></span>

- <span data-ttu-id="5418b-235">Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="5418b-236">Toto nastavení je podobné jako [System. GC. HeapAffinitizeMask](#affinitize-mask)s tím rozdílem, že umožňuje zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="5418b-237">V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.</span><span class="sxs-lookup"><span data-stu-id="5418b-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="5418b-238">Pokud je [spřažení procesoru GC](#affinitize) zakázané, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="5418b-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5418b-239">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5418b-240">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="5418b-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5418b-241">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-241">Setting name</span></span> | <span data-ttu-id="5418b-242">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-242">Values</span></span> | <span data-ttu-id="5418b-243">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-244">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="5418b-245">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5418b-246">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="5418b-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5418b-247">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="5418b-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5418b-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-249">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="5418b-250">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5418b-251">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="5418b-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5418b-252">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="5418b-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5418b-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-253">.NET Core 3.0</span></span> |

<span data-ttu-id="5418b-254">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="5418b-255">Skupiny PROCESORů</span><span class="sxs-lookup"><span data-stu-id="5418b-255">CPU groups</span></span>

- <span data-ttu-id="5418b-256">Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.</span><span class="sxs-lookup"><span data-stu-id="5418b-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="5418b-257">Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU.</span><span class="sxs-lookup"><span data-stu-id="5418b-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="5418b-258">Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.</span><span class="sxs-lookup"><span data-stu-id="5418b-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="5418b-259">Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="5418b-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="5418b-260">Výchozí: GC se nerozšiřuje mezi skupiny PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="5418b-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="5418b-261">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="5418b-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="5418b-262">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="5418b-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5418b-263">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-263">Setting name</span></span> | <span data-ttu-id="5418b-264">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-264">Values</span></span> | <span data-ttu-id="5418b-265">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-266">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="5418b-267">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-267">`0` - disabled</span></span><br/><span data-ttu-id="5418b-268">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-268">`1` - enabled</span></span> | <span data-ttu-id="5418b-269">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-269">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-270">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="5418b-271">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-271">`0` - disabled</span></span><br/><span data-ttu-id="5418b-272">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-272">`1` - enabled</span></span> | <span data-ttu-id="5418b-273">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-274">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="5418b-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="5418b-276">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-276">`false` - disabled</span></span><br/><span data-ttu-id="5418b-277">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="5418b-278">Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5418b-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="5418b-279">U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty `COMPlus_Thread_UseAllCpuGroups` proměnné prostředí na `1` .</span><span class="sxs-lookup"><span data-stu-id="5418b-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="5418b-280">Spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-280">Affinitize</span></span>

- <span data-ttu-id="5418b-281">Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="5418b-282">Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru.</span><span class="sxs-lookup"><span data-stu-id="5418b-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="5418b-283">Pro každé vlákno GC se vytvoří halda.</span><span class="sxs-lookup"><span data-stu-id="5418b-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="5418b-284">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5418b-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5418b-285">Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="5418b-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="5418b-286">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="5418b-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5418b-287">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-287">Setting name</span></span> | <span data-ttu-id="5418b-288">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-288">Values</span></span> | <span data-ttu-id="5418b-289">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-290">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="5418b-291">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-291">`false` - affinitize</span></span><br/><span data-ttu-id="5418b-292">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-292">`true` - don't affinitize</span></span> | <span data-ttu-id="5418b-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-294">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="5418b-295">`0`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-295">`0` - affinitize</span></span><br/><span data-ttu-id="5418b-296">`1`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-296">`1` - don't affinitize</span></span> | <span data-ttu-id="5418b-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-298">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5418b-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="5418b-300">`false`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-300">`false` - affinitize</span></span><br/><span data-ttu-id="5418b-301">`true`– spřažení</span><span class="sxs-lookup"><span data-stu-id="5418b-301">`true` - don't affinitize</span></span> | <span data-ttu-id="5418b-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5418b-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5418b-303">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="5418b-304">Omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-304">Heap limit</span></span>

- <span data-ttu-id="5418b-305">Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.</span><span class="sxs-lookup"><span data-stu-id="5418b-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="5418b-306">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="5418b-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5418b-307">Toto nastavení se ignoruje, pokud jsou nakonfigurované [limity haldy pro jednotlivé objekty](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="5418b-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="5418b-308">Výchozí hodnota, která se vztahuje pouze na určité případy, je větší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5418b-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5418b-309">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="5418b-309">The default value applies if:</span></span>

  - <span data-ttu-id="5418b-310">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5418b-311">Není nastavený [System. GC. HeapHardLimitPercent](#heap-limit-percent) .</span><span class="sxs-lookup"><span data-stu-id="5418b-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="5418b-312">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-312">Setting name</span></span> | <span data-ttu-id="5418b-313">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-313">Values</span></span> | <span data-ttu-id="5418b-314">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-315">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="5418b-316">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-316">*decimal value*</span></span> | <span data-ttu-id="5418b-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-318">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="5418b-319">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-319">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-320">.NET Core 3.0</span></span> |

<span data-ttu-id="5418b-321">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-321">Example:</span></span>

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
> <span data-ttu-id="5418b-322">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-323">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-324">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="5418b-325">Procento omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-325">Heap limit percent</span></span>

- <span data-ttu-id="5418b-326">Určuje povolené využití haldy GC jako procento z celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="5418b-327">Pokud je nastavená taky možnost [System. GC. HeapHardLimit](#heap-limit) , toto nastavení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="5418b-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="5418b-328">Toto nastavení platí pouze pro 64 počítačů.</span><span class="sxs-lookup"><span data-stu-id="5418b-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5418b-329">Pokud je proces spuštěný v kontejneru, který má zadanou mez paměti, vypočítá se procento jako procento tohoto limitu paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="5418b-330">Toto nastavení se ignoruje, pokud jsou nakonfigurované [limity haldy pro jednotlivé objekty](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="5418b-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="5418b-331">Výchozí hodnota, která se vztahuje pouze na určité případy, je menší než 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5418b-331">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5418b-332">Výchozí hodnota platí v případě:</span><span class="sxs-lookup"><span data-stu-id="5418b-332">The default value applies if:</span></span>

  - <span data-ttu-id="5418b-333">Proces je spuštěný v kontejneru, který má zadané omezení paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5418b-334">Není nastavený [System. GC. HeapHardLimit](#heap-limit) .</span><span class="sxs-lookup"><span data-stu-id="5418b-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="5418b-335">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-335">Setting name</span></span> | <span data-ttu-id="5418b-336">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-336">Values</span></span> | <span data-ttu-id="5418b-337">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-338">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="5418b-339">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-339">*decimal value*</span></span> | <span data-ttu-id="5418b-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="5418b-341">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="5418b-342">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-342">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-343">.NET Core 3.0</span></span> |

<span data-ttu-id="5418b-344">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-344">Example:</span></span>

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
> <span data-ttu-id="5418b-345">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-346">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-347">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="5418b-348">Omezení podle objektů a haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-348">Per-object-heap limits</span></span>

<span data-ttu-id="5418b-349">Můžete určit možné využití haldy GC na bázi haldy pro jednotlivé objekty.</span><span class="sxs-lookup"><span data-stu-id="5418b-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="5418b-350">Mezi různé haldy patří halda velkých objektů (LOH), halda malých objektů (SOH) a halda připnutých objektů (POH).</span><span class="sxs-lookup"><span data-stu-id="5418b-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="5418b-351">Pokud zadáte hodnotu pro jakékoli `COMPLUS_GCHeapHardLimitSOH` nastavení, nebo, `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` musíte zadat také hodnotu pro `COMPLUS_GCHeapHardLimitSOH` a `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="5418b-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="5418b-352">Pokud to neuděláte, modul runtime se nepodaří inicializovat.</span><span class="sxs-lookup"><span data-stu-id="5418b-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="5418b-353">Výchozí hodnota pro `COMPLUS_GCHeapHardLimitPOH` je 0.</span><span class="sxs-lookup"><span data-stu-id="5418b-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="5418b-354">`COMPLUS_GCHeapHardLimitSOH`a `COMPLUS_GCHeapHardLimitLOH` nemají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5418b-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="5418b-355">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-355">Setting name</span></span> | <span data-ttu-id="5418b-356">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-356">Values</span></span> | <span data-ttu-id="5418b-357">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-358">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="5418b-359">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-359">*decimal value*</span></span> | <span data-ttu-id="5418b-360">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-360">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-361">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="5418b-362">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-362">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-363">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-363">.NET 5.0</span></span> |

| | <span data-ttu-id="5418b-364">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-364">Setting name</span></span> | <span data-ttu-id="5418b-365">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-365">Values</span></span> | <span data-ttu-id="5418b-366">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-367">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="5418b-368">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-368">*decimal value*</span></span> | <span data-ttu-id="5418b-369">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-369">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-370">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="5418b-371">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-371">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-372">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-372">.NET 5.0</span></span> |

| | <span data-ttu-id="5418b-373">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-373">Setting name</span></span> | <span data-ttu-id="5418b-374">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-374">Values</span></span> | <span data-ttu-id="5418b-375">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-376">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="5418b-377">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-377">*decimal value*</span></span> | <span data-ttu-id="5418b-378">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-378">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-379">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="5418b-380">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-380">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-381">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="5418b-382">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-383">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-384">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="5418b-385">Per – Object – počet procent omezení haldy</span><span class="sxs-lookup"><span data-stu-id="5418b-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="5418b-386">Můžete určit možné využití haldy GC na bázi haldy pro jednotlivé objekty.</span><span class="sxs-lookup"><span data-stu-id="5418b-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="5418b-387">Mezi různé haldy patří halda velkých objektů (LOH), halda malých objektů (SOH) a halda připnutých objektů (POH).</span><span class="sxs-lookup"><span data-stu-id="5418b-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="5418b-388">Pokud zadáte hodnotu pro jakékoli `COMPLUS_GCHeapHardLimitSOHPercent` nastavení, nebo, `COMPLUS_GCHeapHardLimitLOHPercent` `COMPLUS_GCHeapHardLimitPOHPercent` musíte zadat také hodnotu pro `COMPLUS_GCHeapHardLimitSOHPercent` a `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="5418b-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="5418b-389">Pokud to neuděláte, modul runtime se nepodaří inicializovat.</span><span class="sxs-lookup"><span data-stu-id="5418b-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="5418b-390">Tato nastavení budou ignorována `COMPLUS_GCHeapHardLimitSOH` , pokud `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` jsou zadány, a.</span><span class="sxs-lookup"><span data-stu-id="5418b-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="5418b-391">Hodnota 1 znamená, že GC používá pro haldu objektu 1% celkové fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="5418b-392">Každá hodnota musí být větší než 0 a menší než 100.</span><span class="sxs-lookup"><span data-stu-id="5418b-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="5418b-393">Kromě toho součet tří procentuálních hodnot musí být menší než 100.</span><span class="sxs-lookup"><span data-stu-id="5418b-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="5418b-394">V opačném případě se inicializace modulu runtime nezdaří.</span><span class="sxs-lookup"><span data-stu-id="5418b-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="5418b-395">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-395">Setting name</span></span> | <span data-ttu-id="5418b-396">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-396">Values</span></span> | <span data-ttu-id="5418b-397">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-398">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="5418b-399">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-399">*decimal value*</span></span> | <span data-ttu-id="5418b-400">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-400">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-401">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="5418b-402">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-402">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-403">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-403">.NET 5.0</span></span> |

| | <span data-ttu-id="5418b-404">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-404">Setting name</span></span> | <span data-ttu-id="5418b-405">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-405">Values</span></span> | <span data-ttu-id="5418b-406">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-407">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="5418b-408">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-408">*decimal value*</span></span> | <span data-ttu-id="5418b-409">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-409">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-410">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="5418b-411">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-411">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-412">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-412">.NET 5.0</span></span> |

| | <span data-ttu-id="5418b-413">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-413">Setting name</span></span> | <span data-ttu-id="5418b-414">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-414">Values</span></span> | <span data-ttu-id="5418b-415">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-416">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="5418b-417">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-417">*decimal value*</span></span> | <span data-ttu-id="5418b-418">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-418">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-419">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="5418b-420">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-420">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-421">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="5418b-422">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-423">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-424">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="5418b-425">Procentuální hodnota vysoké paměti</span><span class="sxs-lookup"><span data-stu-id="5418b-425">High memory percent</span></span>

<span data-ttu-id="5418b-426">Zatížení paměti je určeno procentuální hodnotou používané fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="5418b-427">Ve výchozím nastavení, když zatížení fyzické paměti dosáhne **90%**, uvolňování paměti se bude mnohem agresivní, aby se prováděly úplné komprimace uvolňování paměti, aby se zabránilo stránkování.</span><span class="sxs-lookup"><span data-stu-id="5418b-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="5418b-428">Když je zatížení paměti nižší než 90%, GC upřednostňuje kolekce na pozadí pro úplné uvolňování paměti, které mají kratší dobu pozastavení, ale neomezují celkovou velikost haldy.</span><span class="sxs-lookup"><span data-stu-id="5418b-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="5418b-429">V počítačích s významnou velikostí paměti (80 GB a více) je výchozí prahová hodnota zatížení mezi 90% a 97%.</span><span class="sxs-lookup"><span data-stu-id="5418b-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="5418b-430">Mezní hodnotu vysokého zatížení paměti lze upravit pomocí `COMPlus_GCHighMemPercent` proměnné prostředí nebo `System.GC.HighMemoryPercent` nastavení konfigurace JSON.</span><span class="sxs-lookup"><span data-stu-id="5418b-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="5418b-431">Pokud chcete řídit velikost haldy, zvažte úpravu prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5418b-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="5418b-432">Například pro dominantní proces na počítači, který má 64 GB paměti, je vhodné, aby se v modulu GC spouštěla práce, když je k dispozici 10% paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="5418b-433">U menších procesů například proces, který spotřebovává jenom 1 GB paměti, může GC pohodlně běžet s méně než 10% dostupné paměti.</span><span class="sxs-lookup"><span data-stu-id="5418b-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="5418b-434">U těchto menších procesů zvažte nastavení prahové hodnoty vyšší.</span><span class="sxs-lookup"><span data-stu-id="5418b-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="5418b-435">Na druhou stranu platí, že pokud chcete, aby větší procesy měly menší velikosti haldy (i když je k dispozici dostatek fyzické paměti), je snížení této prahové hodnoty účinný způsob, jak může GC před komprimací haldy reagovat.</span><span class="sxs-lookup"><span data-stu-id="5418b-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="5418b-436">V případě procesů spuštěných v kontejneru se GC považuje za fyzickou paměť na základě limitu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5418b-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="5418b-437">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-437">Setting name</span></span> | <span data-ttu-id="5418b-438">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-438">Values</span></span> | <span data-ttu-id="5418b-439">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-440">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="5418b-441">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-441">*decimal value*</span></span> | <span data-ttu-id="5418b-442">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5418b-442">.NET 5.0</span></span> |
| <span data-ttu-id="5418b-443">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="5418b-444">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="5418b-445">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-446">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-447">Chcete-li například nastavit mezní hodnotu vysoké paměti na 75%, hodnoty by byly 75 pro soubor JSON a 0x4B nebo 4B pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="5418b-448">Zachovat virtuální počítač</span><span class="sxs-lookup"><span data-stu-id="5418b-448">Retain VM</span></span>

- <span data-ttu-id="5418b-449">Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="5418b-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="5418b-450">Výchozí: uvolnění segmentů verze zpátky do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5418b-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="5418b-451">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="5418b-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5418b-452">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-452">Setting name</span></span> | <span data-ttu-id="5418b-453">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-453">Values</span></span> | <span data-ttu-id="5418b-454">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-455">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="5418b-456">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="5418b-456">`false` - release to OS</span></span><br/><span data-ttu-id="5418b-457">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="5418b-457">`true` - put on standby</span></span> | <span data-ttu-id="5418b-458">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-459">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5418b-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="5418b-460">`false`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="5418b-460">`false` - release to OS</span></span><br/><span data-ttu-id="5418b-461">`true`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="5418b-461">`true` - put on standby</span></span> | <span data-ttu-id="5418b-462">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-463">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="5418b-464">`0`– vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="5418b-464">`0` - release to OS</span></span><br/><span data-ttu-id="5418b-465">`1`– Put do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="5418b-465">`1` - put on standby</span></span> | <span data-ttu-id="5418b-466">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="5418b-467">Příklady</span><span class="sxs-lookup"><span data-stu-id="5418b-467">Examples</span></span>

<span data-ttu-id="5418b-468">*runtimeconfig.jsv* souboru:</span><span class="sxs-lookup"><span data-stu-id="5418b-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="5418b-469">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="5418b-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="5418b-470">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="5418b-470">Large pages</span></span>

- <span data-ttu-id="5418b-471">Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.</span><span class="sxs-lookup"><span data-stu-id="5418b-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="5418b-472">Výchozí: Nepoužívejte velké stránky, pokud je nastaven pevný limit haldy.</span><span class="sxs-lookup"><span data-stu-id="5418b-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="5418b-473">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="5418b-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="5418b-474">Toto je experimentální nastavení.</span><span class="sxs-lookup"><span data-stu-id="5418b-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="5418b-475">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-475">Setting name</span></span> | <span data-ttu-id="5418b-476">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-476">Values</span></span> | <span data-ttu-id="5418b-477">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-478">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="5418b-479">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-479">N/A</span></span> | <span data-ttu-id="5418b-480">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-480">N/A</span></span> | <span data-ttu-id="5418b-481">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-481">N/A</span></span> |
| <span data-ttu-id="5418b-482">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="5418b-483">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-483">`0` - disabled</span></span><br/><span data-ttu-id="5418b-484">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-484">`1` - enabled</span></span> | <span data-ttu-id="5418b-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5418b-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="5418b-486">Povolení velkých objektů</span><span class="sxs-lookup"><span data-stu-id="5418b-486">Allow large objects</span></span>

- <span data-ttu-id="5418b-487">Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="5418b-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="5418b-488">Výchozí: GC podporuje pole větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5418b-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="5418b-489">To je ekvivalentní nastavení hodnoty na `1` .</span><span class="sxs-lookup"><span data-stu-id="5418b-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="5418b-490">Tato možnost může být zastaralá v budoucí verzi .NET.</span><span class="sxs-lookup"><span data-stu-id="5418b-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="5418b-491">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-491">Setting name</span></span> | <span data-ttu-id="5418b-492">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-492">Values</span></span> | <span data-ttu-id="5418b-493">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-494">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="5418b-495">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-495">N/A</span></span> | <span data-ttu-id="5418b-496">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-496">N/A</span></span> | <span data-ttu-id="5418b-497">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-497">N/A</span></span> |
| <span data-ttu-id="5418b-498">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="5418b-499">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-499">`1` - enabled</span></span><br/> <span data-ttu-id="5418b-500">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-500">`0` - disabled</span></span> | <span data-ttu-id="5418b-501">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-502">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-503">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="5418b-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="5418b-504">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="5418b-504">`1` - enabled</span></span><br/> <span data-ttu-id="5418b-505">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="5418b-505">`0` - disabled</span></span> | <span data-ttu-id="5418b-506">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5418b-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="5418b-507">Prahová hodnota haldy velkých objektů</span><span class="sxs-lookup"><span data-stu-id="5418b-507">Large object heap threshold</span></span>

- <span data-ttu-id="5418b-508">Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="5418b-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="5418b-509">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5418b-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="5418b-510">Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="5418b-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="5418b-511">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-511">Setting name</span></span> | <span data-ttu-id="5418b-512">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-512">Values</span></span> | <span data-ttu-id="5418b-513">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-514">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="5418b-515">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-515">*decimal value*</span></span> | <span data-ttu-id="5418b-516">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-517">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="5418b-518">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-518">*hexadecimal value*</span></span> | <span data-ttu-id="5418b-519">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5418b-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="5418b-520">**app.config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5418b-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5418b-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="5418b-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="5418b-522">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="5418b-522">*decimal value*</span></span> | <span data-ttu-id="5418b-523"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="5418b-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="5418b-524">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5418b-524">Example:</span></span>

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
> <span data-ttu-id="5418b-525">Pokud nastavujete možnost v *runtimeconfig.jszapnuto*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5418b-526">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5418b-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5418b-527">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="5418b-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="5418b-528">Samostatná GC</span><span class="sxs-lookup"><span data-stu-id="5418b-528">Standalone GC</span></span>

- <span data-ttu-id="5418b-529">Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.</span><span class="sxs-lookup"><span data-stu-id="5418b-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="5418b-530">Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="5418b-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="5418b-531">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="5418b-531">Setting name</span></span> | <span data-ttu-id="5418b-532">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="5418b-532">Values</span></span> | <span data-ttu-id="5418b-533">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5418b-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5418b-534">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="5418b-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="5418b-535">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-535">N/A</span></span> | <span data-ttu-id="5418b-536">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-536">N/A</span></span> | <span data-ttu-id="5418b-537">N/A</span><span class="sxs-lookup"><span data-stu-id="5418b-537">N/A</span></span> |
| <span data-ttu-id="5418b-538">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="5418b-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="5418b-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="5418b-539">*string_path*</span></span> | <span data-ttu-id="5418b-540">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5418b-540">.NET Core 2.0</span></span> |
