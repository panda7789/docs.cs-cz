---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802776"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="f34b3-103">Možnosti konfigurace běhového běhu pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="f34b3-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="f34b3-104">Invariantní režim</span><span class="sxs-lookup"><span data-stu-id="f34b3-104">Invariant mode</span></span>

- <span data-ttu-id="f34b3-105">Určuje, jestli aplikace .NET Core běží v invariantní režimu globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi nebo jestli má přístup k kulturním datům.</span><span class="sxs-lookup"><span data-stu-id="f34b3-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="f34b3-106">Výchozí: Spusťte aplikaci s přístupem k kulturním datům (`false`).</span><span class="sxs-lookup"><span data-stu-id="f34b3-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="f34b3-107">Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="f34b3-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="f34b3-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34b3-108">Setting name</span></span> | <span data-ttu-id="f34b3-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34b3-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34b3-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34b3-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="f34b3-111">`false` – přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="f34b3-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="f34b3-112">`true`-spustit v režimu invariantování</span><span class="sxs-lookup"><span data-stu-id="f34b3-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="f34b3-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34b3-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="f34b3-114">`0` – přístup k kulturním datům</span><span class="sxs-lookup"><span data-stu-id="f34b3-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="f34b3-115">`1`-spustit v režimu invariantování</span><span class="sxs-lookup"><span data-stu-id="f34b3-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="f34b3-116">Rozsahy roků období</span><span class="sxs-lookup"><span data-stu-id="f34b3-116">Era year ranges</span></span>

- <span data-ttu-id="f34b3-117">Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data přetečení rozsahu data v období přecházejí <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="f34b3-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="f34b3-118">Výchozí: kontroly rozsahu jsou uvolněny (`false`).</span><span class="sxs-lookup"><span data-stu-id="f34b3-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="f34b3-119">Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="f34b3-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="f34b3-120">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34b3-120">Setting name</span></span> | <span data-ttu-id="f34b3-121">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34b3-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34b3-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34b3-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="f34b3-123">`false` – Neuvolněné kontroly rozsahu</span><span class="sxs-lookup"><span data-stu-id="f34b3-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="f34b3-124">`true` – přetečení způsobují výjimku.</span><span class="sxs-lookup"><span data-stu-id="f34b3-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="f34b3-125">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34b3-125">**Environment variable**</span></span> | <span data-ttu-id="f34b3-126">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-126">N/A</span></span> | <span data-ttu-id="f34b3-127">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="f34b3-128">Analýza data v japonštině</span><span class="sxs-lookup"><span data-stu-id="f34b3-128">Japanese date parsing</span></span>

- <span data-ttu-id="f34b3-129">Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".</span><span class="sxs-lookup"><span data-stu-id="f34b3-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="f34b3-130">Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok (`false`).</span><span class="sxs-lookup"><span data-stu-id="f34b3-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="f34b3-131">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="f34b3-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="f34b3-132">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34b3-132">Setting name</span></span> | <span data-ttu-id="f34b3-133">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34b3-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34b3-134">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34b3-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="f34b3-135">`false` – podpora "Gannen" nebo "1" je podporována</span><span class="sxs-lookup"><span data-stu-id="f34b3-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="f34b3-136">`true` – podporuje se jenom 1.</span><span class="sxs-lookup"><span data-stu-id="f34b3-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="f34b3-137">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34b3-137">**Environment variable**</span></span> | <span data-ttu-id="f34b3-138">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-138">N/A</span></span> | <span data-ttu-id="f34b3-139">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="f34b3-140">Formát japonského roku</span><span class="sxs-lookup"><span data-stu-id="f34b3-140">Japanese year format</span></span>

- <span data-ttu-id="f34b3-141">Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.</span><span class="sxs-lookup"><span data-stu-id="f34b3-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="f34b3-142">Výchozí: naformátujte první rok jako "Gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="f34b3-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="f34b3-143">Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="f34b3-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="f34b3-144">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="f34b3-144">Setting name</span></span> | <span data-ttu-id="f34b3-145">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f34b3-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="f34b3-146">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f34b3-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="f34b3-147">`false`-Format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="f34b3-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="f34b3-148">`true` – formát jako číslo</span><span class="sxs-lookup"><span data-stu-id="f34b3-148">`true` - format as number</span></span> |
| <span data-ttu-id="f34b3-149">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="f34b3-149">**Environment variable**</span></span> | <span data-ttu-id="f34b3-150">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-150">N/A</span></span> | <span data-ttu-id="f34b3-151">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="f34b3-151">N/A</span></span> |
