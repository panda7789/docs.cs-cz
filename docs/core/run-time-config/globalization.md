---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733463"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="a39bf-103">Možnosti konfigurace běhového běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="a39bf-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="a39bf-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="a39bf-104">Invariant mode</span></span>

- <span data-ttu-id="a39bf-105">Určuje, jestli aplikace .NET Core běží v invariantní režimu globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi nebo jestli má přístup k kulturním datům.</span><span class="sxs-lookup"><span data-stu-id="a39bf-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="a39bf-106">Výchozí: Spusťte aplikaci s přístupem k kulturním datům (`false`).</span><span class="sxs-lookup"><span data-stu-id="a39bf-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="a39bf-107">Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a39bf-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="a39bf-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a39bf-108">Setting name</span></span> | <span data-ttu-id="a39bf-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a39bf-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a39bf-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a39bf-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="a39bf-111">`false` – přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="a39bf-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="a39bf-112">`true`-spustit v režimu invariantování</span><span class="sxs-lookup"><span data-stu-id="a39bf-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a39bf-113">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a39bf-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="a39bf-114">`false` – přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="a39bf-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="a39bf-115">`true`-spustit v režimu invariantování</span><span class="sxs-lookup"><span data-stu-id="a39bf-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a39bf-116">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a39bf-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="a39bf-117">`0` – přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="a39bf-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="a39bf-118">`1`-spustit v režimu invariantování</span><span class="sxs-lookup"><span data-stu-id="a39bf-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="a39bf-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="a39bf-119">Examples</span></span>

<span data-ttu-id="a39bf-120">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="a39bf-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="a39bf-121">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="a39bf-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="a39bf-122">Rozsahy roků období</span><span class="sxs-lookup"><span data-stu-id="a39bf-122">Era year ranges</span></span>

- <span data-ttu-id="a39bf-123">Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data přetečení rozsahu data v období přecházejí <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="a39bf-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="a39bf-124">Výchozí: kontroly rozsahu jsou uvolněny (`false`).</span><span class="sxs-lookup"><span data-stu-id="a39bf-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="a39bf-125">Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="a39bf-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="a39bf-126">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a39bf-126">Setting name</span></span> | <span data-ttu-id="a39bf-127">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a39bf-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a39bf-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a39bf-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="a39bf-129">`false` – Neuvolněné kontroly rozsahu</span><span class="sxs-lookup"><span data-stu-id="a39bf-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="a39bf-130">`true` – přetečení způsobují výjimku.</span><span class="sxs-lookup"><span data-stu-id="a39bf-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="a39bf-131">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a39bf-131">**Environment variable**</span></span> | <span data-ttu-id="a39bf-132">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-132">N/A</span></span> | <span data-ttu-id="a39bf-133">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="a39bf-134">Analýza data v japonštině</span><span class="sxs-lookup"><span data-stu-id="a39bf-134">Japanese date parsing</span></span>

- <span data-ttu-id="a39bf-135">Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="a39bf-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="a39bf-136">Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok (`false`).</span><span class="sxs-lookup"><span data-stu-id="a39bf-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="a39bf-137">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a39bf-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a39bf-138">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a39bf-138">Setting name</span></span> | <span data-ttu-id="a39bf-139">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a39bf-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a39bf-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a39bf-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="a39bf-141">`false` – podpora "Gannen" nebo "1" je podporována</span><span class="sxs-lookup"><span data-stu-id="a39bf-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="a39bf-142">`true` – podporuje se jenom 1.</span><span class="sxs-lookup"><span data-stu-id="a39bf-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="a39bf-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a39bf-143">**Environment variable**</span></span> | <span data-ttu-id="a39bf-144">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-144">N/A</span></span> | <span data-ttu-id="a39bf-145">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="a39bf-146">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="a39bf-146">Japanese year format</span></span>

- <span data-ttu-id="a39bf-147">Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="a39bf-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="a39bf-148">Výchozí: naformátujte první rok jako "Gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="a39bf-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="a39bf-149">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a39bf-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a39bf-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="a39bf-150">Setting name</span></span> | <span data-ttu-id="a39bf-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a39bf-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a39bf-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a39bf-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="a39bf-153">`false`-Format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="a39bf-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="a39bf-154">`true` – formát jako číslo</span><span class="sxs-lookup"><span data-stu-id="a39bf-154">`true` - format as number</span></span> |
| <span data-ttu-id="a39bf-155">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="a39bf-155">**Environment variable**</span></span> | <span data-ttu-id="a39bf-156">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-156">N/A</span></span> | <span data-ttu-id="a39bf-157">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="a39bf-157">N/A</span></span> |
