---
title: výchozí výrazy hodnot – odkaz jazyka C#
description: Použití výrazů výchozí hodnoty k získání výchozí hodnoty typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507175"
---
# <a name="default-value-expressions-c-reference"></a>výchozí výrazy hodnot (odkaz C#

Výchozí hodnota výrazu vytváří [výchozí hodnotu](../builtin-types/default-values.md) typu. Existují dva druhy výchozích výrazů hodnoty: [volání výchozího operátora](#default-operator) a [výchozí literál](#default-literal).

`default` Klíčové slovo můžete také použít jako výchozí popisek případu v rámci [ `switch` příkazu](../keywords/switch.md).

## <a name="default-operator"></a>default – operátor

Argument pro `default` operátor musí být název typu nebo parametr typu, jak ukazuje následující příklad:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>výchozí literál

Počínaje C# 7.1, můžete `default` použít literál k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu. Výraz `default` literálu vytváří stejnou hodnotu jako výraz, `default(T)` kde `T` je odvozený typ. Literál `default` můžete použít v některém z následujících případů:

- Při přiřazení nebo inicializaci proměnné.
- V deklaraci výchozí hodnoty pro [parametr volitelné metody](../../methods.md#optional-parameters-and-arguments).
- V volání metody poskytnout hodnotu argument.
- V [ `return` příkazu](../keywords/return.md) nebo jako výraz v [členu s výrazem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

Následující příklad ukazuje použití `default` literálu:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Výchozí výrazy hodnot](~/_csharplang/spec/expressions.md#default-value-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o `default` literálu naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Výchozí hodnoty typů jazyka C#](../builtin-types/default-values.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
