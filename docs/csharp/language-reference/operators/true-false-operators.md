---
title: operátory true a false - C# odkaz
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 7cbfca932b5f9f8a6f658e84204da5005da5ffb8
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609842"
---
# <a name="true-and-false-operators-c-reference"></a>operátory true a false (C# odkaz)

`true` Operátor vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand. `false` Operátor vrátí `bool` hodnotu `true` k označení, že operand je jednoznačně false. `true` a `false` operátory zaručené vzájemně doplňují. To znamená i `true` a `false` operátor může vrátit `bool` hodnotu `false` pro stejný operand. Pokud typ definuje jeden dva operátory, musíte také definovat další operátor.

> [!TIP]
> Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují tři vracející typ Boolean. C#poskytuje `&` a `|` operátory, které podporují tři vracející logiky pomocí `bool?` operandy. Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](boolean-logical-operators.md) článku.

## <a name="boolean-expressions"></a>logické výrazy

Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](../keywords/if-else.md), [proveďte](../keywords/do.md), [při](../keywords/while.md), a [ pro](../keywords/for.md) příkazy a [podmiňovací operátor `?:` ](conditional-operator.md). Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Podmíněné logické operátory definované uživatelem

Pokud typ s definovanou `true` a `false` operátory [přetížení](operator-overloading.md) [logického operátoru OR](boolean-logical-operators.md#logical-or-operator-) `|` nebo [logického operátoru AND](boolean-logical-operators.md#logical-and-operator-) `&` určitým způsobem, [podmíněné logického operátoru OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` nebo [podmíněné logického operátoru AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Příklad

Následující příklad představuje typ, který definuje obě `true` a `false` operátory. Typ také přetížení logického operátoru AND `&` takovým způsobem, který operátor `&&` také může být vyhodnocen pro operandy typu.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Všimněte si, že short-circuiting chování `&&` operátor. Když `GetFuelLaunchStatus` vrátí metoda `LaunchStatus.Red`, zpracovával pravý operand z `&&` operator nevyhodnocuje. Důvodem je, že `LaunchStatus.Red` je jednoznačně false. Potom výsledek logický operátor AND nezávisí na hodnotu operandu pravé. Výstup v příkladu vypadá takto:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [true – literál](../keywords/true-literal.md)
- [false – literál](../keywords/false-literal.md)
