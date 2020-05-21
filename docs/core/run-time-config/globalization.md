---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 56228e9a6cb6dbab6a22bdc00d11212e1019776b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761964"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="eb8c7-103">Možnosti konfigurace běhového běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="eb8c7-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="eb8c7-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="eb8c7-104">Invariant mode</span></span>

- <span data-ttu-id="eb8c7-105">Určuje, jestli aplikace .NET Core běží v režimu invariantní v rámci globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="eb8c7-106">Pokud toto nastavení vynecháte, aplikace se bude spouštět s přístupem k kulturním datům.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="eb8c7-107">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="eb8c7-108">Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="eb8c7-109">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="eb8c7-109">Setting name</span></span> | <span data-ttu-id="eb8c7-110">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="eb8c7-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eb8c7-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="eb8c7-112">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="eb8c7-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="eb8c7-113">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="eb8c7-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="eb8c7-114">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="eb8c7-115">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="eb8c7-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="eb8c7-116">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="eb8c7-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="eb8c7-117">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="eb8c7-118">`0`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="eb8c7-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="eb8c7-119">`1`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="eb8c7-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="eb8c7-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="eb8c7-120">Examples</span></span>

<span data-ttu-id="eb8c7-121">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="eb8c7-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="eb8c7-122">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="eb8c7-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="eb8c7-123">Rozsahy roků období</span><span class="sxs-lookup"><span data-stu-id="eb8c7-123">Era year ranges</span></span>

- <span data-ttu-id="eb8c7-124">Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data, která přecházejí do rozsahu dat v období, vyvolají <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="eb8c7-125">Pokud toto nastavení vynecháte, budou se kontroly rozsahu zmírnit.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="eb8c7-126">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="eb8c7-127">Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="eb8c7-128">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="eb8c7-128">Setting name</span></span> | <span data-ttu-id="eb8c7-129">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="eb8c7-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eb8c7-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="eb8c7-131">`false`– Neuvolněné kontroly rozsahu</span><span class="sxs-lookup"><span data-stu-id="eb8c7-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="eb8c7-132">`true`– při přetečení dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="eb8c7-133">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-133">**Environment variable**</span></span> | <span data-ttu-id="eb8c7-134">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-134">N/A</span></span> | <span data-ttu-id="eb8c7-135">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="eb8c7-136">Analýza data v japonštině</span><span class="sxs-lookup"><span data-stu-id="eb8c7-136">Japanese date parsing</span></span>

- <span data-ttu-id="eb8c7-137">Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="eb8c7-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="eb8c7-138">Pokud toto nastavení vynecháte, řetězce, které obsahují buď "1" nebo "Gannen", se budou analyzovat jako rok úspěšně.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="eb8c7-139">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="eb8c7-140">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="eb8c7-141">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="eb8c7-141">Setting name</span></span> | <span data-ttu-id="eb8c7-142">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="eb8c7-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eb8c7-143">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="eb8c7-144">`false`– "Gannen" nebo "1" je podporováno</span><span class="sxs-lookup"><span data-stu-id="eb8c7-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="eb8c7-145">`true`– podporuje se jenom 1.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="eb8c7-146">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-146">**Environment variable**</span></span> | <span data-ttu-id="eb8c7-147">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-147">N/A</span></span> | <span data-ttu-id="eb8c7-148">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="eb8c7-149">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="eb8c7-149">Japanese year format</span></span>

- <span data-ttu-id="eb8c7-150">Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="eb8c7-151">Pokud toto nastavení vynecháte, první rok se zformátuje jako "Gannen".</span><span class="sxs-lookup"><span data-stu-id="eb8c7-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="eb8c7-152">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="eb8c7-153">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="eb8c7-154">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="eb8c7-154">Setting name</span></span> | <span data-ttu-id="eb8c7-155">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="eb8c7-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eb8c7-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="eb8c7-157">`false`– formátovat jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="eb8c7-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="eb8c7-158">`true`– formátovat jako číslo</span><span class="sxs-lookup"><span data-stu-id="eb8c7-158">`true` - format as number</span></span> |
| <span data-ttu-id="eb8c7-159">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-159">**Environment variable**</span></span> | <span data-ttu-id="eb8c7-160">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-160">N/A</span></span> | <span data-ttu-id="eb8c7-161">–</span><span class="sxs-lookup"><span data-stu-id="eb8c7-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="eb8c7-162">NLS</span><span class="sxs-lookup"><span data-stu-id="eb8c7-162">NLS</span></span>

- <span data-ttu-id="eb8c7-163">Určuje, jestli rozhraní .NET pro aplikace pro Windows používá rozhraní API pro globalizaci (National Language Support) nebo mezinárodní komponenty pro rozhraní Unicode (ICU).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="eb8c7-164">Rozhraní .NET 5,0 a novější verze používají rozhraní API globalizace ICU ve výchozím nastavení ve Windows 10 může 2019 Update a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="eb8c7-165">Pokud toto nastavení vynecháte, .NET ve výchozím nastavení používá rozhraní API globalizace ICU.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="eb8c7-166">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="eb8c7-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="eb8c7-167">Další informace naleznete v tématu [rozhraní API globalizace použití knihoven ICU ve Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="eb8c7-168">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="eb8c7-168">Setting name</span></span> | <span data-ttu-id="eb8c7-169">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="eb8c7-169">Values</span></span> | <span data-ttu-id="eb8c7-170">Vedou</span><span class="sxs-lookup"><span data-stu-id="eb8c7-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="eb8c7-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="eb8c7-172">`false`-Použít rozhraní API globalizace ICU</span><span class="sxs-lookup"><span data-stu-id="eb8c7-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="eb8c7-173">`true`– Použití rozhraní API globalizace NLS</span><span class="sxs-lookup"><span data-stu-id="eb8c7-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="eb8c7-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="eb8c7-174">.NET 5.0</span></span> |
| <span data-ttu-id="eb8c7-175">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="eb8c7-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="eb8c7-176">`false`-Použít rozhraní API globalizace ICU</span><span class="sxs-lookup"><span data-stu-id="eb8c7-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="eb8c7-177">`true`– Použití rozhraní API globalizace NLS</span><span class="sxs-lookup"><span data-stu-id="eb8c7-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="eb8c7-178">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="eb8c7-178">.NET 5.0</span></span> |
