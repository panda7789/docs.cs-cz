---
title: výchozí C# reference operátoru
description: Použití výchozího operátoru k vytvoření výchozí hodnoty typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 744bdf1ec683ef32bba508c260590c0ed4c6e987
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712712"
---
# <a name="default-operator-c-reference"></a>Default – operátorC# (Referenční dokumentace)

Operátor `default` vytváří [výchozí hodnotu](../keywords/default-values-table.md) typu. Argument operátoru `default` musí být název typu nebo parametr typu.

Následující příklad ukazuje použití operátoru `default`:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Klíčové slovo `default` lze také použít jako výchozí popisek Case v rámci [příkazu`switch`](../keywords/switch.md).

## <a name="default-literal"></a>výchozí literál

Počínaje C# 7,1 můžete použít literál `default` k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu. Výraz literálu `default` vytvoří stejnou hodnotu jako výraz `default(T)`, kde `T` je odvozený typ. Literál `default` lze použít v některém z následujících případů:

- V přiřazení nebo inicializaci proměnné.
- V deklaraci výchozí hodnoty pro [volitelný parametr metody](../../methods.md#optional-parameters-and-arguments).
- V volání metody pro poskytnutí hodnoty argumentu.
- V [příkazu`return`](../keywords/return.md) nebo jako výraz v [členu Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

Následující příklad ukazuje použití `default` literálu:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [výchozí hodnoty výrazů](~/_csharplang/spec/expressions.md#default-value-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Další informace o `default` literálu naleznete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Tabulka výchozích hodnot](../keywords/default-values-table.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
