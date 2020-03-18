---
title: bool typ - C# odkaz
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846442"
---
# <a name="bool-c-reference"></a>bool (odkaz C#)

Klíčové `bool` slovo typu je alias <xref:System.Boolean?displayProperty=nameWithType> pro typ struktury .NET, který představuje `true` `false`logickou hodnotu, která může být buď nebo .

Chcete-li provádět logické `bool` operace s hodnotami typu, použijte logické operátory [logické hodnoty.](../operators/boolean-logical-operators.md) Typ `bool` je výsledek typ [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) operátory. Výraz `bool` může být řídící podmíněný výraz v [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) statements a v [podmíněném `?:`operátoru ](../operators/conditional-operator.md).

Výchozí hodnota `bool` typu je `false`.

## <a name="literals"></a>Literály

Literály `true` a `false` můžete použít k inicializaci `bool` proměnné `bool` nebo k předání hodnoty:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Trojcenná logická logika

Použijte typ `bool?` s možnou hodnotou null, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují tříhodnotný logický typ. Pro `bool?` operandy předdefinované `&` a `|` operátory podporují logiku se třemi hodnotami. Další informace naleznete v části [Nullable Boolean logické operátory](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) článku [logické operátory logické.](../operators/boolean-logical-operators.md)

Další informace o typech hodnot s možnou hodnotou s možnou hodnotou null naleznete v [tématu Nullable typy hodnot](nullable-value-types.md).

## <a name="conversions"></a>Převody

C# poskytuje pouze dva převody, které zahrnují `bool` typ. Jedná se o implicitní převod `bool?` na odpovídající typ `bool?` s možnou hodnotou null a explicitní převod z typu. Síť .NET však poskytuje další metody, které `bool` můžete použít k převodu na nebo z typu. Další informace naleznete v části [Převod do a z logické hodnoty](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na referenční stránce <xref:System.Boolean?displayProperty=nameWithType> rozhraní API.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Bool typ](~/_csharplang/spec/types.md#the-bool-type) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [true a false – operátory](../operators/true-false-operators.md)
