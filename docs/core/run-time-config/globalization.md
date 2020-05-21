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
# <a name="run-time-configuration-options-for-globalization"></a>Možnosti konfigurace běhového běhu pro globalizaci

## <a name="invariant-mode"></a>Invariantní režim

- Určuje, jestli aplikace .NET Core běží v režimu invariantní v rámci globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi.
- Pokud toto nastavení vynecháte, aplikace se bude spouštět s přístupem k kulturním datům. To je ekvivalentní nastavení hodnoty na `false` .
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

- Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data, která přecházejí do rozsahu dat v období, vyvolají <xref:System.ArgumentOutOfRangeException> .
- Pokud toto nastavení vynecháte, budou se kontroly rozsahu zmírnit. To je ekvivalentní nastavení hodnoty na `false` .
- Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`– Neuvolněné kontroly rozsahu<br/>`true`– při přetečení dojde k výjimce. |
| **Proměnná prostředí** | – | – |

## <a name="japanese-date-parsing"></a>Analýza data v japonštině

- Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".
- Pokud toto nastavení vynecháte, řetězce, které obsahují buď "1" nebo "Gannen", se budou analyzovat jako rok úspěšně. To je ekvivalentní nastavení hodnoty na `false` .
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`– "Gannen" nebo "1" je podporováno<br/>`true`– podporuje se jenom 1. |
| **Proměnná prostředí** | – | – |

## <a name="japanese-year-format"></a>Formát japonského roku

- Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.
- Pokud toto nastavení vynecháte, první rok se zformátuje jako "Gannen". To je ekvivalentní nastavení hodnoty na `false` .
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`– formátovat jako "Gannen"<br/>`true`– formátovat jako číslo |
| **Proměnná prostředí** | – | – |

## <a name="nls"></a>NLS

- Určuje, jestli rozhraní .NET pro aplikace pro Windows používá rozhraní API pro globalizaci (National Language Support) nebo mezinárodní komponenty pro rozhraní Unicode (ICU). Rozhraní .NET 5,0 a novější verze používají rozhraní API globalizace ICU ve výchozím nastavení ve Windows 10 může 2019 Update a novějších verzí.
- Pokud toto nastavení vynecháte, .NET ve výchozím nastavení používá rozhraní API globalizace ICU. To je ekvivalentní nastavení hodnoty na `false` .
- Další informace naleznete v tématu [rozhraní API globalizace použití knihoven ICU ve Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).

| | Název nastavení | Hodnoty | Vedou |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.UseNls` | `false`-Použít rozhraní API globalizace ICU<br/>`true`– Použití rozhraní API globalizace NLS | .NET 5,0 |
| **Proměnná prostředí** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false`-Použít rozhraní API globalizace ICU<br/>`true`– Použití rozhraní API globalizace NLS | .NET 5,0 |
