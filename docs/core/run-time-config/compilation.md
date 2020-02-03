---
title: Konfigurační nastavení kompilace
description: Přečtěte si o nastaveních modulu runtime, která konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733533"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="fd3c6-103">Možnosti konfigurace běhu pro kompilaci</span><span class="sxs-lookup"><span data-stu-id="fd3c6-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="fd3c6-104">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="fd3c6-104">Tiered compilation</span></span>

- <span data-ttu-id="fd3c6-105">Konfiguruje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="fd3c6-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="fd3c6-106">Vrstvená kompilace metody přechází přes dvě úrovně:</span><span class="sxs-lookup"><span data-stu-id="fd3c6-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="fd3c6-107">První vrstva generuje kód rychleji ([rychlá JIT](#quick-jit)) nebo načítá předem kompilovaný kód ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span><span class="sxs-lookup"><span data-stu-id="fd3c6-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span></span>
  - <span data-ttu-id="fd3c6-108">Druhá vrstva generuje optimalizovaný kód na pozadí ("optimalizuje JIT").</span><span class="sxs-lookup"><span data-stu-id="fd3c6-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="fd3c6-109">V rozhraní .NET Core 3,0 a novějších je vrstvená kompilace ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="fd3c6-110">V .NET Core 2,1 a 2,2 je vrstvená kompilace ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="fd3c6-111">Další informace najdete v [Průvodci vrstvenou kompilací](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="fd3c6-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="fd3c6-112">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fd3c6-112">Setting name</span></span> | <span data-ttu-id="fd3c6-113">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fd3c6-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fd3c6-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="fd3c6-115">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-115">`true` - enabled</span></span><br/><span data-ttu-id="fd3c6-116">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-116">`false` - disabled</span></span> |
| <span data-ttu-id="fd3c6-117">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="fd3c6-118">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-118">`true` - enabled</span></span><br/><span data-ttu-id="fd3c6-119">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-119">`false` - disabled</span></span> |
| <span data-ttu-id="fd3c6-120">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="fd3c6-121">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-121">`1` - enabled</span></span><br/><span data-ttu-id="fd3c6-122">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fd3c6-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="fd3c6-123">Examples</span></span>

<span data-ttu-id="fd3c6-124">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="fd3c6-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="fd3c6-125">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="fd3c6-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="fd3c6-126">Rychlá JIT</span><span class="sxs-lookup"><span data-stu-id="fd3c6-126">Quick JIT</span></span>

- <span data-ttu-id="fd3c6-127">Konfiguruje, zda kompilátor JIT používá *rychlou JIT*.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="fd3c6-128">Pro metody, které neobsahují smyčky a pro které není předem kompilovaný kód k dispozici, rychlá kompilátor JIT je zkompiluje rychleji, ale bez optimalizace.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="fd3c6-129">Povolení rychlé deaktivace JIT zkracuje čas spuštění, ale může vytvořit kód s zhoršenými charakteristikami výkonu.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="fd3c6-130">Kód může například použít více místa v zásobníku, přidělit více paměti a spustit pomaleji.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="fd3c6-131">Pokud je rychlá aktivace JIT zakázaná, ale je povolená [vrstvená kompilace](#tiered-compilation) , podílí se v vrstvené kompilaci jenom předem kompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="fd3c6-132">Pokud metoda není předem kompilována s [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), chování JIT je stejné jako v případě zakázání [vrstvené kompilace](#tiered-compilation) .</span><span class="sxs-lookup"><span data-stu-id="fd3c6-132">If a method is not pre-compiled with [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="fd3c6-133">V .NET Core 3,0 a novějších verzích je ve výchozím nastavení povolená rychlá technologie JIT.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="fd3c6-134">V .NET Core 2,1 a 2,2 je rychlá technologie JIT ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="fd3c6-135">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fd3c6-135">Setting name</span></span> | <span data-ttu-id="fd3c6-136">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fd3c6-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fd3c6-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="fd3c6-138">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-138">`true` - enabled</span></span><br/><span data-ttu-id="fd3c6-139">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-139">`false` - disabled</span></span> |
| <span data-ttu-id="fd3c6-140">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="fd3c6-141">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-141">`true` - enabled</span></span><br/><span data-ttu-id="fd3c6-142">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-142">`false` - disabled</span></span> |
| <span data-ttu-id="fd3c6-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="fd3c6-144">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-144">`1` - enabled</span></span><br/><span data-ttu-id="fd3c6-145">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fd3c6-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="fd3c6-146">Examples</span></span>

<span data-ttu-id="fd3c6-147">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="fd3c6-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="fd3c6-148">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="fd3c6-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="fd3c6-149">Rychlá JIT pro smyčky</span><span class="sxs-lookup"><span data-stu-id="fd3c6-149">Quick JIT for loops</span></span>

- <span data-ttu-id="fd3c6-150">Konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="fd3c6-151">Povolení rychlé JIT pro smyčky může zlepšit výkon při spuštění.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="fd3c6-152">Dlouhotrvající smyčky však můžou zablokovat v méně optimalizovaném kódu po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="fd3c6-153">Pokud je [rychlá JIT](#quick-jit) zakázaná, toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="fd3c6-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="fd3c6-154">Výchozí: zakázáno (`false`).</span><span class="sxs-lookup"><span data-stu-id="fd3c6-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="fd3c6-155">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="fd3c6-155">Setting name</span></span> | <span data-ttu-id="fd3c6-156">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="fd3c6-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fd3c6-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="fd3c6-158">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-158">`false` - disabled</span></span><br/><span data-ttu-id="fd3c6-159">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-159">`true` - enabled</span></span> |
| <span data-ttu-id="fd3c6-160">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="fd3c6-161">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-161">`false` - disabled</span></span><br/><span data-ttu-id="fd3c6-162">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-162">`true` - enabled</span></span> |
| <span data-ttu-id="fd3c6-163">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="fd3c6-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="fd3c6-164">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-164">`0` - disabled</span></span><br/><span data-ttu-id="fd3c6-165">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="fd3c6-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fd3c6-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="fd3c6-166">Examples</span></span>

<span data-ttu-id="fd3c6-167">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="fd3c6-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="fd3c6-168">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="fd3c6-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
