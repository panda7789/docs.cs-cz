---
title: Nastavení konfigurace globalizace
description: Informace o nastavení za běhu, které konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje japonská data.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733463"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="a9aab-103">Možnosti konfigurace za běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="a9aab-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="a9aab-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="a9aab-104">Invariant mode</span></span>

- <span data-ttu-id="a9aab-105">Určuje, zda aplikace .NET Core běží v invariantním režimu globalizace bez přístupu k datům a chování můře specifickým pro jazykovou verzi nebo zda má přístup ke kulturním datům.</span><span class="sxs-lookup"><span data-stu-id="a9aab-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="a9aab-106">Výchozí: Spusťte aplikaci s`false`přístupem ke kulturním datům ( ).</span><span class="sxs-lookup"><span data-stu-id="a9aab-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="a9aab-107">Další informace naleznete v tématu [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a9aab-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="a9aab-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a9aab-108">Setting name</span></span> | <span data-ttu-id="a9aab-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a9aab-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a9aab-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a9aab-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="a9aab-111">`false`- přístup ke kulturním údajům</span><span class="sxs-lookup"><span data-stu-id="a9aab-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="a9aab-112">`true`- běh v invariantním režimu</span><span class="sxs-lookup"><span data-stu-id="a9aab-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a9aab-113">**MSBuild, vlastnost**</span><span class="sxs-lookup"><span data-stu-id="a9aab-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="a9aab-114">`false`- přístup ke kulturním údajům</span><span class="sxs-lookup"><span data-stu-id="a9aab-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="a9aab-115">`true`- běh v invariantním režimu</span><span class="sxs-lookup"><span data-stu-id="a9aab-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a9aab-116">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a9aab-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="a9aab-117">`0`- přístup ke kulturním údajům</span><span class="sxs-lookup"><span data-stu-id="a9aab-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="a9aab-118">`1`- běh v invariantním režimu</span><span class="sxs-lookup"><span data-stu-id="a9aab-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="a9aab-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="a9aab-119">Examples</span></span>

<span data-ttu-id="a9aab-120">*soubor runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a9aab-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="a9aab-121">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="a9aab-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="a9aab-122">Rozsahy let era</span><span class="sxs-lookup"><span data-stu-id="a9aab-122">Era year ranges</span></span>

- <span data-ttu-id="a9aab-123">Určuje, zda jsou kontroly rozsahu pro kalendáře, které podporují více období, uvolněná nebo <xref:System.ArgumentOutOfRangeException>zda jsou data, která přetečou časové období období období, vyvolána .</span><span class="sxs-lookup"><span data-stu-id="a9aab-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="a9aab-124">Výchozí: Kontroly rozsahu`false`jsou uvolněné ( ).</span><span class="sxs-lookup"><span data-stu-id="a9aab-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="a9aab-125">Další informace naleznete v [tématu Kalendáře, epochy a rozsahy dat: Kontroly uvolněného rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="a9aab-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="a9aab-126">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a9aab-126">Setting name</span></span> | <span data-ttu-id="a9aab-127">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a9aab-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a9aab-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a9aab-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="a9aab-129">`false`- uvolněné kontroly dosahu</span><span class="sxs-lookup"><span data-stu-id="a9aab-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="a9aab-130">`true`- přetečení způsobí výjimku</span><span class="sxs-lookup"><span data-stu-id="a9aab-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="a9aab-131">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a9aab-131">**Environment variable**</span></span> | <span data-ttu-id="a9aab-132">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-132">N/A</span></span> | <span data-ttu-id="a9aab-133">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="a9aab-134">Analýza japonského data</span><span class="sxs-lookup"><span data-stu-id="a9aab-134">Japanese date parsing</span></span>

- <span data-ttu-id="a9aab-135">Určuje, zda řetězec, který obsahuje "1" nebo "Gannen" jako rok analyzuje úspěšně, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="a9aab-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="a9aab-136">Výchozí: Analyzují řetězce, které obsahují buď "1" nebo`false`"Gannen" jako rok ( ).</span><span class="sxs-lookup"><span data-stu-id="a9aab-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="a9aab-137">Další informace naleznete [v tématu Představují data v kalendářích s více epochami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a9aab-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a9aab-138">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a9aab-138">Setting name</span></span> | <span data-ttu-id="a9aab-139">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a9aab-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a9aab-140">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a9aab-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="a9aab-141">`false`- "Gannen" nebo "1" je podporován</span><span class="sxs-lookup"><span data-stu-id="a9aab-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="a9aab-142">`true`- je podporováno pouze "1"</span><span class="sxs-lookup"><span data-stu-id="a9aab-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="a9aab-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a9aab-143">**Environment variable**</span></span> | <span data-ttu-id="a9aab-144">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-144">N/A</span></span> | <span data-ttu-id="a9aab-145">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="a9aab-146">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="a9aab-146">Japanese year format</span></span>

- <span data-ttu-id="a9aab-147">Určuje, zda je první rok éry japonského kalendáře formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="a9aab-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="a9aab-148">Výchozí: Naformátujte první rok jako`false`"Gannen" ( ).</span><span class="sxs-lookup"><span data-stu-id="a9aab-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="a9aab-149">Další informace naleznete [v tématu Představují data v kalendářích s více epochami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a9aab-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a9aab-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a9aab-150">Setting name</span></span> | <span data-ttu-id="a9aab-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a9aab-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a9aab-152">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a9aab-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="a9aab-153">`false`- formát jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="a9aab-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="a9aab-154">`true`- formát jako číslo</span><span class="sxs-lookup"><span data-stu-id="a9aab-154">`true` - format as number</span></span> |
| <span data-ttu-id="a9aab-155">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a9aab-155">**Environment variable**</span></span> | <span data-ttu-id="a9aab-156">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-156">N/A</span></span> | <span data-ttu-id="a9aab-157">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-157">N/A</span></span> |
