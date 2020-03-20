---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857564"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Nyní podporované kategorie standardu Unicode verze 8.0

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 byla data unicode upgradována z unicode standard verze 6.3 na verzi 8.0.  Při požadování kategorií znaků Unicode v rozhraní .NET Framework 4.6.2 nemusí některé výsledky odpovídat výsledkům v předchozích verzích rozhraní .NET Framework.  Tato změna se týká především Cherokee slabiky a New Tai Lue samohlásek znamení a tón značky.|
|Návrh|Zkontrolujte kód a odeberte/změňte logiku, která závisí na pevně zakódovaných kategoriích znaků Unicode.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
