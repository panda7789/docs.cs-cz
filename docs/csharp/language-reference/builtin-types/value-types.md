---
description: 'Seznamte se s typy hodnot, jejich druhy a integrovanými v jazyce C. #'
title: Hodnotové typy – reference jazyka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 7826e71fee235d32655ccfbc9060c3bbb48d76c5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134767"
---
# <a name="value-types-c-reference"></a>Typy hodnot (Referenční dokumentace jazyka C#)

*Typy hodnot* a [odkazové typy](../keywords/reference-types.md) jsou dvě hlavní kategorie typů C#. Proměnná typu hodnoty obsahuje instanci typu. To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu. Ve výchozím nastavení, při [přiřazení](../operators/assignment-operator.md), předávání argumentu metodě a vrácení výsledku metody, jsou zkopírovány hodnoty proměnných. V případě proměnných typu hodnoty jsou zkopírovány odpovídající instance typu. Následující příklad ukazuje toto chování:

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty, která je uložena v proměnné.

Pokud typ hodnoty obsahuje datový člen typu odkazu, je při zkopírování instance typu hodnota zkopírován pouze odkaz na instanci typu odkazu. Kopie i původní instance typu hodnoty mají přístup ke stejné instanci typu odkazu. Následující příklad ukazuje toto chování:

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Aby byl kód méně odolnější a robustnější, definujte a používejte neměnné typy hodnot. Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.

## <a name="kinds-of-value-types"></a>Druhy hodnotových typů

Typ hodnoty může být jeden z těchto dvou typů:

- [typ struktury](struct.md), který zapouzdřuje data a související funkce
- [typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb

[Typ hodnoty s možnou hodnotou](nullable-value-types.md) null `T?` reprezentuje všechny hodnoty svého základního typu hodnoty `T` a další hodnotu [null](../keywords/null.md) . Nemůžete přiřadit `null` proměnné typu hodnoty, pokud se nejedná o typ hodnoty s možnou hodnotou null.

## <a name="built-in-value-types"></a>Předdefinované typy hodnot

Jazyk C# poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:

- [Celočíselné typy](integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](floating-point-numeric-types.md)
- [bool](bool.md) , která představuje logickou hodnotu
- [char](char.md) , který představuje znak Unicode UTF-16

Všechny jednoduché typy jsou struktury typy a liší se od jiných typů struktury v tom, že umožňují určité další operace:

- Můžete použít literály k poskytnutí hodnoty jednoduchého typu. Například `'A'` je literál typu, který `char` `2001` je literálem typu `int` .

- Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](../keywords/const.md) . Není možné mít konstanty jiných typů struktury.

- Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.

Počínaje jazykem C# 7,0 podporuje C# [n-tice hodnot](value-tuples.md). Hodnota řazené kolekce členů je hodnotový typ, ale ne jednoduchý typ.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Typy hodnot](~/_csharplang/spec/types.md#value-types)
- [Jednoduché typy](~/_csharplang/spec/types.md#simple-types)
- [Proměnné](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Odkazové typy](../keywords/reference-types.md)
