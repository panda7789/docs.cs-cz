---
title: Názvy identifikátorů
description: Přečtěte si pravidla platných názvů identifikátorů v C# programovacím jazyce.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589351"
---
# <a name="identifier-names"></a>Názvy identifikátorů

**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčet), člen, proměnná nebo obor názvů. Platné identifikátory musí dodržovat tato pravidla:

- Identifikátory musí začínat písmenem nebo `_`.
- Identifikátory můžou obsahovat znaky písmen Unicode, desítkové číslice, připojovací znaky Unicode, kombinaci znaků Unicode nebo formátovacích znaků Unicode. Další informace o kategoriích sady Unicode najdete v tématu [databáze kategorií Unicode](https://www.unicode.org/reports/tr44/).
Můžete deklarovat identifikátory, které odpovídají C# klíčovým slovům `@` pomocí předpony na identifikátoru. `@` Není součástí názvu identifikátoru. Například `@if` deklaruje identifikátor s názvem `if`. Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.

Úplnou definici platných identifikátorů najdete v [tématu identifikátory v tématu C# specifikace jazyka](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Zásady vytváření názvů

Kromě pravidel existuje několik konvencí pojmenování identifikátorů používaných [](../../../standard/design-guidelines/naming-guidelines.md) v rámci rozhraní API .NET. Podle konvence C# používají `PascalCase` programy pro názvy typů, obory názvů a všechny veřejné členy. Kromě toho jsou běžné následující konvence:

- Názvy rozhraní začínají velkým písmenem `I`.
- Typy atributů končí slovem `Attribute`.
- Výčtové typy používají podstatná jména pro nepříznaky a v množném čísle pro příznaky.
- Identifikátory by neměly obsahovat dva po `_` sobě jdoucí znaky. Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [V programu v jazyce C#](./index.md)
- [C#Odkaz](../../language-reference/index.md)
- [Třídy](../classes-and-structs/classes.md)
- [Struktury](../classes-and-structs/structs.md)
- [Obory názvů](../namespaces/index.md)
- [Rozhraní](../interfaces/index.md)
- [Delegáti](../delegates/index.md)
