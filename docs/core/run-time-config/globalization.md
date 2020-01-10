---
title: Nastavení konfigurace globalizace
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují aspekty globalizace aplikace .NET Core, například jak analyzuje data v japonštině.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 76cd4a0a0f93f4df3ff243c6024b952576e8e6cb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740541"
---
# <a name="run-time-configuration-options-for-globalization"></a>Možnosti konfigurace běhového běhu pro globalizaci

## <a name="invariant-mode"></a>Invariantní režim

- Určuje, jestli aplikace .NET Core běží v invariantní režimu globalizace bez přístupu k datům a chováním specifickým pro jazykovou verzi nebo jestli má přístup k kulturním datům.
- Výchozí: Spusťte aplikaci s přístupem k kulturním datům (`false`).
- Další informace najdete v tématu [režim invariant globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false` – přístup k kulturním datům<br/>`true`-spustit v režimu invariantování |
| **Proměnná prostředí** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0` – přístup k kulturním datům<br/>`1`-spustit v režimu invariantování |

## <a name="era-year-ranges"></a>Rozsahy roků období

- Určuje, zda jsou uvolněny oblasti pro kalendáře, které podporují více mazání, nebo zda data přetečení rozsahu data v období přecházejí <xref:System.ArgumentOutOfRangeException>.
- Výchozí: kontroly rozsahu jsou uvolněny (`false`).
- Další informace najdete v tématu [kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` – Neuvolněné kontroly rozsahu<br/>`true` – přetečení způsobují výjimku. |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |

## <a name="japanese-date-parsing"></a>Analýza data v japonštině

- Určuje, zda je řetězec, který obsahuje hodnotu "1" nebo "Gannen" jako rok úspěšně analyzován, nebo zda je podporován pouze "1".
- Výchozí: Analyzujte řetězce, které obsahují buď "1" nebo "Gannen" jako rok (`false`).
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false` – podpora "Gannen" nebo "1" je podporována<br/>`true` – podporuje se jenom 1. |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |

## <a name="japanese-year-format"></a>Formát japonského roku

- Určuje, zda je první rok japonského období v japonštině formátován jako "Gannen" nebo jako číslo.
- Výchozí: naformátujte první rok jako "Gannen" (`false`).
- Další informace najdete v tématu [reprezentace kalendářních dat v kalendářích s více vymazáními](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-Format jako "Gannen"<br/>`true` – formát jako číslo |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
