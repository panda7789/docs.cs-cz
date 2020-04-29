---
title: Konfigurační nastavení kompilace
description: Přečtěte si o nastaveních modulu runtime, která konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 4db20ee6d36fe3d3d66f473644b70c02d4e02cb3
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506841"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="36590-103">Možnosti konfigurace běhu pro kompilaci</span><span class="sxs-lookup"><span data-stu-id="36590-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="36590-104">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="36590-104">Tiered compilation</span></span>

- <span data-ttu-id="36590-105">Konfiguruje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="36590-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="36590-106">Vrstvená kompilace metody přechází přes dvě úrovně:</span><span class="sxs-lookup"><span data-stu-id="36590-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="36590-107">První vrstva generuje kód rychleji ([rychlá JIT](#quick-jit)) nebo načítá předem kompilovaný kód ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="36590-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="36590-108">Druhá vrstva generuje optimalizovaný kód na pozadí ("optimalizuje JIT").</span><span class="sxs-lookup"><span data-stu-id="36590-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="36590-109">V rozhraní .NET Core 3,0 a novějších je vrstvená kompilace ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="36590-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="36590-110">V .NET Core 2,1 a 2,2 je vrstvená kompilace ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="36590-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="36590-111">Další informace najdete v [Průvodci vrstvenou kompilací](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="36590-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="36590-112">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="36590-112">Setting name</span></span> | <span data-ttu-id="36590-113">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="36590-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="36590-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="36590-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="36590-115">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-115">`true` - enabled</span></span><br/><span data-ttu-id="36590-116">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-116">`false` - disabled</span></span> |
| <span data-ttu-id="36590-117">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="36590-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="36590-118">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-118">`true` - enabled</span></span><br/><span data-ttu-id="36590-119">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-119">`false` - disabled</span></span> |
| <span data-ttu-id="36590-120">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="36590-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="36590-121">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-121">`1` - enabled</span></span><br/><span data-ttu-id="36590-122">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="36590-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="36590-123">Examples</span></span>

<span data-ttu-id="36590-124">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="36590-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="36590-125">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="36590-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="36590-126">Rychlá JIT</span><span class="sxs-lookup"><span data-stu-id="36590-126">Quick JIT</span></span>

- <span data-ttu-id="36590-127">Konfiguruje, zda kompilátor JIT používá *rychlou JIT*.</span><span class="sxs-lookup"><span data-stu-id="36590-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="36590-128">Pro metody, které neobsahují smyčky a pro které není předem kompilovaný kód k dispozici, rychlá kompilátor JIT je zkompiluje rychleji, ale bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="36590-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="36590-129">Povolení rychlé deaktivace JIT zkracuje čas spuštění, ale může vytvořit kód s zhoršenými charakteristikami výkonu.</span><span class="sxs-lookup"><span data-stu-id="36590-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="36590-130">Kód může například použít více místa v zásobníku, přidělit více paměti a spustit pomaleji.</span><span class="sxs-lookup"><span data-stu-id="36590-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="36590-131">Pokud je rychlá aktivace JIT zakázaná, ale je povolená [vrstvená kompilace](#tiered-compilation) , podílí se v vrstvené kompilaci jenom předem kompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="36590-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="36590-132">Pokud metoda není předem kompilována s [ReadyToRun](#readytorun), chování JIT je stejné jako v případě zakázání [vrstvené kompilace](#tiered-compilation) .</span><span class="sxs-lookup"><span data-stu-id="36590-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="36590-133">V .NET Core 3,0 a novějších verzích je ve výchozím nastavení povolená rychlá technologie JIT.</span><span class="sxs-lookup"><span data-stu-id="36590-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="36590-134">V .NET Core 2,1 a 2,2 je rychlá technologie JIT ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="36590-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="36590-135">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="36590-135">Setting name</span></span> | <span data-ttu-id="36590-136">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="36590-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="36590-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="36590-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="36590-138">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-138">`true` - enabled</span></span><br/><span data-ttu-id="36590-139">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-139">`false` - disabled</span></span> |
| <span data-ttu-id="36590-140">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="36590-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="36590-141">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-141">`true` - enabled</span></span><br/><span data-ttu-id="36590-142">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-142">`false` - disabled</span></span> |
| <span data-ttu-id="36590-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="36590-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="36590-144">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-144">`1` - enabled</span></span><br/><span data-ttu-id="36590-145">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="36590-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="36590-146">Examples</span></span>

<span data-ttu-id="36590-147">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="36590-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="36590-148">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="36590-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="36590-149">Rychlá JIT pro smyčky</span><span class="sxs-lookup"><span data-stu-id="36590-149">Quick JIT for loops</span></span>

- <span data-ttu-id="36590-150">Konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="36590-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="36590-151">Povolení rychlé JIT pro smyčky může zlepšit výkon při spuštění.</span><span class="sxs-lookup"><span data-stu-id="36590-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="36590-152">Dlouhotrvající smyčky však můžou zablokovat v méně optimalizovaném kódu po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="36590-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="36590-153">Pokud je [rychlá JIT](#quick-jit) zakázaná, toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="36590-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="36590-154">Výchozí: disabled`false`().</span><span class="sxs-lookup"><span data-stu-id="36590-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="36590-155">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="36590-155">Setting name</span></span> | <span data-ttu-id="36590-156">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="36590-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="36590-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="36590-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="36590-158">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-158">`false` - disabled</span></span><br/><span data-ttu-id="36590-159">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-159">`true` - enabled</span></span> |
| <span data-ttu-id="36590-160">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="36590-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="36590-161">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-161">`false` - disabled</span></span><br/><span data-ttu-id="36590-162">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-162">`true` - enabled</span></span> |
| <span data-ttu-id="36590-163">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="36590-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="36590-164">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-164">`0` - disabled</span></span><br/><span data-ttu-id="36590-165">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="36590-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="36590-166">Examples</span></span>

<span data-ttu-id="36590-167">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="36590-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="36590-168">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="36590-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="36590-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="36590-169">ReadyToRun</span></span>

- <span data-ttu-id="36590-170">Konfiguruje, zda modul runtime .NET Core používá předem kompilovaný kód pro image s dostupnými ReadyToRun daty.</span><span class="sxs-lookup"><span data-stu-id="36590-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="36590-171">Když se tato možnost zakáže, vynutí modul runtime kód rozhraní kompilování JIT.</span><span class="sxs-lookup"><span data-stu-id="36590-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="36590-172">Další informace najdete v tématu [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="36590-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="36590-173">Výchozí: Enabled (`1`).</span><span class="sxs-lookup"><span data-stu-id="36590-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="36590-174">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="36590-174">Setting name</span></span> | <span data-ttu-id="36590-175">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="36590-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="36590-176">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="36590-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="36590-177">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="36590-177">`1` - enabled</span></span><br/><span data-ttu-id="36590-178">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="36590-178">`0` - disabled</span></span> |
