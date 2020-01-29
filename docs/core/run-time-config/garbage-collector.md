---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733515"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="686e9-103">Možnosti konfigurace běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="686e9-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="686e9-104">Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="686e9-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="686e9-105">Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="686e9-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="686e9-106">Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="686e9-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="686e9-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="686e9-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="686e9-108">Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.</span><span class="sxs-lookup"><span data-stu-id="686e9-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="686e9-109">Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="686e9-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="686e9-110">Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="686e9-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="686e9-111">Tato nastavení jsou vynechána na této stránce.</span><span class="sxs-lookup"><span data-stu-id="686e9-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="686e9-112">Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig. JSON* a hexadecimální zápis pro nastavení proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="686e9-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="686e9-113">U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="686e9-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="686e9-114">Charakter uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="686e9-114">Flavors of garbage collection</span></span>

<span data-ttu-id="686e9-115">Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="686e9-116">Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="686e9-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="686e9-117">Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.</span><span class="sxs-lookup"><span data-stu-id="686e9-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="686e9-118">Pro výběr charakteru uvolňování paměti použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="686e9-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="686e9-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="686e9-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="686e9-120">Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="686e9-121">Výchozí: shromažďování paměti pracovní stanice (`false`).</span><span class="sxs-lookup"><span data-stu-id="686e9-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="686e9-122">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-122">Setting name</span></span> | <span data-ttu-id="686e9-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-123">Values</span></span> | <span data-ttu-id="686e9-124">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="686e9-126">`false` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="686e9-126">`false` - workstation</span></span><br/><span data-ttu-id="686e9-127">`true` – Server</span><span class="sxs-lookup"><span data-stu-id="686e9-127">`true` - server</span></span> | <span data-ttu-id="686e9-128">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-129">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="686e9-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="686e9-130">`false` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="686e9-130">`false` - workstation</span></span><br/><span data-ttu-id="686e9-131">`true` – Server</span><span class="sxs-lookup"><span data-stu-id="686e9-131">`true` - server</span></span> | <span data-ttu-id="686e9-132">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-133">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="686e9-134">`0` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="686e9-134">`0` - workstation</span></span><br/><span data-ttu-id="686e9-135">`1` – Server</span><span class="sxs-lookup"><span data-stu-id="686e9-135">`1` - server</span></span> | <span data-ttu-id="686e9-136">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-137">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="686e9-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="686e9-139">`false` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="686e9-139">`false` - workstation</span></span><br/><span data-ttu-id="686e9-140">`true` – Server</span><span class="sxs-lookup"><span data-stu-id="686e9-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="686e9-141">Příklady</span><span class="sxs-lookup"><span data-stu-id="686e9-141">Examples</span></span>

<span data-ttu-id="686e9-142">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="686e9-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="686e9-143">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="686e9-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="686e9-144">System. GC. souběžné/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="686e9-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="686e9-145">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).</span><span class="sxs-lookup"><span data-stu-id="686e9-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="686e9-146">Výchozí: povoleno (`true`).</span><span class="sxs-lookup"><span data-stu-id="686e9-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="686e9-147">Další informace najdete v tématu [kolekce uvolnění paměti na pozadí](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) a [uvolňování paměti serveru na pozadí](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="686e9-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="686e9-148">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-148">Setting name</span></span> | <span data-ttu-id="686e9-149">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-149">Values</span></span> | <span data-ttu-id="686e9-150">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-151">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="686e9-152">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="686e9-152">`true` - background GC</span></span><br/><span data-ttu-id="686e9-153">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="686e9-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="686e9-154">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-155">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="686e9-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="686e9-156">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="686e9-156">`true` - background GC</span></span><br/><span data-ttu-id="686e9-157">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="686e9-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="686e9-158">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-159">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="686e9-160">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="686e9-160">`true` - background GC</span></span><br/><span data-ttu-id="686e9-161">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="686e9-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="686e9-162">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-163">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="686e9-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="686e9-165">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="686e9-165">`true` - background GC</span></span><br/><span data-ttu-id="686e9-166">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="686e9-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="686e9-167">Příklady</span><span class="sxs-lookup"><span data-stu-id="686e9-167">Examples</span></span>

<span data-ttu-id="686e9-168">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="686e9-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="686e9-169">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="686e9-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="686e9-170">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="686e9-170">Manage resource usage</span></span>

