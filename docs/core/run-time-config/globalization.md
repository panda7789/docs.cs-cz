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
# <a name="run-time-configuration-options-for-globalization"></a>Možnosti konfigurace za běhu pro globalizaci

## <a name="invariant-mode"></a>Invariantní režim

- Určuje, zda aplikace .NET Core běží v invariantním režimu globalizace bez přístupu k datům a chování můře specifickým pro jazykovou verzi nebo zda má přístup ke kulturním datům.
- Výchozí: Spusťte aplikaci s`false`přístupem ke kulturním datům ( ).
- Další informace naleznete v tématu [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false`- přístup ke kulturním údajům<br/>`true`- běh v invariantním režimu |
| **MSBuild, vlastnost** | `InvariantGlobalization` | `false`- přístup ke kulturním údajům<br/>`true`- běh v invariantním režimu |
| **Proměnná prostředí** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- přístup ke kulturním údajům<br/>`1`- běh v invariantním režimu |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Rozsahy let era

- Určuje, zda jsou kontroly rozsahu pro kalendáře, které podporují více období, uvolněná nebo <xref:System.ArgumentOutOfRangeException>zda jsou data, která přetečou časové období období období, vyvolána .
- Výchozí: Kontroly rozsahu`false`jsou uvolněné ( ).
- Další informace naleznete v [tématu Kalendáře, epochy a rozsahy dat: Kontroly uvolněného rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- uvolněné kontroly dosahu<br/>`true`- přetečení způsobí výjimku |
| **Proměnná prostředí** | Není dostupné. | Není dostupné. |

## <a name="japanese-date-parsing"></a>Analýza japonského data

- Určuje, zda řetězec, který obsahuje "1" nebo "Gannen" jako rok analyzuje úspěšně, nebo zda je podporován pouze "1".
- Výchozí: Analyzují řetězce, které obsahují buď "1" nebo`false`"Gannen" jako rok ( ).
- Další informace naleznete [v tématu Představují data v kalendářích s více epochami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- "Gannen" nebo "1" je podporován<br/>`true`- je podporováno pouze "1" |
| **Proměnná prostředí** | Není dostupné. | Není dostupné. |

## <a name="japanese-year-format"></a>Formát japonského roku

- Určuje, zda je první rok éry japonského kalendáře formátován jako "Gannen" nebo jako číslo.
- Výchozí: Naformátujte první rok jako`false`"Gannen" ( ).
- Další informace naleznete [v tématu Představují data v kalendářích s více epochami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- formát jako "Gannen"<br/>`true`- formát jako číslo |
| **Proměnná prostředí** | Není dostupné. | Není dostupné. |
