---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621073"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Podporuje se teď Standard Unicode Standard verze 8,0.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 byla data Unicode upgradována z verze Standard Unicode 6,3 na verzi 8,0.  Při požadování kategorií znaků Unicode v .NET Framework 4.6.2 nemusí některé výsledky odpovídat výsledkům v předchozích .NET Framework verzích.  Tato změna většinou ovlivňuje modifikátory slabik a nové Tai Lue – značky a značky tónů.

#### <a name="suggestion"></a>Návrh

Zkontrolujte kód a odeberte nebo změňte logiku, která závisí na pevně zakódovaných kategoriích znaků Unicode.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