<span data-ttu-id="686e9-171">Pomocí nastavení popsaných v této části můžete spravovat paměť a využití procesoru systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="686e9-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="686e9-172">Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="686e9-173">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="686e9-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="686e9-174">Omezuje počet hald vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="686e9-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="686e9-175">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="686e9-176">Je-li povoleno spřažení procesoru uvolňování paměti, což je výchozí nastavení počet haldy spřáhne `n` haldy GC nebo vlákna na první `n` procesory.</span><span class="sxs-lookup"><span data-stu-id="686e9-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="686e9-177">(K určení přesně těch procesorů, které mají spřažení, použijte nastavení maska spřažení nebo rozsahy spřažení.)</span><span class="sxs-lookup"><span data-stu-id="686e9-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="686e9-178">Pokud je spřažení procesoru GC zakázané, toto nastavení omezuje počet hald GC.</span><span class="sxs-lookup"><span data-stu-id="686e9-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="686e9-179">Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="686e9-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="686e9-180">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-180">Setting name</span></span> | <span data-ttu-id="686e9-181">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-181">Values</span></span> | <span data-ttu-id="686e9-182">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-183">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="686e9-184">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-184">*decimal value*</span></span> | <span data-ttu-id="686e9-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-186">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="686e9-187">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-187">*hexadecimal value*</span></span> | <span data-ttu-id="686e9-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-189">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="686e9-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="686e9-191">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-191">*decimal value*</span></span> | <span data-ttu-id="686e9-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="686e9-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="686e9-193">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-193">Example:</span></span>

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
> <span data-ttu-id="686e9-194">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="686e9-195">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="686e9-196">Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="686e9-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="686e9-197">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="686e9-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="686e9-198">Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="686e9-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="686e9-199">Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="686e9-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="686e9-200">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="686e9-201">Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="686e9-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="686e9-202">Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="686e9-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="686e9-203">Určuje, že se má používat prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="686e9-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="686e9-204">Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="686e9-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="686e9-205">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-205">Setting name</span></span> | <span data-ttu-id="686e9-206">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-206">Values</span></span> | <span data-ttu-id="686e9-207">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-208">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="686e9-209">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-209">*decimal value*</span></span> | <span data-ttu-id="686e9-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-211">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="686e9-212">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-212">*hexadecimal value*</span></span> | <span data-ttu-id="686e9-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-214">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="686e9-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="686e9-216">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-216">*decimal value*</span></span> | <span data-ttu-id="686e9-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="686e9-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="686e9-218">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="686e9-219">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="686e9-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="686e9-220">Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="686e9-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="686e9-221">Toto nastavení je podobné jako u `System.GC.HeapAffinitizeMask`, s výjimkou případů, kdy je možné zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="686e9-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="686e9-222">V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.</span><span class="sxs-lookup"><span data-stu-id="686e9-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="686e9-223">Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="686e9-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="686e9-224">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="686e9-225">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="686e9-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="686e9-226">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-226">Setting name</span></span> | <span data-ttu-id="686e9-227">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-227">Values</span></span> | <span data-ttu-id="686e9-228">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-229">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="686e9-230">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="686e9-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="686e9-231">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="686e9-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="686e9-232">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="686e9-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="686e9-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-234">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="686e9-235">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="686e9-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="686e9-236">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="686e9-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="686e9-237">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="686e9-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="686e9-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-238">.NET Core 3.0</span></span> |

