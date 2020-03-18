---
title: výchozí operátor – odkaz jazyka C#
description: Vytvoření výchozí hodnoty typu pomocí výchozího operátoru
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399481"
---
# <a name="default-operator-c-reference"></a>výchozí operátor (odkaz C# )

Operátor `default` vytvoří [výchozí hodnotu](../builtin-types/default-values.md) typu. Argument pro `default` operátor musí být název typu nebo parametr typu.

Následující příklad ukazuje použití `default` operátoru:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

`default` Klíčové slovo můžete také použít jako výchozí popisek případu v rámci [ `switch` příkazu](../keywords/switch.md).

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
