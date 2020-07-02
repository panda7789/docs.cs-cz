---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614484"
---
### <a name="path-colon-checks-are-stricter"></a>Kontroly dvojtečky cest jsou přísnější

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (jak v délce, tak ve formátu). Kontroluje správnost syntaxe oddělovače jednotek (dvojtečky), která měla vedlejší účinky blokování některých cest URI v několika rozhraních API pro výběr cest, kde se používají k tolerování.

#### <a name="suggestion"></a>Návrh

Pokud předáváte identifikátor URI ovlivněným rozhraním API, upravte nejprve řetězec na platnou cestu.<ul><li>Ruční odebrání schématu z adres URL (např. odebrání `file://` z adres URL)

- Předat identifikátor URI <xref:System.Uri> třídě a použít<xref:System.Uri.LocalPath>

Alternativně můžete odhlásit normalizaci nové cesty nastavením `Switch.System.IO.UseLegacyPathHandling` přepínače AppContext na hodnotu true.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