<span data-ttu-id="686e9-239">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="686e9-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="686e9-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="686e9-241">Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.</span><span class="sxs-lookup"><span data-stu-id="686e9-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="686e9-242">Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU.</span><span class="sxs-lookup"><span data-stu-id="686e9-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="686e9-243">Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.</span><span class="sxs-lookup"><span data-stu-id="686e9-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="686e9-244">Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="686e9-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="686e9-245">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="686e9-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="686e9-246">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="686e9-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="686e9-247">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-247">Setting name</span></span> | <span data-ttu-id="686e9-248">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-248">Values</span></span> | <span data-ttu-id="686e9-249">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-250">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="686e9-251">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-251">N/A</span></span> | <span data-ttu-id="686e9-252">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-252">N/A</span></span> | <span data-ttu-id="686e9-253">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-253">N/A</span></span> |
| <span data-ttu-id="686e9-254">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="686e9-255">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="686e9-255">`0` - disabled</span></span><br/><span data-ttu-id="686e9-256">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="686e9-256">`1` - enabled</span></span> | <span data-ttu-id="686e9-257">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-258">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="686e9-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="686e9-260">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="686e9-260">`false` - disabled</span></span><br/><span data-ttu-id="686e9-261">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="686e9-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="686e9-262">Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="686e9-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="686e9-263">U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty proměnné prostředí `COMPlus_Thread_UseAllCpuGroups` na `1`.</span><span class="sxs-lookup"><span data-stu-id="686e9-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="686e9-264">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="686e9-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="686e9-265">Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="686e9-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="686e9-266">Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru.</span><span class="sxs-lookup"><span data-stu-id="686e9-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="686e9-267">Pro každé vlákno GC se vytvoří halda.</span><span class="sxs-lookup"><span data-stu-id="686e9-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="686e9-268">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="686e9-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="686e9-269">Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů (`false`).</span><span class="sxs-lookup"><span data-stu-id="686e9-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="686e9-270">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-270">Setting name</span></span> | <span data-ttu-id="686e9-271">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-271">Values</span></span> | <span data-ttu-id="686e9-272">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-273">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="686e9-274">`false` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-274">`false` - affinitize</span></span><br/><span data-ttu-id="686e9-275">`true` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-275">`true` - don't affinitize</span></span> | <span data-ttu-id="686e9-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-277">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="686e9-278">`0` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-278">`0` - affinitize</span></span><br/><span data-ttu-id="686e9-279">`1` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-279">`1` - don't affinitize</span></span> | <span data-ttu-id="686e9-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-281">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="686e9-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="686e9-283">`false` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-283">`false` - affinitize</span></span><br/><span data-ttu-id="686e9-284">`true` – spřažení</span><span class="sxs-lookup"><span data-stu-id="686e9-284">`true` - don't affinitize</span></span> | <span data-ttu-id="686e9-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="686e9-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="686e9-286">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="686e9-287">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="686e9-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="686e9-288">Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.</span><span class="sxs-lookup"><span data-stu-id="686e9-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="686e9-289">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-289">Setting name</span></span> | <span data-ttu-id="686e9-290">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-290">Values</span></span> | <span data-ttu-id="686e9-291">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-292">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="686e9-293">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-293">*decimal value*</span></span> | <span data-ttu-id="686e9-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-295">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="686e9-296">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-296">*hexadecimal value*</span></span> | <span data-ttu-id="686e9-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-297">.NET Core 3.0</span></span> |

<span data-ttu-id="686e9-298">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-298">Example:</span></span>

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
> <span data-ttu-id="686e9-299">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="686e9-300">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="686e9-301">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="686e9-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="686e9-302">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="686e9-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="686e9-303">Určuje využití haldy GC jako procento z celkové paměti.</span><span class="sxs-lookup"><span data-stu-id="686e9-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="686e9-304">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-304">Setting name</span></span> | <span data-ttu-id="686e9-305">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-305">Values</span></span> | <span data-ttu-id="686e9-306">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-307">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="686e9-308">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-308">*decimal value*</span></span> | <span data-ttu-id="686e9-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="686e9-310">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="686e9-311">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-311">*hexadecimal value*</span></span> | <span data-ttu-id="686e9-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-312">.NET Core 3.0</span></span> |

<span data-ttu-id="686e9-313">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-313">Example:</span></span>

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
> <span data-ttu-id="686e9-314">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="686e9-315">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="686e9-316">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="686e9-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="686e9-317">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="686e9-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="686e9-318">Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="686e9-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="686e9-319">Výchozí: segmenty verze zpět do operačního systému (`false`).</span><span class="sxs-lookup"><span data-stu-id="686e9-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="686e9-320">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-320">Setting name</span></span> | <span data-ttu-id="686e9-321">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-321">Values</span></span> | <span data-ttu-id="686e9-322">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="686e9-324">`false` – vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="686e9-324">`false` - release to OS</span></span><br/><span data-ttu-id="686e9-325">`true` – vložit do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="686e9-325">`true` - put on standby</span></span> | <span data-ttu-id="686e9-326">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-327">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="686e9-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="686e9-328">`false` – vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="686e9-328">`false` - release to OS</span></span><br/><span data-ttu-id="686e9-329">`true` – vložit do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="686e9-329">`true` - put on standby</span></span> | <span data-ttu-id="686e9-330">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-331">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="686e9-332">`0` – vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="686e9-332">`0` - release to OS</span></span><br/><span data-ttu-id="686e9-333">`1` – vložit do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="686e9-333">`1` - put on standby</span></span> | <span data-ttu-id="686e9-334">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="686e9-335">Příklady</span><span class="sxs-lookup"><span data-stu-id="686e9-335">Examples</span></span>

