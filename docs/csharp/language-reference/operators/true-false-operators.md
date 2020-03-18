---
title: true a false operátory - C# odkaz
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 5ccd08a348478902bbbac36e99acf7ffc1fc814b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846213"
---
# <a name="true-and-false-operators-c-reference"></a>true a false operátory (C# odkaz)

Operátor `true` vrátí [bool](../builtin-types/bool.md) `true` hodnotu označující, že jeho operand je určitě true. Operátor `false` vrátí `bool` hodnotu `true` označující, že jeho operand je rozhodně false. A `true` `false` operátory se nezaručují, aby se vzájemně doplňovaly. To znamená, `true` že `false` i operátor `bool` `false` může vrátit hodnotu pro stejný operand. Pokud typ definuje jeden ze dvou operátorů, musí také definovat jiný operátor.

> [!TIP]
> Použijte `bool?` typ, pokud potřebujete podporovat logiku se třemi hodnotami (například při práci s databázemi, které podporují tříhodnotný logický typ). C# poskytuje `&` `|` a operátory, které podporují `bool?` logiku se třemi hodnotami s operandy. Další informace naleznete v části [Nullable Boolean logické operátory](boolean-logical-operators.md#nullable-boolean-logical-operators) článku [logické operátory logické.](boolean-logical-operators.md)

## <a name="boolean-expressions"></a>Logické výrazy

Typ s `true` definovaným operátorem může být typem výsledku výsledku řídícího podmíněného výrazu v [příkazech if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněném operátoru `?:` ](conditional-operator.md). Další informace naleznete v části [Logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Uživatelem definované podmíněné logické operátory

Pokud typ s `true` definovaným operátorem `false` a operátory určitým způsobem [přetíží](operator-overloading.md) [logický operátor](boolean-logical-operators.md#logical-or-operator-) `|` OR nebo [logický operátor](boolean-logical-operators.md#logical-and-operator-) `&` AND, může být pro operandy tohoto typu vyhodnocen [podmíněný logický operátor](boolean-logical-operators.md#conditional-logical-or-operator-) `||` OR nebo [podmíněný logický operátor](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`AND . Další informace naleznete v části [Uživatelem definované podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Příklad

Následující příklad představuje typ, který `true` `false` definuje oba a operátory. Typ také přetíží logický `&` operátor AND takovým `&&` způsobem, že operátor může být také vyhodnocen pro operandy tohoto typu.

[!code-csharp[true and false operators example](snippets/TrueFalseOperators.cs)]

Všimněte si chování zkratování `&&` operátora. Když `GetFuelLaunchStatus` metoda `LaunchStatus.Red`vrátí , pravý operand `&&` operátoru není vyhodnocen. To proto, že `LaunchStatus.Red` je rozhodně nepravdivé. Výsledek logického operátoru and pak nezávisí na hodnotě pravostranného operandu. Výstup příkladu je následující:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
