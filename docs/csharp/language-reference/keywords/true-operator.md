---
title: True – – operátor (C# odkaz)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130673"
---
# <a name="true-operator-c-reference"></a>True – – operátor (C# odkaz)

Vrátí [bool](bool.md) hodnotu `true` označuje jednoznačně true operand. Pokud typ definuje `true` operátoru, je třeba definovat [false – – operátor](false-operator.md). `true` a `false` operátory zaručené vzájemně doplňují.

Pro příklad, který definuje obě `true` a `false` operátory, najdete v článku [false – – operátor](false-operator.md) článku.

> [!TIP]
> Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují logický typ s hodnotou tři. Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

Pokud typ s definovanou `true` operátor [přetížení](operator.md) [logický operátor OR](../operators/or-operator.md) `|` určitým způsobem, [podmíněné logický operátor OR](../operators/conditional-or-operator.md) `||`, což je short-circuiting, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](if-else.md), [proveďte](do.md), [při](while.md), a [ pro](for.md) příkazy a [podmiňovací operátor `?:` ](../operators/conditional-operator.md). Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Operátory jazyka C#](../operators/index.md)
- [`true` literál](true-literal.md)