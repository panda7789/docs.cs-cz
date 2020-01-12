---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900100"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="6db24-103">Možnosti konfigurace běhu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="6db24-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="6db24-104">Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6db24-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="6db24-105">Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="6db24-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="6db24-106">Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.</span><span class="sxs-lookup"><span data-stu-id="6db24-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="6db24-107">Nastavení jsou uspořádána do skupin na této stránce.</span><span class="sxs-lookup"><span data-stu-id="6db24-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="6db24-108">Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.</span><span class="sxs-lookup"><span data-stu-id="6db24-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="6db24-109">Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.</span><span class="sxs-lookup"><span data-stu-id="6db24-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="6db24-110">Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="6db24-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="6db24-111">Tato nastavení jsou vynechána na této stránce.</span><span class="sxs-lookup"><span data-stu-id="6db24-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="6db24-112">Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig. JSON* a hexadecimální zápis pro nastavení proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="6db24-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="6db24-113">U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.</span><span class="sxs-lookup"><span data-stu-id="6db24-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="6db24-114">Charakter uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="6db24-114">Flavors of garbage collection</span></span>

<span data-ttu-id="6db24-115">Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="6db24-116">Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="6db24-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="6db24-117">Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.</span><span class="sxs-lookup"><span data-stu-id="6db24-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="6db24-118">Pro výběr charakteru uvolňování paměti použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="6db24-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="6db24-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="6db24-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="6db24-120">Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="6db24-121">Výchozí: shromažďování paměti pracovní stanice (`false`).</span><span class="sxs-lookup"><span data-stu-id="6db24-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="6db24-122">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-122">Setting name</span></span> | <span data-ttu-id="6db24-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-123">Values</span></span> | <span data-ttu-id="6db24-124">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="6db24-126">`false` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="6db24-126">`false` - workstation</span></span><br/><span data-ttu-id="6db24-127">`true` – Server</span><span class="sxs-lookup"><span data-stu-id="6db24-127">`true` - server</span></span> | <span data-ttu-id="6db24-128">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-129">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="6db24-130">`0` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="6db24-130">`0` - workstation</span></span><br/><span data-ttu-id="6db24-131">`1` – Server</span><span class="sxs-lookup"><span data-stu-id="6db24-131">`1` - server</span></span> | <span data-ttu-id="6db24-132">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-133">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="6db24-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="6db24-135">`false` – pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="6db24-135">`false` - workstation</span></span><br/><span data-ttu-id="6db24-136">`true` – Server</span><span class="sxs-lookup"><span data-stu-id="6db24-136">`true` - server</span></span> |  |

