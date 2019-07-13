---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857564"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Standardní verze 8.0 kategorie sady Unicode teď podporuje

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 data ve formátu Unicode byl upgradován z úrovně Unicode Standard verze 6.3 verzi 8.0.  Při požadování znaky kódování Unicode kategorií v rozhraní .NET Framework 4.6.2, nemusí některé výsledky odpovídají výsledky v předchozích verzích rozhraní .NET Framework.  Změnit to většinou ovlivňuje Čerokézština slabik a nové značky samohlásky Tai odrá a tón znaky.|
|Doporučení|Revize kódu a odebrat nebo změnit logiku, která závisí na pevně zakódované kategoriích znaků Unicode.|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

