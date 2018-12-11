---
title: operátory true a false - C# odkaz
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 0a75566fdb6222157ecda12a50fd78e22f92fcb4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245747"
---
# <a name="true-and-false-operators-c-reference"></a>operátory true a false (C# odkaz)

`true` Operátor vrátí [bool](bool.md) hodnotu `true` označuje jednoznačně true operand. `false` Operátor vrátí `bool` hodnotu `true` k označení, že operand je jednoznačně false. `true` a `false` operátory zaručené vzájemně doplňují. To znamená i `true` a `false` operátor může vrátit `bool` hodnotu `false` pro stejný operand. Pokud typ definuje jeden dva operátory, musíte také definovat další operátor.

Pokud typ s definovanou `true` a `false` operátory [přetížení](operator.md) [logického operátoru OR](../operators/or-operator.md) `|` nebo [logického operátoru AND](../operators/and-operator.md) `&` určitým způsobem, [podmíněné logického operátoru OR](../operators/conditional-or-operator.md) `||` nebo [podmíněné logického operátoru AND](../operators/conditional-and-operator.md) `&&`, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](if-else.md), [proveďte](do.md), [při](while.md), a [ pro](for.md) příkazy a [podmiňovací operátor `?:` ](../operators/conditional-operator.md). Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](../language-specification/index.md).

> [!TIP]
> Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují logický typ s hodnotou tři. Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

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
- [Klíčová slova jazyka C#](index.md)
- [Operátory jazyka C#](../operators/index.md)
- [`true` literál](true-literal.md)
- [`false` literál](false-literal.md)