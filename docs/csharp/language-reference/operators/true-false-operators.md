---
description: operátory true a false – Referenční dokumentace jazyka C#
title: operátory true a false – Referenční dokumentace jazyka C#
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f20f71e31c77c035c48702f01208c5b29c90109c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132375"
---
# <a name="true-and-false-operators-c-reference"></a>operátory true a false (Referenční dokumentace jazyka C#)

`true`Operátor vrátí hodnotu [bool](../builtin-types/bool.md) `true` pro indikaci, že jeho operand je jednoznačně true. `false`Operátor vrátí `bool` hodnotu `true` pro indikaci, že jeho operand je jednoznačně false. `true`Operátory and nejsou `false` zaručené doplňují sebe. To znamená, že `true` operátor i `false` může vracet `bool` hodnotu `false` pro stejný operand. Pokud typ definuje jeden ze dvou operátorů, musí také definovat jiný operátor.

> [!TIP]
> Použijte `bool?` typ, pokud potřebujete podporovat logiku se třemi hodnotami (například při práci s databázemi, které podporují logický typ se třemi hodnotami). Jazyk C# poskytuje `&` `|` operátory a, které podporují logiku se třemi hodnotami s `bool?` operandy. Další informace naleznete v části s [možnou hodnotou null logických operátorů](boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](boolean-logical-operators.md) .

## <a name="boolean-expressions"></a>Logické výrazy

Typ s definovaným `true` operátorem může být typ výsledku řídicího podmíněného výrazu v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:` ](conditional-operator.md). Další informace naleznete v části [booleovské výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Podmíněné logické operátory definované uživatelem

Pokud typ s definovanými `true` a `false` operátory [přetěžuje](operator-overloading.md) [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) `|` nebo [logického](boolean-logical-operators.md#logical-and-operator-) operátoru and, `&` lze pro operandy daného typu vyhodnotit [podmíněný logický operátor](boolean-logical-operators.md#conditional-logical-or-operator-) or `||` nebo [podmíněný logický operátor and](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` (v uvedeném pořadí). Další informace naleznete v části [Podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Příklad

Následující příklad představuje typ, který definuje `true` `false` operátory and. Typ také přetěžuje logický operátor AND tak `&` , že `&&` operátor lze také vyhodnotit pro operandy daného typu.

[!code-csharp[true and false operators example](snippets/shared/TrueFalseOperators.cs)]

Všimněte si chování operátoru při krátkém obvodu `&&` . Když se `GetFuelLaunchStatus` Metoda vrátí `LaunchStatus.Red` , není `&&` vyhodnocen pravý operand operátoru. Důvodem je, že `LaunchStatus.Red` je jednoznačně false. Pak výsledek logické hodnoty a není závislý na hodnotě operandu na pravé straně. Výstup příkladu je následující:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
