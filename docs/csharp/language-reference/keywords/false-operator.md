---
title: false – – operátor (referenční dokumentace jazyka C#)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152302"
---
# <a name="false-operator-c-reference"></a>false – – operátor (referenční dokumentace jazyka C#)

Vrátí [bool](bool.md) hodnotu `true` k označení, že operand je jednoznačně false. Pokud typ definuje `false` operátoru, je třeba definovat [true – – operátor](true-operator.md). `true` a `false` operátory zaručené vzájemně doplňují.

> [!TIP]
> Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují logický typ s hodnotou tři. Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

Pokud typ s definovanou `false` operátor [přetížení](operator.md) [logického operátoru AND](../operators/and-operator.md) `&` určitým způsobem, [podmíněné logického operátoru AND](../operators/conditional-and-operator.md) `&&`, což je short-circuiting, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

Následující příklad představuje typ, který definuje obě `true` a `false` operátory. Kromě toho přetížení logického operátoru AND `&` takovým způsobem, který operátor `&&` také může být vyhodnocen pro operandy typu.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Všimněte si, že short-circuiting chování `&&` operátor. Když `GetFuelLaunchStatus` vrátí metoda `LaunchStatus.Red`, druhý operand `&&` operator nevyhodnocuje. Důvodem je, že `LaunchStatus.Red` je jednoznačně false. Potom výsledek logický operátor AND nezávisí na hodnotu druhého operandu. Výstup v příkladu vypadá takto:

```console
Getting fuel launch status...
Wait!
```

Všimněte si také, že podmíněný výraz [podmiňovací operátor `?:` ](../operators/conditional-operator.md) je `LaunchStatus` typu. Je to možné, protože `LaunchStatus` definuje `true` operátor. Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Operátory jazyka C#](../operators/index.md)
- [`false` literál](false-literal.md)