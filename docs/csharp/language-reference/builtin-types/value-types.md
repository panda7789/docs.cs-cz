---
title: Typy hodnot – odkaz jazyka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399579"
---
# <a name="value-types-c-reference"></a>Typy hodnot (odkaz C# )

*Typy hodnot* a [typy odkazů](../keywords/reference-types.md) jsou dvě hlavní kategorie c# typy. Proměnná typu hodnoty obsahuje instanci typu. To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu. Ve výchozím nastavení se při [přiřazení](../operators/assignment-operator.md), předání argumentu metodě a vrácení výsledku metody zkopírují hodnoty proměnných. V případě proměnných typu hodnoty se zkopírují odpovídající instance typu. Následující příklad ukazuje, že chování:

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty uloženou v proměnné.

Pokud typ hodnoty obsahuje datový člen typu odkazu, zkopíruje se při kopírování instance typu hodnoty pouze odkaz na instanci typu odkazu. Instance kopie i původní instance typu value mají přístup ke stejné instanci typu odkazu. Následující příklad ukazuje, že chování:

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Chcete-li, aby váš kód byl méně náchylný k chybám a robustnější, definujte a používejte neměnné typy hodnot. Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.

## <a name="kinds-of-value-types"></a>Druhy typů hodnot

Typ hodnoty může být jeden ze dvou následujících typů:

- [typ struktury](struct.md), který zapouzdřuje data a související funkce
- [typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb

`T?` [Typ hodnoty s možnou hodnotou null](nullable-value-types.md) představuje všechny hodnoty jeho základního typu `T` hodnoty a další [hodnotu null.](../keywords/null.md) Proměnné typu `null` hodnoty nelze přiřadit, pokud se nejedná o hodnotu s hodnotou s možnou hodnotou s hodnotou s možnou hodnotou.

## <a name="built-in-value-types"></a>Předdefinované typy hodnot

C# poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:

- [Celočíselné typy](integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](floating-point-numeric-types.md)
- [bool,](bool.md) který představuje logickou hodnotu
- [znak,](char.md) který představuje znak Unicode UTF-16

Všechny jednoduché typy jsou typy struktur a liší se od jiných typů struktury v tom, že umožňují určité další operace:

- Literály můžete použít k zadání hodnoty jednoduchého typu. Například `'A'` je literál typu `char` `2001` a je literál `int`typu .

- Můžete deklarovat konstanty jednoduchých typů s [const](../keywords/const.md) klíčové slovo. Není možné mít konstanty jiných typů struktur.

- Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.

Počínaje C# 7.0, C# podporuje [kolekce členů hodnot](../../tuples.md). Řazená kolekce členů s hodnotou je typ hodnoty, ale ne jednoduchý typ.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Typy hodnot](~/_csharplang/spec/types.md#value-types)
- [Jednoduché typy](~/_csharplang/spec/types.md#simple-types)
- [Proměnné](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Referenční typy](../keywords/reference-types.md)
