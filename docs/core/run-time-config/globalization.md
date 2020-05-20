---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703126"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="e7c2d-103">Možnosti konfigurace běhového běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="e7c2d-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="e7c2d-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="e7c2d-104">Invariant mode</span></span>

- <span data-ttu-id="e7c2d-105">Určuje, jestli aplikace .NET Core běží v režimu invariantní v rámci globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="e7c2d-106">Výchozí: Spusťte aplikaci s přístupem k kulturním datům ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="e7c2d-107">Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="e7c2d-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e7c2d-108">Setting name</span></span> | <span data-ttu-id="e7c2d-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7c2d-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e7c2d-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="e7c2d-111">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="e7c2d-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="e7c2d-112">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="e7c2d-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="e7c2d-113">**Vlastnost MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="e7c2d-114">`false`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="e7c2d-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="e7c2d-115">`true`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="e7c2d-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="e7c2d-116">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="e7c2d-117">`0`– přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="e7c2d-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="e7c2d-118">`1`-Run v režimu invariant</span><span class="sxs-lookup"><span data-stu-id="e7c2d-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="e7c2d-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="e7c2d-119">Examples</span></span>

<span data-ttu-id="e7c2d-120">soubor *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="e7c2d-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="e7c2d-121">Soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="e7c2d-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="e7c2d-122">Rozsahy roků období</span><span class="sxs-lookup"><span data-stu-id="e7c2d-122">Era year ranges</span></span>

- <span data-ttu-id="e7c2d-123">Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data, která přecházejí do rozsahu dat v období, vyvolají <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="e7c2d-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="e7c2d-124">Výchozí: kontroly rozsahu jsou uvolněny ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="e7c2d-125">Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="e7c2d-126">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e7c2d-126">Setting name</span></span> | <span data-ttu-id="e7c2d-127">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7c2d-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e7c2d-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="e7c2d-129">`false`– Neuvolněné kontroly rozsahu</span><span class="sxs-lookup"><span data-stu-id="e7c2d-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="e7c2d-130">`true`– při přetečení dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="e7c2d-131">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-131">**Environment variable**</span></span> | <span data-ttu-id="e7c2d-132">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-132">N/A</span></span> | <span data-ttu-id="e7c2d-133">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="e7c2d-134">Analýza data v japonštině</span><span class="sxs-lookup"><span data-stu-id="e7c2d-134">Japanese date parsing</span></span>

- <span data-ttu-id="e7c2d-135">Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="e7c2d-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="e7c2d-136">Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="e7c2d-137">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="e7c2d-138">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e7c2d-138">Setting name</span></span> | <span data-ttu-id="e7c2d-139">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7c2d-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e7c2d-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="e7c2d-141">`false`– "Gannen" nebo "1" je podporováno</span><span class="sxs-lookup"><span data-stu-id="e7c2d-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="e7c2d-142">`true`– podporuje se jenom 1.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="e7c2d-143">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-143">**Environment variable**</span></span> | <span data-ttu-id="e7c2d-144">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-144">N/A</span></span> | <span data-ttu-id="e7c2d-145">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="e7c2d-146">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="e7c2d-146">Japanese year format</span></span>

- <span data-ttu-id="e7c2d-147">Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="e7c2d-148">Výchozí: naformátujte první rok jako "Gannen" ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="e7c2d-149">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="e7c2d-150">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e7c2d-150">Setting name</span></span> | <span data-ttu-id="e7c2d-151">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7c2d-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e7c2d-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="e7c2d-153">`false`– formátovat jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="e7c2d-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="e7c2d-154">`true`– formátovat jako číslo</span><span class="sxs-lookup"><span data-stu-id="e7c2d-154">`true` - format as number</span></span> |
| <span data-ttu-id="e7c2d-155">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-155">**Environment variable**</span></span> | <span data-ttu-id="e7c2d-156">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-156">N/A</span></span> | <span data-ttu-id="e7c2d-157">–</span><span class="sxs-lookup"><span data-stu-id="e7c2d-157">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="e7c2d-158">NLS</span><span class="sxs-lookup"><span data-stu-id="e7c2d-158">NLS</span></span>

- <span data-ttu-id="e7c2d-159">Určuje, jestli rozhraní .NET pro aplikace pro Windows používá rozhraní API pro globalizaci (National Language Support) nebo mezinárodní komponenty pro rozhraní Unicode (ICU).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-159">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="e7c2d-160">Rozhraní .NET 5,0 a novější verze používají rozhraní API globalizace ICU ve výchozím nastavení ve Windows 10 může 2019 Update a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-160">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="e7c2d-161">Pokud toto nastavení vynecháte, .NET ve výchozím nastavení používá rozhraní API globalizace ICU.</span><span class="sxs-lookup"><span data-stu-id="e7c2d-161">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="e7c2d-162">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="e7c2d-162">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="e7c2d-163">Další informace naleznete v tématu [rozhraní API globalizace použití knihoven ICU ve Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="e7c2d-163">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="e7c2d-164">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="e7c2d-164">Setting name</span></span> | <span data-ttu-id="e7c2d-165">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e7c2d-165">Values</span></span> | <span data-ttu-id="e7c2d-166">Vedou</span><span class="sxs-lookup"><span data-stu-id="e7c2d-166">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e7c2d-167">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-167">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="e7c2d-168">`false`-Použít rozhraní API globalizace ICU</span><span class="sxs-lookup"><span data-stu-id="e7c2d-168">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="e7c2d-169">`true`– Použití rozhraní API globalizace NLS</span><span class="sxs-lookup"><span data-stu-id="e7c2d-169">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="e7c2d-170">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e7c2d-170">.NET 5.0</span></span> |
| <span data-ttu-id="e7c2d-171">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="e7c2d-171">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="e7c2d-172">`false`-Použít rozhraní API globalizace ICU</span><span class="sxs-lookup"><span data-stu-id="e7c2d-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="e7c2d-173">`true`– Použití rozhraní API globalizace NLS</span><span class="sxs-lookup"><span data-stu-id="e7c2d-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="e7c2d-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e7c2d-174">.NET 5.0</span></span> |