<span data-ttu-id="6db24-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="6db24-138">System. GC. souběžné/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="6db24-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="6db24-139">Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).</span><span class="sxs-lookup"><span data-stu-id="6db24-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="6db24-140">Výchozí: povoleno (`true`).</span><span class="sxs-lookup"><span data-stu-id="6db24-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="6db24-141">Další informace najdete v tématu [kolekce uvolnění paměti na pozadí](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) a [uvolňování paměti serveru na pozadí](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="6db24-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="6db24-142">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-142">Setting name</span></span> | <span data-ttu-id="6db24-143">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-143">Values</span></span> | <span data-ttu-id="6db24-144">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-145">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="6db24-146">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="6db24-146">`true` - background GC</span></span><br/><span data-ttu-id="6db24-147">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="6db24-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="6db24-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-149">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="6db24-150">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="6db24-150">`true` - background GC</span></span><br/><span data-ttu-id="6db24-151">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="6db24-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="6db24-152">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-153">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="6db24-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="6db24-155">`true` – GC na pozadí</span><span class="sxs-lookup"><span data-stu-id="6db24-155">`true` - background GC</span></span><br/><span data-ttu-id="6db24-156">`false` – nesouběžný GC</span><span class="sxs-lookup"><span data-stu-id="6db24-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="6db24-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="6db24-158">Správa využití prostředků</span><span class="sxs-lookup"><span data-stu-id="6db24-158">Manage resource usage</span></span>

<span data-ttu-id="6db24-159">Pomocí nastavení popsaných v této části můžete spravovat paměť a využití procesoru systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6db24-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="6db24-160">Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="6db24-161">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="6db24-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="6db24-162">Omezuje počet hald vytvořených systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6db24-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="6db24-163">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="6db24-164">Je-li povoleno spřažení procesoru uvolňování paměti, což je výchozí nastavení počet haldy spřáhne `n` haldy GC nebo vlákna na první `n` procesory.</span><span class="sxs-lookup"><span data-stu-id="6db24-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="6db24-165">(K určení přesně těch procesorů, které mají spřažení, použijte nastavení maska spřažení nebo rozsahy spřažení.)</span><span class="sxs-lookup"><span data-stu-id="6db24-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="6db24-166">Pokud je spřažení procesoru GC zakázané, toto nastavení omezuje počet hald GC.</span><span class="sxs-lookup"><span data-stu-id="6db24-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="6db24-167">Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="6db24-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="6db24-168">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-168">Setting name</span></span> | <span data-ttu-id="6db24-169">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-169">Values</span></span> | <span data-ttu-id="6db24-170">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="6db24-172">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-172">*decimal value*</span></span> | <span data-ttu-id="6db24-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-174">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="6db24-175">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-175">*hexadecimal value*</span></span> | <span data-ttu-id="6db24-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-177">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="6db24-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="6db24-179">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-179">*decimal value*</span></span> | <span data-ttu-id="6db24-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6db24-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="6db24-181">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-181">Example:</span></span>

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
> <span data-ttu-id="6db24-182">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="6db24-183">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="6db24-184">Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="6db24-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="6db24-185">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="6db24-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="6db24-186">Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6db24-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="6db24-187">Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="6db24-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="6db24-188">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="6db24-189">Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="6db24-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="6db24-190">Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu.</span><span class="sxs-lookup"><span data-stu-id="6db24-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="6db24-191">Určuje, že se má používat prvních 10 procesorů.</span><span class="sxs-lookup"><span data-stu-id="6db24-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="6db24-192">Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="6db24-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="6db24-193">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-193">Setting name</span></span> | <span data-ttu-id="6db24-194">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-194">Values</span></span> | <span data-ttu-id="6db24-195">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-196">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="6db24-197">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-197">*decimal value*</span></span> | <span data-ttu-id="6db24-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-199">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="6db24-200">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-200">*hexadecimal value*</span></span> | <span data-ttu-id="6db24-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-202">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="6db24-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="6db24-204">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-204">*decimal value*</span></span> | <span data-ttu-id="6db24-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6db24-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="6db24-206">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="6db24-207">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="6db24-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="6db24-208">Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6db24-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="6db24-209">Toto nastavení je podobné jako u `System.GC.HeapAffinitizeMask`, s výjimkou případů, kdy je možné zadat více než 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="6db24-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="6db24-210">V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.</span><span class="sxs-lookup"><span data-stu-id="6db24-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="6db24-211">Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.</span><span class="sxs-lookup"><span data-stu-id="6db24-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="6db24-212">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="6db24-213">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="6db24-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="6db24-214">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-214">Setting name</span></span> | <span data-ttu-id="6db24-215">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-215">Values</span></span> | <span data-ttu-id="6db24-216">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-217">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="6db24-218">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="6db24-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="6db24-219">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="6db24-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="6db24-220">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="6db24-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="6db24-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-222">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="6db24-223">Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.</span><span class="sxs-lookup"><span data-stu-id="6db24-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="6db24-224">Příklad systému UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="6db24-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="6db24-225">Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="6db24-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="6db24-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-226">.NET Core 3.0</span></span> |

<span data-ttu-id="6db24-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="6db24-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="6db24-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="6db24-229">Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6db24-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="6db24-230">Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU.</span><span class="sxs-lookup"><span data-stu-id="6db24-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="6db24-231">Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.</span><span class="sxs-lookup"><span data-stu-id="6db24-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="6db24-232">Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="6db24-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="6db24-233">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="6db24-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="6db24-234">Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="6db24-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="6db24-235">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-235">Setting name</span></span> | <span data-ttu-id="6db24-236">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-236">Values</span></span> | <span data-ttu-id="6db24-237">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-238">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="6db24-239">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-239">N/A</span></span> | <span data-ttu-id="6db24-240">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-240">N/A</span></span> | <span data-ttu-id="6db24-241">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-241">N/A</span></span> |
| <span data-ttu-id="6db24-242">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="6db24-243">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="6db24-243">`0` - disabled</span></span><br/><span data-ttu-id="6db24-244">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="6db24-244">`1` - enabled</span></span> | <span data-ttu-id="6db24-245">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-246">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="6db24-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="6db24-248">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="6db24-248">`false` - disabled</span></span><br/><span data-ttu-id="6db24-249">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="6db24-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="6db24-250">Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6db24-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="6db24-251">U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty proměnné prostředí `COMPlus_Thread_UseAllCpuGroups` na `1`.</span><span class="sxs-lookup"><span data-stu-id="6db24-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="6db24-252">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="6db24-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="6db24-253">Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="6db24-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="6db24-254">Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru.</span><span class="sxs-lookup"><span data-stu-id="6db24-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="6db24-255">Pro každé vlákno GC se vytvoří halda.</span><span class="sxs-lookup"><span data-stu-id="6db24-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="6db24-256">Platí jenom pro shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6db24-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="6db24-257">Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů (`false`).</span><span class="sxs-lookup"><span data-stu-id="6db24-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="6db24-258">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-258">Setting name</span></span> | <span data-ttu-id="6db24-259">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-259">Values</span></span> | <span data-ttu-id="6db24-260">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-261">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="6db24-262">`false` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-262">`false` - affinitize</span></span><br/><span data-ttu-id="6db24-263">`true` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-263">`true` - don't affinitize</span></span> | <span data-ttu-id="6db24-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-265">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="6db24-266">`0` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-266">`0` - affinitize</span></span><br/><span data-ttu-id="6db24-267">`1` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-267">`1` - don't affinitize</span></span> | <span data-ttu-id="6db24-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-269">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="6db24-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="6db24-271">`false` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-271">`false` - affinitize</span></span><br/><span data-ttu-id="6db24-272">`true` – spřažení</span><span class="sxs-lookup"><span data-stu-id="6db24-272">`true` - don't affinitize</span></span> | <span data-ttu-id="6db24-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6db24-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="6db24-274">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="6db24-275">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="6db24-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="6db24-276">Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.</span><span class="sxs-lookup"><span data-stu-id="6db24-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="6db24-277">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-277">Setting name</span></span> | <span data-ttu-id="6db24-278">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-278">Values</span></span> | <span data-ttu-id="6db24-279">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-280">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="6db24-281">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-281">*decimal value*</span></span> | <span data-ttu-id="6db24-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-283">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="6db24-284">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-284">*hexadecimal value*</span></span> | <span data-ttu-id="6db24-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-285">.NET Core 3.0</span></span> |

<span data-ttu-id="6db24-286">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-286">Example:</span></span>

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
> <span data-ttu-id="6db24-287">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="6db24-288">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="6db24-289">Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="6db24-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="6db24-290">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="6db24-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="6db24-291">Určuje využití haldy GC jako procento z celkové paměti.</span><span class="sxs-lookup"><span data-stu-id="6db24-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="6db24-292">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-292">Setting name</span></span> | <span data-ttu-id="6db24-293">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-293">Values</span></span> | <span data-ttu-id="6db24-294">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-295">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="6db24-296">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-296">*decimal value*</span></span> | <span data-ttu-id="6db24-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="6db24-298">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="6db24-299">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-299">*hexadecimal value*</span></span> | <span data-ttu-id="6db24-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-300">.NET Core 3.0</span></span> |

<span data-ttu-id="6db24-301">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-301">Example:</span></span>

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
> <span data-ttu-id="6db24-302">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="6db24-303">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="6db24-304">Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="6db24-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="6db24-305">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="6db24-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="6db24-306">Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="6db24-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="6db24-307">Výchozí: segmenty verze zpět do operačního systému (`false`).</span><span class="sxs-lookup"><span data-stu-id="6db24-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="6db24-308">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-308">Setting name</span></span> | <span data-ttu-id="6db24-309">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-309">Values</span></span> | <span data-ttu-id="6db24-310">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-311">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="6db24-312">`false` – vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="6db24-312">`false` - release to OS</span></span><br/><span data-ttu-id="6db24-313">`true` – vložit do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="6db24-313">`true` - put on standby</span></span>| <span data-ttu-id="6db24-314">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-315">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="6db24-316">`0` – vydání na operační systém</span><span class="sxs-lookup"><span data-stu-id="6db24-316">`0` - release to OS</span></span><br/><span data-ttu-id="6db24-317">`1` – vložit do úsporného režimu</span><span class="sxs-lookup"><span data-stu-id="6db24-317">`1` - put on standby</span></span> | <span data-ttu-id="6db24-318">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-318">.NET Core 1.0</span></span> |

<span data-ttu-id="6db24-319">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="6db24-320">Velké stránky</span><span class="sxs-lookup"><span data-stu-id="6db24-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="6db24-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="6db24-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="6db24-322">Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.</span><span class="sxs-lookup"><span data-stu-id="6db24-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="6db24-323">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="6db24-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="6db24-324">Toto je experimentální nastavení.</span><span class="sxs-lookup"><span data-stu-id="6db24-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="6db24-325">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-325">Setting name</span></span> | <span data-ttu-id="6db24-326">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-326">Values</span></span> | <span data-ttu-id="6db24-327">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-328">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="6db24-329">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-329">N/A</span></span> | <span data-ttu-id="6db24-330">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-330">N/A</span></span> | <span data-ttu-id="6db24-331">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-331">N/A</span></span> |
| <span data-ttu-id="6db24-332">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="6db24-333">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="6db24-333">`0` - disabled</span></span><br/><span data-ttu-id="6db24-334">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="6db24-334">`1` - enabled</span></span> | <span data-ttu-id="6db24-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6db24-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="6db24-336">Velké objekty</span><span class="sxs-lookup"><span data-stu-id="6db24-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="6db24-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="6db24-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="6db24-338">Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="6db24-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="6db24-339">Výchozí: povoleno (`1`).</span><span class="sxs-lookup"><span data-stu-id="6db24-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="6db24-340">Tato možnost může být zastaralá v budoucí verzi .NET.</span><span class="sxs-lookup"><span data-stu-id="6db24-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="6db24-341">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-341">Setting name</span></span> | <span data-ttu-id="6db24-342">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-342">Values</span></span> | <span data-ttu-id="6db24-343">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-344">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="6db24-345">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-345">N/A</span></span> | <span data-ttu-id="6db24-346">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-346">N/A</span></span> | <span data-ttu-id="6db24-347">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-347">N/A</span></span> |
| <span data-ttu-id="6db24-348">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="6db24-349">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="6db24-349">`1` - enabled</span></span><br/> <span data-ttu-id="6db24-350">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="6db24-350">`0` - disabled</span></span> | <span data-ttu-id="6db24-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-352">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-353">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="6db24-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="6db24-354">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="6db24-354">`1` - enabled</span></span><br/> <span data-ttu-id="6db24-355">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="6db24-355">`0` - disabled</span></span> | <span data-ttu-id="6db24-356">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="6db24-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="6db24-357">Prahová hodnota haldy velkých objektů</span><span class="sxs-lookup"><span data-stu-id="6db24-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="6db24-358">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="6db24-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="6db24-359">Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="6db24-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="6db24-360">Výchozí prahová hodnota je 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="6db24-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="6db24-361">Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="6db24-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="6db24-362">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-362">Setting name</span></span> | <span data-ttu-id="6db24-363">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-363">Values</span></span> | <span data-ttu-id="6db24-364">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-365">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="6db24-366">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-366">*decimal value*</span></span> | <span data-ttu-id="6db24-367">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-368">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="6db24-369">*hexadecimální hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-369">*hexadecimal value*</span></span> | <span data-ttu-id="6db24-370">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6db24-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="6db24-371">**App. config pro .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="6db24-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="6db24-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="6db24-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="6db24-373">*desetinná hodnota*</span><span class="sxs-lookup"><span data-stu-id="6db24-373">*decimal value*</span></span> | <span data-ttu-id="6db24-374">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="6db24-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="6db24-375">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6db24-375">Example:</span></span>

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
> <span data-ttu-id="6db24-376">Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="6db24-377">Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6db24-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="6db24-378">Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="6db24-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="6db24-379">Samostatná GC</span><span class="sxs-lookup"><span data-stu-id="6db24-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="6db24-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="6db24-380">COMPlus_GCName</span></span>

- <span data-ttu-id="6db24-381">Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.</span><span class="sxs-lookup"><span data-stu-id="6db24-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="6db24-382">Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="6db24-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="6db24-383">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="6db24-383">Setting name</span></span> | <span data-ttu-id="6db24-384">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="6db24-384">Values</span></span> | <span data-ttu-id="6db24-385">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6db24-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="6db24-386">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6db24-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="6db24-387">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-387">N/A</span></span> | <span data-ttu-id="6db24-388">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-388">N/A</span></span> | <span data-ttu-id="6db24-389">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="6db24-389">N/A</span></span> |
| <span data-ttu-id="6db24-390">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="6db24-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="6db24-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="6db24-391">*string_path*</span></span> | <span data-ttu-id="6db24-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6db24-392">.NET Core 2.0</span></span> |
