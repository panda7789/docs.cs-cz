---
title: Názvy identifikátorů
description: Přečtěte si pravidla platných názvů identifikátorů v C# programovacím jazyce.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673365"
---
# <a name="identifier-names"></a>Názvy identifikátorů

**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčet), člen, proměnná nebo obor názvů. Platné identifikátory musí dodržovat tato pravidla:

- Identifikátory musí začínat písmenem nebo `_`.
- Identifikátory můžou obsahovat znaky písmen Unicode, desítkové číslice, připojovací znaky Unicode, kombinaci znaků Unicode nebo formátovacích znaků Unicode. Další informace o kategoriích sady Unicode najdete v tématu [databáze kategorií Unicode](https://www.unicode.org/reports/tr44/).
Identifikátory, které odpovídají C# klíčovým slovům, můžete deklarovat pomocí předpony `@` v identifikátoru. `@` není součástí názvu identifikátoru. Například `@if` deklaruje identifikátor s názvem `if`. Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.

Úplnou definici platných identifikátorů najdete v [tématu identifikátory v tématu C# specifikace jazyka](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Zásady vytváření názvů

Kromě pravidel existuje několik [konvencí pojmenování](../../../standard/design-guidelines/naming-guidelines.md) identifikátorů používaných v rámci rozhraní API .NET. Podle konvence C# používají programy `PascalCase` pro názvy typů, obory názvů a všechny veřejné členy. Kromě toho jsou běžné následující konvence:

- Názvy rozhraní začínají velkým `I`m.
- Typy atributů končí slovem `Attribute`.
- Výčtové typy používají podstatná jména pro nepříznaky a v množném čísle pro příznaky.
- Identifikátory by neměly obsahovat dva po sobě jdoucí `_` znaky. Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.

## <a name="c-language-specification"></a>C# – jazyková specifikace

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [V programu v jazyce C#](./index.md)
- [C#Odkaz](../../language-reference/index.md)
- [Třídy](../classes-and-structs/classes.md)
- [Typy struktury](../../language-reference/builtin-types/struct.md)
- [Obory názvů](../namespaces/index.md)
- [Rozhraní](../interfaces/index.md)
- [Delegáty](../delegates/index.md)
