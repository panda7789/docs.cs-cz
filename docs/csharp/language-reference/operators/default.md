---
title: výchozí C# reference operátoru
description: Použití výchozího operátoru k vytvoření výchozí hodnoty typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 651c4698514aee8cf4dab75ea32c98493e19a30b
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964624"
---
# <a name="default-operator-c-reference"></a>Default – operátorC# (Referenční dokumentace)

Operátor `default` vytváří [výchozí hodnotu](../builtin-types/default-values.md) typu. Argument operátoru `default` musí být název typu nebo parametr typu.

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
- [Výchozí hodnoty C# typů](../builtin-types/default-values.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
