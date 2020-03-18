---
title: Ladění nastavení konfigurace profilování
description: Přečtěte si o nastavení za běhu, které konfigurují ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802797"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="2bae6-103">Možnosti konfigurace za běhu pro ladění a profilování</span><span class="sxs-lookup"><span data-stu-id="2bae6-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="2bae6-104">Povolení diagnostiky</span><span class="sxs-lookup"><span data-stu-id="2bae6-104">Enable diagnostics</span></span>

- <span data-ttu-id="2bae6-105">Konfiguruje, zda ladicí program, profiler a diagnostika EventPipe jsou povoleny nebo zakázány.</span><span class="sxs-lookup"><span data-stu-id="2bae6-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="2bae6-106">Výchozí hodnota:`1`Povoleno ( ).</span><span class="sxs-lookup"><span data-stu-id="2bae6-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="2bae6-107">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-107">Setting name</span></span> | <span data-ttu-id="2bae6-108">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2bae6-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bae6-110">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-110">N/A</span></span> | <span data-ttu-id="2bae6-111">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-111">N/A</span></span> |
| <span data-ttu-id="2bae6-112">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="2bae6-113">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2bae6-113">`1` - enabled</span></span><br/><span data-ttu-id="2bae6-114">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2bae6-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="2bae6-115">Povolit profilování</span><span class="sxs-lookup"><span data-stu-id="2bae6-115">Enable profiling</span></span>

- <span data-ttu-id="2bae6-116">Konfiguruje, zda je profilování povoleno pro aktuálně spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="2bae6-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="2bae6-117">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="2bae6-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="2bae6-118">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-118">Setting name</span></span> | <span data-ttu-id="2bae6-119">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2bae6-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bae6-121">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-121">N/A</span></span> | <span data-ttu-id="2bae6-122">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-122">N/A</span></span> |
| <span data-ttu-id="2bae6-123">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="2bae6-124">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2bae6-124">`0` - disabled</span></span><br/><span data-ttu-id="2bae6-125">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2bae6-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="2bae6-126">Identifikátor GUID profileru</span><span class="sxs-lookup"><span data-stu-id="2bae6-126">Profiler GUID</span></span>

- <span data-ttu-id="2bae6-127">Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="2bae6-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="2bae6-128">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-128">Setting name</span></span> | <span data-ttu-id="2bae6-129">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2bae6-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bae6-131">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-131">N/A</span></span> | <span data-ttu-id="2bae6-132">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-132">N/A</span></span> |
| <span data-ttu-id="2bae6-133">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="2bae6-134">*řetězec-guid*</span><span class="sxs-lookup"><span data-stu-id="2bae6-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="2bae6-135">Umístění profileru</span><span class="sxs-lookup"><span data-stu-id="2bae6-135">Profiler location</span></span>

- <span data-ttu-id="2bae6-136">Určuje cestu k dll profileru, která se má načíst do aktuálně spuštěného procesu (nebo 32bitového nebo 64bitového procesu).</span><span class="sxs-lookup"><span data-stu-id="2bae6-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="2bae6-137">Pokud je nastavena více než jedna proměnná, mají přednost proměnné specifické pro bitness.</span><span class="sxs-lookup"><span data-stu-id="2bae6-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="2bae6-138">Určují, jakou bitovou vlastnost profileru má být načíst.</span><span class="sxs-lookup"><span data-stu-id="2bae6-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="2bae6-139">Další informace naleznete [v tématu Hledání knihovny profileru](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="2bae6-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="2bae6-140">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-140">Setting name</span></span> | <span data-ttu-id="2bae6-141">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-142">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="2bae6-143">*cesta řetězce*</span><span class="sxs-lookup"><span data-stu-id="2bae6-143">*string-path*</span></span> |
| <span data-ttu-id="2bae6-144">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="2bae6-145">*cesta řetězce*</span><span class="sxs-lookup"><span data-stu-id="2bae6-145">*string-path*</span></span> |
| <span data-ttu-id="2bae6-146">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="2bae6-147">*cesta řetězce*</span><span class="sxs-lookup"><span data-stu-id="2bae6-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="2bae6-148">Napsat perf mapu</span><span class="sxs-lookup"><span data-stu-id="2bae6-148">Write perf map</span></span>

- <span data-ttu-id="2bae6-149">Povolí nebo zakáže zápis */tmp/perf-$pid.map* na linuxové systémy.</span><span class="sxs-lookup"><span data-stu-id="2bae6-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="2bae6-150">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="2bae6-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="2bae6-151">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-151">Setting name</span></span> | <span data-ttu-id="2bae6-152">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-153">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2bae6-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bae6-154">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-154">N/A</span></span> | <span data-ttu-id="2bae6-155">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-155">N/A</span></span> |
| <span data-ttu-id="2bae6-156">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="2bae6-157">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2bae6-157">`0` - disabled</span></span><br/><span data-ttu-id="2bae6-158">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2bae6-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="2bae6-159">Značky protokolu Perf</span><span class="sxs-lookup"><span data-stu-id="2bae6-159">Perf log markers</span></span>

- <span data-ttu-id="2bae6-160">Pokud `COMPlus_PerfMapEnabled` je `1`nastavena na , umožňuje nebo zakáže zadaný signál, které mají být přijaty a ignorovány jako značka v perf protokoly.</span><span class="sxs-lookup"><span data-stu-id="2bae6-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="2bae6-161">Výchozí: Zakázáno (`0`).</span><span class="sxs-lookup"><span data-stu-id="2bae6-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="2bae6-162">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="2bae6-162">Setting name</span></span> | <span data-ttu-id="2bae6-163">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="2bae6-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2bae6-164">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="2bae6-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bae6-165">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-165">N/A</span></span> | <span data-ttu-id="2bae6-166">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="2bae6-166">N/A</span></span> |
| <span data-ttu-id="2bae6-167">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="2bae6-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="2bae6-168">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="2bae6-168">`0` - disabled</span></span><br/><span data-ttu-id="2bae6-169">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="2bae6-169">`1` - enabled</span></span> |
