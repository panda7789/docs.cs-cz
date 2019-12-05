---
title: Ladění nastavení konfigurace profilace
description: Přečtěte si o nastaveních za běhu, které konfiguruje ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802797"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="246b9-103">Možnosti konfigurace běhu pro ladění a profilování</span><span class="sxs-lookup"><span data-stu-id="246b9-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="246b9-104">Povolení diagnostiky</span><span class="sxs-lookup"><span data-stu-id="246b9-104">Enable diagnostics</span></span>

- <span data-ttu-id="246b9-105">Nakonfiguruje, jestli jsou povolené nebo zakázané diagnostiky ladicího programu, profileru a EventPipe.</span><span class="sxs-lookup"><span data-stu-id="246b9-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="246b9-106">Výchozí: povoleno (`1`).</span><span class="sxs-lookup"><span data-stu-id="246b9-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="246b9-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-107">Setting name</span></span> | <span data-ttu-id="246b9-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="246b9-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="246b9-110">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-110">N/A</span></span> | <span data-ttu-id="246b9-111">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-111">N/A</span></span> |
| <span data-ttu-id="246b9-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="246b9-113">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="246b9-113">`1` - enabled</span></span><br/><span data-ttu-id="246b9-114">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="246b9-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="246b9-115">Povolit profilaci</span><span class="sxs-lookup"><span data-stu-id="246b9-115">Enable profiling</span></span>

- <span data-ttu-id="246b9-116">Nakonfiguruje, jestli je profilace povolená pro aktuálně běžící proces.</span><span class="sxs-lookup"><span data-stu-id="246b9-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="246b9-117">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="246b9-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="246b9-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-118">Setting name</span></span> | <span data-ttu-id="246b9-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="246b9-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="246b9-121">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-121">N/A</span></span> | <span data-ttu-id="246b9-122">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-122">N/A</span></span> |
| <span data-ttu-id="246b9-123">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="246b9-124">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="246b9-124">`0` - disabled</span></span><br/><span data-ttu-id="246b9-125">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="246b9-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="246b9-126">Identifikátor GUID profileru</span><span class="sxs-lookup"><span data-stu-id="246b9-126">Profiler GUID</span></span>

- <span data-ttu-id="246b9-127">Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="246b9-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="246b9-128">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-128">Setting name</span></span> | <span data-ttu-id="246b9-129">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="246b9-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="246b9-131">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-131">N/A</span></span> | <span data-ttu-id="246b9-132">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-132">N/A</span></span> |
| <span data-ttu-id="246b9-133">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="246b9-134">*řetězec GUID*</span><span class="sxs-lookup"><span data-stu-id="246b9-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="246b9-135">Umístění profileru</span><span class="sxs-lookup"><span data-stu-id="246b9-135">Profiler location</span></span>

- <span data-ttu-id="246b9-136">Určuje cestu k souboru DLL profileru, která se má načíst do aktuálně spuštěného procesu (nebo 32 nebo 64 procesu).</span><span class="sxs-lookup"><span data-stu-id="246b9-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="246b9-137">Pokud je nastavena více než jedna proměnná, budou mít proměnné specifické pro bitová verze přednost.</span><span class="sxs-lookup"><span data-stu-id="246b9-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="246b9-138">Určují, které bitová verze profileru se má načíst.</span><span class="sxs-lookup"><span data-stu-id="246b9-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="246b9-139">Další informace najdete v tématu [vyhledání knihovny profileru](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="246b9-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="246b9-140">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-140">Setting name</span></span> | <span data-ttu-id="246b9-141">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-142">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="246b9-143">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="246b9-143">*string-path*</span></span> |
| <span data-ttu-id="246b9-144">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="246b9-145">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="246b9-145">*string-path*</span></span> |
| <span data-ttu-id="246b9-146">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="246b9-147">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="246b9-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="246b9-148">Zapsat mapu výkonu</span><span class="sxs-lookup"><span data-stu-id="246b9-148">Write perf map</span></span>

- <span data-ttu-id="246b9-149">Povoluje nebo zakazuje zápis */tmp/perf-$PID. map* na systémy Linux.</span><span class="sxs-lookup"><span data-stu-id="246b9-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="246b9-150">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="246b9-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="246b9-151">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-151">Setting name</span></span> | <span data-ttu-id="246b9-152">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="246b9-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="246b9-154">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-154">N/A</span></span> | <span data-ttu-id="246b9-155">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-155">N/A</span></span> |
| <span data-ttu-id="246b9-156">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="246b9-157">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="246b9-157">`0` - disabled</span></span><br/><span data-ttu-id="246b9-158">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="246b9-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="246b9-159">Značky protokolu výkonu</span><span class="sxs-lookup"><span data-stu-id="246b9-159">Perf log markers</span></span>

- <span data-ttu-id="246b9-160">Pokud je `COMPlus_PerfMapEnabled` nastaveno na hodnotu `1`, povolí nebo zakáže, aby byl zadaný signál přijat a ignorován jako značka v protokolech výkonu.</span><span class="sxs-lookup"><span data-stu-id="246b9-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="246b9-161">Výchozí: zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="246b9-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="246b9-162">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="246b9-162">Setting name</span></span> | <span data-ttu-id="246b9-163">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="246b9-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="246b9-164">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="246b9-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="246b9-165">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-165">N/A</span></span> | <span data-ttu-id="246b9-166">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="246b9-166">N/A</span></span> |
| <span data-ttu-id="246b9-167">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="246b9-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="246b9-168">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="246b9-168">`0` - disabled</span></span><br/><span data-ttu-id="246b9-169">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="246b9-169">`1` - enabled</span></span> |
