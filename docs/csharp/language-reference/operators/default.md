---
title: výchozí C# reference operátoru
ms.custom: seodec18
description: Použít výchozí operátor k vytvoření výchozí hodnoty typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804238"
---
# <a name="default-operator-c-reference"></a>Default – operátorC# (Referenční dokumentace)

Operátor vytvoří [výchozí hodnotu typu.](../keywords/default-values-table.md) `default` Argument `default` operátoru musí být název typu nebo parametr typu.

Následující příklad ukazuje použití `default` operátoru:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

`default` Klíčové slovo se používá také jako výchozí popisek Case [ `switch` ](../keywords/switch.md)v rámci příkazu.

## <a name="default-literal"></a>výchozí literál

Počínaje C# 7,1 můžete použít `default` literál k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu. Literálový výraz vytvoří stejnou hodnotu `default(T)` jako výraz, ve kterém `T` je odvozený typ. `default` `default` Literál můžete použít v některém z následujících případů:

- V přiřazení nebo inicializaci proměnné.
- V deklaraci výchozí hodnoty pro volitelný parametr metody.
- V volání metody pro poskytnutí hodnoty argumentu.
- `return` V příkazu nebo jako výraz v členu Expression-těle.

Následující příklad ukazuje použití `default` literálu:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [výchozí hodnoty výrazů](~/_csharplang/spec/expressions.md#default-value-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Další informace o `default` literálu naleznete v poznámkách k [návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Tabulka výchozích hodnot](../keywords/default-values-table.md)
