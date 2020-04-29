---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 7668c345181d7c08cfca9c5cb76b8addd76223ec
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506802"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="0fb27-103">Možnosti konfigurace běhového běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="0fb27-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="0fb27-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="0fb27-104">Invariant mode</span></span>

- <span data-ttu-id="0fb27-105">Určuje, jestli aplikace .NET Core běží v režimu invariantní v rámci globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="0fb27-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="0fb27-106">Výchozí: Spusťte aplikaci s přístupem k kulturním datům (`false`).</span><span class="sxs-lookup"><span data-stu-id="0fb27-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="0fb27-107">Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="0fb27-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="0fb27-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="0fb27-108">Setting name</span></span> | <span data-ttu-id="0fb27-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="0fb27-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fb27-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fb27-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="0fb27-111">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="0fb27-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="0fb27-112">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="0fb27-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0fb27-113">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="0fb27-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="0fb27-114">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="0fb27-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="0fb27-115">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="0fb27-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0fb27-116">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="0fb27-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="0fb27-117">`0`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="0fb27-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="0fb27-118">`1`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="0fb27-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="0fb27-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="0fb27-119">Examples</span></span>

<span data-ttu-id="0fb27-120">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="0fb27-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="0fb27-121">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="0fb27-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="0fb27-122">Rozsahy roků období</span><span class="sxs-lookup"><span data-stu-id="0fb27-122">Era year ranges</span></span>

- <span data-ttu-id="0fb27-123">Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data, která přecházejí do rozsahu <xref:System.ArgumentOutOfRangeException>dat v období, vyvolají.</span><span class="sxs-lookup"><span data-stu-id="0fb27-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="0fb27-124">Výchozí: kontroly rozsahu jsou uvolněny`false`().</span><span class="sxs-lookup"><span data-stu-id="0fb27-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="0fb27-125">Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="0fb27-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="0fb27-126">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="0fb27-126">Setting name</span></span> | <span data-ttu-id="0fb27-127">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="0fb27-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fb27-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fb27-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="0fb27-129">`false`– Neuvolněné kontroly rozsahu</span><span class="sxs-lookup"><span data-stu-id="0fb27-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="0fb27-130">`true`– při přetečení dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0fb27-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="0fb27-131">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="0fb27-131">**Environment variable**</span></span> | <span data-ttu-id="0fb27-132">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-132">N/A</span></span> | <span data-ttu-id="0fb27-133">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="0fb27-134">Analýza data v japonštině</span><span class="sxs-lookup"><span data-stu-id="0fb27-134">Japanese date parsing</span></span>

- <span data-ttu-id="0fb27-135">Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="0fb27-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="0fb27-136">Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok`false`().</span><span class="sxs-lookup"><span data-stu-id="0fb27-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="0fb27-137">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0fb27-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0fb27-138">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="0fb27-138">Setting name</span></span> | <span data-ttu-id="0fb27-139">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="0fb27-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fb27-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fb27-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="0fb27-141">`false`– "Gannen" nebo "1" je podporováno</span><span class="sxs-lookup"><span data-stu-id="0fb27-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="0fb27-142">`true`– podporuje se jenom 1.</span><span class="sxs-lookup"><span data-stu-id="0fb27-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="0fb27-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="0fb27-143">**Environment variable**</span></span> | <span data-ttu-id="0fb27-144">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-144">N/A</span></span> | <span data-ttu-id="0fb27-145">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="0fb27-146">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="0fb27-146">Japanese year format</span></span>

- <span data-ttu-id="0fb27-147">Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="0fb27-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="0fb27-148">Výchozí: naformátujte první rok jako "Gannen"`false`().</span><span class="sxs-lookup"><span data-stu-id="0fb27-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="0fb27-149">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0fb27-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0fb27-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="0fb27-150">Setting name</span></span> | <span data-ttu-id="0fb27-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="0fb27-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fb27-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fb27-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="0fb27-153">`false`– formátovat jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="0fb27-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="0fb27-154">`true`– formátovat jako číslo</span><span class="sxs-lookup"><span data-stu-id="0fb27-154">`true` - format as number</span></span> |
| <span data-ttu-id="0fb27-155">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="0fb27-155">**Environment variable**</span></span> | <span data-ttu-id="0fb27-156">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-156">N/A</span></span> | <span data-ttu-id="0fb27-157">–</span><span class="sxs-lookup"><span data-stu-id="0fb27-157">N/A</span></span> |
