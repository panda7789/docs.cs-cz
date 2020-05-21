---
title: Ladění nastavení konfigurace profilace
description: Přečtěte si o nastaveních za běhu, které konfiguruje ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761990"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="a8340-103">Možnosti konfigurace běhu pro ladění a profilování</span><span class="sxs-lookup"><span data-stu-id="a8340-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="a8340-104">Povolení diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a8340-104">Enable diagnostics</span></span>

- <span data-ttu-id="a8340-105">Nakonfiguruje, jestli jsou povolené nebo zakázané diagnostiky ladicího programu, profileru a EventPipe.</span><span class="sxs-lookup"><span data-stu-id="a8340-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="a8340-106">Pokud toto nastavení vynecháte, bude Diagnostika povolena.</span><span class="sxs-lookup"><span data-stu-id="a8340-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="a8340-107">To je ekvivalentní nastavení hodnoty na `1` .</span><span class="sxs-lookup"><span data-stu-id="a8340-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="a8340-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-108">Setting name</span></span> | <span data-ttu-id="a8340-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a8340-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="a8340-111">–</span><span class="sxs-lookup"><span data-stu-id="a8340-111">N/A</span></span> | <span data-ttu-id="a8340-112">–</span><span class="sxs-lookup"><span data-stu-id="a8340-112">N/A</span></span> |
| <span data-ttu-id="a8340-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="a8340-114">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="a8340-114">`1` - enabled</span></span><br/><span data-ttu-id="a8340-115">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="a8340-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="a8340-116">Povolit profilaci</span><span class="sxs-lookup"><span data-stu-id="a8340-116">Enable profiling</span></span>

- <span data-ttu-id="a8340-117">Nakonfiguruje, jestli je profilace povolená pro aktuálně běžící proces.</span><span class="sxs-lookup"><span data-stu-id="a8340-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="a8340-118">Pokud toto nastavení vynecháte, profilace je zakázána.</span><span class="sxs-lookup"><span data-stu-id="a8340-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="a8340-119">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="a8340-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="a8340-120">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-120">Setting name</span></span> | <span data-ttu-id="a8340-121">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a8340-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="a8340-123">–</span><span class="sxs-lookup"><span data-stu-id="a8340-123">N/A</span></span> | <span data-ttu-id="a8340-124">–</span><span class="sxs-lookup"><span data-stu-id="a8340-124">N/A</span></span> |
| <span data-ttu-id="a8340-125">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="a8340-126">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="a8340-126">`0` - disabled</span></span><br/><span data-ttu-id="a8340-127">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="a8340-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="a8340-128">Identifikátor GUID profileru</span><span class="sxs-lookup"><span data-stu-id="a8340-128">Profiler GUID</span></span>

- <span data-ttu-id="a8340-129">Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="a8340-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="a8340-130">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-130">Setting name</span></span> | <span data-ttu-id="a8340-131">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-132">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a8340-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="a8340-133">–</span><span class="sxs-lookup"><span data-stu-id="a8340-133">N/A</span></span> | <span data-ttu-id="a8340-134">–</span><span class="sxs-lookup"><span data-stu-id="a8340-134">N/A</span></span> |
| <span data-ttu-id="a8340-135">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="a8340-136">*řetězec GUID*</span><span class="sxs-lookup"><span data-stu-id="a8340-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="a8340-137">Umístění profileru</span><span class="sxs-lookup"><span data-stu-id="a8340-137">Profiler location</span></span>

- <span data-ttu-id="a8340-138">Určuje cestu k souboru DLL profileru, která se má načíst do aktuálně spuštěného procesu (nebo 32 nebo 64 procesu).</span><span class="sxs-lookup"><span data-stu-id="a8340-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="a8340-139">Pokud je nastavena více než jedna proměnná, budou mít proměnné specifické pro bitová verze přednost.</span><span class="sxs-lookup"><span data-stu-id="a8340-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="a8340-140">Určují, které bitová verze profileru se má načíst.</span><span class="sxs-lookup"><span data-stu-id="a8340-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="a8340-141">Další informace najdete v tématu [vyhledání knihovny profileru](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="a8340-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="a8340-142">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-142">Setting name</span></span> | <span data-ttu-id="a8340-143">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-144">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="a8340-145">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="a8340-145">*string-path*</span></span> |
| <span data-ttu-id="a8340-146">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="a8340-147">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="a8340-147">*string-path*</span></span> |
| <span data-ttu-id="a8340-148">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="a8340-149">*řetězec – cesta*</span><span class="sxs-lookup"><span data-stu-id="a8340-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="a8340-150">Zapsat mapu výkonu</span><span class="sxs-lookup"><span data-stu-id="a8340-150">Write perf map</span></span>

- <span data-ttu-id="a8340-151">Povoluje nebo zakazuje zápis */tmp/perf-$PID. map* na systémy Linux.</span><span class="sxs-lookup"><span data-stu-id="a8340-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="a8340-152">Pokud toto nastavení vynecháte, bude zápis mapy výkonu zakázán.</span><span class="sxs-lookup"><span data-stu-id="a8340-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="a8340-153">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="a8340-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="a8340-154">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-154">Setting name</span></span> | <span data-ttu-id="a8340-155">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a8340-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="a8340-157">–</span><span class="sxs-lookup"><span data-stu-id="a8340-157">N/A</span></span> | <span data-ttu-id="a8340-158">–</span><span class="sxs-lookup"><span data-stu-id="a8340-158">N/A</span></span> |
| <span data-ttu-id="a8340-159">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="a8340-160">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="a8340-160">`0` - disabled</span></span><br/><span data-ttu-id="a8340-161">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="a8340-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="a8340-162">Značky protokolu výkonu</span><span class="sxs-lookup"><span data-stu-id="a8340-162">Perf log markers</span></span>

- <span data-ttu-id="a8340-163">Povolí nebo zakáže přijetí a ignorování zadaného signálu jako značky v protokolech výkonu.</span><span class="sxs-lookup"><span data-stu-id="a8340-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="a8340-164">Pokud toto nastavení vynecháte, zadaný signál se Neignoruje.</span><span class="sxs-lookup"><span data-stu-id="a8340-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="a8340-165">To je ekvivalentní nastavení hodnoty na `0` .</span><span class="sxs-lookup"><span data-stu-id="a8340-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="a8340-166">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a8340-166">Setting name</span></span> | <span data-ttu-id="a8340-167">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a8340-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a8340-168">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a8340-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="a8340-169">–</span><span class="sxs-lookup"><span data-stu-id="a8340-169">N/A</span></span> | <span data-ttu-id="a8340-170">–</span><span class="sxs-lookup"><span data-stu-id="a8340-170">N/A</span></span> |
| <span data-ttu-id="a8340-171">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a8340-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="a8340-172">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="a8340-172">`0` - disabled</span></span><br/><span data-ttu-id="a8340-173">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="a8340-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="a8340-174">Toto nastavení je ignorováno, pokud je [COMPlus_PerfMapEnabled](#write-perf-map) vynecháno nebo nastaveno na `0` (to je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="a8340-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
