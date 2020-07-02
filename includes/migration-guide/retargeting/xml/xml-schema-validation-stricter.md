---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617235"
---
### <a name="xml-schema-validation-is-stricter"></a>Ověřování schématu XML je přísnější

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5 je ověřování schématu XML přísnější. Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže. V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně. Tato změna ovlivní pouze aplikace, které cílí na .NET Framework 4,5.

#### <a name="suggestion"></a>Návrh

Pokud je potřeba ověření k dis.NET Framework 4,0, ověřování aplikace může cílit na verzi 4,0 .NET Framework. Při přecílení na .NET Framework 4,5 byste však měli provést revizi kódu, aby bylo zajištěno, že neplatné identifikátory URI (s mezerami) nejsou očekávány jako hodnoty atributu s datovým typem anyURI.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |
