---
title: Názvy identifikátorů
description: Další pravidla pro názvy platný identifikátor v programovacím jazyce C#.
ms.date: 08/21/2018
ms.openlocfilehash: 2147b3846d4ba6d5471b81448489c6d716e3cd61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680490"
---
# <a name="identifier-names"></a>Názvy identifikátorů

**Identifikátor** je název přiřadit k typu (třída, rozhraní, struktury, delegáta nebo výčtu), člen, proměnná nebo oboru názvů. Platné identifikátory musí dodržovat tato pravidla:

- Identifikátory musí začínat písmenem, nebo `_`.
- Identifikátory mohou obsahovat písmena, znaky desítkových číslic, připojení znaků Unicode, kombinace znaků Unicode nebo formátování znaků Unicode kódování Unicode. Další informace o kódování Unicode kategorií, najdete v článku [databáze kategorie sady Unicode](https://www.unicode.org/reports/tr44/).
Je možné deklarovat identifikátory, které odpovídají klíčová slova jazyka C# s použitím `@` předpony u identifikátoru. `@` Není součástí název identifikátoru. Například `@if` deklaruje identifikátor s názvem `if`. Tyto [verbatim identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarované v jiných jazycích.

Kompletní definici platné identifikátory, najdete v článku [identifikátory tématu ve specifikaci jazyka C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Zásady vytváření názvů

Kromě pravidel, existuje mnoho identifikátoru [zásady vytváření názvů](../../../standard/design-guidelines/naming-guidelines.md) používaný v celém rozhraní .NET API. Podle konvence, C# programy používají `PascalCase` pro názvy typů, obory názvů a všechny veřejné členy. Kromě toho jsou společné následující konvence:

- Rozhraní názvy začíná na velké `I`.
- Atribut typy končí slovem `Attribute`.
- Typy výčtu pomocí příznaků singulární podstatné jméno pro jiné příznaky a množném čísle podstatné jméno.
- Identifikátory by neměly obsahovat dva po sobě jdoucích `_` znaků. Tyto názvy jsou vyhrazené pro identifikátory generovaný kompilátorem.

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [V programu v jazyce C#](../inside-a-program/index.md)
- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Třídy](../classes-and-structs/classes.md)
- [Struktury](../classes-and-structs/structs.md)
- [Obory názvů](../namespaces/index.md)
- [Rozhraní](../interfaces/index.md)
- [Delegáti](../delegates/index.md)
