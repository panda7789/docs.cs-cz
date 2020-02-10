---
title: typ bool – C# referenční informace
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 720ece2f7f47961e0ab6ebf03c8afeb5fa3a6271
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093263"
---
# <a name="bool-c-reference"></a>bool (C# Referenční dokumentace)

Klíčové slovo typu `bool` je alias pro typ struktury .NET <xref:System.Boolean?displayProperty=nameWithType>, který představuje logickou hodnotu, která může být buď `true`, nebo `false`.

K provedení logických operací s hodnotami `bool`ho typu použijte logické [logické](../operators/boolean-logical-operators.md) operátory. Typ `bool` je výsledný typ operátoru [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) . Výraz `bool` může být řídicí podmíněný výraz v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:`](../operators/conditional-operator.md).

Výchozí hodnota typu `bool` je `false`.

## <a name="literals"></a>Literály

Můžete použít `true` a `false` literály k inicializaci `bool` proměnné nebo pro předání hodnoty `bool`:

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logická logika se třemi hodnotami

Použijte `bool?` typ s možnou hodnotou null, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují logický typ se třemi hodnotami. Pro operandy `bool?` jsou předdefinované operátory `&` a `|` podporovány v rámci logiky se třemi hodnotami. Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .

Další informace o typech hodnot s možnou hodnotou null naleznete v tématu [typy hodnot s možnou hodnotou null](nullable-value-types.md).

## <a name="conversions"></a>Převody

C#poskytuje pouze dva převody, které zahrnují `bool` typ. Jedná se o implicitní převod na odpovídající typ `bool?` s možnou hodnotou null a explicitní převod z `bool?` typu. Nicméně rozhraní .NET poskytuje další metody, které lze použít pro převod na nebo z `bool`ho typu. Další informace naleznete v části [Převod do a z logických hodnot](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na referenční stránce rozhraní API <xref:System.Boolean?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typ bool](~/_csharplang/spec/types.md#the-bool-type) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Typy hodnot](value-types.md)
- [operátory true a false](../operators/true-false-operators.md)
