---
title: operátory true a false – C# referenční informace
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f65ed3b362080d7a8afe89e22bd132d1fc190b06
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552466"
---
# <a name="true-and-false-operators-c-reference"></a>operátory true a false (C# Referenční dokumentace)

Operátor `true` vrátí hodnotu [bool](../builtin-types/bool.md) `true`, která značí, že jeho operand je jednoznačně true. Operátor `false` vrací hodnotu `bool` `true` k indikaci, že jeho operand je jednoznačně false. Operátory `true` a `false` nezaručují vzájemné doplnění. To znamená, že operátor `true` i `false` může vrátit hodnotu `bool` `false` pro stejný operand. Pokud typ definuje jeden ze dvou operátorů, musí také definovat jiný operátor.

> [!TIP]
> `bool?` typ použijte, pokud potřebujete podporovat logiku se třemi hodnotami (například při práci s databázemi, které podporují logický typ se třemi hodnotami). C#poskytuje operátory`&`a`|`, které podporují logiku se třemi hodnotami s operandy`bool?`. Další informace naleznete v části s [možnou hodnotou null logických operátorů](boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](boolean-logical-operators.md) .

## <a name="boolean-expressions"></a>logické výrazy

Typ s definovaným operátorem `true` může být typ výsledku řídicího podmíněného výrazu v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:`](conditional-operator.md). Další informace naleznete v části [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Podmíněné logické operátory definované uživatelem

Pokud typ s definovanými operátory `true` a `false` [přetěžuje](operator-overloading.md) [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) `|` nebo [logický operátor and](boolean-logical-operators.md#logical-and-operator-) `&` určitým způsobem, [podmíněný logický operátor OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` nebo [ podmíněný logický operátor AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, v uvedeném pořadí, lze vyhodnotit pro operandy daného typu. Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Příklad

Následující příklad představuje typ, který definuje operátory `true` i `false`. Typ také přetěžuje logický operátor AND `&` takovým způsobem, že operátor `&&` lze také vyhodnotit pro operandy daného typu.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Všimněte si chování operátoru `&&` při zkrácení okruhu. Když metoda `GetFuelLaunchStatus` vrátí `LaunchStatus.Red`, není vyhodnocen pravý operand operátoru `&&`. Důvodem je, že `LaunchStatus.Red` je jednoznačně false. Pak výsledek logické hodnoty a není závislý na hodnotě operandu na pravé straně. Výstup příkladu je následující:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
