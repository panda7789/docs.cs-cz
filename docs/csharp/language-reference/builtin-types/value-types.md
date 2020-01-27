---
title: Typy hodnot – C# referenční informace
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6b96d65f657f2af1af5c9a245e956640ee06260e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748515"
---
# <a name="value-types-c-reference"></a>Typy hodnot (C# referenční)

*Typy hodnot* a [odkazové typy](../keywords/reference-types.md) jsou dvě hlavní kategorie C# typů. Proměnná typu hodnoty obsahuje instanci typu. To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu. Ve výchozím nastavení, při [přiřazení](../operators/assignment-operator.md), předávání argumentu metodě nebo vrácení výsledku metody, jsou zkopírovány hodnoty proměnných. V případě proměnných typu hodnoty jsou zkopírovány odpovídající instance typu. Následující příklad ukazuje toto chování:

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty, která je uložena v proměnné.

Pokud typ hodnoty obsahuje datový člen typu odkazu, je při zkopírování instance typu hodnota zkopírován pouze odkaz na instanci typu odkazu. Kopie i původní instance typu hodnoty mají přístup ke stejné instanci typu odkazu. Následující příklad ukazuje toto chování:

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Aby byl kód méně odolnější a robustnější, definujte a používejte neměnné typy hodnot. Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.

## <a name="kinds-of-value-types"></a>Druhy hodnotových typů

Typ hodnoty může být jeden z těchto dvou typů:

- [typ struktury](../keywords/struct.md), který zapouzdřuje data a související funkce
- [typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb

[Typ hodnoty s možnou hodnotou null](nullable-value-types.md) `T?` představuje všechny hodnoty svého základního typu hodnoty `T` a další hodnotu [null](../keywords/null.md) . Nelze přiřadit `null` k proměnné typu hodnoty, pokud se nejedná o typ hodnoty s možnou hodnotou null.

## <a name="built-in-value-types"></a>Předdefinované typy hodnot

C#poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:

- [Celočíselné číselné typy](integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](floating-point-numeric-types.md)
- [bool](bool.md) , která představuje logickou hodnotu
- [char](char.md) , který představuje znak Unicode UTF-16

Všechny jednoduché typy jsou struktury typy a liší se od jiných typů struktury v tom, že umožňují určité další operace:

- Můžete použít literály k poskytnutí hodnoty jednoduchého typu. Například `'A'` je literál typu `char` a `2001` je literál typu `int`.

- Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](../keywords/const.md) . Není možné mít konstanty jiných typů struktury.

- Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.

Počínaje C# 7,0 C# podporuje [Tuple hodnot](../../tuples.md). Hodnota řazené kolekce členů je hodnotový typ, ale ne jednoduchý typ.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Typy hodnot](~/_csharplang/spec/types.md#value-types)
- [Jednoduché typy](~/_csharplang/spec/types.md#simple-types)
- [Proměnné](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Typy odkazů](../keywords/reference-types.md)
