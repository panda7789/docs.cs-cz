---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981885"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Standardní verze 8.0 kategorie sady Unicode teď podporuje

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 data ve formátu Unicode byl upgradován z úrovně Unicode Standard verze 6.3 verzi 8.0.  Při požadování znaky kódování Unicode kategorií v rozhraní .NET Framework 4.6.2, nemusí některé výsledky odpovídají výsledky v předchozích verzích rozhraní .NET Framework.  Změnit to většinou ovlivňuje Čerokézština slabik a nové značky samohlásky Tai odrá a tón znaky.|
|Doporučení|Revize kódu a odebrat nebo změnit logiku, která závisí na pevně zakódované kategoriích znaků Unicode.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
