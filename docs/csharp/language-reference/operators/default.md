---
title: výrazy výchozích hodnot – reference jazyka C#
description: Použití výchozích hodnotových výrazů k získání výchozí hodnoty typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: c07eb8e50dc2ec3413882fa841d2f896b28d2e8d
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556706"
---
# <a name="default-value-expressions-c-reference"></a>výrazy výchozích hodnot (Referenční dokumentace jazyka C#)

Výchozí hodnota výrazu vytvoří [výchozí hodnotu](../builtin-types/default-values.md) typu. Existují dva druhy výchozích hodnot výrazů: [výchozí volání operátoru](#default-operator) a [výchozí literál](#default-literal).

Klíčové slovo se používá také `default` jako výchozí popisek Case v rámci [ `switch` příkazu](../keywords/switch.md).

## <a name="default-operator"></a>default – operátor

Argument `default` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>výchozí literál

Počínaje jazykem C# 7,1 můžete použít `default` literál pro vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu. `default`Literálový výraz vytvoří stejnou hodnotu jako výraz, `default(T)` ve kterém `T` je odvozený typ. Literál můžete použít `default` v některém z následujících případů:

- V přiřazení nebo inicializaci proměnné.
- V deklaraci výchozí hodnoty pro [volitelný parametr metody](../../methods.md#optional-parameters-and-arguments).
- V volání metody pro poskytnutí hodnoty argumentu.
- V [ `return` příkazu](../keywords/return.md) nebo jako výraz v [členu Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

Následující příklad ukazuje použití `default` literálu:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [výchozí hodnoty Expressions](~/_csharplang/spec/expressions.md#default-value-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o `default` literálu naleznete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Výchozí hodnoty typů C#](../builtin-types/default-values.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
