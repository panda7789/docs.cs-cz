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
# <a name="run-time-configuration-options-for-globalization"></a>Možnosti konfigurace běhového běhu pro globalizaci

## <a name="invariant-mode"></a>Invariantní režim

- Určuje, jestli aplikace .NET Core běží v režimu invariantní v rámci globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi.
- Výchozí: Spusťte aplikaci s přístupem k kulturním datům (`false`).
- Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`– přístup k kulturním datům<br/>`true`-Run v režimu invariant |
| **Vlastnost MSBuild** | `InvariantGlobalization` | `false`– přístup k kulturním datům<br/>`true`-Run v režimu invariant |
| **Proměnná prostředí** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`– přístup k kulturním datům<br/>`1`-Run v režimu invariant |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

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

## <a name="era-year-ranges"></a>Rozsahy roků období

- Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data, která přecházejí do rozsahu <xref:System.ArgumentOutOfRangeException>dat v období, vyvolají.
- Výchozí: kontroly rozsahu jsou uvolněny`false`().
- Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`– Neuvolněné kontroly rozsahu<br/>`true`– při přetečení dojde k výjimce. |
| **Proměnná prostředí** | – | – |

## <a name="japanese-date-parsing"></a>Analýza data v japonštině

- Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".
- Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok`false`().
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`– "Gannen" nebo "1" je podporováno<br/>`true`– podporuje se jenom 1. |
| **Proměnná prostředí** | – | – |

## <a name="japanese-year-format"></a>Formát japonského roku

- Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.
- Výchozí: naformátujte první rok jako "Gannen"`false`().
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`– formátovat jako "Gannen"<br/>`true`– formátovat jako číslo |
| **Proměnná prostředí** | – | – |
