---
title: Nastavení konfigurace kompilace
description: Přečtěte si o nastavení za běhu, které konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092886"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="2db4e-103">Možnosti konfigurace za běhu pro kompilaci</span><span class="sxs-lookup"><span data-stu-id="2db4e-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="2db4e-104">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="2db4e-104">Tiered compilation</span></span>

- <span data-ttu-id="2db4e-105">Konfiguruje, zda kompilátor just-in-time (JIT) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="2db4e-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="2db4e-106">Vrstvené metody přechodů kompilace prostřednictvím dvou úrovní:</span><span class="sxs-lookup"><span data-stu-id="2db4e-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="2db4e-107">První vrstva generuje kód rychleji[(rychlé JIT)](#quick-jit)nebo načte předkompilovaný kód[(ReadyToRun).](#readytorun)</span><span class="sxs-lookup"><span data-stu-id="2db4e-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="2db4e-108">Druhá vrstva generuje optimalizovaný kód na pozadí ("optimalizace JIT").</span><span class="sxs-lookup"><span data-stu-id="2db4e-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="2db4e-109">V rozhraní .NET Core 3.0 a novější je ve výchozím nastavení povolena vrstvená kompilace.</span><span class="sxs-lookup"><span data-stu-id="2db4e-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="2db4e-110">V rozhraních .NET Core 2.1 a 2.2 je vrstvená kompilace ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="2db4e-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="2db4e-111">Další informace naleznete v [průvodci vrstvenou kompilací](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="2db4e-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="2db4e-112">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2db4e-112">Setting name</span></span> | <span data-ttu-id="2db4e-113">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2db4e-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2db4e-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2db4e-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="2db4e-115">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-115">`true` - enabled</span></span><br/><span data-ttu-id="2db4e-116">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-116">`false` - disabled</span></span> |
| <span data-ttu-id="2db4e-117">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="2db4e-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="2db4e-118">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-118">`true` - enabled</span></span><br/><span data-ttu-id="2db4e-119">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-119">`false` - disabled</span></span> |
| <span data-ttu-id="2db4e-120">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2db4e-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="2db4e-121">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-121">`1` - enabled</span></span><br/><span data-ttu-id="2db4e-122">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="2db4e-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="2db4e-123">Examples</span></span>

<span data-ttu-id="2db4e-124">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="2db4e-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="2db4e-125">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="2db4e-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="2db4e-126">Rychlé JIT</span><span class="sxs-lookup"><span data-stu-id="2db4e-126">Quick JIT</span></span>

- <span data-ttu-id="2db4e-127">Konfiguruje, zda kompilátor JIT používá *rychlé JIT*.</span><span class="sxs-lookup"><span data-stu-id="2db4e-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="2db4e-128">Pro metody, které neobsahují smyčky a pro které není k dispozici předkompilovaný kód, rychlé JIT zkompiluje rychleji, ale bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="2db4e-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="2db4e-129">Povolení rychlé JIT snižuje dobu spuštění, ale může produkovat kód se sníženou charakteristikou výkonu.</span><span class="sxs-lookup"><span data-stu-id="2db4e-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="2db4e-130">Kód může například využít více místa v zásobníku, přidělit více paměti a spustit pomaleji.</span><span class="sxs-lookup"><span data-stu-id="2db4e-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="2db4e-131">Pokud je rychlá JIT [zakázána, ale je povolena vrstvená kompilace,](#tiered-compilation) účastní se vrstvené kompilace pouze předkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2db4e-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="2db4e-132">Pokud metoda není předkompilován s [ReadyToRun](#readytorun), chování JIT je stejný, jako kdyby [vrstvené kompilace](#tiered-compilation) byly zakázány.</span><span class="sxs-lookup"><span data-stu-id="2db4e-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="2db4e-133">V rozhraní .NET Core 3.0 a novějším je ve výchozím nastavení povolen rychlý JIT.</span><span class="sxs-lookup"><span data-stu-id="2db4e-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="2db4e-134">V rozhraní .NET Core 2.1 a 2.2 je rychlé JIT ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="2db4e-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="2db4e-135">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2db4e-135">Setting name</span></span> | <span data-ttu-id="2db4e-136">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2db4e-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2db4e-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2db4e-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="2db4e-138">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-138">`true` - enabled</span></span><br/><span data-ttu-id="2db4e-139">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-139">`false` - disabled</span></span> |
| <span data-ttu-id="2db4e-140">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="2db4e-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="2db4e-141">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-141">`true` - enabled</span></span><br/><span data-ttu-id="2db4e-142">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-142">`false` - disabled</span></span> |
| <span data-ttu-id="2db4e-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2db4e-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="2db4e-144">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-144">`1` - enabled</span></span><br/><span data-ttu-id="2db4e-145">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="2db4e-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="2db4e-146">Examples</span></span>

<span data-ttu-id="2db4e-147">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="2db4e-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="2db4e-148">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="2db4e-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="2db4e-149">Rychlé JIT pro smyčky</span><span class="sxs-lookup"><span data-stu-id="2db4e-149">Quick JIT for loops</span></span>

- <span data-ttu-id="2db4e-150">Konfiguruje, zda kompilátor JIT používá rychlé JIT na metody, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="2db4e-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="2db4e-151">Povolení rychlé JIT pro smyčky může zlepšit výkon při spuštění.</span><span class="sxs-lookup"><span data-stu-id="2db4e-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="2db4e-152">Dlouhotrvající smyčky však může uvíznout v méně optimalizovaný kód pro dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="2db4e-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="2db4e-153">Pokud je [funkce rychléHO JIT](#quick-jit) zakázána, nemá toto nastavení žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="2db4e-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="2db4e-154">Výchozí: Zakázáno (`false`).</span><span class="sxs-lookup"><span data-stu-id="2db4e-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="2db4e-155">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2db4e-155">Setting name</span></span> | <span data-ttu-id="2db4e-156">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2db4e-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2db4e-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2db4e-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="2db4e-158">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-158">`false` - disabled</span></span><br/><span data-ttu-id="2db4e-159">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-159">`true` - enabled</span></span> |
| <span data-ttu-id="2db4e-160">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="2db4e-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="2db4e-161">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-161">`false` - disabled</span></span><br/><span data-ttu-id="2db4e-162">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-162">`true` - enabled</span></span> |
| <span data-ttu-id="2db4e-163">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2db4e-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="2db4e-164">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-164">`0` - disabled</span></span><br/><span data-ttu-id="2db4e-165">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="2db4e-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="2db4e-166">Examples</span></span>

<span data-ttu-id="2db4e-167">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="2db4e-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="2db4e-168">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="2db4e-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="2db4e-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="2db4e-169">ReadyToRun</span></span>

- <span data-ttu-id="2db4e-170">Konfiguruje, zda runtime jádra .NET používá předkompilovaný kód pro bitové kopie s dostupnými daty ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="2db4e-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="2db4e-171">Zakázání této možnosti vynutí runtime na kód architektury kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="2db4e-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="2db4e-172">Další informace naleznete v tématu [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="2db4e-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="2db4e-173">Výchozí hodnota:`1`Povoleno ( ).</span><span class="sxs-lookup"><span data-stu-id="2db4e-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="2db4e-174">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2db4e-174">Setting name</span></span> | <span data-ttu-id="2db4e-175">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2db4e-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2db4e-176">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2db4e-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="2db4e-177">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2db4e-177">`1` - enabled</span></span><br/><span data-ttu-id="2db4e-178">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2db4e-178">`0` - disabled</span></span> |
