---
title: operátory true a false - C# odkaz
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 003ca79343de14aa3a3b1d95d84d0637c873652c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66307075"
---
# <a name="true-and-false-operators-c-reference"></a>operátory true a false (C# odkaz)

`true` Operátor vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand. `false` Operátor vrátí `bool` hodnotu `true` k označení, že operand je jednoznačně false. `true` a `false` operátory zaručené vzájemně doplňují. To znamená i `true` a `false` operátor může vrátit `bool` hodnotu `false` pro stejný operand. Pokud typ definuje jeden dva operátory, musíte také definovat další operátor.

Pokud typ s definovanou `true` a `false` operátory [přetížení](../keywords/operator.md) [logického operátoru OR](boolean-logical-operators.md#logical-or-operator-) `|` nebo [logického operátoru AND](boolean-logical-operators.md#logical-and-operator-) `&` určitým způsobem, [podmíněné logického operátoru OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` nebo [podmíněné logického operátoru AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](../keywords/if-else.md), [proveďte](../keywords/do.md), [při](../keywords/while.md), a [ pro](../keywords/for.md) příkazy a [podmiňovací operátor `?:` ](conditional-operator.md). Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

> [!TIP]
> Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují tři vracející typ Boolean. C#poskytuje `&` a `|` operátory, které podporují tři vracející logiky pomocí `bool?` operandy. Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](boolean-logical-operators.md) článku.

Následující příklad představuje typ, který definuje obě `true` a `false` operátory. Kromě toho přetížení logického operátoru AND `&` takovým způsobem, který operátor `&&` také může být vyhodnocen pro operandy typu.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Všimněte si, že short-circuiting chování `&&` operátor. Když `GetFuelLaunchStatus` vrátí metoda `LaunchStatus.Red`, druhý operand `&&` operator nevyhodnocuje. Důvodem je, že `LaunchStatus.Red` je jednoznačně false. Potom výsledek logický operátor AND nezávisí na hodnotu druhého operandu. Výstup v příkladu vypadá takto:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [`true` literál](../keywords/true-literal.md)
- [`false` literál](../keywords/false-literal.md)