<span data-ttu-id="686e9-336">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="686e9-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="686e9-337">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="686e9-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="686e9-338">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="686e9-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="686e9-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="686e9-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="686e9-340">Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.</span><span class="sxs-lookup"><span data-stu-id="686e9-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="686e9-341">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="686e9-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="686e9-342">Toto je experimentální nastavení.</span><span class="sxs-lookup"><span data-stu-id="686e9-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="686e9-343">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-343">Setting name</span></span> | <span data-ttu-id="686e9-344">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-344">Values</span></span> | <span data-ttu-id="686e9-345">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-346">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="686e9-347">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-347">N/A</span></span> | <span data-ttu-id="686e9-348">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-348">N/A</span></span> | <span data-ttu-id="686e9-349">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-349">N/A</span></span> |
| <span data-ttu-id="686e9-350">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="686e9-351">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="686e9-351">`0` - disabled</span></span><br/><span data-ttu-id="686e9-352">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="686e9-352">`1` - enabled</span></span> | <span data-ttu-id="686e9-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="686e9-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="686e9-354">Velké objekty</span><span class="sxs-lookup"><span data-stu-id="686e9-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="686e9-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="686e9-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="686e9-356">Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="686e9-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="686e9-357">Výchozí: povoleno (`1`).</span><span class="sxs-lookup"><span data-stu-id="686e9-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="686e9-358">Tato možnost může být zastaralá v budoucí verzi .NET.</span><span class="sxs-lookup"><span data-stu-id="686e9-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="686e9-359">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-359">Setting name</span></span> | <span data-ttu-id="686e9-360">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-360">Values</span></span> | <span data-ttu-id="686e9-361">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-362">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="686e9-363">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-363">N/A</span></span> | <span data-ttu-id="686e9-364">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-364">N/A</span></span> | <span data-ttu-id="686e9-365">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-365">N/A</span></span> |
| <span data-ttu-id="686e9-366">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="686e9-367">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="686e9-367">`1` - enabled</span></span><br/> <span data-ttu-id="686e9-368">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="686e9-368">`0` - disabled</span></span> | <span data-ttu-id="686e9-369">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-370">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="686e9-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="686e9-372">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="686e9-372">`1` - enabled</span></span><br/> <span data-ttu-id="686e9-373">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="686e9-373">`0` - disabled</span></span> | <span data-ttu-id="686e9-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="686e9-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="686e9-375">Prahová hodnota haldy velkých objektů</span><span class="sxs-lookup"><span data-stu-id="686e9-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="686e9-376">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="686e9-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="686e9-377">Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="686e9-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="686e9-378">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="686e9-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="686e9-379">Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="686e9-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="686e9-380">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-380">Setting name</span></span> | <span data-ttu-id="686e9-381">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-381">Values</span></span> | <span data-ttu-id="686e9-382">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-383">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="686e9-384">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-384">*decimal value*</span></span> | <span data-ttu-id="686e9-385">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-386">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="686e9-387">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-387">*hexadecimal value*</span></span> | <span data-ttu-id="686e9-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="686e9-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="686e9-389">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="686e9-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="686e9-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="686e9-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="686e9-391">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="686e9-391">*decimal value*</span></span> | <span data-ttu-id="686e9-392">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="686e9-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="686e9-393">Příklad:</span><span class="sxs-lookup"><span data-stu-id="686e9-393">Example:</span></span>

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
> <span data-ttu-id="686e9-394">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="686e9-395">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686e9-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="686e9-396">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="686e9-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="686e9-397">Samostatná GC</span><span class="sxs-lookup"><span data-stu-id="686e9-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="686e9-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="686e9-398">COMPlus_GCName</span></span>

- <span data-ttu-id="686e9-399">Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.</span><span class="sxs-lookup"><span data-stu-id="686e9-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="686e9-400">Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="686e9-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="686e9-401">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="686e9-401">Setting name</span></span> | <span data-ttu-id="686e9-402">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="686e9-402">Values</span></span> | <span data-ttu-id="686e9-403">Představená verze</span><span class="sxs-lookup"><span data-stu-id="686e9-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="686e9-404">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="686e9-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="686e9-405">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-405">N/A</span></span> | <span data-ttu-id="686e9-406">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-406">N/A</span></span> | <span data-ttu-id="686e9-407">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="686e9-407">N/A</span></span> |
| <span data-ttu-id="686e9-408">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="686e9-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="686e9-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="686e9-409">*string_path*</span></span> | <span data-ttu-id="686e9-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="686e9-410">.NET Core 2.0</span></span> |
