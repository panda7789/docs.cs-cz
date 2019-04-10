---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234639"
---
### <a name="xml-schema-validation-is-stricter"></a>Je ověřování schématu XML přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je ověřování schématu XML přísnější. Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže. V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně. Změna ovlivní pouze aplikace, které se zaměřují na rozhraní .NET Framework 4.5.|
|Doporučení|V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.0 rozhraní .NET Framework. Pokud mění se cílení na .NET Framework 4.5, však musí ujistit se, že nejsou neplatné identifikátory URI (s mezerami) stanovená jako hodnoty atributů s datovým typem anyURI provedena revize kódu.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
