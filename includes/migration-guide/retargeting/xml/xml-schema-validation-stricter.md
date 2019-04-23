---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118474"
---
### <a name="xml-schema-validation-is-stricter"></a>Je ověřování schématu XML přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je ověřování schématu XML přísnější. Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže. V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně. Změna ovlivní pouze aplikace, které se zaměřují na rozhraní .NET Framework 4.5.|
|Doporučení|V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.0 rozhraní .NET Framework. Pokud mění se cílení na .NET Framework 4.5, však musí ujistit se, že nejsou neplatné identifikátory URI (s mezerami) stanovená jako hodnoty atributů s datovým typem anyURI provedena revize kódu.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
